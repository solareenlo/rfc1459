# 7. クライアントとサーバの認証

クライアントもサーバも同じレベルの認証が行われます．両者とも，サーバへのすべての接続について，IP 番号とホスト名のルックアップ（およびこの逆チェック）が実行されます．その後，両方の接続に対してパスワードチェックが行われます（その接続にパスワードが設定されている場合）．これらのチェックはすべての接続で可能ですが，パスワードチェックはサーバでのみ一般的に使用されます．

さらに，最近増えているのが，接続に使用したユーザ名のチェックです．接続の相手側のユーザ名を見つけるには，通常，RFC1413 に記載されている IDENT などの認証サーバに接続する必要があります．

パスワードがなければ，ネットワーク接続の相手方を確実に特定することは容易ではないため，サーバ間接続では，ID サーバの使用などの対策に加え，パスワードの使用を強く推奨します．