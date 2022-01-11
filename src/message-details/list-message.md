# 4.2.6 リストメッセージ

```
   Command:  LIST
Parameters:  [<channel>{,<channel>} [<server>]]
```

LIST メッセージは，チャネルとそのトピックを一覧表示するために使用されます．\<channel\> パラメータを使用した場合，そのチャネルの状態のみが表示されます．プライベートチャネルは，クエリを生成したクライアントが実際にそのチャネルにいない限り，チャネル "Prv" としてリストされます（トピックは含まれません）．同様に，シークレットチャネルは，クライアントがそのチャネルのメンバーでない限り，まったく表示されません．

数値返信：
```
    ERR_NOSUCHSERVER    RPL_LISTSTART
    RPL_LIST            RPL_LISTEND
```

例：
```
LIST                       ;すべてのチャネルを一覧表示します．

LIST #twilight_zone,#42    ; #twilight_zone と #42 チェネルを一覧表示します．
```
