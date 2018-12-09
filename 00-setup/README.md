# 00-setup

## Node.jsバージョン

このリポジトリは、以下の環境で作成されています。  
動作しない場合は、バージョンを確認してください。

- node v10.14.1
- npm 6.4.1


## エディタ

便利なプラグインが利用できる、以下のエディタがオススメです。

- Visual Studio Code
- Atom


## Visual Studio Code の便利なプラグイン

|||
|:---|:---|
|Vetur|Vue.jsのシンタックスハイライト|
|Prettier - Code formatter|JSコードの自動整形ツール|

setting.jsonで以下を追加
```json
"[javascript]": {
    "editor.formatOnSave": true
}
```

## Atom の便利なプラグイン

|||
|:--|:--|
|language-vue-component|Vue.jsのシンタックスハイライト|
|prettier-atom|JSコードの自動整形ツール|
