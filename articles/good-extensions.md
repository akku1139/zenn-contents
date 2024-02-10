---
title: "おすすめ拡張機能2"
emoji: "🛠"
type: "idea"
topics: ["chrome", "拡張機能", "作業効率"]
published: false
---

こんにちは。生徒会情報機構（TRANs）のakkuです。
TRANsに何の関連性もないですが、kyonshiさんが記事を書いていたため
便乗してChromeの拡張機能をいくつか紹介したいと思います。

↓ きょんしーさんの記事も読んでね ↓
https://note.com/kyonshi_/n/nfba460771acc

## AdGuard AdBlocker
https://chromewebstore.google.com/detail/adguard-adblocker/bgnkhhnnamicmpeenaelnjfhikgbkllg
https://adguard.com/ja/welcome.html
みんな大好き広告ブロッカーです。
きょんしーさんはuBlock Originをおすすめしていますが、AdGuardさんはUIが美しいです。
このシンプルなところがまた良いですね。
![AdGuardのシンプルで洗練されたUI](/images/good-extensions/adguard1.png)

また、AdGuardさんはManifest v3への完全な対応を発表しています。
https://adguard.com/ja/blog/adguard-mv3.html

(uBlockさんはuBlock Origin Liteを公開したようです)
https://chromewebstore.google.com/detail/ublock-origin-lite/ddkjiahejlhfcafbddmgiahcphecmpfh

AdGuardさんの特徴のひとつに「ステルスモード」があります。
主な機能はこちら
- トラッカー(あなたのWeb履歴を追跡し、送信します) 及び
  トラッキングパラメータ(`?utm_source=...` などの本質的ではないパラメータ)の削除
- Cookieの自動削除 (カスタマイズ可能)
- WebRTCの禁止 (オンライン会議に使われますが、そうでない場合にあなたを特定するために使われます)
- その他の追跡方法の禁止

### YouTubeの広告を削除するために
金の亡者YouTubeは日々新しい広告ブロック対策を講じます。
YouTubeは利用規約違反であると主張しますが、利用規約にはその根拠が書かれていません。
[またEUではYouTube側が違法です。](https://gigazine.net/news/20231110-youtube-blocker-detection/)
ですから、積極的に広告ブロックを薦めましょう。
※ あなたのYouTubeアカウントが B☆A☆N されても責任は負いません
AdGuardは自動でフィルターを更新しますが、ポップアップを開き ↺ を押すと手動で最新のフィルターに更新します。
![フィルターの更新](/images/good-extensions/adguard2.png)

## AutoPagerize
https://chromewebstore.google.com/detail/autopagerize/igiofjhpmpihnifddepnpngfjhkfenbp
http://autopagerize.net
検索で次のページを開くことは非常にめんどくさいですね。
しかしAutoPagerizeはその手間を解消します。
なんとスクロールするだけで次のページを繋げて表示することが出来ます。
検索サイト以外にも、謎にページが分けられているサイトでも効力を発揮します。
入れておいて損はないと思います。

## Simple Translate
https://chromewebstore.google.com/detail/simple-translate/ibplnjkanclpjokhdolnendpplpjiace
シンプルかつ洗練された翻訳拡張機能です。
![素晴らしい使用画面](/images/good-extensions/simple-translate1.png)
Google翻訳とDeepL(無料版APIキーが必要)に対応しています。
- 自動で言語を切り替える機能
- 選択したテキストをで翻訳する機能
- ショートカットキーを設定し翻訳画面を開く
などがあります。
英語のサイトなどを読むときに重宝しています。

## Violentmonkey
https://chromewebstore.google.com/detail/violentmonkey/jinjaccalgkegednnccohejagnlnfdag
https://violentmonkey.github.io
ユーザースクリプトを設定・管理するための拡張機能です。
よく比較されるものに
- Greasemonkey (Firefox向け)
- Tampermonkey
があります。 これらは少しずつ提供するAPIが違うそうです。
(実は拡張機能を入れなくてもChromeは標準で対応しています)
https://qiita.com/aoirint/items/3467427c28fe71d3cd57

Violentmonkeyにこだわる理由は特にありませんが、
- 最初に知った
- UIが好み
だったため使っています。

## Vencord Web
https://chromewebstore.google.com/detail/vencord-web/cbghhgpcnddeihccjmnadmkaejncjndb
https://vencord.dev
某Betterと並ぶ改造DiscordのChrome拡張機能版(公式配布なので安心)です。
(Discordの利用規約違反ですから積極的に使いましょう)

## Dark Reader
https://chromewebstore.google.com/detail/dark-reader/eimadpbcbfnmbkopoojfekhnkhdbieeh
https://darkreader.org
Webサイトをダークテーマ化する拡張機能です。
きょんしーさんも紹介しましたが、本当に便利です。
Dark Readerの無いWebブラウジングは想像するだけでも地獄です。
[ダークテーマに対する反論](https://wired.jp/2019/10/05/dark-mode-chrome-android-ios-science/)はありますが、ダークテーマの嫌いな人だけが勝手に騒いでいればいいと思います。
適切に設定されたダークテーマと部屋の明かりは、確かに目の疲労感などを軽減します。
参考までに設定を公開します。
```yaml
明るさ: -15
コントラスト: +10
セピア: off
グレースケール: off
```
![設定例](/images/good-extensions/darkreader-setting.png)

## Save to Scrapbox
https://chromewebstore.google.com/detail/save-to-scrapbox/jcdhmhfihdilhhnjhflmanmoimfjpakh
読んでいるサイトをScrapboxに保存する拡張機能です。
簡単にメモとして使えるのでおすすめです。
時々ミスって押すことがありますから、少し押しにくいポジションに設置しましょう。

## Checker Plus for Gmail™
https://chromewebstore.google.com/detail/checker-plus-for-gmail/oeopbcgkkoapgobdbedcemjljbihmemj
https://jasonsavard.com/?ext=gmail
Gmailの新着メールを監視して通知する拡張機能です。
メールボックスを開かなくてもメールを確認できるので、使用しています。

## Bitwarden - Free Password Manager
https://chromewebstore.google.com/detail/bitwarden-free-password-m/nngceckbapebfimnlniiiahkandclblb
https://bitwarden.com
オンラインパスワードマネージャです。
大量のパスワードを複数ブラウザで使用できるため便利です。
![大量のパスワード](/images/good-extensions/bitwarden-passwords.png)
パスワード生成も付属していますから、弱いパスワードを使ってしまうことがなくなります。
![パスワード生成](/images/good-extensions/bitwarden-generate-password.png)
また、保存サーバーをセルフホストすることによって更なる安心を得ることが出来ます。

## Authenticator
https://chromewebstore.google.com/detail/authenticator/bhghoamapcdpbohphigoooaddinpkbai
https://authenticator.cc
2段階認証にスマートフォンを使う時代は終わりました。
これからはブラウザ拡張機能を使います。
Authenticatorは[ソースコードが公開](https://github.com/Authenticator-Extension/Authenticator)されていますので安心です。

## Old Twitter Layout (2024)
https://chromewebstore.google.com/detail/old-twitter-layout-2024/jgejdcdoeeabklepnkdbglgccjpdgpmf
https://github.com/dimdenGD/OldTwitter
今は変わってしまった 𝕏 のUIを懐かしのTwitterに戻すための拡張機能です。
久しぶりに有効化したら青い鳥が熱烈に歓迎してくれました。
![青い鳥](/images/good-extensions/bluebird.png)

## Vivaldi
https://vivaldi.com
https://vivaldi.net
拡張機能ではありませんが、私が使っているWebブラウザの紹介です。
Vivaldiは非常にカスタマイズ性の高いWebブラウザです。
使う人によってUIコンポーネントが上下左右逆の位置にある可能性も少なくはないでしょう。

便利に使用している主な機能
- パネル
  ![素晴らしいパネルの機能](/images/good-extensions/vivaldi-panel.png)
  ![検索も出来ます](/images/good-extensions/vivaldi-search.png)
- アドレスバーを隠す (ショートカットキーで表示します)
- Chrome拡張機能 (Chromiumベースで開発されていますためChrome拡張機能が動作します)
- 全自動の同期
特に縦方向に配置したパネルに拡張機能を設置できるブラウザは他に知らないです。
また、
- 広告ブロック
は一部のサイトで正常に動作しなかった為無効化しました。

Vivaldiは95%のオープンソースで開発されています。
これをどう捉えるかは貴方次第です。
https://note.com/histone/n/n725fa71d3a55
私は5%のクローズドソースが嫌いですからWebブラウザを自作する計画があります。

## 終わりに、記事の内容を3行で振り返る。
- ブラウザ拡張機能は非常に便利ですから積極的に使いましょう。
- 広告ブロックは正義
- Vivaldiは便利
