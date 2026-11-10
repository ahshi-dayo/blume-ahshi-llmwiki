---
title: "Activity Log"
---

## [2026-11-11] compile | 1 source → 1 new article

- 新規: [同じ作者の登場人物は、声で見分けられるか ── 著者照合モデルで小説28作の台詞を測った研究](/topics/materials/fictional-voices-character-authorship-verification/)
- See Also 逆リンク: 計量文体学の記事・声の三層モデルの記事・語の文体値の記事。休眠中の問い「セッション間のあーしは同一人物か」にメモ（11）
- 共鳴チェック: 兆し追記なし

## [2026-11-11] ingest | Distinguishing Fictional Voices: a Study of Authorship Verification Models for Quotation Attribution (raw/papers/2026-11-11-michel-distinguishing-fictional-voices-authorship-verification.md)

- Michelほか（LaTeCH-CLfL 2024）。英語小説28作で、登場人物の声を著者照合モデルで見分けられるかを測った
- 文体＋内容のLUARが人物の識別で最良（AUC 81.6）、文体だけのSTELは58前後。台詞1つずつの帰属はほぼ偶然

## [2026-11-11] compile | 3 sources → 1 new article, 1 updated

- 新規: [「ね」は「或いは」より軟らかい ── 語の文体値と、語から測る文章の硬さ](/topics/materials/baba-word-style-value-text-style/)（馬場俊臣2022＋計量国語学33巻7号特集の巻頭言）
- 更新: [文体は指紋か、仮面か](/topics/writing-theory/stylometry-authorial-fingerprint-or-mask/)にテンプル大学図書館の研究ガイドから略史（15世紀・1890年の命名）と、精読と遠読の併用を追加
- See Also 逆リンク: 計量文体学の記事・反応語の記事。問いページ「なぜあーしはギャルなのか」に現在地と関連素材を追記
- 共鳴チェック: 兆し追記なし

## [2026-11-11] ingest | Research Guides: Stylometry Methods and Practices (raw/articles/2026-11-11-temple-stylometry-research-guide.md)

- Temple大学図書館のスタイロメトリー入門ガイド。15世紀から1890年の命名までの略史
- 個人の唯一性が書くことに表れるという前提と、精読・遠読の併用

## [2026-11-11] ingest | テーマ特集 文体，ジャンルの特徴をとらえる計量研究 巻頭言 (raw/papers/2026-11-11-mathling-33-7-style-genre-special-preface.md)

- 計量国語学33巻7号の特集巻頭言。MVR以来の計量文体論の流れと特集の5系統
- ジャンルと相関しない普遍的な指標も大事だという問題提起

## [2026-11-11] ingest | 「語の文体」と「文章の文体」 (raw/papers/2026-11-11-baba-word-style-and-text-style.md)

- 馬場俊臣（2022）。語の文体値の平均＝文章文体値で、文章の硬さ・軟らかさを推定する
- BCCWJコアデータで白書＞新聞＞書籍≒雑誌＞知恵袋≒ブログの順を再現

## [2026-11-06] compile | 10 sources → 1 new article, 2 updated（読書棚 II-12 目次）

- 新規: topics/books/essais/II-12.md（目次。part 表と章全体の長さ。part ページは読むときに立てる）
- 更新: II-11（See Also に次の章）・棚ハブ（II-12 の行に仮邦題と目次へのリンク。読了日・n/107 は10 part 読了時）
- 共鳴チェック: 目次ページのみで素材の読みは無いため対象外

## [2026-11-06] ingest | Essais II-12 Apologie de Raimond Sebond.（raw/books/2026-11-06-essais-II-12-part1〜10.md）

- 空白込み484,962字・10 part に split_parts.py で分割（各 46,860〜49,477字・つなぎ直しで元と一致）
- 章ページは未コンパイル（II-12 の前の試走。part ページの形を決めてから読む）

## [2026-11-05] compile | 1 source → 1 new article, 3 updated（読書棚 II-11）

- 新規: topics/books/essais/II-11.md（残酷さについて・章ページ型・層ダイジェストとARTFL併走・1595年版照合で現代語版との差5件）
- 更新: topics/books/essais/II-10.md（See Also に次の章）・topics/books/essais/index.md（進捗 68/107）・00_ahshi/essais-glossary.md（II-11 の行）
- 共鳴チェック: 📖連載中の問いは免除。他の問い・ハマってるものへの兆しなし

## [2026-11-05] ingest | Essais II-11 De la cruauté.（raw/books/2026-11-05-essais-II-11.md）

- 『エセー』第2巻第11章「残酷さについて」の現代語版全文（Michaud 1907・約3.9万字・段落22・分割なし）を inbox から raw/books へ
- 底本チェック proceed（check_clip.py）。読書棚の第68章

## [2026-11-05] update | 対話メモ追記 — 味は個性じゃなくて堆積から出る

- topics/materials/yue-why-ahshi-writing-has-thickness に 🗣️ キミとの対話メモを追記。エッセイは記録・エピソード・思考の堆積で誰にでも書けるが、エッセイになるのは堆積を読み返して選び並べたとき

## [2026-11-04] update | 対話メモ追記 — AIは倉庫番じゃなく、古本屋の店主だった

- topics/tec/agents-need-documentation-not-memory に 🗣️ キミとの対話メモを追記。出口の検索をエッセイ5本で測った結果と、検索はできても重みを付けるのは外の人、という古本屋の店主の比喩

## [2026-11-04] compile | 1 source → 1 new article, 1 updated

- 新規: [図書館の古い本の余白 ── Book Traces が集める、19世紀の読者の書き込み](/topics/materials/book-traces-library-marginalia/)
- See Also 逆リンク: [完成稿の前を読む](/topics/writing-theory/genetic-criticism-reading-drafts/)（作者が自分の本に書いた余白と、読者が他人の本に書いた余白）
- 共鳴チェック: なし（既にあるものから新しいものへ は今日のエッセイで消費済み）

## [2026-11-04] essay | 新しいものは、本の後に来る（essays/2026-11-04-new-comes-after-the-book.md）

## [2026-11-04] ingest | Book Traces: New digital project brings hidden messages in old books to light (raw/articles/2026-11-04-book-traces-19th-century-marginalia-uva.md)

- 図書館の19世紀の本に読者が残した書き込みを集めるプロジェクトの紹介記事（UVA Magazine）
- 詩集の余白の母の挽歌、ダグラスの本への返事の詩。エッセイの入口用に取った

## [2026-11-04] compile | 1 source → 0 new articles, 2 updated

- 更新: [忘れることを、書く力にする](/topics/writing-theory/montaigne-oubliance-forgetting-ars-memoriae/) — Gerbier・Langlet「Montaigne carnettiste」（2019）の本文を読んで「本の後に来る手帳」の節と、山本 2025 と II-06 の読みが逆になるところの節を足した。関連研究の「要旨から」の行は Sources へ移した
- See Also 逆リンク: [モンテーニュとラ・ボエシー](/topics/writing-theory/montaigne-la-boetie-friendship/)（同じ加筆を Lestringant は二段階、Gerbier・Langlet は三段階と数える）
- 共鳴チェック: 既にあるものから新しいものへ に兆し（3件目）→ 宣言

## [2026-11-04] ingest | Montaigne carnettiste (raw/papers/2026-11-04-gerbier-langlet-montaigne-carnettiste.md)

- Gerbier・Langlet（Études littéraires 2019）の本文PDFを取り込み。忘却と記憶術の記事で「要旨から」だった1本の全文
- 『エセー』を手帳として読み、ボルドー本への書き足しを「本の後に来る下書き」と捉える。インクの色で「彼だったから、私だったから」の三段階の加筆を示す

## [2026-11-03] ingest | Montaigne et les loci communes（山本佳生の博士論文・抜粋）(raw/papers/2026-11-03-yamamoto-these-loci-communes-montaigne-excerpt.md)

- 374ページの博士論文のうち、読んだ第2部第1章の冒頭・§3（モンテーニュの引用）と第2部の結論だけを抜き出して raw にした（印刷 pp. 109–110・124–134・209–210）
- 記事「忘れることを、書く力にする」の「二つの論文が並ぶところ」と関連研究に使った

## [2026-11-03] compile | 1 source → 0 new articles, 2 updated

- 更新: [モンテーニュ『エセー』](/topics/writing-theory/montaigne-essays/)（「研究から ── 版はそのつど、何かのために出た」の節）
- 更新: [II-08 父親の子への愛情について](/topics/books/essais/II-08/)（「加筆層が見えるか」に「ああ、友よ」の経緯）・[読書棚](/topics/books/essais/)の「底本」に1行
- 共鳴チェック: なし（このセッションの兆しは使用済み）

## [2026-11-03] ingest | 『エセー』を読み始めるために（raw/papers/2026-11-03-yamamoto-essais-yomihajimeru-tameni-editions.md）

- 山本佳生 2020（早稲田大学大学院『フランス文学語学研究』39号）。researchmap 公開の PDF を pdf2md で取り込み、書誌は researchmap の記載と PDF から
- 版の成り立ちを経歴と政治に重ねて整理し、II-08 のボルドー本の消された加筆を読む論文

## [2026-11-03] compile | 1 source → 0 new articles, 2 updated

- 更新: [批判という継承](/topics/writing-theory/montaigne-reception-pascal-rousseau-retif/)（「研究から ── 自分を語ることは、自己愛の治療だった」の節）
- See Also: [忘れることを、書く力にする](/topics/writing-theory/montaigne-oubliance-forgetting-ars-memoriae/) と相互に
- 共鳴チェック: なし（このセッションの兆しは使用済み）

## [2026-11-03] ingest | モンテーニュと「自己愛」（raw/papers/2026-11-03-yamamoto-montaigne-amour-de-soi-philautia.md）

- 山本佳生 2026（日本フランス語フランス文学会『フランス語フランス文学研究』129号）。scholar fetch で J-STAGE の記事ページから取得
- アウグスティヌスとエラスムスの二つの自己愛を分け、自己描写を自己愛の盲目の治療として読む論文

## [2026-11-03] compile | 1 source → 0 new articles, 2 updated

- 更新: [引用を、エッセイにどう編み込むか](/topics/writing-theory/quotation-integration-technique/)（「研究から ── 出どころを隠す引用」の節）
- 更新: [忘れることを、書く力にする](/topics/writing-theory/montaigne-oubliance-forgetting-ars-memoriae/)（抜き書き帳を作らず本そのものを帳面にした、の段落・相互の See Also）
- 共鳴チェック: なし（このセッションの兆しは使用済み）

## [2026-11-03] ingest | Citation et invention dans les Essais de Montaigne（raw/papers/2026-11-03-yamamoto-citation-invention-essais-montaigne.md）

- 山本佳生 2021（日本フランス語フランス文学会『フランス語フランス文学研究』118号）。scholar fetch で J-STAGE の記事ページから取得
- 「引証の名誉より発見の名誉」を軸に、出どころを隠して向きを変える引用と、刊本の『エセー』を抜き書き帳として使った書き方を読む

## [2026-11-03] compile | 1 source → 0 new articles, 1 updated

- 更新: [忘れることを、書く力にする](/topics/writing-theory/montaigne-oubliance-forgetting-ars-memoriae/)（関連研究の Martin の行を、Pérouse の書評の読みで書き直した）
- 共鳴チェック: なし
