# 8.11.2 ユーザ名（Ident）ルックアップ

他のプログラムに組み込んで使用するための ident ライブラリは数多く存在しますが，これらは同期的に動作するため，遅延が頻繁に発生するという問題がありました．この場合も，サーバの他の部分と協調し，ノンブロッキング IO で動作するルーチン群を書くことが解決策となりました．
