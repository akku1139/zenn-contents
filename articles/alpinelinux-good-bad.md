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

Alpine LinuxはLinux 3大デカいパッケージ(小泉構文)(諸説あり)である

- Systemd ([32MB](https://archlinux.org/packages/core/x86_64/systemd/))
- The GNU C Library (glibc) ([47MB](https://archlinux.org/packages/core/x86_64/glibc/))
- GNU Core Utilities (coreutils) ([15MB](https://archlinux.org/packages/core/x86_64/coreutils/))

が含まれません。
代わりに

- OpenRC ([1.6MB](https://pkgs.alpinelinux.org/package/edge/main/x86_64/openrc))
- musl libc ([664KB](https://pkgs.alpinelinux.org/package/edge/main/x86_64/musl))
- BusyBox ([798KB](https://pkgs.alpinelinux.org/package/edge/main/x86_64/busybox))

が使用されます。
めっちゃ小さいですね。

## パッケージマネージャが速い

Alpine Linuxが採用しているパッケージマネージャの `apk` は爆速です。

体感レベルの話ですが、 `apt` の3倍は速いと思います。

Arch Linuxの `pacman` より速いです。

スペックの低いマシンではこの差がかなり顕著に出ます。

それぞれのパッケージマネージャ自体のサイズを比較すると

| パッケージマネージャ | ディストリビューション | サイズ | リンク |
| --- | --- | --- | --- |
| apk | Alpine Linux | 300KB | https://pkgs.alpinelinux.org/package/edge/main/x86_64/apk-tools |
| pacman | Arch Linux | 4.8MB | https://archlinux.org/packages/core/x86_64/pacman/ |
| apt + dpkg | Debian | 4MB + 6MB | https://packages.debian.org/bookworm/apt https://packages.debian.org/bookworm/dpkg |

となります。実際は依存関係も有りますがapkは一番小さいです。
