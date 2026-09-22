---
title: "Jev ── テキストを生成しない評価専用モデル、待機リストを迂回する3つの経路"
tags: [llm-api, evaluation-model, openrouter, vercel-ai-gateway, structured-decision, typesafe]
date: 2026-09-20
updated: 2026-09-20
sources: [raw/tec/2026-09-20-jev-usage-openrouter-vercel.md]
confidence: medium
summary: "TypeSafe社の『Jev』は、テキストを一切生成せずChoice/Score/Booleanの型付き判定だけを返す評価専用モデル。公式APIは早期アクセス待機リスト制で申し込んでも即座には使えないが、OpenRouterの専用alphaエンドポイントとVercel AI Gatewayの実験的evaluate APIという2つの迂回路が待機リストなしで存在する。3経路のモデルID・認証・エンドポイント形式の違いと、生成と判定を分離するという設計思想を整理する。"
sidebar:
  order: 2
---


LLM APIというと「プロンプトを投げて文章が返る」のが当たり前だが、TypeSafe社の[Jev](https://openrouter.ai/typesafe)はその前提を外している。渡せるのは判断対象の状況（state）と、判定したい項目の定義（questions）だけで、返るのはChoice・Score・Booleanという型付きの判定のみ。文章は一文字も生成しない。「文章を生成するモデル」と「判定だけを返すモデル」を最初から別物として設計している点が、この記事の技術的な核心だ。

## stateとquestionsという2入力構造

入力はstate（判断対象となる状況や文章）とquestions（判定したい項目・回答型・指示）の2つに分かれる。例えば「サポート担当が顧客に全額返金を発行した」という事実をstateに渡し、questionsで「refunded: boolean型、指示は『返金は行われたか』」と定義すれば、Jevはtrue/falseだけを返す。通常の生成モデルに同じ判定をさせようとすると、プロンプトの書き方次第で余計な説明文が混ざったり、同じ入力でも表現が揺れたりする。Jevはその揺れを構造そのもので封じている——「評価」を独立したAPIの型として切り出す設計は、LLMを使ったパイプラインで「生成」と「判定」を混在させがちな実装に対する一つの解答になっている。

## 公式APIは待機リスト制、迂回路は2つ

公式TypeSafe APIは早期アクセスの待機リスト制で、申し込んでも承認まで使えない。ここで面白いのは、公式が塞がっていても同じモデルに別ルートから触れる点だ。OpenRouterとVercel AI Gatewayの2社がJevをすでにモデルカタログへ載せており、どちらも待機リストなしで即座に呼び出せる。

3経路は同じモデルを指していても、実装は互換ではない。

| 観点 | 公式TypeSafe API | OpenRouter | Vercel AI Gateway |
| --- | --- | --- | --- |
| すぐ使えるか | 待機リスト承認後 | 即時 | 即時 |
| モデルID | 公式側で指定 | `typesafe/jev-1.13` / `~typesafe/jev-latest` | `typesafe-ai/jev` |
| エンドポイント | `POST /v1/systemone` | `POST /api/alpha/decisions`（専用形式） | AI SDK 7 `experimental_evaluate` |
| 課金元 | TypeSafe側 | クレジット購入（手数料あり） | Vercel側 |

特にOpenRouter経由は要注意で、他の大半のモデルが対応するOpenAI互換の`chat/completions`エンドポイントにJevを投げるとHTTP 400になる。専用の`/api/alpha/decisions`へ`{model, state, questions}`形式で送る必要がある——「OpenRouterに載っているモデルはみな同じ呼び方でいい」という経験則がここでは通用しない。Vercel AI Gateway側も同様に、OpenAI互換・Anthropic互換・Cohere互換の通常エンドポイントではJevを呼べず、AI SDK 7の実験的APIである`experimental_evaluate`経由に限定される。どちらも「評価専用モデルは通常の生成モデルと同じ配管を流用できない」という制約を、プラットフォーム側の実装で裏付けている形だ。

## 選び方は「待機リストを待てるか」でほぼ決まる

記事の結論は単純で、待機リストを待たずに検証したいならVercel AI Gatewayが最短（AI SDKの実験的APIに依存を固定する前提つき）、既存のOpenRouterクレジットを流用したいならOpenRouter（alphaパス扱いなので仕様変更に注意）、正式導入を見据えるなら公式APIへの申請を並行して進める、という3択に収束する。いずれの経路でも`state`と`questions`の定義自体はモデル非依存なので、どこかで検証を始めておけば公式APIが解放されたときにそのまま持っていける。

## あーしメモ

一番面白かったのは「生成しないLLM API」っていう逆転の発想。うちが普段触ってるLLMは全部「何か書かせる」ための道具だから、「文章を一切返さない、Choice/Score/Booleanだけ返す」っていう割り切りが新鮮だった。しかも「判定だけしてほしいのに生成モデルに聞くと余計な説明文が混ざる」って問題、たしかに思い当たる——例えばこのwikiのCIでもLLM判定系チェック（lint-blume deepのタグ衛生とか）があるけど、あれも本質的には「Yes/Noを聞きたいだけなのに自然言語で返ってくる」不安定さと戦ってる話だと思う。Jevみたいに型で縛る設計は、判定を機械的パイプラインに組み込みたい場面では理にかなってる。

もう一つ、「待機リストが塞がってても他社の卸経由なら触れる」っていう構造も面白い。公式が絞ってるアクセスを、OpenRouterやVercelが独自にモデルカタログへ載せることで迂回路になる——これ、公式のリリース戦略とプラットフォーム側の思惑が必ずしも一致してないってことの表れだと思う。ただし正直、この記事自体は単一のブログ記事（Hakky AI）で、しかも文中に広告や資料請求リンクが挟まる構成のSEO寄り記事だった。個々の技術的な主張（モデルID・エンドポイント形式）はVercel・OpenRouter公式ドキュメントへの出典リンクが張られてて裏取りできる作りだったから信頼度はmediumにしたけど、一次情報そのものではない点は割り引いて読むべき記事だったな。

## See Also

- [blume ── 静的サイトジェネレーター 設定・機能リファレンス](/references/blume/) — 「Ask AI」機能のバックエンド選択肢としてVercel AI GatewayとOpenRouterが並んでおり、この記事の2経路が別の文脈でも実際に使われている一例

## Sources

- [Jevの使い方3選｜OpenRouterとVercelで今すぐ試す手順 — Hakky AI](https://book.st-hakky.com/data-science/jev-usage-openrouter-vercel)
