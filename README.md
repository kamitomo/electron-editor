# electron-editor

vue.js & electron でファイルを開くプログラムを書く。

`IPC`でメインプロセスとレンダラープロセスのプロセス間通信をする。

- レンダラープロセス：`ipcRenderer.invoke`でイベントを通知
- メインプロセス：`ipcMain.handle`でイベントを受け取る

レンダラープロセス側はファイルを開くボタンクリック時にイベントを飛ばす。

メインプロセス側でファイルオープンダイアログを開き、ファイルの中身を読み取ってレンダラープロセスへ返す。

## セットアップ

```
npm install
npm run electron:serve
```
