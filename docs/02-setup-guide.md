# 環境構築方法

このガイドでは、開発環境を一から構築する方法を説明します。

## 目次

1. [Windowsユーザー向け: WSLのセットアップ](#windowsユーザー向け-wslのセットアップ)
2. [GitとGitHubの基本](#gitとgithubの基本)
3. [リポジトリのクローン](#リポジトリのクローン)
4. [Node.jsとnpmの準備](#nodejsとnpmの準備)
5. [依存パッケージのインストール](#依存パッケージのインストール)

## Windowsユーザー向け: WSLのセットアップ

WSL（Windows Subsystem for Linux）は、Windows上でLinux環境を利用できるようにする機能です。ウェブ開発では多くのツールがLinux環境を前提としているため、WSLを使うとトラブルが少なくなります。

### WSLのインストール手順

- [公式ドキュメント](https://learn.microsoft.com/ja-jp/windows/wsl/install)
- 「Ubuntu」アプリを開くことでLinuxターミナルを使えるようになります。

## GitとGitHubの基本

### GitとGitHubの違い

初心者の方のために、GitとGitHubの違いを簡単に説明します：

#### Gitとは？

- ローカル（あなたのパソコン）で動作するバージョン管理ツール
- コードの変更履歴を記録・管理する
- コマンドラインで操作する
- パソコンにインストールして使う

#### GitHubとは？

- Gitで管理したコードをクラウド上に保存・共有できるサービス
- ウェブブラウザで操作できる
- チーム開発がしやすい
- コードのバックアップとしても使える
- ウェブサイトのホスティングにも使える（今回のプロジェクトではこれを使用）

簡単に言うと：

- Git = コードの変更履歴を管理するツール
- GitHub = Gitで管理したコードを保存・共有するためのクラウドサービス

### GitHubのアカウント作成

1. [GitHub](https://github.com/)にアクセス
2. 「Sign up」をクリック
3. メールアドレス、パスワード、ユーザー名を入力
4. メール認証を完了

### Gitのインストール

#### Windows（WSL）の場合

WSL上のUbuntuには、通常Gitが最初からインストールされています。確認するには：

```bash
git --version
```

#### macOSの場合

macOSには、通常Gitが最初からインストールされています。確認するには：

ターミナルで以下のコマンドを実行：

```bash
git --version
```

もしインストールされていなければ、Gitのインストーラが自動的に表示されます。

### Gitの基本設定

Gitをインストールしたら、まず自分の情報を設定します：
ここでのメールアドレス、名前はGitHubに登録してあるユーザー名とメールアドレスを推奨します。

```bash
git config --global user.name "あなたの名前"
git config --global user.email "あなたのメールアドレス"
```

## リポジトリのクローン

リポジトリのクローンとは、Gitで管理されているプロジェクトをあなたのパソコンにコピーすることです。

### クローンの手順

1. **ターミナル（コマンドプロンプト、WSLのUbuntuなど）を開く**

2. **作業フォルダに移動する**
   ファイルを保存したい場所に移動します：

3. **リポジトリをクローンする**

   ```bash
   git clone https://github.com/ユーザー名/labo-hp.git
   ```

   ※実際のURLはプロジェクト管理者に確認してください。

4. **プロジェクトフォルダに移動する**
   ```bash
   cd labo-hp
   ```

## Node.jsとnpmの準備

### Node.jsとは？

Node.jsは、JavaScriptをブラウザ以外の環境（パソコン上など）で動かすためのソフトウェアです。npmは「Node Package Manager」の略で、JavaScriptのライブラリやツールをインストールするために使います。

### Node.jsのインストール

#### Windows（WSL）の場合

nodebrewを使ってNode.jsをインストールします：

1. **Homebrewのインストール**

```bash
# Homebrewのインストール
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# PATHの設定
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.bashrc
source ~/.bashrc
```

2. **nodebrewのインストール**

```bash
# Homebrewを使ってnodebrewをインストール
brew install nodebrew
```

3. **Node.jsのインストール**

```bash
# 最新のLTS版をインストール
nodebrew install-binary stable

# インストールしたバージョンを使用するように設定
nodebrew use stable
```

#### macOSの場合

Homebrewを使ってNode.jsをインストールします：

1. **Homebrewのインストール**

```bash
# Homebrewのインストール
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# PATHの設定（M1/M2 Macの場合）
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
source ~/.zshrc
```

2. **nodebrewのインストール**

```bash
# Homebrewを使ってnodebrewをインストール
brew install nodebrew
```

3. **Node.jsのインストール**

```bash
# 最新のLTS版をインストール
nodebrew install-binary stable

# インストールしたバージョンを使用するように設定
nodebrew use stable
```

### バージョン確認

Node.jsとnpmが正しくインストールされたか確認します：

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
