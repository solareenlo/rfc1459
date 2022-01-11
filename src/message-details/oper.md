# 4.1.5 オペレータメッセージ

```
   Command:  OPER
Parameters:  <user> <password>
```

OPER メッセージは，一般ユーザがオペレータ権限を取得するために使用します．Operator 権限を取得するためには，\<user\> と \<password\> の組み合わせが必要です．

OPER コマンドを送信したクライアントが，指定されたユーザの正しいパスワードを提供した場合，サーバはクライアントのニックネームに対して "MODE +o" を発行して，新しいオペレータをネットワークの残りの部分に通知します．

OPER メッセージは，クライアント・サーバのみです．

数値返信：
```
    ERR_NEEDMOREPARAMS    RPL_YOUREOPER
    ERR_NOOPERHOST        ERR_PASSWDMISMATCH
```

例：
```
OPER foo bar    ; ユーザ名に "foo"，パスワードに "bar" を使ってオペレータ登録を試みます．
```
