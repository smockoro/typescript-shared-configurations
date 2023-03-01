# 設定の共通化方法

[公式情報](https://prettier.io/docs/en/configuration.html#sharing-configurations)[^sharing-config]
を参考に設定の共通化を考える。

[^sharing-config]: https://prettier.io/docs/en/configuration.html#sharing-configurations


<!-- vim-markdown-toc GFM -->

* [NPM パッケージでの共通化と展開](#npm-パッケージでの共通化と展開)
* [共通定義リポジトリに複数の共通定義を入れる方法](#共通定義リポジトリに複数の共通定義を入れる方法)
* [共通定義リポジトリ内での定義の共通化方法](#共通定義リポジトリ内での定義の共通化方法)

<!-- vim-markdown-toc -->

## NPM パッケージでの共通化と展開

npm のパッケージで展開するのが便利。

パッケージ名は npm の慣習に従って、`@scope/prettier-config`のようにするのが良い。

取り込まれる側は、`index.js`にベースになる設定を記載する。

取り込む側は取り込み方が以下 2 種類存在する。

- `package.json`の`pretter`部にパッケージ名を記載して取り込む
- 自リポジトリの`.prettierrc.js`で`require`で取り込む

それぞれの定義例は以下の通り。

**`package.json`の`pretter`部にパッケージ名を記載して取り込む**

```json
{
  "name": "@scope/example-use-shared-config",
  "version": "X.Y.Z",
  "prettier": "@scope/prettier-config" // 適切な名前に置き換える。本例では上述の名前を利用。
  ...
}
```

**自リポジトリの`.prettierrc.js`で`require`で取り込む**

```javascript
module.exports = {
  ...require("@scope/prettier-config"), // 適切な名前に置き換える。本例では上述の名前を利用。
  semi: false, // この部分は共通定義を上書きしてくれる。
};
```

それぞれのメリット・デメリットは以下の通り。

| 観点               | `package.json`内での取り込み | 設定ファイルでの取り込み |
| ------------------ | ---------------------------- | ------------------------ |
| 設定の上書き       | ✕                            | ○                        |
| 設定ファイルの要否 | いらない                     | 個別作成                 |

上記のため、デフォルト設定をそのまま利用する場合は、`package.json`で取り込んでしまうのが便利。

個別定義上書きが必要になるのであれば、後々でも設定ファイルを作成して取り込めば良い。

ただし、prettier は`.json`や`.yaml`等複数の拡張子に対応しているが、`.js`拡張子に限定される。
(ので基本 prettier の設定ファイルは`.js`拡張子が推奨)

## 共通定義リポジトリに複数の共通定義を入れる方法

TBD

## 共通定義リポジトリ内での定義の共通化方法

TBD
