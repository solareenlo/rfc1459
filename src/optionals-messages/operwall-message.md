# 5.6 Operwall メッセージ

```
Command   :  WALLOPS
Parameters:  現在オンライン中の全オペレータに送信されるテキスト
```

現在オンライン中の全オペレータにメッセージを送信します．ユーザコマンドとして WALLOPS を実装した後，それが多くの人にメッセージを送る手段としてしばしば一般的に乱用されることがわかりました（WALL によく似ています）．このため，WALLOPS の現在の実装は，WALLOPS の送信者としてサーバだけを許可し，認識することによって，例として使用されることが推奨されます．

数値返信：
```
    ERR_NEEDMOREPARAMS
```

例：
```
:csd.bu.edu WALLOPS :Connect ’*.uiuc.edu 6667’ from Joshua
        ; csd.bu.edu からの WALLOPS メッセージは、Joshua から受信し処理した CONNECT メッセージを通知しています。
        ; csd.bu.edu からの WALLOPS メッセージは，Joshua から受信し対応した CONNECT メッセージを知らせています．
```
