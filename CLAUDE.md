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
├── CNAME           （GitHub Pages のカスタムドメイン設定）
├── DESIGN.md       （Elite Editorial デザインシステム、編集時は必ず参照）
├── README.md       （プロジェクト概要、人間向け）
├── CLAUDE.md       （このファイル、Claude Code 起動時に読む）
├── index.html      （トップページ）
├── paper.html      （paper Sample Book 詳細ページ）
└── style.css       （共通CSS、index と paper で参照）
```

---

## 5. 絶対に守るルール

### ルール1：CNAME ファイルは絶対に変更・削除しない

このファイルが破損すると perfectgreen.net でのサイト公開が止まる。中身は `perfectgreen.net` の1行のみ。他の値を書かない。

### ルール2：DESIGN.md に従う

すべてのCSS、デザイン判断、色、フォント、余白は DESIGN.md（Elite Editorial）を参照すること。独自の判断で配色や typography を変えない。

### ルール3：重要な配色ルール

- 基調: 黒 (`#000000`) × アイボリー (`#fcf9f2`)
- アクセント: 深い森の緑 (`#1a4d3a`) を一点だけ使用（ロゴの「GREEN」、フッターなど）
- 緑をビカビカに使わない。Elite Editorial の静寂を壊さない。

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

## 9. 直近の状態（2026-05-20 時点）

サイトは公開済み。フェス出展告知セクション、paper Sample Book 紹介、14種類の紙詳細ページまで実装済み。  
製品写真（Matcha Color Chart、Matcha Coaster、paper Sample Book）の追加が未着手。  
5月23日（土）のZINEフェス東京がブランドの公開デビュー。
