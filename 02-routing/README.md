# 02-routing


## やること

Nuxt.jsのルーティング機能を使って、画面遷移を実装してみましょう。


## 学習のポイント

- [ ] aaa
- [ ] bbb
- [ ] ccc


## 手順

`01-hello-nuxt`で作成したプロジェクトに追加実装していきます。

1. [設計の確認](#設計の確認)
2. [vueファイルの作成](#vueファイルの作成)
3. [メニューコンポーネントの実装](#メニューコンポーネントの実装)
4. [レイアウトファイルの実装](#レイアウトファイルの実装)
5. [アイテム一覧の実装](#アイテム一覧の実装)
6. [アイテム詳細の実装](#アイテム詳細の実装)


## 設計の確認

今回は例として「Item Managemant System」を実装します。


### 画面一覧

|画面名|URL|作成するファイル|
|---|---|---|
|ホーム|/|/pages/index.vue|
|アイテム一覧|/items|/pages/items/index.vue|
|アイテム詳細|/items/:id|/pages/items/_id.vue|
|アイテム新規作成|/items/new|/pages/items/new.vue|


### 画面遷移

- 初期表示は`ホーム`
- メニューから`ホーム`と`アイテム一覧`に遷移可能
- `アイテム一覧`で任意のアイテムを押すと`アイテム詳細`に遷移
- `アイテム一覧`で追加ボタンを押すと`アイテム新規作成`に遷移


### Itemオブジェクトのプロパティ

Itemは以下のプロパティを持ちます。

|プロパティ名|型|
|---|---|
|id|Number|
|name|String|
|price|Number|
|description|String|


## vueファイルの作成

- Nuxt.jsでは`pages`配下のディレクトリとファイル名によって、ルーティングが設定されます。
- 動的なルーティングを設定する場合は、ファイル名やディレクトリ名の先頭にアンダースコアをつけます。
- `/pages/items`ディレクトリを作成して、その配下に３つのファイルを作成してください。

**/pages/items/index.vue**

```html
<template>
  <h1>Items</h1>
</template>
```

**/pages/items/_id.vue**

```html
<template>
  <h1>Items Id</h1>
</template>
```

**/pages/items/new.vue**

```html
<template>
  <h1>Items New</h1>
</template>
```

### ここまで実装できたら

- Webブラウザから以下のURLでアクセスできることを確認してください。
- `/items/1`のidにあたる部分は、何を入れても動的にルーティングされます。(`new`の場合を除く)

`http://localhost:3000/items`  
`http://localhost:3000/items/1`  
`http://localhost:3000/items/new`


## メニューコンポーネントの実装

- 今回はメニューコンポーネントを実装し、それぞれのページに組み込んで使用します。
- `/components/MenuList.vue`ファイルを作成してください。
- このとき、`pages`ディレクトリの外で作成していることを確認してください。
- HTMLタグとの名前衝突を防ぐため、コンポーネント名は複数単語で作成しなければなりません。 <[Vue/スタイルガイド](https://jp.vuejs.org/v2/style-guide/index.html)>


**/components/MenuList.vue**

```html
<template>
  <div>
    <ul>
      <li><router-link to="/">HOME</router-link></li>
      <li><router-link to="/items">ITEMS</router-link></li>
    </ul>
    <hr />
  </div>
</template>
```


## レイアウトファイルの実装

- 作成したコンポーネントを全てのページに組み込むために、レイアウトファイルを実装します。
- `/layouts/default.vue`ファイルを作成してください。
- `script`タグで`MenuList`コンポーネントを読み込みます。
- templateでは`menu-list`のようにケバブケースにします。
- 各ページを挿入したい部分に`nuxt`タグを書きます。

**/layouts/default.vue**

```html
<template>
  <div>
    <menu-list />
    <nuxt />
  </div>
</template>

<script>
import MenuList from "~/components/MenuList";

export default {
  components: { MenuList }
};
</script>
```

### ここまで実装できたら

- 各ページでメニューが表示され、画面遷移が正常にできることを確認してください。


## アイテム一覧の実装

- `/pages/items/index.vue`を以下のように実装してください。
- `script`タグ内の`data`でItemsの配列を定義しています。
- `v-for`で`items`を`item`として展開しています。
- `router-link`タグの`to属性`に遷移先のURLで使用する`id`を入れています。

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
export default {
  data: function() {
    return {
      items: [
        {
          id: 1,
          name: "apple",
          price: 120
        },
        {
          id: 2,
          name: "banana",
          price: 80
        }
      ]
    };
  }
};
</script>
```

### ここまで実装できたら

- アイテム一覧の各データの名前を押したときに、各詳細画面のURLに遷移することを確認してください。
- 追加ボタンを押したときに、新規作成画面に遷移することを確認してください。


## アイテム詳細の実装

- 今回はルーターからidを取得して画面上に表示する実装をします。
- 実際の開発では、idをもとにWebAPIを叩いて詳細データを取得するのが一般的です。(`03-api-connection`で実装します)
- `/pages/items/_id.vue`を以下のように実装してください。
- `data`の`function(){}`内の`this`でコンポーネントのインスタンスを取得できます。
- `$route`オブジェクトがルーティングに関する情報です。

**/pages/items/_id.vue**

```html
<template>
  <div>
    <h1>Items Id</h1>
    <h2>{{id}}</h2>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      id: this.$route.params.id
    };
  }
};
</script>
```

### ここまで実装できたら

- 詳細画面でidが表示できていることを確認してください。


## (再) 学習のポイント

- [x] aaa
- [x] bbb
- [x] ccc
