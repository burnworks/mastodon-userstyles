# userstyles.scss for Mastodon Web

Mastodon（マストドン）の Web インターフェースをカスタマイズする SCSS ファイル。

## 使用方法

以下、2通りの使用方法があります。

1. mastodon/assets/stylesheets/ 下に burnworks-theme/userstyles.scss ファイルを置いてビルドすれば適用される（はず / まだ試してない）
2. ブラウザのユーザースタイルシートとして読み込む（拡張機能などを利用すると楽です / 下記 CSS 参照）

## 実際に適用した例

![実際にスタイルを適用した画面のキャプチャ](src/userstyles.scss.preview.sample.jpg)

## コンパイル済み CSS

src/userstyles.css は コンパイル済みの CSS ファイルになります。ユーザースタイルシートとして使用する場合はこちらを使用してください。

なお、各スタイル宣言はセレクタで `.app-holder ...` としてスコープする必要はないのですが念のため。

### userstyles.css

    /*!
     userstyles.css for Mastodon Web by yoshiki kato - burnworks@mastodon.burnworks.com
     Version 1.0.0 - 2017-05-02
    */

    @media (min-width: 1025px) {

      /* ブラウザ画面が小さいと左右が切れてしまう問題を解決 */
      .app-body .app-holder {
        width: auto;
        overflow-x: auto;
        -webkit-box-align: stretch;
        -moz-box-align: stretch;
        box-align: stretch;
        justify-content: flex-start;
      }

      .app-holder .ui {
        width: auto;
      }

      /* タイムライン切り替えボタンを移動 */
      .app-holder .drawer__header {
        position: absolute;
        right: calc(25% + 10px + 2.5px);
        top: 10px;
        z-index: 1000;
        width: calc(25% - 2.5px);
      }

      .app-holder .columns-area > div:last-of-type {
        margin-top: 50px;
      }
      
      .app-holder .columns-area > div:nth-of-type(2) .scrollable {
        border-top: 2px solid #191b22;
      }

      /* 通知エリアを一番右に移動 */
      .app-holder .columns-area > div:nth-of-type(3) {
        order: 1;
      }

      /* 通知（ブーストとお気に入り） 1件あたりの表示エリア（高さ）を制限 */
      .app-holder .notification.notification-favourite .status__content,
      .app-holder .notification.notification-reblog .status__content {
        max-height: calc(2em + 1.5em / 2);
        overflow: hidden;
      }

      /* タイムライン上でブーストされた投稿を少しわかりやすく */
      .app-holder .status__wrapper {
        background-color: #313543;
      }

      .app-holder .status__wrapper .status__prepend-icon-wrapper {
        color: #2588d0;
      }

    }

    @media (min-width: 1025px) and (min-height: 750px) {


      /* 検索結果表示時の調整 */
      .app-holder .drawer__inner.darker {
        z-index: 99999;
      }

      /* トゥート入力欄の初期サイズを大きく。入力文字数による自動リサイズを無効に */
      .app-holder .autosuggest-textarea__textarea {
        padding-right: 0;
        padding: 8px;
        padding-bottom: 10px;
        height: calc(10em + 1.8em / 2);
        max-height: calc(10em + 1.8em / 2);
        min-height: calc(10em + 1.8em / 2);
        overflow-y: auto;
        border-radius: 4px 4px 4px 0;
      }

      /* 絵文字ダイアログを移動して常に表示 */
      .app-holder .compose-form__autosuggest-wrapper .dropdown__trigger.emoji-button {
        display: none !important;
      }

      .app-holder .compose-form__autosuggest-wrapper .dropdown {
        left: 0;
        top: 0;
      }

      .app-holder .compose-form__autosuggest-wrapper .dropdown__content {
        display: block;
        line-height: 18px;
        text-align: left;
        z-index: 9999;
        top: 200px;
        width: 265px;
        height: 370px;
      }

      .app-holder .emoji-dialog.with-search {
        width: 100%;
        height: 100%;
      }

      /* 画像添付のプレビューを移動 */
      .app-holder .compose-form__modifiers {
        position: absolute;
        width: 265px;
        bottom: 10px;
        background-color: transparent;
      }
      
      .app-holder .compose-form__uploads-wrapper {
        padding: 0;
      }
      
      .app-holder .compose-form__upload {
        margin: 0;
      }

    }

## Mastodon

[Mastodon - A GNU Social-compatible microblogging server](https://github.com/tootsuite/mastodon)