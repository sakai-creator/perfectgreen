name: Elite Editorial
colors:
  surface: '#fcf9f2'
  surface-dim: '#dcdad3'
  surface-bright: '#fcf9f2'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f6f3ec'
  surface-container: '#f1eee6'
  surface-container-high: '#ebe8e0'
  surface-container-highest: '#e5e2da'
  on-surface: '#1c1c17'
  on-surface-variant: '#48473e'
  outline: '#79776d'
  outline-variant: '#c9c7ba'
  primary: '#000000'
  on-primary: '#ffffff'
  primary-container: '#262626'
  on-primary-container: '#b3b3b3'
  secondary: '#5f5e52'
  on-secondary: '#ffffff'
  secondary-container: '#e5e3d4'
  on-secondary-container: '#1c1c14'
  tertiary: '#51605f'
  on-tertiary: '#ffffff'
  tertiary-container: '#d4e5e4'
  on-tertiary-container: '#0e1e1e'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#410002'

  # --- GREEN: ブランドの緑 -------------------------------------
  # 線・文字に使う緑（小面積・暗い）
  green-mark: '#1a4d3a'         # ロゴの「GREEN」、フッター、Event 日付

  # 面に使う緑（大面積・淡い）
  # 出典: Matcha Color Chart（自社製品）の印字 CMYK
  # 変換: Japan Color 2001 Coated / 知覚的
  matcha-light:     '#E3E38A'   # 001 LIGHT LATTE     C15 M5  Y55
  matcha-standard:  '#B6C872'   # 002 STANDARD LATTE  C35 M10 Y65
  matcha-daily:     '#83AD28'   # 003 DAILY MATCHA    C55 M15 Y100
  matcha-deep:      '#2E792A'   # 004 DEEP MATCHA     C75 M20 Y100 K30（未使用）
  matcha-sovereign: '#065120'   # 005 SOVEREIGN SHOT  C85 M35 Y100 K50（未使用）

  # ヒーローのヴェール。matcha-daily を 35% ティントした #D2DEAB の
  # 色相を +24° 回して黄色味を抜いた色
  hero-veil: '#BEDEAB'

typography:
  font-family: 'Playfair Display', serif
  headings:
    family: 'Playfair Display', serif
    weight: 700
    line-height: 1.2
  body:
    family: 'Inter', sans-serif
    weight: 400
    line-height: 1.6

spacing:
  base: 4
  scale: [0, 4, 8, 12, 16, 24, 32, 48, 64, 96, 128]

elevation:
  none: 'none'
  low: '0 2px 4px rgba(0,0,0,0.05)'
  medium: '0 4px 12px rgba(0,0,0,0.08)'
  high: '0 12px 24px rgba(0,0,0,0.12)'

roundness:
  none: 0
  small: 4px
  medium: 8px
  large: 16px
  full: 9999px
---

# Elite Editorial Design System

## Vision
「グランドレヴェリー」の美学を継承した、圧倒的な高級感と静寂を感じさせるデザインシステム。余白の美（間の取り方）を重視し、情報の密度を抑えることで、各要素の存在感を際立たせます。

色は自社製品から採る。緑は「環境対応の記号」ではなく、Matcha Color Chart という実在の製品から抽出された色である。だから緑を使うことが、そのまま製品を語ることになる。緑は入口に置き、中間は黒とアイボリーで静寂を保つ。

## Core Principles
1. **The Luxury of Space**: 贅沢なホワイトスペースにより、ユーザーに視覚的なゆとりとプレミアムな体験を提供。
2. **Typographic Hierarchy**: 美しいセリフ体（Playfair Display）をヒーロー要素に使用し、伝統と格調を表現。
3. **Monochromatic Elegance, with One Green**: 黒とアイボリーの基調に、繊細な中間トーンを重ねることで、奥行きのある質感を創出。緑は入口の面と、ブランドマークの一点にのみ置く。基調そのものは変えない。

## Color Usage

### 緑には2つの役割がある

| 役割 | 色 | 使う場所 | 面積 |
|---|---|---|---|
| **マークの緑** | `green-mark` #1a4d3a | ロゴの「GREEN」、フッター、Event 日付 | 小（文字・線のみ） |
| **面の緑** | `hero-veil` / `matcha-*` | ヒーローのヴェール、Pillars 3枠 | 大（背景） |

この2つを混ぜない。**マークの緑を背景に敷かない。面の緑を small text に使わない。**

### 面の緑は「入口」にだけ置く

- **ヒーロー**（入口）: `hero-veil` #BEDEAB のグラデーション
- **Pillars**（提供価値）: Matcha 3色をアイボリーと混ぜたティント
- **商品セクション・Concept・FAQ**: アイボリーのまま。緑を使わない
- **Contact**（出口）: 黒のまま。「終わりと誘い」を黒のコントラストで機能させる

緑が主体に見えつつ、緑の面積はページ全体の3割以下に収まる。面積ではなく置き場所で主体性をつくる。

### Pillars のティント

01 → 02 → 03 で段階的に緑が濃くなる。**ベタでは使わず、必ずアイボリーと混ぜる。**

```css
background: color-mix(in srgb, rgb(var(--matcha-x)) var(--pillar-tint), var(--surface));
```

| 枠 | 元色 | 既定 35% での結果 |
|---|---|---|
| 01 | matcha-light | `#F3F1CE` |
| 02 | matcha-standard | `#E4E8C5` |
| 03 | matcha-daily | `#D2DEAB` |

**ティントの上限は 40%。** 45% にすると 03 が `#C6D797` となり、ヒーローのヴェール `#BEDEAB` より暗くなって視線の階層が逆転する。

### 緑の上に置ける文字色

面の緑はすべて明度が高いため、**黒系のみ**。アイボリー・白は使わない。

| 背景 | `#000000` | `#1c1c17` | `#48473e` | `#fcf9f2` |
|---|---|---|---|---|
| hero-veil `#BEDEAB` | 14.23 AAA | — | **6.33 AA** | 1.3 × |
| Pillars 01 `#F3F1CE` | 18.28 AAA | — | 8.14 AA | × |
| Pillars 03 `#D2DEAB` | 14.78 AAA | — | 6.58 AA | × |
| matcha-daily ベタ `#83AD28` | 7.97 AAA | 6.49 AA | 3.55 **×** | 2.50 × |

**面の色を変えたら必ずコントラスト比を再計算すること。** Daily Matcha をベタで使うと `#48473e` が 3.55:1 で AA を割る。

## Component Patterns
- **Cards**: 境界線を極限まで細くするか、わずかな色差（Surface Container Low）で表現し、浮遊感を演出。
- **Buttons**: 塗りの黒（Primary）またはアウトラインのみのミニマルなスタイル。
- **Imagery**: 高解像度で彩度を抑えた、情緒的な写真を大胆に使用。