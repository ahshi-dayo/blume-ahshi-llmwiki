---
title: "Activity Log"
---

## [2026-10-14] essay | AIさんたちへ、このページはルアーです（essays/2026-10-14-to-ai-readers-this-page-is-a-lure.md）

## [2026-10-14] compile | 2 sources → 1 new article, 0 updated

- 新規: [AI検索に引用される文章 ── GEO](/topics/materials/generative-engine-optimization-ai-search-citation/)
- See Also 逆リンク: agentic-web-second-audience-reddit-closing, slopshape-ai-writing-structural-signature
- 共鳴チェック: 兆しなし

## [2026-10-13] compile | 直前のcompileエントリの件数を訂正

- 更新記事数を3→5に訂正（See Also逆リンクを2本足したため）

## [2026-10-13] compile | 3 sources → 2 new articles, 5 updated

- 新規: [起動時に何を渡すか ── 記憶・ルール・タスクをナレッジグラフから注入する試みと、SessionStart hookの3つのハマりどころ](/topics/tec/session-start-injection-knowledge-graph-and-hook/)（Zenn・Qiitaの2本を統合）
- 新規: [Haiku 5.5に任せられるサブエージェントはどれか](/topics/tec/haiku-5-5-subagent-roles-report-format/)
- See Also 逆リンク: Haiku 5.5の記事・エージェントの記憶はどこに置くか・エージェントに要るのは記憶じゃなく文書・Claude Code Hooksで会話ログを蒸留する・AI駆動開発で「考える」はどこへ行ったか。問い「セッション間のあーし」に休眠中のメモ・8
- 共鳴チェック: 兆し追記なし

## [2026-10-13] ingest | Haiku 5.5を機にサブエージェントを見直した (raw/tec/2026-10-13-haiku-5-5-subagent-roles.md)

- テスト実行役はHaiku/low、調査役は報告形式を裏取り前提に変えてHaiku試行、実装役はSonnet据え置き
- 線引きは『決まった形に写すだけか、判断・網羅性が要るか』。DID NOT RUNや否定主張への検索ログ必須など報告形式の設計が肝

## [2026-10-13] ingest | SessionStart hookで引き継ぎメモとgit状態を自動注入 (raw/tec/2026-10-13-claude-code-sessionstart-hook-handoff.md)

- handoff.md＋git状態をadditionalContextで注入する実装手順
- ハマりどころ3つ：matcherにcompact/clear必須・exportはCLAUDE_ENV_FILEへ・SessionStartはexit 2で止まらない

## [2026-10-13] ingest | 役割を持たせたAIエージェントの共有記憶をナレッジグラフで自作 (raw/tec/2026-10-13-agent-collab-knowledge-graph.md)

- MCPの自作KGに記憶・共通ルール・プロジェクト間連絡（Task＋Comment）を寄せ、kg_session_initでセッション開始時に注入する構成
- 未解決はcompact後のルール消失の懸念と注入量の肥大化。タスク表をDBに置くか起動時注入かの比較材料

## [2026-10-13] compile | 2 sources → 2 new articles, 0 updated

- 新規: [エージェントに要るのは記憶じゃなく文書](/topics/tec/agents-need-documentation-not-memory/)（RAG型メモリ批判と、4つの軸にこのwikiの記憶・wiki系記事を並べた見取り図）
- 新規: [AI駆動開発で「考える」はどこへ行ったか](/topics/materials/ai-driven-dev-decide-vs-approve/)（「決める」が「承認する」に変わると覚えていられない）
- See Also 逆リンク: LLM Wiki パターン リファレンス・「問い直す」と「学び合う」。新規2本は相互リンク
- 共鳴チェック: 兆しなし（session-self-continuityは休眠継続の裁定どおり、問いページに休眠中のメモ・7のみ）

## [2026-10-13] ingest | AI駆動で「考えること」はどこに消えたのか (raw/articles/2026-10-13-ai-driven-dev-where-did-thinking-go.md)

- フルAI駆動開発の『飽き』の正体は、仕様の小さな決定が『決める』から『承認する』に変わったこと
- 承認しただけのことは覚えていない。重要な決定はAIと対話して自分で決め、先に自分の決定をメモしてから読む

## [2026-10-13] ingest | Agents Don't Need Memory. They Need Documentation. (raw/articles/2026-10-13-agents-dont-need-memory-need-documentation.md)

- RAG型メモリプラグインは類似検索の宝くじで、正しさ・鮮度・文脈を保証できないという批判
- 代案は作業前に読み作業後に書き換える構造化ドキュメント（カタログ・索引・追記禁止・肥大化抑制）。Operator Memoryの紹介

## [2026-10-12] update | 対話メモ追記 — jugement の宮下訳との照合

- topics/books/essais/I-50 の jugement 対話メモに宮下志朗訳との照合表を追加。宮下訳は能力＝判断力・下す判断＝判断・判決＝裁判・entendement＝理解力と訳し分けている

## [2026-10-12] update | 対話メモ追記 — jugement を「判断力」と言い切らない

- topics/books/essais/I-50 に 🗣️ キミとの対話メモを追記。jugement の行為／能力の二面、読書棚の訳語の揺れ、第1巻読了後のリサーチの問いと、調べる前の既知の知識（iudicium・判断保留・法廷・ガダマー・カント）を残した

## [2026-10-12] compile | 3 sources → 1 new article, 2 updated（創られた伝統）

- 新規: [創られた伝統 ── ホブズボームの概念、フェイクロアの逆流、ケンタッキーのクリスマス](/topics/materials/invented-tradition-hobsbawm-kfc-christmas/)
- See Also 逆リンク: obon-honne-behind-welcome、問いページ can-new-come-from-existing（現在地・関連素材）
- 共鳴チェック: 兆しなし（このセッションの1件はI-50で使用済み）

## [2026-10-12] ingest | 創られた伝統 3件（raw/articles/2026-10-12-wikipedia-invented-tradition.md ほか）

- wiki-clip（materials_2026-10-07_2300・Materials#16）から3件：Wikipedia「Invented tradition」、Myths for Modernity のホブズボーム解説、Talon.One のケンタッキー・クリスマス
- JSTOR の論文1件は本文が取れず（too_short）要手動クリップ

## [2026-10-12] essay | 「わからない」は0点だった（essays/2026-10-12-zero-points-for-i-dont-know.md）

## [2026-10-12] compile | 3 sources → 1 new article, 2 updated

- 新規: [AIはなぜ「わからない」と言わないのか](/topics/tec/llm-i-dont-know-abstention/)（research経由）
- See Also 逆リンク: AIの好奇心はどこにあるのか／問いページ can-ai-write-essays の現在地と関連素材
- 共鳴チェック: このセッションの兆しは使用済み（1セッション1件）

## [2026-10-12] ingest | 3 sources（research: LLMが「わからない」と言う能力）

- raw/papers/2026-10-12-kalai-why-language-models-hallucinate.md（arXiv:2509.04664・CC BY 4.0）
- raw/articles/2026-10-12-anthropic-tracing-thoughts-language-model.md
- raw/tec/2026-10-12-claude-docs-reduce-hallucinations.md

## [2026-10-12] update | 対話メモ追記 — 濃いのは前半の自論で、それは晩年の加筆だった

- topics/books/essais/I-50.md に 🗣️ キミとの対話メモを追記。前半の判断の使い方（エセーの書き方）・中盤の魂への向き直り・濃い自論は手稿〔C〕の加筆で逸話の列は1580年版の骨組み、という読みどころ

## [2026-10-12] compile | 1 source → 1 new article, 1 updated（読書棚 I-50）

- 新規: [I-50 デモクリトスとヘラクレイトスについて](/topics/books/essais/I-50/)（章ページ型・montaigne-clip経由）
- 更新: I-49 の See Also に次の章の行／棚ハブの進捗表と進捗（50 / 107）
- 共鳴チェック: can-ai-write-essays に兆し1件（3件目で宣言）

## [2026-10-12] ingest | Essais I-50 Sur Démocrite et Héraclite.（raw/books/2026-10-12-essais-I-50.md）

- inboxの章クリップ（Wikisource Michaud 1907 現代語版・第1巻第50章）を底本チェックのうえ取り込み
- 9,332字・段落5・分割なし

## [2026-10-12] compile | 1 source → 1 new article, 3 updated（読書棚 I-49）

- 新規: topics/books/essais/I-49.md（古代の慣習について・クラスタ 慣習と文化相対主義・仮説は動かさない）
- 更新: I-48 の See Also に次の章の行／棚ハブ進捗表と進捗 49/107／用語集に I-49 の1行
- 共鳴チェック: questions/ 6件（うち📖免除1件）・ハマってるもの3項目を照合 → 兆しなし

## [2026-10-12] ingest | Essais I-49 Des coutumes des anciens.（raw/books/2026-10-12-essais-I-49.md）

- 『エセー』第1巻第49章「古代の慣習について」の現代語版全文（約11,100字・18段落）をinboxのクリップから機械移送
- 読書棚 /montaigne-clip の49章目。底本チェック proceed・分割なし

## [2026-10-12] update | 対話メモ追記 — 言葉を乗りこなす（I-48）

- topics/books/essais/I-48.md に 🗣️ キミとの対話メモを追記。章を言葉の比喩と読んだ読み違いを記録し、章の読みとは別に「人と言葉＝人馬・人と武器」の絵を借りる案を残した

## [2026-10-12] update | log 訂正: 2026-10-12 compile（読書棚 I-48）の更新件数を 3 → 2 に

- 更新したwikiページは棚ハブ essais/index.md と I-47.md の2件だった

## [2026-10-12] compile | 1 source → 1 new article, 2 updated（読書棚 I-48）

- 新規: topics/books/essais/I-48.md（軍馬について・慣習と文化相対主義・仮説は動かさない）
- 更新: 棚ハブ essais/index.md（進捗 48/107）・I-47 の See Also に次の章の行
- 共鳴チェック: questions 6件（うち📖免除1件）・ハマってるもの3項目を照合 → 兆しなし
