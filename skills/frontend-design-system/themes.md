# Theme Examples

このドキュメントでは、具体的なテーマ例とその実装ガイドラインを提供します。

## 1. Nordic Minimal

**コンセプト：** スカンジナビアデザインにインスパイアされた、機能美と静謐さ

```css
:root {
  /* Colors */
  --color-primary: #2d3748; /* Charcoal */
  --color-secondary: #718096; /* Slate */
  --color-accent: #c17f59; /* Terracotta */
  --color-background: #f7f5f3; /* Warm White */
  --color-surface: #ffffff;
  --color-text: #1a202c;
  --color-text-muted: #4a5568;

  /* Typography */
  --font-heading: 'DM Serif Display', serif;
  --font-body: 'DM Sans', sans-serif;

  /* Spacing */
  --space-unit: 8px;
}
```

**特徴：**

- 温かみのある白背景
- テラコッタのアクセント
- 大胆な余白
- セリフ見出し × サンセリフ本文

---

## 2. Neon Brutalism

**コンセプト：** ブルータリズムとサイバーパンクの融合、大胆で反抗的

```css
:root {
  /* Colors */
  --color-primary: #000000;
  --color-secondary: #ffffff;
  --color-accent: #00ff88; /* Electric Green */
  --color-accent-alt: #ff6b35; /* Safety Orange */
  --color-background: #0a0a0a;
  --color-surface: #1a1a1a;
  --color-text: #ffffff;
  --color-border: #333333;

  /* Typography */
  --font-heading: 'Space Grotesk', sans-serif;
  --font-body: 'JetBrains Mono', monospace;

  /* Effects */
  --shadow-brutal: 4px 4px 0 var(--color-accent);
  --border-brutal: 3px solid var(--color-secondary);
}
```

**特徴：**

- 高コントラスト
- ハードシャドウ（ドロップシャドウなし）
- モノスペースフォント
- 太いボーダー

---

## 3. Organic Growth

**コンセプト：** 自然と持続可能性、有機的な形状と穏やかな色調

```css
:root {
  /* Colors */
  --color-primary: #2d4a3e; /* Forest */
  --color-secondary: #8b7355; /* Earth */
  --color-accent: #d4a574; /* Sand */
  --color-background: #f5f1eb; /* Cream */
  --color-surface: #ffffff;
  --color-text: #2c3e2d;
  --color-text-muted: #5d6b5e;

  /* Typography */
  --font-heading: 'Fraunces', serif;
  --font-body: 'Work Sans', sans-serif;

  /* Shapes */
  --radius-organic: 60% 40% 30% 70% / 60% 30% 70% 40%;
}
```

**特徴：**

- アースカラーパレット
- 有機的なブロブシェイプ
- 手書き風アクセント
- テクスチャ背景

---

## 4. Tech Noir

**コンセプト：** ダークモードファースト、洗練されたテック感

```css
:root {
  /* Colors */
  --color-primary: #6366f1; /* Indigo */
  --color-secondary: #8b5cf6; /* Violet */
  --color-accent: #22d3ee; /* Cyan */
  --color-background: #0f0f23; /* Deep Navy */
  --color-surface: #1a1a2e;
  --color-surface-elevated: #252542;
  --color-text: #e2e8f0;
  --color-text-muted: #94a3b8;

  /* Typography */
  --font-heading: 'Syne', sans-serif;
  --font-body: 'Outfit', sans-serif;

  /* Effects */
  --glow-primary: 0 0 20px rgba(99, 102, 241, 0.3);
  --gradient-hero: linear-gradient(
    135deg,
    #6366f1 0%,
    #8b5cf6 50%,
    #22d3ee 100%
  );
}
```

**特徴：**

- 深いネイビー背景
- グロー効果のアクセント
- グラデーションのポイント使用
- モダンなサンセリフ

---

## 5. Editorial Elegance

**コンセプト：** 雑誌のような洗練されたエディトリアルデザイン

```css
:root {
  /* Colors */
  --color-primary: #1a1a1a;
  --color-secondary: #6b7280;
  --color-accent: #dc2626; /* Editorial Red */
  --color-background: #fafafa;
  --color-surface: #ffffff;
  --color-text: #111827;
  --color-text-muted: #6b7280;

  /* Typography */
  --font-heading: 'Playfair Display', serif;
  --font-body: 'Source Serif Pro', serif;
  --font-accent: 'Libre Baskerville', serif;

  /* Layout */
  --column-width: 65ch;
  --grid-editorial: 1fr 2fr 1fr;
}
```

**特徴：**

- クラシックなセリフ体
- 赤のアクセント（見出し・リンク）
- 65文字幅のコラム
- 豊富な余白と行間

---

## Application Guidelines

### テーマ適用時のチェックリスト

- [ ] CSS変数として定義し、一貫性を確保
- [ ] ダークモード/ライトモードの両方を考慮
- [ ] アクセシビリティ（コントラスト比4.5:1以上）を確認
- [ ] レスポンシブ時のフォントサイズ調整
- [ ] インタラクティブ要素のホバー/フォーカス状態を定義
