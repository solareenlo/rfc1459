# 4.2.4 トピックメッセージ

```
   Command:  TOPIC
Parameters:  <channel> [<topic>]
```

TOPIC メッセージは，チャネルのトピックを変更または表示するために使用されます．\<topic\> が指定されていない場合は，チャネル \<channel\> のトピックが返されます．\<topic\> パラメータがある場合，チャネルモードが許可していれば，そのチャネルのトピックが変更されます．

数値返信：
```
    ERR_NEEDMOREPARAMS    ERR_NOTONCHANNEL
    RPL_NOTOPIC           RPL_TOPIC
    ERR_CHANOPRIVSNEEDED
```

例：
```
:Wiz TOPIC #test :New topic    ;トピックを設定するユーザ Wiz．

TOPIC #test :another topic     ;#test のトピックを "別のトピック" に設定します．

TOPIC #test                    ; #test のトピックを確認します．
```
