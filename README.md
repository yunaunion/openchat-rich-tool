# リッチ投稿ツール（個人用）

Flex MessageのJSONを貼り付け、ボタンのリンク先URLを編集して、**開いたそのトーク（オプチャ・グループ・1対1）に直接送信**するための個人用ツールです。`liff.sendMessages()`を使用します。LIFF ID（`2006439463-vBCAM0Fz`）はHTMLに埋め込み済みなので、入力は不要です。

## 仕組み（調べた事実）

- `liff.shareTargetPicker()`（送信先を選ぶ方式）は**オープンチャットを選択肢に出せません**（[LIFF API reference](https://developers.line.biz/en/reference/liff/)）。
- 代わりに`liff.sendMessages()`を使うと、**LIFFを開いたそのトーク**にそのまま送信できます。オプチャに送るには、オプチャ内に貼った`liff.line.me`リンクをオプチャ内からタップして開く必要があります。
- `liff.sendMessages()`には`chat_message.write`スコープが必要です。

## LINE Developers Console側の設定（初回のみ）

該当のLIFFアプリ（`2006439463-vBCAM0Fz`）で以下を確認：

- **エンドポイントURL**: `https://yunaunion.github.io/openchat-rich-tool/`
- **Scope**: `profile` と **`chat_message.write`** にチェック
- **サイズ**: Full 推奨

## 使い方

1. 送りたいオプチャ・トークの中に、**`https://liff.line.me/2006439463-vBCAM0Fz`** を一度メッセージとして貼る。
2. **そのトークの中から**、貼ったリンクをタップして開く。
3. Flex MessageのJSONを貼り付ける（貼った時点でプレビューとボタンURL編集欄が自動表示）。
4. 必要ならボタンのリンク先URLを書き換える。
5. 「このトークに送信」を押す。

## 注意

- このツールは自分専用です。他人への配布や、権限のないトークへの投稿目的での使用は意図していません。
