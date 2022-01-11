# 4.3.8 Info コマンド

```
   Command:  INFO
Parameters:  [<server>]
```

INFO コマンドは，サーバのバージョン，コンパイル日，パッチレベル，起動日，その他関連すると思われる雑多な情報など，サーバに関する情報を返すことが要求されます．

数値返信：
```
    ERR_NOSUCHSERVER
    RPL_INFO            RPL_ENDOFINFO
```

例：
```
INFO csd.bu.edu      ; csd.bu.edu から INFO の返信を要求します．
:Avalon INFO *.fi    ; Avalon からの *.fi に一致する最初のサーバへの INFO リクエスト．
INFO Angel           ; Angel が接続されているサーバに情報を要求します．
```
