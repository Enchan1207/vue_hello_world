# 足跡

## 初回セットアップ

 - `npm init` でいつものように雛形を作成
 - 依存関係:
    - 言わずもがな `vue`
    - TSで書きたいので、以下を追加
        - `typescript`
        - `vue-tsc` (`tsc`のVue用ラッパ)
        - `@vue/tsconfig` (上と同様)
        - `vite` (開発用サーバが立ち上がる?)
 - tsconfig
    - `npx tsc --init` で `tsconfig.json` の雛形を生成
    - 内容は本家 `create-vue` を参考に
 - ソースファイル
    - ルートは `index.html`
    - なぜかtsファイルを直接記述できてしまうが、当然これは汎用のサーバでは動かない
    - コードは `src/` 配下

## なぜTSを直に参照できるのか?

本来TSはJSにトランスパイルしないといけない(そのためのコンパイラ: `tsc`)
つまり、htmlから直接参照された `src/main.ts` はどこかしらのタイミングでトランスパイルされ、JSとして返されている……はず

ビルドツールviteの提供する開発サーバを立ち上げて

```sh
npm run dev
```

TSファイルをcurlすれば…

```sh
curl -i localhost:5173/src/main.ts
HTTP/1.1 200 OK
# 略
Content-Type: text/javascript
# 略
Content-Length: 589

const now = /* @__PURE__ */ new Date();
const message = `Hello, TypeScript! now: ${now.toISOString()}`;
console.log(message);

# 略
```

トランスパイルされたJSが返ってくる！ よくできたツールですよほんと…
ゆえに、こういう特別な処理ができない普通のサーバ(`python -m http.server`)ではこの芸当はできない

## デプロイするときはどうするのか?

viteがやってくれる すげえ

```sh
npx vite build
```

これでdist配下にWebAppが出力されるので、これをまるごと持っていけばよい

## linter, formatterの設定

eslintとprettierを開発用の依存関係として追加、eslintはそのままだと怒られるので `eslintrc.cjs` を追加 prettierも同様に `prettierrc.json` を追加 (公式のそれとは異なり、行末セミコロンを有効化)

