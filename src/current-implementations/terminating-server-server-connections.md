# 8.8 サーバ・サーバ間の接続の終了

サーバとサーバの接続が，リモートで生成された SQUIT または’自然な’原因によって閉じられた場合，接続されている残りの IRC ネットワークは，閉鎖を検出したサーバによってその情報が更新されなければなりません．サーバは，SQUIT のリスト（その接続の背後にある各サーバについて1つ）と QUIT のリスト（再び，その接続の背後にある各クライアントについて1つ）を送信します．
