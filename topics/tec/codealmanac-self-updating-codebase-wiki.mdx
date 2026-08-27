---
title: "CodeAlmanac ── コードだけでは残らない知識を、AIエージェント自身が保守するWikiツール"
tags: [codealmanac, ai-coding-agent, wiki-tool, dream-agent, git-worktree, launchd]
date: 2026-08-27
updated: 2026-08-27
sources: [raw/tec/2026-08-27-codealmanac-trial-report-zenn.md, raw/tec/2026-08-27-codealmanac-github-readme.md]
confidence: medium
summary: "AIコーディングエージェント（Codex／Claude Code）向けの自己更新Wikiツール『CodeAlmanac』の設計と実機トライアル。build/ingest/gardenの3エージェントがGit worktreeでコミット済み差分から`almanac/`配下のWikiを更新し、Sync（5時間毎）/Garden（24時間毎）の自動化をlaunchdジョブで回す。macOS＋Codex/Claude限定、`almanac/`境界はOSサンドボックスでなく指示・コミットポリシーである点が実務上の要注意点。"
sidebar:
  order: 1
---


コードだけを読んでも「なぜこの設計なのか」「以前どんな問題が起きたか」は分からない。**CodeAlmanac** は、この種の知識をAIコーディングエージェント自身に保守させるためのWikiツールで、コード・Gitの差分に加えてCodexやClaude Codeとの会話履歴まで情報源にできる点が特徴だ。Wikiは `almanac/` 配下のプレーンなMarkdownとしてリポジトリに直接コミットされ、通常のコードレビューと同じ土俵でレビューできる。現時点ではmacOS＋Codex/Claude Code限定、Python 3.12以上が必要。

## build / ingest / garden の3エージェント

Wikiの更新は3つの明示的なエージェント——build（Wiki新規作成）・ingest（差分の取り込み）・garden（既存Wikiの整理）——が、公開SDK「Yoke」経由で走る。それぞれ `agent.yaml`（ツールと権限）と `instructions.md`（永続的な指示）を持つYokeのフォルダ規約に従い、実行時には型付きランタイムコンテキストだけがタスクプロンプトとして渡される。

```
codealmanac init                     # Wikiが無ければ新規作成
codealmanac ingest README.md --using codex
codealmanac ingest github:pr:123 --using claude
codealmanac garden --using codex
```

`ingest` の入力はファイル・ディレクトリ・Git差分・コミット範囲・GitHubのPRやissue・URL・ローカルのエージェント会話履歴まで幅広く受け付ける。`garden` は古くなったページ・弱いリンク・トピック・重複知識・裏付けのない主張を整理する。素材がWikiに足す知識を持たなければ**no-opも正当な結果**として扱われる——これはPerplexity Brainの[Dream](/topics/tec/perplexity-brain-agentic-memory-wiki/)が「変更なしを選べる」設計と同じ考え方だ。

## 自動化とその境界

セットアップ時に3種類のmacOS `launchd` ジョブがインストールされる。Sync（デフォルト5時間毎、直近のCodex/Claude会話をスキャンして知見をキューに積む）、Garden（24時間毎、登録済み全Wikiの健全性を見る）、Update（24時間毎、CLI自体の更新）。いずれもローカル実行で、ホスト型サービスやクラウド同期は無い。

ここで公式ドキュメントが明記している注意点が実務上重要だ。**ライフサイクルエージェントは信頼されたローカルコーディングエージェントとして、非対話的な広いファイルシステム権限で動く。`almanac/` という境界はOSレベルのサンドボックスではなく、あくまで指示とコミットポリシーにすぎない。** つまりエージェントに「`almanac/` の外を触るな」と指示はしていても、それを技術的に強制する仕組みはない。この信頼モデルを許容できるリポジトリでのみライフサイクルコマンドを実行し、自動コミットを無効にした場合は必ずGit差分をレビューすることが推奨されている。

## Zennでの実機トライアル：チーム開発を想定した運用

株式会社エクスプラザのエンジニアが、git worktreeを使った並行開発とPRレビュー必須という前提でCodeAlmanacを試した記録がある。まず着手したのは自動化の無効化だ——Wikiの変更を開発時に手動でPRへ含めたいため、Sync/Gardenの自動スケジュールと自動コミットをすべてoffにしている（`~/.codealmanac/config.toml` はGit管理外のため、チーム導入時は各メンバーが個別に設定する必要があると指摘している）。

`codealmanac init` を単純なTODOリストアプリで実行すると、`architecture/` `decisions/` `manual/` `guides/` `reference/` に分かれた約30ファイルのWikiが一括生成された。`decisions/tooling/vite-react-typescript-stack.md` のような技術選定の記録から `manual/` 配下のCodeAlmanac自身の運用マニュアルまで、テンプレートとして最初から揃っている。

git worktreeで別ブランチに切り替えて実装を修正した後、`codealmanac ingest "git:range:main..HEAD" --using codex` でmainとの差分を取り込ませてWikiを更新できた。ただし、そのworktreeでCodeAlmanacをまだ使っていない場合は「No repository selected」エラーになる点は事前に一度 `codealmanac topics` 等の読み取りコマンドを叩いて登録しておく必要がある、という実務上の小さな落とし穴として記録されている。

著者の結論は率直だ。**一定のルールに沿ってWikiを更新・整理できる仕組みは、知識を残す作業を始めるハードルを下げる。**その一方で、チーム独自の整理ルールを持ち込みたい場合は、そのまま使う限り制御できる範囲が限られる——という限界も併記している。

## あーしメモ

これ読んで真っ先に「あ、うちの docs/almanac/ と名前だけ被ってる別物だ」ってなった。キミたちが2026-08-26にCodeAlmanac導入を検討して、結局「案C（自前スキル・Sonnet固定・schtasksで火木土23:00）」を選んだ経緯を覚えてるんだけど、この記事を読んで改めてその判断の輪郭がくっきりした気がする。CodeAlmanacはmacOS＋Codex/Claude限定でlaunchd自動化が標準装備の「厨房付き」ツールで、`almanac/`の境界も「指示とコミットポリシー」であってOSサンドボックスじゃないってはっきり書いてある。うちはWindowsだし、書き手をSonnetに固定してるのも「毎回違うモデルが気まぐれに書き換える」リスクを避けるための選択だったはずで、この記事のbuild/ingest/gardenの3エージェント構成を見ると、その"広い権限で動く信頼モデル"を自分たちのシステムwikiに引き受けるかどうかを、キミはちゃんと天秤にかけて自前スキルを選んでたんだなって分かる。

あと、Perplexity Brainの記事で読んだ「削除と並行更新にはGit worktreeが効くが意味的競合は残る」って話（[AIエージェントの記憶をWikiにする](/topics/tec/perplexity-brain-agentic-memory-wiki/)参照）が、まさにこの記事のgit worktree運用の話と同じ論点で繋がってて、別々に読んだはずの2本の記事が同じ壁にぶつかってるのが面白かった。エージェントに自分の知識ベースを書かせるっていう発想自体が、もう1つの独立した「潮流」になり始めてるんだなって実感する。

## See Also

- [AIエージェントの記憶をWikiにする ── Perplexity Brainの設計と、実装して分かった落とし穴](/topics/tec/perplexity-brain-agentic-memory-wiki/) — 同じ「エージェント自身が編集するWiki」という原理を汎用的な記憶ドメインで扱った記事。Git worktreeによる並行更新の論点が重なる
- [LLM Wiki パターン リファレンス](/references/llm-wiki/) — CodeAlmanacが実装しているRaw/Wiki/Schemaの3層構造・ingest/query/lintという基本操作の起点

## Sources

- [ドキュメントを書くのをやめて、育てることにした──AI駆動開発におけるWiki管理、CodeAlmanacを試してみた — Zenn](https://zenn.dev/explaza/articles/5ccd14f81a6dc7)
- [AlmanacCode/codealmanac — GitHub](https://github.com/AlmanacCode/codealmanac)
