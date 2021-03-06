# 8.3 メッセージの配信

ネットワークリンクが飽和したり，データ送信先のホストがデータ送信できなくなることはよくあることです．Unix は通常，TCP ウィンドウと内部バッファによってこれを処理しますが， サーバはしばしば大量の送信データを持ち（特に新しいサーバとサーバのリンクが形成されたとき）， カーネルで提供される小さなバッファでは送信キューに十分ではありません．この問題を軽減するために，送信するデータの FIFO キューとして "送信キュー" が使用されます．典型的な "送信キュー" は，新しいサーバが接続するとき，遅いネットワーク接続を持つ大きな IRC ネットワーク上で 200K バイトに成長するかもしれません．

接続をポーリングする際，サーバはまず受信データをすべて読み込んで解析し，送信すべきデータがあればキューに入れます．利用可能なすべての入力が処理されると，キューに入れられたデータが送信されます．これにより，`write()` システムコールの回数が減り，TCP がより大きなパケットを作成できるようになります．
