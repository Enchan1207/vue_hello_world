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

## Vueっぽいことする

under construction...
