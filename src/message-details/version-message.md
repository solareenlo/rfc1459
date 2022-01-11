# 4.3.1 Version メッセージ

```
   Command:  VERSION
Parameters:  [<server>]
```

VERSION メッセージはサーバプログラムのバージョンを問い合わせるために使用されます．オプションのパラメータ `<server>` は，クライアントが直接接続していないサーバプログラムのバージョンを問い合わせるために使用されます．

数値返信：
```
    ERR_NOSUCHSERVER    RPL_VERSION
```

例：
```
:Wiz VERSION *.se
		; Wizから "*.se" に一致するサーバのバージョンを確認するメッセージ

VERSION tolsun.oulu.fi
		; サーバ "tolsun.oulu.fi "のバージョンを確認します．
```
