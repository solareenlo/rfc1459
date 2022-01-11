# 4.3.4 Time メッセージ

```
   Command:  TIME
Parameters:  [<server>]
```

TIME メッセージは，指定されたサーバからローカルタイムを問い合わせるために使用されます．`<server>` パラメータが指定されない場合，コマンドを処理するサーバは問い合わせに応答する必要があります．

数値返信：
```
    ERR_NOSUCHSERVER    RPL_TIME
```

例：
```
TIME tolsun.oulu.fi    ; サーバ "tolson.oulu.fi" の時刻を確認します．
Angel TIME *.au        ; ユーザ Angel が "*.au" に一致するサーバで時刻を確認しています．
```
