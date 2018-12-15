# 01-hello-nuxt


## やること

ゼロの状態からNuxt.jsをインストールして、「Hello, Nuxt!!」と表示してみましょう。


## 手順

1. [作業用ディレクトリの作成](#作業用ディレクトリの作成)
2. [package.jsonの作成](#package.jsonの作成)
3. [Nuxt.jsのインストール](#Nuxt.jsのインストール)
4. [pagesディレクトリの作成](#pagesディレクトリの作成)
5. [index.vueの作成](#index.vueの作成)
6. [開発サーバの起動](#開発サーバの起動)
7. [ブラウザで確認](#ブラウザで確認)
8. [ホットリロードの確認](#ホットリロードの確認)


## 作業用ディレクトリの作成

- 作業用のディレクトリを作成してください。
- 例では、ホーム直下に`hello-nuxt`というディレクトリを作成します。

```sh
$ cd ~
$ mkdir hello-nuxt
$ cd hello-nuxt
```


## package.jsonの作成

- 作業ディレクトリ直下に、`package.json`を作成し、以下の内容を書いて保存してください。
- `npm start`で`node_modules/.bin/nuxt`が実行されるようにスクリプトを定義します。

**/package.json**

```json
{
  "name": "hello-nuxt",
  "dependencies": {
    "nuxt": "2.3.4"
  },
  "scripts": {
    "start": "nuxt"
  }
}
```


## Nuxt.jsのインストール

- 作業用ディレクトリ直下で、以下を実行してください。
- `package.json`に従ってNuxt.jsがインストールされます。

```sh
$ npm install
```


## pagesディレクトリの作成

- 作業用ディレクトリ直下に、`pages`ディレクトリを作成してください。

```sh
$ mkdir pages
```


## index.vueの作成

- `pages`ディレクトリ直下に`index.vue`を作成し、以下の内容を書いて保存してください。

```html
<template>
  <h1>Hello, Nuxt!!</h1>
</template>
```


## 開発サーバの起動

- 作業用ディレクトリ直下で、以下を実行してください。

```sh
$ npm start
```


## ブラウザで確認

- Web ブラウザで `http://localhost:3000` にアクセスしてみましょう。
- 「Hello, Nuxt!!」と表示されていればOKです。


## ホットリロードの確認

- `index.vue`内のテキストを変更すると、自動的にビルドされ Webブラウザに反映されます。
