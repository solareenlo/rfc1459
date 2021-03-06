# 8.12 設定ファイル

サーバの設定や運用を柔軟に行うために，以下のようなサーバへの指示を含む設定ファイルを使用することが推奨されます．

* クライアントからの接続を受け付けるホストを指定します．
* サーバとして接続を許可するホストを指定します．
* サーバとして接続を許可するホストを指定します．
* どのホストに接続するか（アクティブおよびパッシブの両方）．
* サーバがどこにあるかという情報（大学，都市／州，会社がその例です）．
* サーバの責任者と連絡可能な電子メールアドレス．
* 制限されたオペレータコマンドへのアクセスを希望するクライアントのホスト名とパスワード．

ホスト名の指定は，ドメイン名とドット表記（127.0.0.1）の両方が可能である必要があります．送信および受信のすべての接続で使用/受信するパスワードを指定できるようにしなければなりません（ただし，送信接続は他のサーバへの接続のみ）．

上記のリストは，他のサーバとの接続を希望するサーバに最低限必要なものです．その他，参考になる項目は以下の通りです．

* 他のサーバが導入できるサーバを指定する．
* サーバの分岐をどこまで深くするか．
* クライアントが接続可能な時間帯
