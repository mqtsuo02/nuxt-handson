# 03-api-connection


## やること

axoisを導入して、WebAPIを繋ぎこみましょう。


## 学習のポイント

- [ ] `script`タグ内で外部モジュールをimportする
- [ ] `asyncData`メソッドをつかうと、コンポーネントのロード前に処理ができる
- [ ] `asyncData`メソッドのreturnで、`data`を更新することができる


## 手順

`02-routing`で使用したプロジェクトに追加実装していきます。

1. [APIモックサーバの起動](#APIモックサーバの起動)
2. [axiosのインストール](#axiosのインストール)
3. [アイテム一覧の繋ぎこみ](#アイテム一覧の繋ぎこみ)
4. [アイテム詳細の繋ぎこみ](#アイテム詳細の繋ぎこみ)


## APIモックサーバの起動

- `99-api-mock`に実装済みのAPIモックがあります。
- `$ npm install`後に`$ npm start`を実行することで、`http://localhost:3001`に起動します。
- 起動できたら`curl`コマンドを使って、Itemsのデータが取得できるか確認してください。

```sh
$ cd 99-api-mock
$ npm install
$ npm start

$ curl http://localhost:3001/items
$ curl http://localhost:3001/items/1
```


## axiosのインストール

- プロジェクトにaxiosを導入します。
- `package.json`の`dependencies`に`"axios": "0.18.0",`を追加してください。
- 追加したら、`$ npm install`を実行してください。

**/package.json**

```json
{
  "name": "hello-nuxt",
  "dependencies": {
    "axios": "0.18.0",
    "nuxt": "2.3.4"
  },
  "scripts": {
    "start": "nuxt"
  }
}
```


## アイテム一覧の繋ぎこみ

- `/pages/items/index.vue`の`script`タグ内を以下のように実装してください。
- `script`タグで`axios`をimportしています。
- `asyncData`はコンポーネントのロード前に呼び出され、結果が`data`とマージされるメソッドです。

**/pages/items/index.vue**

```html
<template>
  <div>
    <h1>Items</h1>
    <table border="1">
      <thead>
        <tr>
          <th>id</th>
          <th>name</th>
          <th>price</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{item.id}}</td>
          <td>
            <router-link :to="'/items/' + item.id">{{item.name}}</router-link>
          </td>
          <td>{{item.price}}</td>
        </tr>
      </tbody>
    </table>
    <button>
      <router-link to="/items/new">Add Item</router-link>
    </button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      items: []
    };
  },
  asyncData: async function () {
    const response = await axios.get("http://localhost:3001/items")
    return { items: response.data }
  }
};
</script>
```

### ここまで実装できたら

- アイテム一覧にWebAPIから取得したデータが表示されていることを確認してください。(５つのItemが表示されます)


## アイテム詳細の繋ぎこみ

- `/pages/items/_id.vue`を以下のように実装してください。
- `asyncData`内では`context`オブジェクトを使用することができます。
- `context.params`は`$route.params`のエイリアスになっています。
- `template`は取得したデータを表示できるように追加実装しています。

**/pages/items/index.vue**

```html
<template>
  <div>
    <h1>Items Id</h1>
    <ul>
      <li>id: {{item.id}}</li>
      <li>name: {{item.name}}</li>
      <li>price: {{item.price}}</li>
      <li>description: {{item.description}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: function() {
    return {
      item: {}
    };
  },
  asyncData: async function (context) {
    const response = await axios.get(`http://localhost:3001/items/${context.params.id}`)
    return { item: response.data }
  }
};
</script>
```

### ここまで実装できたら

- 各アイテム詳細にWebAPIから取得したデータが表示されていることを確認してください。


## (再) 学習のポイント

- [x] `script`タグ内で外部モジュールをimportする
- [x] `asyncData`メソッドをつかうと、コンポーネントのロード前に処理ができる
- [x] `asyncData`メソッドのreturnで、`data`を更新することができる
