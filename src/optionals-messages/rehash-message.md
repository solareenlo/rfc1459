# 5.2 Rehash メッセージ

```
Command   :  REHASH
Parameters:  None
```

REHASH メッセージは，オペレータがサーバに設定ファイルの再読み込みと処理を強制するために使用することができます．

数値返信：
```
    RPL_REHASHING    ERR_NOPRIVILEGES
```

例：
```
REHASH    ; オペレータの状態を示すクライアントからサーバにメッセージを送信し，サーバに設定ファイルの再読み込みを要求します．
```
