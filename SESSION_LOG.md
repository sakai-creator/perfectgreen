# SESSION LOG

**日付:** 2026年5月20日（火）  
**セッション名:** PERFECT GREEN プロジェクト初日

---

## 1. ブランドコンセプト確立

### 「美しいものは、循環する。」の成立

ZINELAB（zinelab.tokyo）からコピーした index.html を出発点に、スバルグラフィックの新ブランドとしてゼロから設計。環境対応印刷を「我慢・正しさ」ではなく「美しさの条件」として語るという思想から、メインキャッチ「美しいものは、循環する。」が確定した。

### Elite Editorial デザインシステムの採用

DESIGN.md に定義済みの Elite Editorial を完全準拠として採用。黒×アイボリー基調、Playfair Display×Inter の typography 階層、The Luxury of Space（余白の贅沢な使い方）を実装の軸に据えた。

### ZINELAB との差別化方針

- ZINELAB: ポップ、丸ゴシック、カラフル、「はじめてでも大丈夫」のやさしさ
- PERFECT GREEN: 静寂、セリフ体、モノクロ×アイボリー、「美しさの格」で語る環境対応
- 両者は並列・独立。コードの骨格参考のみで流用なし。

---

## 2. 実装した内容

### 初版サイト作成（index.html, style.css）

ZINELAB の HTML 構造を参考に、PERFECT GREEN のコンテンツで全面書き直し。CSS はインライン `<style>` で完結させた初版を作成。古い `images/` フォルダ（zine-sample-01.png, dummy）も同時削除。

### paperSampleBook セクション追加

「3つの柱」と「FAQ」の間に挿入。紙ソムリエがセレクトした14種を紹介し、`paper.html` への CTA（枠線ボタン）を配置。フェスでの現物配布告知も添えた。

### Event（フェス告知）セクション追加

paperSampleBook セクションの直後に配置。`--surface-low`（#f6f3ec）で背景を切り替え、視覚的に独立させた。5.23 SAT — ASAKUSA の日付を緑アクセントで提示。Matcha 2商品は「存在の予告」のみで、詳細ページなし・価格なし・購入リンクなしの設計。

### paper.html（14種一覧）新規作成

`perfectgreen.net/paper.html` を QRコード先として設計。14種の紙を番号（Playfair italic、`--outline-variant` 色）＋銘柄名＋スペック＋説明文の縦リストで展開。フェス会場での無料配布告知をページ末尾に配置。

### CSS の共通ファイル化（style.css）

index.html と paper.html で共通する全 CSS を `style.css` に切り出し。両ページが `<link rel="stylesheet" href="style.css">` で参照する構造に移行。

### 余白圧縮（モバイル離脱対策）

| 箇所 | Before | After |
|---|---|---|
| ヒーロー padding（上） | 128px | 64px |
| ヒーロー padding（下） | 120px | 56px |
| 全セクション padding | 128px | 80px |
| FAQ 各アイテム padding | 48px 0 | 32px 0 |
| paper.html 各エントリ padding | 64px 0 | 36px 0 |
| paper.html 番号フォントサイズ | 64px | 48px |
| section-label margin-bottom | 32px | 24px |

14種 × 36px × 2 = 縦約1,008px の短縮。スマホで3〜4スクリーン分の節約。

### コピー微修正

コンタクトセクション見出しを変更：  
「美しい、循環するZINEを、**一緒に。**」→「美しい、循環するZINEを、**まずは相談から。**」

### 改行制御

日本語見出しの「ソムリ／エ」「相談か／ら。」「14／種。」などの不正な改行を修正。style.css の `h1, h2, h3` および `.faq-q` に以下を追加：

```css
text-wrap: balance;
word-break: keep-all;
overflow-wrap: break-word;
```

---

## 3. デザイン判断

### 「PERFECT」黒、「GREEN」深緑（#1a4d3a）の使い分け

ロゴとフッターの2箇所のみ深緑を使用。他には一切出さない。The Luxury of Space を「色」にも適用する考え方。緑を多用すると Elite Editorial の静寂が崩れる。

### ヒーロー h1 を italic にした理由

Playfair Display は italic のときに最もエディトリアルらしい表情を出す。「美しいものは、循環する。」という詩的なコピーに italic は必然。通常ウェイトだと Force が出すぎてブランドのトーンと合わない。

### FAQ をアコーディオンにしなかった理由

Elite Editorial は「情報を隠す」ではなく「情報の密度を下げる」で勝負する。Q が3問・A も短いため、全展開してヘアライン区切りで静かに並べた方が気品を保てる。

### コンタクトセクションを黒背景にした理由

アイボリー → 黒への転換で、ページの「終わり」と「誘い」が同時に機能する。CTA に一番強いコントラストを与えるため。緑は出さず、黒の中にメールアドレスを italic Playfair で浮かせた。

### 画像を一切置かなかった判断

タイポグラフィと余白だけで成立させるのが Elite Editorial の核心。素材なしに「高級感」を出せるかの実証でもある。製品写真は今後フェス後に追加予定。

---

## 4. 次回セッションでやること

- Matcha Color Chart の製品写真をフェス告知セクションに追加
- Matcha Coaster の製品写真を追加
- paper Sample Book の写真追加（トップページと paper.html 両方）
- paper.html を指す QRコード生成
- paperSampleBook 表紙への QRコード組み込み

---

## 5. プロジェクト全体の主要決定事項

- ドメイン: perfectgreen.net
- ホスティング: GitHub Pages（sakai-creator/perfectgreen）
- HTTPS 有効、Let's Encrypt 自動更新
- 連絡先: hello@perfectgreen.net（Google Workspace グループ）
- メンバー: 坂井陽一 1人（拡充は今後検討）

---

## 6. 5月23日（土）のZINEフェス東京について

- `perfectgreen.net/paper.html` が QRコードからの誘導先（本番サイト）
- フェス会場で paper Sample Book（全14種・計70枚・ハトメ綴じ）を無料配布
- Matcha 2商品をフェス限定で販売
  - Matcha Color Chart — 抹茶5段階グラデーションのしおり形状1枚もの
  - Matcha Coaster（5枚組）— シルバー下地・厚盛りニス・ホワイト二度刷り
- 両商品の詳細ページは作らない。フェスで実物を見て、欲しい人に買ってもらう設計。
