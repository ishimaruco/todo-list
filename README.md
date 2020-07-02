# 筋トレ用TODOリスト

## 1.仕様
### 1-1. 対象環境
環境は以下の通り

- OS
    - Windows7
    - macOS 10.15~
    - iOS 12~
    - android 7.x ~ 8.x

- ブラウザ
    - PC
        - Edge
        - Chrome 最新
        - Firefox 最新
        - Safari 最新
    - SP
        - Android Chrome
        - iOS Safari

### 1-2.開発環境
以下の構成

#### フロントエンド
- HTML
- CSS
- TypeScript
- Vue.js
- Nuxt.js

#### バックエンド
- TypeScript
- Nest.js
- node.js
- Express

#### インフラ環境
- AWS

#### データベース
- MySQL

### 1-3.ディレクトリ・ファイル命名

リソースファイルの命名・配置は以下の通り

#### 命名基本方針
- 小文字を基本とした半角英数、アンダースコア`_`、ハイフン`-`から構成

##### ディレクトリ配置規則
TBD

##### ファイル命名規則
TDB

##### 画像命名規則
TDB

## 2.コーディングルール
### 2-1 パス記述
- ルート相対パス

### HTML
- 文字コード： UTF-8
- インデント：スペース4つ

### CSS
- 文字コード：UTF-8
- インデント：なし

#### ID,Class命名規則
- Block,Element,Modifierの要素をベースにしたBEMを使用
- BlockとElementは`_`（アンダースコア）1つで区切る
- ElementとModifierは`-`（ハイフン）1つで区切る
- 複数の単語同士はキャメルケースで記述
    - 例：`.block_elementElement-modifier`

- TypeScript側で吐き出すclass属性がある場合、接頭辞に`ts-`を必ずつける
    - 例`.block_elementElement-modifier .ts-active`

- コンポーネントの要素については接頭辞に名前空間を与える
    - グローバル要素：g-
    - レイアウト要素：l-
    - コンポーネント：c-
    - ユーティリティ：u-

### TypeScript
- 文字コード：UTF-8
- 可読性確保のため適宜コメントを記述

## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).