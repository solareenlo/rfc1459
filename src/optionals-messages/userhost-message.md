# 5.7 Userhost メッセージ

```
Command   :  USERHOST
Parameters:  <nickname>{<space><nickname>}
```

USERHOST コマンドはスペース文字で区切られた最大5つのニックネームのリストを受け取り，見つけたそれぞれのニックネームに関する情報のリストを返します．返されるリストには，それぞれの返答がスペースで区切られています．

数値返信：
```
    RPL_USERHOST    ERR_NEEDMOREPARAMS
```

例：
```
USERHOST Wiz Michael Marty p
        ; ニックネーム "Wiz", "Michael", "Marty", "p" の情報に関する USERHOST リクエスト．
```
