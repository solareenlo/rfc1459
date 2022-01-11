# 1.2 サーバ

サーバは IRC のバックボーンを形成し，クライアントが互いに会話するために接続するポイント，および他のサーバが IRC ネットワークを形成するために接続するポイントを提供します．IRC サーバに許されるネットワーク構成は，スパニングツリー（図1参照）のみで，各サーバは，それが見るネットの残りの部分に対して中心ノードとして機能します．

```
             [ Server 15 ]   [ Server 13 ]      [ Server 14]
                 /                 \                /
                /                   \              /
        [ Server 11 ] ------ [ Server 1 ]    [ Server 12]
                              /        \        /
                             /          \      /
                  [ Server 2 ]        [ Server 3 ]
                    /       \                   \
                   /         \                   \
           [ Server 4 ]    [ Server 5 ]      [ Server 6 ]
            /    |   \                         /
           /     |    \                       /
          /      |     \____                 /
         /       |          \               /
[ Server 7 ] [ Server 8 ] [ Server 9 ] [ Server 10 ]
                                :
                             [ etc. ]
                                :
               [ Fig. 1. Format of IRC server network ]
```
