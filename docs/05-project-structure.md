# 構造とファイル説明

このガイドでは、ウェブサイトの全体構造と主要なファイル・フォルダについて説明します。プロジェクトの構造を理解することで、どのファイルを編集すればよいかが分かるようになります。

## プロジェクト全体の構造

```
labo-hp/
├── node_modules/        # 依存パッケージ（自動生成）
├── public/              # 静的ファイル（画像やアイコンなど）
├── src/                 # ソースコード
│   ├── components/      # 再利用可能なコンポーネント
│   ├── pages/           # ページコンポーネント
│   ├── App.tsx          # アプリケーションのメインコンポーネント
│   ├── index.css        # グローバルなCSS
│   └── main.tsx         # エントリーポイント
├── .eslintrc.js         # ESLint設定ファイル
├── .gitignore           # Gitが無視するファイルの設定
├── .prettierrc          # Prettier設定ファイル
├── index.html           # HTMLのエントリーポイント
├── package.json         # プロジェクト設定と依存関係
├── package-lock.json    # 依存関係のバージョン固定
├── tailwind.config.js   # TailwindCSSの設定
├── tsconfig.json        # TypeScriptの設定
└── vite.config.ts       # Viteの設定
```

## 主要なフォルダとファイルの説明

### `/public` フォルダ

静的ファイルを格納するフォルダです。ここに配置したファイルは、ビルド時にそのまま出力ディレクトリにコピーされます。

- **用途**: 画像、アイコン、PDFなどの静的ファイル
- **例**: `public/shoin.ico`（ファビコン）

### `/src` フォルダ

アプリケーションのソースコードを格納するフォルダです。ほとんどの編集作業はこのフォルダ内のファイルに対して行います。

#### `/src/components` フォルダ

再利用可能なUIコンポーネントを格納するフォルダです。

- **用途**: ボタン、ナビゲーションバー、カードなどのUIパーツ
- **主要ファイル**:
  - `Navbar.tsx`: ウェブサイトのナビゲーションバー
  - `ImageSlider.tsx`: トップページのスライダー
  - `Introduction.tsx`: 研究室紹介セクション
  - `ResearchAreas.tsx`: 研究分野セクション
  - `AboutLab.tsx`: 研究室について
  - `ParticleBackground.tsx`: 背景のパーティクルエフェクト

#### `/src/pages` フォルダ

各ページのコンポーネントを格納するフォルダです。

- **用途**: ウェブサイトの各ページ
- **主要ファイル**:
  - `PastResearch.tsx`: 過去の研究ページ
  - `ITSupportDesk.tsx`: ITサポートデスクページ
  - `Information.tsx`: 情報ページ

#### `/src/App.tsx`

アプリケーションのメインコンポーネントです。ルーティング（ページ遷移）の設定などが含まれています。

#### `/src/main.tsx`

アプリケーションのエントリーポイントです。Reactアプリケーションの初期化を行います。

#### `/src/index.css`

グローバルなCSSスタイルを定義するファイルです。

### ルートディレクトリの主要ファイル

#### `index.html`

ウェブサイトのHTMLテンプレートファイルです。メタ情報（タイトル、説明など）の編集はこのファイルで行います。

#### `package.json`

プロジェクトの設定や依存関係を管理するファイルです。スクリプトコマンドもここで定義されています。

#### `tailwind.config.js`

TailwindCSSのカスタマイズ設定を行うファイルです。

#### `vite.config.ts`

Viteのビルド設定を行うファイルです。

## 主なファイルの編集ガイド

### コンテンツの編集

ウェブサイトのコンテンツを編集する場合は、主に以下のファイルを変更します：

1. **トップページの内容変更**

   - `src/components/Introduction.tsx`: 研究室紹介
   - `src/components/ResearchAreas.tsx`: 研究分野
   - `src/components/AboutLab.tsx`: 研究室について

2. **サブページの内容変更**

   - `src/pages/PastResearch.tsx`: 過去の研究
   - `src/pages/ITSupportDesk.tsx`: ITサポートデスク
   - `src/pages/Information.tsx`: 情報ページ

3. **画像の追加・変更**
   - 新しい画像は `public` フォルダに配置します
   - 参照は `/画像ファイル名` のように行います（例：`<img src="/nameplate.JPG" />`)

### レイアウトの編集

サイト全体のレイアウトを変更する場合は、以下のファイルを編集します：

1. **ナビゲーションバー**

   - `src/components/Navbar.tsx`

2. **全体レイアウト**

   - `src/App.tsx`

3. **グローバルスタイル**
   - `src/index.css`

## 次のステップ

プロジェクト構造を理解したら、[ウェブサイト更新ガイド](./06-update-guide.md)に進み、具体的な更新方法について学びましょう。
