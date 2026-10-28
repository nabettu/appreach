# appreach（ブログパーツの画像の配信用）

アプリーチ (https://mama-hack.com/app-reach/) が作るブログパーツが読み込む画像を、`https://nabettu.github.io/appreach/` で配信するためだけのリポジトリ。
ツールのソースは private の `nabettu/appreach-legacy` (旧版) と `nabettu/appreach-vue` (現行) にある。ここには置かない。

## ⚠️ ここにあるファイルは消さない・名前を変えない・中身を変えない

ブログパーツは HTML をコピーして各自のブログに貼る仕組みなので、**貼られたあとの HTML はこちらから直せない**。
ここのファイルを消したり変えたりすると、世界中の貼られたパーツの画像が壊れる。2014 年から貼られ続けている。

| パス | 参照しているもの |
|---|---|
| `img/itune_ja.svg` | **今のブログパーツ** (2017-02〜。`appreach-vue` の `AppResult.vue` に直書き) |
| `img/gplay_ja.png` | **今のブログパーツ** (同上。2024-01 に画像を差し替えた版) |
| `img/itune_en.png`・`img/gplay_en.png` | 2014〜2016 年のブログパーツ (`http://` で参照しているものもある) |
| `img/logo.png` | 2014〜2016 年のブログパーツ |
| `/` (`index.html`) | 2015〜2016 年のブログパーツの「posted with アプリーチ」のリンク先 (`http://nabettu.github.io/appreach/`)。mama-hack.com へ転送する |
| `img/itune_en.png.pagespeed.ce.8asOsm0ta-.png`・`img/gplay_en.png.pagespeed.ce.1AAXzseXga.png` | 2017 年に旧サイトの PageSpeed が書き換えた URL。貼られたパーツに残っている可能性がある |
| `img/facebook.png`・`img/twitter.png`・`img/gplay_s.png`・`img/itunes_s.png`・`img/loading.gif` | 旧版のツール画面の画像。外から直リンクされている可能性を否定できないので残す |
| `img/itune_jp.png`・`img/itune_s.png` | 2014-05 に消されていた画像。履歴から戻した (消していた間は 404 だった) |

- 一覧は 2026-10-28 に、旧リポジトリの全ブランチ・全コミットに一度でも入った画像と、旧版・現行・mama-hack.com の記事に残る
  `nabettu.github.io/appreach/...` の参照をすべて洗い出して作った。GitHub Pages にはアクセスログが無いので、実際に何が叩かれているかは分からない。だから全部残す
- 中身は `KEEP.sha256` で固定してある。CI (`.github/workflows/keep-files.yml`) が push と PR のたびに `sha256sum --check --strict` で確かめ、
  消えた・変わったファイルがあれば落ちる。`main` は ruleset で削除と force push を禁止している
- 新しい画像を足すのはよい (足したら `KEEP.sha256` にも足す)。既存のファイルの差し替えが必要なら、新しい名前で足してブログパーツ側の参照を変える

## 経緯

2026-10-28 まで、画像は旧版のツールのリポジトリ (private) の GitHub Pages から配信されていた。private のリポジトリの Pages は有料プランの機能なので、
プランを落とすと全ブログパーツの画像が消える状態だった。ソースは公開したくないので、旧リポジトリを `appreach-legacy` に改名し、
同じ名前で画像だけの public リポジトリ (ここ) を作り直した。URL は変わっていない。
