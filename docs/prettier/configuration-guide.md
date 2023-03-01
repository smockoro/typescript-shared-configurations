# 設定値の検討

設定値の一覧は[公式](https://prettier.io/docs/en/options.html)[^prettier-config-list]参照。

[^prettier-config-list]: https://prettier.io/docs/en/options.html

ここでは、個別に共通定義を作る場合、どういった検討をして設定値を決めたのか記載する。

<!-- vim-markdown-toc GFM -->

* [設定値一覧](#設定値一覧)
* [各設定値の設定根拠](#各設定値の設定根拠)
  * [`printWidth`](#printwidth)
  * [`tabWidth`](#tabwidth)
  * [`useTabs`](#usetabs)
  * [`semi`](#semi)
  * [`singleQuote`](#singlequote)
  * [`Quote Props`](#quote-props)
  * [`jsxSingleQuote`](#jsxsinglequote)
  * [`Trailing Commas`](#trailing-commas)
  * [`Bracket Spacing`](#bracket-spacing)
  * [`Bracket Line`](#bracket-line)
  * [[Deprecated]`jsxBracketSameLine`](#deprecatedjsxbracketsameline)
  * [`Arrow Function Parentheses`](#arrow-function-parentheses)
  * [`Range`](#range)
  * [`Parser`](#parser)
  * [`File Path`](#file-path)
  * [`Require Pragma`](#require-pragma)
  * [`Insert Pragma`](#insert-pragma)
  * [`Prose Wrap`](#prose-wrap)
  * [`HTML Whitespace Sensitivity`](#html-whitespace-sensitivity)
  * [`Vue files script and style tags indentation`](#vue-files-script-and-style-tags-indentation)
  * [`End of Line`](#end-of-line)
  * [`Embedded Language Formatting`](#embedded-language-formatting)
  * [`Single Attribute Per Line`](#single-attribute-per-line)

<!-- vim-markdown-toc -->

## 設定値一覧

以下に設定値一覧を示す。各設定地の根拠は[各設定値の設定根拠](#各設定値の設定根拠)を参照。

| 設定値       | デフォルト値 | 設定値 |
| ------------ | ------------ | ------ |
| `printWidth` | `80`         | ←      |
| `tabWidth`   | `2`          | ←      |

## 各設定値の設定根拠

### `printWidth`

以下公式記載の通り、**80 文字以内が昨今のベストプラクティスのためデフォルト値を推奨。**

> For readability we recommend against using more than 80 characters:
>
> In code styleguides, maximum line length rules are often set to 100 or 120. However, when humans write code, they don’t strive to reach the maximum number of columns on every line. Developers often use whitespace to break up long lines for readability. In practice, the average line length often ends up well below the maximum.
>
> Prettier’s printWidth option does not work the same way. It is not the hard upper allowed line length limit. It is a way to say to Prettier roughly how long you’d like lines to be. Prettier will make both shorter and longer lines, but generally strive to meet the specified printWidth.
>
> Remember, computers are dumb. You need to explicitly tell them what to do, while humans can make their own (implicit) judgements, for example on when to break a line.
>
> In other words, don’t try to use printWidth as if it was ESLint’s max-len – they’re not the same. max-len just says what the maximum allowed line length is, but not what the generally preferred length is – which is what printWidth specifies.

### `tabWidth`

タブでない 2 スペースを利用することが一般的[^tabwidth]。(Airbnb や npm、React でもこれ)

そのため**デフォルト値`2`を推奨。**

[^tabwidth]: https://typescript-jp.gitbook.io/deep-dive/styleguide#supsu

### `useTabs`

`tabWidth`同様。タブでない 2 スペースを利用することが一般的。

そのため**デフォルト値`false`を推奨。**

### `semi`

ステートメントの末尾に`;`を付与するか。

ECMAScript の仕様 TC39 で付与を推奨している。[^semicolons]

[^semicolons]: https://tc39.es/ecma262/#sec-automatic-semicolon-insertion

そのため**デフォルト値`true`を推奨。**

### `singleQuote`

設定値を`true`にすると、エスケープが多い文字列にならないようにしてくれる。

- `'I will be back'`→ そのまま
- `'I\'ll be back'`→`"I'll be back"`(`"`はバッククオートでも可)

原則、文字列は`'`で囲む。`'`をエスケープしないといけない場合、`"`or バッククオートに整形する。

Prettier 公式[^prettier-string]でもこの設定は`true`が推奨。
また、Airbnb や React でも`'`で文字列を囲む。[^singlequote]

そのため**デフォルト値`true`を推奨する。**

[^prettier-string]: https://prettier.io/docs/en/rationale.html#strings
[^singlequote]: https://typescript-jp.gitbook.io/deep-dive/styleguide#yin-yong-fu

### `Quote Props`

オブジェクトのプロパティが引用されたときに変更します。

|設定値候補|概要|推奨|
|`as-needed` | 必要な場合のみ、オブジェクト・プロパティの周りに引用符を追加します。|
|`consistent` | オブジェクトの少なくとも 1 つのプロパティで引用符が必要な場合、すべてのプロパティを引用符で囲みます。|
|`preserve` | オブジェクト・プロパティでの引用符の入力使用を尊重する。|

### `jsxSingleQuote`

JSX での文字列を囲む場合の引用符について。

デフォルトは`false`で`singleQuote`を無視して、`'`ではなく`"`を JSX の場合だけ利用する。

上記設定が Airbnb の JSX スタイルガイド[^airbnb-jsx-styleguide]でも推奨であり、**デフォルト値`false`を推奨する。**

[^airbnb-jsx-styleguide]: https://airbnb.io/javascript/react/#quotes

### `Trailing Commas`

### `Bracket Spacing`

### `Bracket Line`

### [Deprecated]`jsxBracketSameLine`

利用しない。廃止されたらこの項目は削除する。

### `Arrow Function Parentheses`

### `Range`

### `Parser`

### `File Path`

### `Require Pragma`

### `Insert Pragma`

### `Prose Wrap`

### `HTML Whitespace Sensitivity`

TBD

> 一旦TypeScriptのみ考慮するため除外。必要になったら設定値検討する。

### `Vue files script and style tags indentation`

### `End of Line`

### `Embedded Language Formatting`

### `Single Attribute Per Line`
