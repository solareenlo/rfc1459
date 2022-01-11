# 4.3.7 Admin メッセージ

```
Command   :  ADMIN
Parameters:  [<server>]
```

ADMIN メッセージは，指定されたサーバ（`<server>` パラメータが省略された場合は現在のサーバ）の管理者名を検索するために使用されます．各サーバは，ADMIN メッセージを他のサーバに転送する機能を持つ必要があります．

数値返信：
```
    ERR_NOSUCHSERVER
    RPL_ADMINME      RPL_ADMINLOC1
    RPL_ADMINLOC2    RPL_ADMINEMAIL
```

例：
```
ADMIN tolsun.oulu.fi    ; tolsun.oulu.fi から ADMIN の返信を要求します．
:WiZ ADMIN *.edu        ; WiZからの *.edu に一致する最初のサーバへの ADMIN リクエスト．
```
