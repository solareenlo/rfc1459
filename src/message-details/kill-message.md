# 4.6.1 Kill メッセージ

```
Command   :  KILL
Parameters:  <nickname> <comment>
```

KILL メッセージは，クライアントとサーバの接続を，実際に接続しているサーバに閉じさせるために使用されます．KILL は，有効なニックネームのリストに重複したエントリがある場合に，サーバによって使用され，両方のエントリを削除するために使用されます．また，オペレータも利用することができます．

自動再接続のアルゴリズムを持っているクライアントは，切断が短時間であるため，このコマンドは事実上無意味です．しかし，データの流れを断ち切り，大量の不正使用を阻止するために使うことができます．どのユーザでも，他のユーザがトラブルスポットを ’監視’ するために生成された KILL メッセージを受け取ることを選択できます．

ニックネームは常にグローバルにユニークであることが要求されるため，’重複’（同じニックネームで2人のユーザを登録しようとすること）が検出されるたびにKILLメッセージが送られ，2人とも消えて1人だけが再び現れることが期待されるのです．

コメントには，KILL の実際の理由を反映させる必要があります．サーバが生成した KILL の場合は，通常，2 つの衝突するニックネームの起源に関する詳細が含まれます．ユーザの場合は，それを見た人が満足するような適切な理由を提供するように任されています．KILLer を隠すために偽の KILL が生成されるのを防ぐために，コメントには ’kill-path’ が表示され，通過する各サーバによってそのパスが更新され，それぞれのサーバ名が先頭に追加されます．

数値返信：
```
    ERR_NOPRIVILEGES ERR_NEEDMOREPARAMS
    ERR_NOSUCHNICK ERR_CANTKILLSERVER
```

例：
```
KILL David (csd.bu.edu <- tolsun.oulu.fi)
        ; csd.bu.edu と tolson.oulu.fi の間のニックネームの衝突
```

NOTE:
オペレータだけが KILL メッセージで他のユーザを KILL することができるようにすることを推奨します．理想的な世界では，オペレータでさえもこれを行う必要はなく，サーバが対処することになるでしょう．