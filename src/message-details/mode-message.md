# 4.2.3 Mode メッセージ

```
Command: MODE
```

MODE コマンドは，IRC では2つの用途を持つコマンドです．これはユーザ名とチャネルの両方にモードを変更させることができます．この選択の根拠は，いつの日かニックネームが廃れ，同等のプロパティがチャネルになることです．

MODE メッセージを解析する場合，まずメッセージ全体を解析し，その結果生じた変更を引き継ぐことをお勧めします．