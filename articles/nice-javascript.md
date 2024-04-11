---
title: "野蛮な言語であるJavaScriptを3+αステップで文明的な言語にする方法"
emoji: "🪨"
type: "tech"
topics: ["JavaScript", "TypeScript", "雑記"]
published: false
---

:::message
この記事には個人の主観が多く含まれることに注意してください
:::

# TL;DR

1. `var` をやめよう → `const` か `let`
2. `function` をやめよう → `const` とアロー関数
3. `import` で始まり `export` で終わるようにしよう
4. TypeScriptを使おう

# あなたのJavaScriptは野蛮な言語です

例えば、こんなコードを書いていませんか?

```js
var data = 10
function b(c) {
  c--
	console.log(c)
  if(c = 5)
  	b(c)
}
var data = 7
b(data)
```

このコードにはあらゆる危険が含まれています。

## `var` の使用

`var` は

- グローバルスコープ
- 再宣言可能

で危険な変数宣言です。

コードをよく見てください。
最初に `var data = 10` と定義されていますが、`b()` の呼び出し前に `var data = 7` と再宣言されています。

どちらが本来の意図でしょうか?

代わりに `const` か `let` を使ってください。
もちろん再宣言はエラーとなります。

![エラー](/images/nice-javascript/const-let-error.png)

原則的に `const` を使ってください。
どうしても再代入したい場合は `let` を使います。

![再代入できるconst](/images/nice-javascript/reassign-const.png)

但し、このような操作は許可されます。
