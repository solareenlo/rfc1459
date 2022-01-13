# 8.10 クライアントからの大量の情報への対策

IRC サーバが相互に接続された大規模なネットワークでは，ネットワークに接続している任意の1つのクライアントが連続的にメッセージを供給することは非常に簡単で，その結果，ネットワークが氾濫するだけでなく，他のクライアントに提供するサービスのレベルを低下させることになるのです．大量リクエスト対策は，すべての’犠牲者’に独自の対策を要求するのではなく，サーバに書き込まれ，サービスを除くすべてのクライアントに適用されます．現在のアルゴリズムは以下の通りである．

* クライアントの‘メッセージタイマ‘が現在の時刻より小さいかどうかを確認します（小さい場合は等しくなるように設定します）．
* クライアントから存在するあらゆるデータを読み取ります．
* タイマーが現在時刻より 10 秒以上進んでいる間に，現在のメッセージを解析し，メッセージごとにクライアントに 2 秒のペナルティーを課します．

これは要するに，クライアントが2秒に1回メッセージを送信しても悪影響がないことを意味します．