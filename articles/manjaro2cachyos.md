---
title: "【簡単】ManjaroをCachyOSに交換方法"
emoji: "☕️"
type: "tech"
topics: ["Linux", "Manjaro", "CachyOS"]
published: true
---

皆さんLinux、使っていますか?
Windowsで消耗している方も多いかと思われますが、
今回はManjaroからCachyOSに交換する方法を解説します。

# 何故CachyOS?

CachyOSはArchLinux系のディストリビューションで、高速と安定性をテーマに開発されています。

1. パッケージが最適化れている
O3, LTOを始めとし、pgo, boltと盛り沢山な最適化が行われています。
O3は安全な最適化の中で最も高レベルなもので、
LTOにより呼び出し関係の無駄が省かれ、アプリケーションはより高速に動作します。

3. アーキテクチャに合わせた最適化
LTOのみならず、x86-64-v3 または x86-64-v4 に合わせた最適化の行われているパッケージもあります。
命令セットや内部動作に合わせた最適化によりパフォーマンスがさらに加速されます。

4. かっこいい
デスクトップのデフォルト設定がかっこいいですね。
(私は使っていませんが...)

これは完全にCachyOS一択の流れですね。

## しかしManjaroも素晴らしいディストリビューションです。

ではManjaroのメリットを検討してみましょう。

1. ローリングリリースと安定性の両立
ManjaroはArchLinuxと同じくローリングリリースモデルを採用していますが、
闇雲にパッケージを新しくするのではなく、十分に試験を行ってからリポジトリに追加されます。
これでArchLinux特有の「いつの間にか壊れた」状態を回避できます。
(私はアップデートを3ヶ月放置したので何も問題ありません)

2. GUIツールの充実
ManjaroにはPamacを始めとした素晴らしいGUIツールがあります。
カーネル切り替えツールも実装されているので良いですね。
(私はBootstrapしセットアップしたのでそんなものは入っていません)

3. かっこいい
この項目CachyOSでも見ましたね。
ArchとFedoraはだいたいかっこいいと相場は決まっています。

4. ARMに公式対応がある
ARM勢の皆様に残念なお知らせです。
CachyOSはARMに対応していないためManjaroのARMエディションを使っている方は諦めてください。
ArchLinux ARMの方もここでお帰りください。

ひとつ分かっていることを言えば、ここでManjaroとCachyOSを比較しどちらが優れているのか議論することには何も有益性がないということです。
少なくとも私はCachyOSに交換しました。
では次の章からは実際に換装していきましょう。

# 注意

## この方法を使用した場合、CachyOSのチューニングされた設定は使用されません。

全て終わった後に[CachyOSの設定](https://github.com/CachyOS/CachyOS-Settings)を移植することをおすすめします。
有識者によれば `cachyos-setting` に全て入っている可能性が高いそうです。

## 作業中に絶対再起動しないでください。

途中でカーネルを交換するので起動しなくなる可能性があります。

## 私はやってないですが、一般常識としてバックアップもおすすめします。

## 問題が起きたら自力で解決します

pacmanは不安定なArchLinuxを管理するためのツールです。
そのため、pacmanはほとんど壊れることがありません。
(逆に依存関係のしっかりしているDebianを管理するapt/dpkgはよく壊れます)

# この記事は記憶を元に書いています。

もしかすると忘れてしまったことがあるかもしれないので上手く行かなかったら自分で考えて修正してください。

# 0. 準備

この方法はある程度危険を伴います。
最悪の場合OSが起動しなくなるかもしれないので十分な覚悟は必要です。
また、メモ帳を準備してください。「あとでやる」を忘れないために必要です。

全てのパッケージを交換するので孤児パッケージは削除してしまいましょう。
```
# pacman -Rs $(pacman -Qdtq)
```
普段から `pacman -Rs` でパッケージ削除を行えば孤児パッケージがないのでおすすめです。

問題が発生すれば良くないので、pacmanのキャッシュを削除します。
私はキャッシュをtmpfsに載せているのでこの作業は必要ありません。

```
# pacman -Scc
```
or
```
# rm -r /var/cache/pacman
```

カーネルも交換するのでカーネルパッケージも削除してください。

# 1. リポジトリの交換

CachyOSにはCachyOSのリポジトリとArchLinuxのリポジトリが必要なようです。
まずは[公式Wiki](https://wiki.cachyos.org/cachyos_repositories/how_to_add_cachyos_repo/)に従ってCachyOSのミラーを追加します。

```
$ wget https://mirror.cachyos.org/cachyos-repo.tar.xz
```

```
$ tar xvf cachyos-repo.tar.xz && cd cachyos-repo
```

ここでrootになる必要があります。 私はopendoasを使用しました。
```
# ./cachyos-repo.sh
```
このスクリプトはおそらく失敗しますが問題ありません。

```
$ ls /etc/pacman.d
```
としたときに `cachyos-(|v3-|v4-)mirrorlist` があれば成功です。
ここからはマシンによって少し違います。
`cachyos` だけ追加される場合、`cachyos-v3` や `cachyos-v4` が追加される場合があります。

CPU世代がHaswellならv3 (私の場合)
もっと古ければ `cachyos` のみ
Skylake以降ならv4が追加されると思います。
(v3とv4が同時にあるかはわかりません)

自動で追加されますが、不安がある場合は
```
$ /lib/ld-linux-x86-64.so.2 --help
```
としてください。
最後の行に
```
〜いろいろ〜
Subdirectories of glibc-hwcaps directories, in priority order:
  x86-64-v4
  x86-64-v3 (supported, searched)
  x86-64-v2 (supported, searched)
```
のような表記があると思います。

また、`/etc/pacman.conf` に以下の行が追加されていることを確認してください。
```
[cachyos-v3]
Include = /etc/pacman.d/cachyos-v3-mirrorlist

[cachyos-core-v3]
Include = /etc/pacman.d/cachyos-v3-mirrorlist

[cachyos-extra-v3]
Include = /etc/pacman.d/cachyos-v3-mirrorlist

[cachyos]
Include = /etc/pacman.d/cachyos-mirrorlist
```

上手く行かなかった場合は[公式Wiki](https://wiki.cachyos.org/cachyos_repositories/how_to_add_cachyos_repo/)の `Option 2: Manual Installation` を参考にしながらいい感じにやってください。

この後大量のダウンロード作業を行うため、勇気のある方はCachyOSのmirrorlistでミラー優先順位を変更してください。
韓国のミラーは結構速いと思います。(シンガポールとどちらが良いですか?)

## ここからは公式Wikiに記載がないことを行います。

これまでの手順でCachyOSのレポジトリが追加されましたが、一部のパッケージはArchLinuxのリポジトリから賄う必要があるみたいです。
しかし今はManjaroのmirrorlistが入っています。
この場合あらゆる問題が発生する可能性があるためArchLinuxのmirrorlistに交換します。

何らかの手段を用いてArchLinuxのmirrorlistを手に入れてください。
私は `pacman-mirrorlist` を展開して突っ込みました。

最後に全部のパッケージを再インストールします。

```
# pacman -Qnq | pacman -S - --needed
```

コンフリクトが発生した場合、`pacman -Rd` などで対応してください。
私は `mkinitcpio` と `systemd` がコンフリクトしました。
削除したパッケージは必ずメモしておきましょう。

# 2. Manjaroのパッケージを削除

いくつかのManjaro由来のパッケージが残っていますが、そのパッケージは今後アップデートされなくなるので削除してしまいましょう。

`manjaro-keyring` を始めとするいくつかのパッケージが削除されました。

# 3. 削除したパッケージを戻す

1の工程で削除したパッケージがあると思います。
そのようなパッケージは再度インストールしてください。

# 4. カーネルを選ぶ

一番時間のかかる工程がこれです。
カーネルパッケージを入れてください。

- `-lto` の付いているパッケージを入れる
- `cachyos-v[34]` がある場合はそこから入れる
のがおすすめです。

私は `linux-cachyos-lts-lto` を入れました。
困ったらLTSカーネルを入れれば良いと思います。
友人によれば boreカーネルがおすすめだそうです。

`ls /boot` に基づき必要なブートローダー設定を変更してください。

# 5. 完成です。

再起動しましょう。
また、パッケージ交換時に一部の設定が変更されていることもあるので気になる方は戻してください。

# スクリーンショット

`base` パッケージを削除したときの様子。
後に `systemd-sysvcompat` は必要だったことがわかった。
![base パッケージを削除したときの様子](/images/manjaro2cachyos/remove-base.png)

tmpfsが溢れないかおどおどしている様子。
![tmpfsが溢れないかおどおどしている様子](/images/manjaro2cachyos/free-mem.png)

mkinitcpioとsystemdがコンフリクトしている様子。
アップデートを3ヶ月サボったのが悪かったと考える。
![mkinitcpioとsystemdがコンフリクトしている様子](/images/manjaro2cachyos/mkinitcpio-system-conflict.png)

ArchLinuのリポジトリを入れていなくて問題が発生したときの様子。
![ArchLinuのリポジトリを入れていなくて問題が発生したときの様子](/images/manjaro2cachyos/no-arch-repo.png)

Powerlevel10kでManjaroとArchのアイコンが共存している様子。
この後Manjaroのアイコンの行方を知るものはいない。
![Powerlevel10kでManjaroとArchのアイコンが共存している様子](/images/manjaro2cachyos/p10k.png)

# 参考

[CachyOS公式Wiki](https://wiki.cachyos.org/cachyos_repositories/how_to_add_cachyos_repo/)
[全てを残したままArchからManjaroへ移行する - 山田ハヤオ様](https://blog.fascode.net/2021/01/20/archlinux-move-to-manjaro/)
