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
---