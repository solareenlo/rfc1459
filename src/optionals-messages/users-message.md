# 5.5 Users メッセージ

```
Command   :  USERS
Parameters:  [<server>]
```

USERS コマンドは，who(1), rusers(1), finger(1) と同様のフォーマットで，サーバにログインしているユーザのリストを返します．人によっては，セキュリティ関連の理由から，サーバ上でこのコマンドを無効にしている場合があります．無効にした場合は，それを示すために正しい数値を返さなければなりません．

数値返信：
```
    ERR_NOSUCHSERVER    ERR_FILEERROR
    RPL_USERSSTART      RPL_USERS
    RPL_NOUSERS         RPL_ENDOFUSERS
    ERR_USERSDISABLED
```

返信不可の場合：
```
    ERR_USERSDISABLED
```

例：
```
USERS eff.org                 ; サーバ eff.org にログインしているユーザのリストを要求します．
:John USERS tolsun.oulu.fi    ; John がサーバ tolsun.oulu.fi にログインしているユーザのリストを要求しています．
```
