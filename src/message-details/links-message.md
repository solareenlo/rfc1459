# 4.3.3 Links メッセージ

```
   Command:  LINKS
Parameters:  [[<remote server>] <server mask>]
```

LINKS を使用すると，ユーザはクエリに応答するサーバが知っているすべてのサーバをリストアップすることができます．返されるサーバのリストはマスクと一致しなければならず，マスクが与えられない場合は完全なリストが返されます．`<server mask>` に加えて `<remote server>` が指定された場合，LINKS コマンドはその名前にマッチする最初のサーバに転送され，そのサーバは問い合わせに応答することが要求されます．

数値返信：
```
    ERR_NOSUCHSERVER
    RPL_LINKS           RPL_ENDOFLINKS
```

例：
```
LINKS *.au                   ; *.au に一致する名前を持つすべてのサーバをリストアップします．

:WiZ LINKS *.bu.edu *.edu    ; WiZから *.bu.edu に一致するサーバリストの *.edu に最初にマッチするサーバへの LINKS メッセージ．
```
