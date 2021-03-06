# 4.1.3 User メッセージ

```
Command   :  USER
Parameters:  <username> <hostname> <servername> <realname>
```

USER メッセージは，接続の最初に新しいユーザのユーザ名，ホスト名，サーバ名，実名 を指定するために使用されます．また，サーバ間の通信でも，新しいユーザが IRC に到着したことを示すために使われます．なぜなら，クライアントから USER と NICK の両方を受け取って初めて，ユーザが登録されるからです．

サーバ間では，USER の前にクライアントの NICKname を付ける必要があります．ホスト名とサーバ名は，通常，IRC サーバが直接接続されたクライアントから USER コマンドが来た場合には（セキュリティ上の理由から）無視されますが，サーバ間の通信では使用されることに注意してください．つまり，新しいユーザをネットワークの他の部分に紹介するときには，必ず NICK をリモートサーバに送信してから，付随する USER を送信しなければなりません．

realname パラメータは，スペース文字を含む可能性があるため，最後のパラメータとする必要があり，そのように認識されるようにコロン（`:`）を先頭に付ける必要があることに注意しなければなりません．

USER メッセージのみに依存すると，クライアントがユーザ名について簡単に嘘をつ くことができるため，「ID サーバ」の使用を推奨します．ユーザが接続するホストでこのようなサーバが有効になっている場合，ユーザ名は「ID サーバ」からの返信と同じように設定されます．

数値返信：
```
    ERR_NEEDMOREPARAMS    ERR_ALREADYREGISTRED
```

例：
```
USER guest tolmoon tolsun :Ronnie Reagan
        ; ユーザ名「guest」，本名「Ronnie Reagan」で登録されたユーザ

:testnick USER guest tolmoon tolsun :Ronnie Reagan
        ; USERコマンドが属するニックネームで，サーバ間でメッセージをやり取りします
```
