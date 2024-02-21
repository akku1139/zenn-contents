---
title: "使って気がついた、Astroの問題点"
emoji: "🚀"
type: "tech"
topics: ["Astro"]
published: false
publication_name: "trans"
---

こんにちは。生徒会情報機構（TRANs）の[公式Webサイト](https://trans.stki.org)を作っているakkuです。
TRANs公式サイトではフレームワークとしてAstroを使っていますが、開発をしているといくつかの問題点が見えてきたので紹介しようと思います。

# 依存関係が大きい
1. `$ npm create astro` (Template: Empty)
2. `$ du -h -d0 --total node_modules/`
するとどうでしょうか? 結果はこちらです。
```sh
155M	node_modules/
155M	total
```
なんと150MBも依存関係があります! また、インストールされたパッケージは495もあります。
(ちなみにSvelteKitの空プロジェクトを作った場合は70MB/130パッケージ程度でした。)
しかし実際に作るサイトにこれほどの機能は必要ありません。
Astroは必要とやりすぎを勘違いしています!
UNIXを見習ってください。

例えば、UNIXという考え方には
> スモール・イズ・ビューティフル

という定理が書かれています。

例えば、Life with UNIXには

> 10%-90%の法則
> UNIXのテープアクセスは10%-90%の法則の典型的な例である。
> つまり、テープのサポートは簡単なものでしかない(10%の作業)が、非常に実用的(問題の90%を解決する)なのだ。

(改行はakkuによるもの)
が書かれています。

例えば、The Art of UNIX Programmingには

> モジュール化の原則
があります。


少なくとも150MBの依存関係が「スモール」では無いことは事実でしょう。

#
