---
title: "Alpin eLinuxを1年くらい使ってわかったメリットとデメリット"
emoji: "🐧"
type: "idea"
topics: ["Linux", "AlpineLinux", "比較"]
published: false
---

皆さんはLinuxを使っているでしょうか?

私はLinuxが好きで、この記事もArch Linux上のSwayWMで動かしているFirefox Developer Editionで書いています。

友達の[にしさんはLinuxが嫌いでNetBSD使い](https://nishi.boats/mejp/)だったり、
私の尊敬する[テクニカル諏訪子さんはLinuxが嫌いでOpenBSD使い](https://technicalsuwako.moe/blog/digital-autonomy-linux-to-openbsd.xhtml)だったりしますが、
私はまだLinuxが大好きです。

前置きはこのくらいにして、Alpine Linuxを知っているでしょうか?
よくDockerのベースイメージにされるやつです。

私はそんなAlpine Linuxを[ディスクレスモード](https://wiki.alpinelinux.org/wiki/Installation#Diskless_Mode)でサブPCにインストールして使っています。

サブPCのスペック

| key | value |
| --- | --- |
| Name | Asus EeePC S101 |
| CPU | Intel Atom N270 1.6GHz (1C2T) |
| MEM | 2GB (換装済み) |
| ストレージ | 32GB SDHC (内蔵SSDは壊れた) |
| Wi-Fi | IEEE 802.11 bgn |
| Bluetooth | なし (抜いた) |
| ディスプレイ | 1024x600 |

これは貰い物で、最初はLinux Mint、ZorinOS、openSUSE、NetBSD、antiXなどを入れてGUIで使っていましたが、
最終的に現在のAlpine Linuxをインストールしてサーバー用途に使用し10か月くらい立ちました。

ここからは使っていくうちにわかったAlpine Linuxのメリットとデメリットを紹介します。


# メリット

## 小さい
