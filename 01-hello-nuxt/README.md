# 01-hello-nuxt


## やること

ゼロの状態からNuxt.jsをインストールして、「Hello, Nuxt !!」と表示してみましょう。


## 学習のポイント

- [] aaa
- [] bbb
- [] ccc


## 手順

1. [ディレクトリの作成](#ディレクトリの作成)
2. [package.jsonの作成](#package.jsonの作成)
3. [Nuxt.jsのインストール](#Nuxt.jsのインストール)
4. [pagesディレクトリの作成](#pagesディレクトリの作成)
5. [index.vueの作成](#index.vueの作成)
6. [開発サーバの起動](#開発サーバの起動)
7. [ブラウザで確認](#ブラウザで確認)


## ディレクトリの作成

- ホーム直下に「hello-nuxt」というディレクトリを作成してください。

```sh
$ cd ~
$ mkdir hello-nuxt
$ cd hello-nuxt
```


## package.jsonの作成

- 「hello-nuxt」ディレクトリ直下に、「package.json」を作成し、以下の内容を書いて保存してください。

```json
{
  "name": "hello-nuxt",
  "scripts": {
    "start": "nuxt"
  }
}
```


## Nuxt.jsのインストール

- 「hello-nuxt」ディレクトリ直下で、以下を実行してください。

```sh
$ npm install --save nuxt
```


## pagesディレクトリの作成

- 「hello-nuxt」ディレクトリ直下に、「pages」ディレクトリを作成してください。

```sh
$ mkdir pages
```


## index.vueの作成

- 「pages」ディレクトリ直下に「index.vue」を作成し、以下の内容を書いて保存してください。

```html
<template>
  <h1>Hello,Nuxt !!</h1>
</template>
```


## 開発サーバの起動

- 「hello-nuxt」ディレクトリ直下で、以下を実行してください。

```sh
$ npm start
```


## ブラウザで確認

- Webブラウザで「 http://localhost:3000 」にアクセスしてみましょう。
- 「Hello, Nuxt !!」と表示されていればOKです。


## (再) 学習のポイント

- [] aaa
- [] bbb
- [] ccc
