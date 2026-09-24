# PERFECT GREEN プロジェクト

Claude Code がこのプロジェクトを扱うときに必ず読むファイル。プロジェクトの記憶。

---

## 1. このプロジェクトは何か

- 株式会社スバルグラフィックの新ブランド「PERFECT GREEN」の公式サイト
- ドメイン: perfectgreen.net
- ホスティング: GitHub Pages（sakai-creator/perfectgreen）
- 主体: 坂井陽一（factory マネージャー、ブランドオーナー）
- ZINELAB（zinelab.tokyo）とは独立した姉妹ブランド

---

## 2. ブランド哲学

> 美しいものは、循環する。

良いモノ、美しいモノはサステナブルであるべき。リサイクル・リユースができ、循環するプロダクトであること。環境対応は「我慢」ではなく「美しさの条件」。美しさが先にあり、サステナブルはその結果として現れる。

---

## 3. 技術スタック

- 静的サイト（HTML / CSS のみ）
- フロントエンドフレームワーク不使用
- ビルドツール不使用
- GitHub Pages による自動デプロイ
- HTTPS 有効（Let's Encrypt 自動更新）
- カスタムドメイン: perfectgreen.net

---

## 4. ファイル構成

```
~/projects/perfectgreen/
├── .gitignore      （.DS_Store / node_modules 等を除外）
├── CNAME           （GitHub Pages のカスタムドメイン設定）
├── DESIGN.md       （Elite Editorial デザインシステム、編集時は必ず参照）
├── README.md       （プロジェクト概要、人間向け）
├── CLAUDE.md       （このファイル、Claude Code 起動時に読む）
├── SESSION_LOG.md  （セッションごとの作業記録）
├── index.html      （トップページ）
├── style.css       （共通CSS、index が参照）
└── images/
    ├── title_010.webp   （ヒーロー背景：Return 3冊、3702×1693）
    ├── return_010.webp  （HardWorkNote Return：3冊）
    ├── zine_010.webp    （このZINEは、森からできている。：4冊）
    └── score_010.webp   （Hard Work Score：見開き）
```

---

## 5. 絶対に守るルール

### ルール1：CNAME ファイルは絶対に変更・削除しない

このファイルが破損すると perfectgreen.net でのサイト公開が止まる。中身は `perfectgreen.net` の1行のみ。他の値を書かない。

### ルール2：DESIGN.md に従う

すべてのCSS、デザイン判断、色、フォント、余白は DESIGN.md（Elite Editorial）を参照すること。独自の判断で配色や typography を変えない。

### ルール3：重要な配色ルール

- 基調: 黒 (`#000000`) × アイボリー (`#fcf9f2`)。**これは変えない。**
- 緑には2つの役割があり、混ぜてはいけない。

| 役割 | 色 | 使う場所 |
|---|---|---|
| マークの緑 | `--green-mark` #1a4d3a | ロゴの「GREEN」、フッター、Event 日付（文字・線のみ） |
| 面の緑 | `--hero-veil` #BEDEAB / Matcha 3色ティント | ヒーローのヴェール、Pillars 3枠（背景のみ） |

- **マークの緑を背景に敷かない。面の緑を small text に使わない。**
- 面の緑は入口（ヒーロー・Pillars）にだけ置く。商品セクション・Concept・FAQ・Contact には使わない。
- Pillars のティント上限は 40%（超えるとヒーローより暗くなり階層が逆転する）。
- 面の色を変えたら必ずコントラスト比を再計算する。アイボリー・白の文字は緑の上で使えない。
- 詳細は DESIGN.md の `## Color Usage` を参照。

### ルール4：フォント

- 見出し: Playfair Display, serif（italic を効果的に使う）
- 本文: Inter, sans-serif
- Google Fonts から読み込み

### ルール5：改行制御の重要設定

日本語見出しの改行が崩れないよう、style.css の見出しセレクタに以下を保持する：

```css
text-wrap: balance;
word-break: keep-all;
overflow-wrap: break-word;
```

### ルール6：CJK 改行制御に .nowrap ユーティリティを使う

日本語と英語が混在する見出しで「PERFECT GREEN の」のような塊が改行で分断されないよう、CSS の `.nowrap` クラス（`white-space: nowrap`）を使う。`&nbsp;` だけでは PERFECT と GREEN の間が改行されてしまうため、span でラップして `.nowrap` を当てる方式を採用している。

```html
<span class="nowrap">PERFECT GREEN の</span>
```

### ルール7：.gitignore で OS ゴミファイルを除外

`.DS_Store` などの OS が自動生成するファイルは絶対にコミットしない。`.gitignore` で除外設定済み。新規にゴミファイルが発生し得る環境（IDE、ログなど）は `.gitignore` に追記する。

---

## 6. デプロイ方法

ローカルで編集 → コミット → push で自動デプロイ。

```bash
cd ~/projects/perfectgreen
git add .
git commit -m "変更の説明"
git push
```

GitHub Pages が自動でビルド・デプロイ。  
進捗確認: https://github.com/sakai-creator/perfectgreen/actions

---

## 7. 連絡先・運用

- お問い合わせメール: hello@perfectgreen.net
- Google Workspace のグループとして運用（メンバー: 坂井陽一）
- 返信時の From: hello@perfectgreen.net（グループアドレス）

---

## 8. 関連する外部設定

### お名前.com（DNS）

- ネームサーバー: 01〜04.dnsv.jp
- A レコード × 4: 185.199.108〜111.153（GitHub Pages）
- CNAME (www): sakai-creator.github.io
- MX × 5: aspmx.l.google.com, alt1〜4.aspmx.l.google.com
- TXT (SPF): `v=spf1 include:_spf.google.com ~all`
- TXT (Google認証): google-site-verification=（値は省略）

### Google Workspace

- セカンダリドメインとして perfectgreen.net 登録済み
- グループ「PERFECT GREEN Hello」（hello@perfectgreen.net）

---

## 9. 直近の状態（2026-09-24 時点）

Day 3 で、5月のZINEフェス向けラインナップを 9月26日（土）ZINEフェス東京向けに全面入れ替え。

### 削除したもの
- paperSampleBook セクション、`paper.html`、`images/papersample_010.webp`
- Matcha Color Chart / Matcha Coaster セクションと画像（chart / coaster）
- ナビの「Paper」リンク
- style.css の paper.html 専用CSS と .matcha-* 系CSS

### 商品セクション3点（`.product` クラス）
1. **HardWorkNote Return** — 森からできて、森へ帰るnote
2. **このZINEは、森からできている。** — カーボンオフセット入門書
3. **Hard Work Score for Guitarist** — タブ譜ノート

### レイアウト規則（重要）

```
768px 以上 : .product-grid が 45fr / 55fr の2カラム
             写真の左右を交互に（Return 左／ZINE 右／Score 左）
             ② には .product-reverse を付け、写真を order:2 で右へ
768px 未満 : 1カラムで縦積み（写真 → テキスト）
```

セクション内の並びは、写真 → 英字ラベル（section-label）→ キャッチ（h2）→ 商品名（.product-name）＋サブ（.product-sub）→ 本文 → スペック。

**スペック行（.product-spec）は 2カラムの外に置く。** テキストカラム（約480px）では1行に収まらないため、セクション全幅（880px）に出している。上の細罫がセクションを締めるフッター帯として機能する。

### ルール8：改行制御は3層で守る

1. `body` に `word-break: auto-phrase`（Chrome が文節単位で改行する）
2. 見出し（h1-h3）は `word-break: keep-all` が詳細度で勝つ。`<br>` で明示制御する方針は変えない
3. Safari は auto-phrase 未対応。**語中で割れる箇所は `.nowrap` で個別に止める**

現在 `.nowrap` で固定している箇所：`2026.09.26` ／ 排出分 ／「このZINEは、 ／ 手に取って ／ 一冊まるごと ／ ZINEという ／ ノンVOCインキ ／「HardWorkNote Return」／「Hard Work Score」／ 布ではなく紙。／ プロダクトであること。／ 各スペック項目

スペック行は区切り「／」ごとに `<span class="nowrap">` で囲んでいる。スマホではこの位置でのみ折り返す。

### ヒーロー背景（2層構造）

`title_010.webp` は HardWorkNote Return 3冊の写真（3702×1693、Pillow で quality 84 変換）。

ヒーローは**写真とヴェールの2層**でできている。触るときは必ず両方をセットで考えること。

| 層 | 役割 |
|---|---|
| `.hero::before` | 写真本体。`opacity: var(--hero-photo)` = **1**（フル） |
| `.hero::after` | **Daily Matcha** のグラデーション。写真の上・本文の下に重ねて文字の可読性を確保する |

### Matcha Color Chart（色の出どころ）

削除した Matcha Color Chart（`chart_010.webp`）に印字されていた CMYK 値が唯一の原典。git 履歴のテキストには色定義が一切存在しない。CMYK → sRGB は **Japan Color 2001 Coated / 知覚的**で変換した。

| # | 名前 | CMYK | sRGB | 変数 |
|---|---|---|---|---|
| 001 | LIGHT LATTE | C15 M5 Y55 | `#E3E38A` | `--matcha-light` |
| 002 | STANDARD LATTE | C35 M10 Y65 | `#B6C872` | `--matcha-standard` |
| 003 | DAILY MATCHA | C55 M15 Y100 | `#83AD28` | `--matcha-daily` |
| 004 | DEEP MATCHA | C75 M20 Y100 K30 | `#2E792A` | （未定義） |
| 005 | SOVEREIGN SHOT | C85 M35 Y100 K50 | `#065120` | （未定義） |

`:root` に `R, G, B` の数値列で定義し、`rgba(var(--matcha-light), α)` / `rgb(var(--matcha-light))` で使う。

### ヒーローのヴェール色

`--hero-veil: 190, 222, 171`（**#BEDEAB**）。Pillars 03枠の背景 `#D2DEAB` を基準に、色相を +24°（74° → 98°）回して黄色味を抜いた色。明度・彩度は基準色とほぼ同じ。

Daily Matcha `#83AD28` → LIGHT LATTE `#E3E38A` → **#BEDEAB** と2回調整している。Daily Matcha は濃すぎ、LIGHT LATTE は黄色が強すぎた。

この色の上のコントラスト比：

| 文字色 | 比 | 判定 |
|---|---|---|
| `#000000` 見出し | **14.23:1** | AAA |
| `#48473e` `--on-surface-variant`（本文・アイブロウ） | **6.33:1** | AA |
| `#79776d` `--outline` | 3.04:1 | 小さい文字では不足 |

**ヴェール色を変えたら必ずコントラスト比を再計算すること。**

### Pillars（WHAT WE OFFER）の3枠

01 → 02 → 03 で緑が段階的に濃くなる。**ベタでは使わず、アイボリーと `color-mix` で混ぜる。** 混合率は `.pillars` の `--pillar-tint`（既定 **35%**）1箇所で変えられる。

| 枠 | 元色 | 35%混合後 |
|---|---|---|
| 01 | LIGHT LATTE | `#F3F1CE` |
| 02 | STANDARD LATTE | `#E4E8C5` |
| 03 | DAILY MATCHA | `#D2DEAB` |

番号（`.pillar-num`）は `--outline-variant` だとティントの上で 1.2:1 まで落ちるため **`--outline` に一段濃くした**（3.16:1 以上、52px の大きな文字なので大文字基準 3.0 をクリア）。

**ティントを上げるときの注意**：45% にすると 03 が `#C6D797` となり、ヒーローのヴェールより暗くなって視線の階層が逆転する。40% 程度が上限。

### ルール9：罫線は「全幅」か「なし」の二択

区切りの罫線はセクション要素に `border-bottom` を付けて**必ず全幅**にする。`.wrap` の内側に区切り線を置かない。

- セクション間（hero / concept / pillars / product / event / faq）：全幅 ✓
- 商品と商品の間（Return / ZINE / Score）：`.product` の `border-bottom` で全幅 ✓
- 商品内のスペック行の上：**罫線を使わず余白 48px で区切る**（余白スケールから選択）

- FAQ の各問の間：**罫線を使わず余白 48px で区切る**（480px 以下は 32px）

**区切りの罫線はすべて全幅になっている。** コンテンツ幅で止まっている線は次の2本だけで、どちらも区切り線ではないため対象外。

| 箇所 | 幅 | 性質 |
|---|---|---|
| `.pillars-grid` | 880px | 3枠カードの外枠 |
| `.contact-email` | 352px | リンクの下線 |

ヴェールの向きは画面幅で切り替える。

- **768px 以上**：左→右の横グラデーション。左端は Daily Matcha ベタ、74% で完全に透明。文字は左に、リサイクルマーク・Return ロゴ・小口は右に置いて干渉させない
- **767px 以下**：上→下の縦グラデーション。スマホは文字が全幅に乗るため横方向では逃げ場がない。上部は写真を見せ（0.16）、本文が始まる 54% 以降は Daily Matcha ベタにして可読性を優先する

`background-position` も幅で切り替える。**768px 以上は `center`、767px 以下は `70% center`。** スマホは縦長の枠に横長写真を cover で敷くため左右が大きく切れる。70% にするとリサイクルマークと「Return」の文字が両方残る（50% では文字が入らず、85% ではマークが消える）。

画像URLには `?v=day3` を付けてキャッシュを回避している。**画像を差し替えたらこのクエリも必ず更新すること。** ブラウザのキャッシュが強く、付け忘れると「差し替えたのに前の画像が出る」状態になる。

残タスク：なし（フェス当日対応のみ）。