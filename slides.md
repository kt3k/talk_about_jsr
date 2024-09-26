class: middle, center

# <img src="./assets/logo.png" width="300" /> の話

Yoshiya Hinosawa @kt3k

---
class: text-4xl

# 目次

- JSR の狙い
- JSR の特徴

---

## Yoshiya Hinosawa

<img src="./assets/hinosawa.jpg" width="180" />

- x.com / github - @kt3k
- Deno の中の人。最近は Deno Standard Library と Deno CLI の Node 互換周り担当
- 昔はサウス 37 - 38Fで働いていました (- 2019)

---
# npm レジストリのすごい点

- プログラミング界の最大のパッケージレジストリ
- 300万パッケージが存在

<img src="./assets/modulecounts.png" width="500" />

---

# npm レジストリのよく無い点

- ES6 も TS も無い時にデザインされたため古くなっている
- CommonJS がデフォルト
  - CJS と ESM をサポートするための仕組み (Conditional exports) はあるが複雑
- TypeScript に関するサポートが無い
  - 自前で d.ts をビルド or DefinitelyTyped を手動でメンテ -> 辛い

---
## npm レジストリの開発は低調(?)

- 新機能があまり追加されていない
- npm は2020年に github に買収された
- 買収直前に主要メンバーが npm を去った
- Open Source では無いので、コミュニティー主体で開発を進めることも出来ない

---

## JSR チームが考えたこと

--

=> レジストリに関する革新がここ数年止まってしまっているのではないか?

--

=> TS はメインストリームと言われているのに「TS で普通にライブラリを書くこと」が難しいのはおかしいのでは?

--

=> ESM と TS を前提としたレジストリを0から設計したら良いのではないか?

---
class: middle center

# Introducing

<img src="./assets/logo.png" width="400" />

--

JSR = JavaScript Registry

---

# JSR の特徴

- TypeScript を直接パブリッシュ出来る
- モジュール解決は ESM だけ (CommonJS は無し)
- npm と互換性あり
- 複数ランタイムを意識した作り
- レジストリ全体がオープンソース

---

# npm 互換性

- JSR パッケージから npm パッケージを使える
- npm パッケージから JSR パッケージを使える

---

# npm 互換性

- JSR は npm とは別の何かではなく、npm の資産を活用しつつ拡張するもの (スーパーセット)

<p class="text-center">
  <img src="./assets/jsr-include-npm.png" width="500" />
</p>

---

# TypeScript サポート

- TypeScript を直接パブリッシュできる
- トランスパイルが不要
- d.ts は JSR が自動生成
- TypeScript の doc コメントからドキュメントページ(APIリファレンス)を自動生成

--

<p class="text-center">
「ソースコードを書いて publish するだけ」
</p>

---

# 複数ランタイム前提

- サポートしてるランタイムを JSR 上で設定できる

<p class="text-center">
<img src="./assets/runtime-supports.png" width="500" />
</p>

---
## 改善されたDX(ライブラリ提供者目線)

- TS をビルドしなくて良い
- ドキュメントはソースコードに書くだけで良い
- Publish ミスの自動検出
  - ES Module / 型定義のチェックが自動で行われる

---
## 改善されたDX(ライブラリ利用者目線)

- 型が壊れている事が無い
- 何が export されているか必ず分かる
- ドキュメントがある可能性が高い
- どのランタイムがサポートされているか分かる

---
# JSR はオープンソース

- https://github.com/jsr-io/jsr で開発されている
- レジストリの全体が公開
- セルフホストも可能
- 機能要望、機能提案なども可能

---
### 注意点

- JSR は ESM しかサポートしない
- CJS を使っているユーザーはサポートできない

--
- CJS からの利用が絶対必要な人は「まだ」使わないほうが良いかもしれません

--
- ただし Node.js v22 で require(ESM) ができるようになる

---
### デモ

- npm 経由で使うデモ
- publish するデモ

---
# Deno と JSR の関係

- JSR の開発者は今のところ Deno の開発者が多い
- Deno のためのより良いレジストリを作りたいと言うのがモチベーションの1つとしてあった
- 設計を進める中で、Deno に限らず、すべてのランタイムのためのレジストリを作るべきという目的意識に変わっていった
- Deno は JSR でマネタイズする予定はない

---
# Deno と JSR の関係

- Deno と JSR はあくまで独立したプロジェクト
  - Deno - github.com/denoland
  - JSR - github.com/jsr-io


---
# Deno にとっての JSR

- Deno にとって JSR はとても重要なレジストリ

--
- Deno はこれまで URL import を依存解決に用いてきたが、URL インポートでは SemVer レンジでの依存や、SemVer レンジの重複した依存の dedupe をすることが出来なかった。

--
- JSR に移行することでこれらの問題が解決される。

--
- Deno ユーザーは今後 JSR にパッケージを publish することが推奨

---
# Deno にとっての JSR

- [What we got wrong about HTTP imports](https://deno.com/blog/http-imports)


---
class: middle center

# <p class="flex items-center justify-center gap-2">Let's try <img src="./assets/logo.png" width="180" /></p>

# https://jsr.io

ご清聴ありがとうございました!



