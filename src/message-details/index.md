# 4. メッセージ詳細

以下のページでは，IRC サーバとクライアントが認識する各メッセージについて説明します．この章で説明されているすべてのコマンドは，このプロトコルのための任意のサーバで実装されている必要があります．

ERR_NOSUCHSERVER が記載されている場合，パラメータが見つからなかったことを意味します．サーバはこれ以降，そのコマンドに対して他の応答を送ってはなりません．

クライアントが接続されているサーバは，メッセージ全体を解析し，適切なエラーを返すことが要求されます．メッセージの解析中に致命的なエラーが発生した場合，クライアントにエラーを返し，解析は終了しなければなりません．致命的なエラーとは，不正なコマンド，サーバにとって未知の宛先（サーバ名，ニックネーム，チャネル名がこれに該当），十分なパラメータがない，不正な権限などが考えられます．

パラメータの完全なセットが提示された場合，それぞれの有効性をチェックし，適切なレスポンスをクライアントに返さなければなりません．コンマを区切り文字としてパラメータリストを使用するメッセージの場合，各項目に対して応答を送信しなければなりません．

以下の例では，一部のメッセージはフルフォーマットで表示されます．

```
:Name COMMAND parameter list
```

このような例は，サーバ間で転送中の「名前」からのメッセージを表し，リモートサーバが正しい経路で返信できるように，メッセージの元の送信者の名前を含めることが重要です．