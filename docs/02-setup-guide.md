# 環境構築方法

このガイドでは、開発環境を一から構築する方法を説明します。

## 目次

1. [Windows ユーザー向け: WSL のセットアップ](#windowsユーザー向け-wslのセットアップ)
2. [Git と GitHub の基本](#gitとgithubの基本)
3. [リポジトリのクローン](#リポジトリのクローン)
4. [Node.js と npm の準備](#nodejsとnpmの準備)
5. [依存パッケージのインストール](#依存パッケージのインストール)

## Windows ユーザー向け: WSL のセットアップ

WSL（Windows Subsystem for Linux）は、Windows 上で Linux 環境を利用できるようにする機能です。ウェブ開発では多くのツールが Linux 環境を前提としているため、WSL を使うとトラブルが少なくなります。

### WSL のインストール手順

- [公式ドキュメント](https://learn.microsoft.com/ja-jp/windows/wsl/install)
- 「Ubuntu」アプリを開くことで Linux ターミナルを使えるようになります。

## Git と GitHub の基本

### Git と GitHub の違い

初心者の方のために、Git と GitHub の違いを簡単に説明します：

#### Git とは？

- ローカル（あなたのパソコン）で動作するバージョン管理ツール
- コードの変更履歴を記録・管理する
- コマンドラインで操作する
- パソコンにインストールして使う

#### GitHub とは？

- Git で管理したコードをクラウド上に保存・共有できるサービス
- ウェブブラウザで操作できる
- チーム開発がしやすい
- コードのバックアップとしても使える
- ウェブサイトのホスティングにも使える（今回のプロジェクトではこれを使用）

簡単に言うと：

- Git = コードの変更履歴を管理するツール
- GitHub = Git で管理したコードを保存・共有するためのクラウドサービス

### GitHub のアカウント作成

1. [GitHub](https://github.com/)にアクセス
2. 「Sign up」をクリック
3. メールアドレス、パスワード、ユーザー名を入力
4. メール認証を完了

### SSH キーの設定

GitHub でリポジトリをクローンするには、SSH キーの設定が必要です。以下の手順で設定しましょう：

1. **SSH キーの生成**

```bash
# SSHキーを生成
ssh-keygen -t ed25519 -C "あなたのメールアドレス"

# キーの保存場所を確認（デフォルトのままEnterを押す）
# パスフレーズの設定（任意）
```

2. **SSH キーの確認**

```bash
# 公開キーの内容を表示
cat ~/.ssh/id_ed25519.pub
```

3. **GitHub に SSH キーを登録**

- GitHub の右上のプロフィールアイコン → Settings
- 左サイドバーの「SSH and GPG keys」
- 「New SSH key」をクリック
- Title: 識別しやすい名前（例：My Laptop）
- Key: 先ほど表示した公開キーの内容をコピー＆ペースト
- 「Add SSH key」をクリック

4. **接続テスト**

```bash
# GitHubとの接続をテスト
ssh -T git@github.com
```

「Hi username! You've successfully authenticated...」と表示されれば成功です！

### Git のインストール

#### Windows（WSL）の場合

WSL 上の Ubuntu には、通常 Git が最初からインストールされています。確認するには：

```bash
git --version
```

#### macOS の場合

macOS には、通常 Git が最初からインストールされています。確認するには：

ターミナルで以下のコマンドを実行：

```bash
git --version
```

もしインストールされていなければ、Git のインストーラが自動的に表示されます。

### Git の基本設定

Git をインストールしたら、まず自分の情報を設定します：
ここでのメールアドレス、名前は GitHub に登録してあるユーザー名とメールアドレスを推奨します。

```bash
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

## リポジトリのクローン

リポジトリのクローンとは、Git で管理されているプロジェクトをあなたのパソコンにコピーすることです。

### クローンの手順

1. **ターミナル（コマンドプロンプト、WSL の Ubuntu など）を開く**

2. **作業フォルダに移動する**
   ファイルを保存したい場所に移動します：

3. **リポジトリをクローンする**

   ```bash
   git clone https://github.com/ユーザー名/labo-hp.git
   ```

   ※実際の URL はプロジェクト管理者に確認してください。

4. **プロジェクトフォルダに移動する**
   ```bash
   cd labo-hp
   ```

## Node.js と npm の準備

### Node.js とは？

Node.js は、JavaScript をブラウザ以外の環境（パソコン上など）で動かすためのソフトウェアです。npm は「Node Package Manager」の略で、JavaScript のライブラリやツールをインストールするために使います。

### Node.js のインストール

#### Windows（WSL）の場合

nodebrew を使って Node.js をインストールします：

1. **Homebrew のインストール**

```bash
# Homebrewのインストール
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# PATHの設定
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.bashrc
source ~/.bashrc
```

2. **nodebrew のインストール**

```bash
# Homebrewを使ってnodebrewをインストール
brew install nodebrew
```

3. **Node.js のインストール**

```bash
# 最新のLTS版をインストール
nodebrew install-binary stable

# インストールしたバージョンを使用するように設定
nodebrew use stable
```

#### macOS の場合

Homebrew を使って Node.js をインストールします：

1. **Homebrew のインストール**

```bash
# Homebrewのインストール
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# PATHの設定（M1/M2 Macの場合）
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
source ~/.zshrc
```

2. **nodebrew のインストール**

```bash
# Homebrewを使ってnodebrewをインストール
brew install nodebrew
```

3. **Node.js のインストール**

```bash
# 最新のLTS版をインストール
nodebrew install-binary stable

# インストールしたバージョンを使用するように設定
nodebrew use stable
```

### バージョン確認

Node.js と npm が正しくインストールされたか確認します：

```bash
node -v
npm -v
```

それぞれバージョン番号が表示されれば成功です！

## 依存パッケージのインストール

プロジェクトで使用している外部ライブラリやツールをインストールします。

```bash
# プロジェクトフォルダ内で実行
npm install
```

このコマンドは`package.json`ファイルに記載されているすべての依存パッケージをインストールします。インストールには少し時間がかかる場合があります。

## 次のステップ

環境構築が完了したら、[動作確認方法](./03-testing-guide.md)に進み、ウェブサイトが正しく動作するか確認しましょう。
