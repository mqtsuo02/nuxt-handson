# 03-vuetify


## やること

Vuetify.jsを使って、マテリアルデザインに適応したコンポーネントを実装しましょう。


## 学習のポイント

- [ ] aaa
- [ ] bbb
- [ ] ccc


## 手順

`03-api-connection`で使用したプロジェクトに追加実装していきます。

1. [](#)



## Vuetify.jsの導入

- プロジェクトにVuetify.jsを導入します。
- 今回は[`@nuxtjs/vuetify`パッケージ](https://github.com/nuxt-community/modules/tree/master/packages/vuetify)を使用します。
- `package.json`の`dependencies`に`"@nuxtjs/vuetify": "0.4.3"`を追加してください。
- 追加したら、`$ npm install`を実行してください。

**/package.json**

```json
{
  "name": "hello-nuxt",
  "dependencies": {
    "@nuxtjs/vuetify": "0.4.3",
    "axios": "0.18.0",
    "nuxt": "2.3.4"
  },
  "scripts": {
    "start": "nuxt"
  }
}
```

- `/nuxt.config.js`を作成し、以下の内容を書いて保存してください。
- `vuetify.theme`にカラーテーマを設定することができます。
- 便利な[Theme generator](https://vuetifyjs.com/ja/theme-generator)が利用できます。

```
module.exports = {
  modules: ["@nuxtjs/vuetify"],
  vuetify: {
    theme: {
      primary: "#009688",
      secondary: "#80CBC4",
      accent: "#1565C0",
      error: "#f44336",
      warning: "#ffeb3b",
      info: "#2196f3",
      success: "#4caf50"
    }
  }
};
```

これで`Vuetify.js`を使う準備が整いました。


## Vuetify.jsの使い方

- [Vuetify.jsのサイト](https://vuetifyjs.com/ja/)の`UI components`のメニューからコンポーネントを探して実装していきます。
- コンポーネントの詳細ページでデモやサンプルコード、APIを確認することができます。
- 基本的にはサンプルコードをベースに、APIを見ながらカスタマイズした上でプロジェクトに実装していきます。


## 基本レイアウトの実装

- [Pre-defined layouts](https://vuetifyjs.com/ja/layout/pre-defined)の`Default application markup`を参考にレイアウトを実装していきます。
- 全体を`v-app`タグでラップし、`v-navigation-drawer`と`v-toolbar`については`menu-list`で実装することとします。

```html
<template>
  <v-app>
    <menu-list />
    <v-content>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import MenuList from "~/components/MenuList";

export default {
  components: { MenuList }
};
</script>
```


## Navigation drawerとToolbarの導入

- [Toolbar](https://vuetifyjs.com/ja/components/toolbars)と[Navigation drawer](https://vuetifyjs.com/ja/components/navigation-drawers)を導入します。
- `/components/MenuList.vue`を以下のように実装してください。
- `data`でdrawerの表示と非表示のフラグを定義し、`v-navigation-drawer`タグの`v-model`に渡しています。
- `v-toolbar-side-icon`タグの`@click`でフラグを切り替えています。

**/components/MenuList.vue**

```html
<template>
  <div>
    <v-navigation-drawer app v-model="drawer">
      <v-list>
        <v-list-tile @click="route('/')">
          <v-list-tile-content>
            <v-list-tile-title>HOME</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
        <v-list-tile @click="route('/items')">
          <v-list-tile-content>
            <v-list-tile-title>ITEMS</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar app dark color="primary">
      <v-toolbar-side-icon  @click="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title>Item Management System</v-toolbar-title>
    </v-toolbar>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      drawer: false
    };
  },
  methods: {
    route(url) {
      this.$router.push(url)
    }
  }
};
</script>
```
