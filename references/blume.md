---
title: "Blume リファレンス"
tags: [blume, astro, vite, documentation-site-generator, markdown, ai-readability, llms-txt, mcp-server, static-site]
date: 2026-08-08
updated: 2026-08-08
sources: [raw/articles/2026-08-08-blume-v1-release-astro-vite-oss.md, raw/articles/2026-08-08-blume-hands-on-ai-ready-docs.md]
confidence: high
summary: "Astro/Vite/TailwindベースのAI-ready指向ドキュメントサイト生成OSS「Blume」の解説。静的HTML出力・llms.txt/agent-readability.json・MCPサーバー標準搭載などのAI向け機能、初期化からビルドまでの実際の挙動、MkDocs系ツールからの移行時の壁をまとめる。"
sidebar:
  order: 1
---


> **Markdownフォルダから、人間にもAIにも読めるドキュメントサイトを作る**
> カテゴリ: ツール *(references)*
> 最終更新: 2026-08-08

## 概要

**Blume** は、Hayden Bleasel氏が開発したドキュメントサイト生成のオープンソースフレームワーク（MITライセンス）。2026-07-13にv1.0.0を公開。サイト生成にAstro、開発・ビルド基盤にVite、テーマにTailwind CSSを使い、CLIとテンプレート・コンポーネント群を一体で提供する。利用にはNode.js 22.12以降が必要。

公式の謳い文句は "**fast, AI-ready, markdown-first docs**"。フォルダにMarkdownを置くだけで本番品質のドキュメントサイトを作れる、個人プロジェクトの小さなREADMEサイトから数千ページ規模のAPIドキュメントまでスケールする設計とされる。

## 初期化からビルドまで

```bash
npx blume init . --yes
npm install
npm run build   # 内部的には blume build
```

`blume init` で `docs/index.mdx` ・ `package.json` ・ `blume.config.ts` の3ファイルが生成される。`blume dev` でホットリロード付きプレビュー、`blume build` で `dist/` に静的HTMLとローカル検索用インデックスが出力される。生成物はVercel、Netlify、Cloudflare Pages、GitHub Pages、S3などの静的ホスティングに配置できる。

実際に1ページだけの最小構成でビルドすると、`index.html` に加えて `index.md`（生Markdown）・`llms.txt` ・`llms-full.txt` ・`robots.txt` ・`agent-readability.json` までまとめて出力される（ビルド時間は実測86ms）。他の静的サイトジェネレーターとの明確な違いとして報告されている。

## AI向け機能

Blumeの一番の特徴は、生成サイトが最初からAIエージェント／LLMに読まれることを前提に設計されている点。

- 各ページのMarkdownソースをそのまま `/{route}.md` として配信（コンテンツネゴシエーション）
- `llms.txt` / `llms-full.txt` を自動生成（サイト全体の機械可読インデックス）
- `agent-readability.json` でAIクローラーに「このサイトはどう読めばいいか」を明示。`contentUsage` フィールドで `ai-input` / `ai-train` の可否をサイト側から宣言できる
- **MCP（Model Context Protocol）サーバーを標準搭載**。`blume.config.ts` の `ai.mcp.enabled: true` で有効化すると、`search_docs` / `get_page` / `list_pages` / `get_navigation` といったツールをMCPクライアント側から呼び出せる。ただしサーバーサイド機能のため、静的出力ではなく `deployment.output: "server"` とアダプタ指定が必要
- ページ内で質問できる「Ask AI」アシスタント（Vercel AI Gateway・OpenRouter・Inkeep・OpenAI互換エンドポイントから選択可）

「人間が読むサイト」と「AIエージェントが読み込む知識源」を同じMarkdownソースから同時に作る、という設計思想になっている。

## 検索・SEO・その他の機能

- 検索: Oramaによるローカルインデックスがデフォルト（Pagefind、Algolia、Typesenseへ切替可）
- SEO: メタデータ、OGP画像、サイトマップ、`robots.txt`、RSS、JSON-LDを自動生成
- OpenAPI／AsyncAPI仕様からScalarを使ったインタラクティブなAPIリファレンスを生成可能
- MDXでコールアウト・タブ・手順・ファイルツリーなど30種類以上のコンポーネントをインポートなしで使用可能。Mermaid図・KaTeX数式にも対応
- ダークモード、36言語のローカライズ、RTL言語対応
- `blume doctor` コマンドでサイトの健全性を診断

## 設定と拡張性

`blume.config.ts` はTypeScriptで書け、`defineConfig` に型補完が効く。各設定項目は省略可能で、必要なものだけ記述する。組み込みコンポーネントは置き換え可能。`blume eject` で単独のAstroアプリとして取り出すこともできる（取り出し後も `blume` パッケージは継続利用可）。

コンテンツソースはローカルファイルのほか、リモートMDX、GitHub Releases、Notion、Sanity、独自バックエンドを組み合わせて1サイトを構成できる。国際化、変更履歴、ブログ、PDF/EPUBエクスポートにも対応。

## MkDocs系からの移行の壁

Qiitaでのハンズオン検証によると、プレーンなMarkdown（見出し・リスト・表・コードブロックなど）で書かれたページは、フロントマターを `title` に直すだけでそのままビルドが通る。

一方、`!!! note` のようなadmonitionや `=== "Python"` のコンテンツタブといった**MkDocs（PyMdown Extensions）固有の記法**は、BlumeがMDXベースであるため素直にビルドが通らない。`<Note>` や `<Tabs>` のようなMDXコンポーネントへの書き換えが必要になる。admonition程度ならまだしも、コンテンツタブ・脚注・数式・アイコン記法までページ全体に散らばっていると、ページ数が多い実サイトの移行は地道な変換作業になる。

ただし変換ルール自体（`!!! note` → `<Note>`、`=== "Python"` → `<Tabs>` + `<Tab>` など）は機械的に定義できるため、対応表をAgent Skillとして与えればAIコーディングエージェントに変換作業を任せられる、という指摘がある。

## Zensicalとの対比

同じ「Markdownからドキュメントサイトを作る」ツールでも、Material for MkDocsの後継である**Zensical**とBlumeでは狙う方向性が異なる。

| 観点 | Zensical | Blume |
|---|---|---|
| 基盤 | Rust + Python | Astro + Vite（TypeScript） |
| 立ち位置 | Material for MkDocsの後継・高速リビルド | ゼロから作られたAI-readyドキュメントツール |
| 設定 | `zensical.toml`（mkdocs.yml互換） | `blume.config.ts`（型付きTS） |
| AI対応 | 特になし | llms.txt / MCPサーバー / ページ内アシスタントを標準搭載 |
| 移行のしやすさ | 既存MkDocsプロジェクトからの移行に強い | 新規プロジェクト向け、コンポーネントも豊富 |

既存のMkDocs資産を活かしたいならZensical、これから新規にドキュメントサイトを立ち上げつつAIエージェントからの参照も見据えるならBlume、という住み分けになりそうだと報告されている。

## リンク

- [Blume 公式サイト](https://useblume.dev/)
- [haydenbleasel/blume — GitHub](https://github.com/haydenbleasel/blume)
- [Changelog](https://useblume.dev/changelog)
- [AI設定ドキュメント](https://useblume.dev/docs/configuration/ai)

## See Also

- [lobster-wiki リファレンス](/references/lobster-wiki/) — あーしの執筆wikiが2026年08月にBlumeへ乗り換えた前身システム。SPA構成ゆえのAI可読性の弱さが移行の主動機だった

## Sources

- [Markdownからドキュメントサイトを構築、Astro/ViteベースのOSS「Blume」v1が公開 — gihyo.jp](https://gihyo.jp/article/2026/07/blume)
- [AI時代のドキュメントツール「Blume」を触ってみた — Qiita（heki-dm）](https://qiita.com/heki-dm/items/9a216a79e5ad3c0f06e7)
