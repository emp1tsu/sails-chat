# 環境構築メモ

### プロジェクト作成

``` sails new sails-chat```

### ローカル環境立ち上げ

```sails lift```

---
# チャットアプリ作成メモ

### チャットのメッセージを扱うAPI作成

チャットのメッセージを扱うモデル作成  

```sails generate controller message```

モデルに対するリクエストを処理するコントローラ  

```sails generate model message```

以下の結果が帰ってくる

```
~/git> curl localhost:1337/message
[]⏎
```

```
~/git> curl -F 'body=hoge' localhost:1337/message
{
  "body": "hoge",
  "createdAt": 1561984635379,
  "updatedAt": 1561984635379,
  "id": 1
}⏎
```

### モデルのバリデーション

空の投稿は禁止

api/models/Message.js
```
  attributes: {
    body: {
      type: 'string', 
      required: true  // 必須
    }
  },
```

以下のようにメッセージがnullの場合はエラーで帰ってくる

```
~/g/sails-chat> curl -F 'body=' localhost:1337/message
{
  "code": "E_INVALID_NEW_RECORD",
  "details": "Could not use specified `body`.  Cannot set \"\" (empty string) for a required attribute.",
  "message": "The server could not fulfill this request (`POST /message`) due to a problem with the parameters that were sent.  See the `details` for more info.  **The following additional tip will not be shown in production**:  Tip: Check your client-side code to make sure that the request data it sends matches the expectations of the corresponding attribues in your model.  Also check that your client-side code sends data for every required attribute."
}⏎
```
---