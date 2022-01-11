# 3. IRC コンセプト

この章では，IRC プロトコルの構成の背後にある実際の概念と，現在の実装がどのようにメッセージの異なるクラスを提供するかを説明することに専念します．

```
    1--\
        A        D---4
    2--/ \      /
          B----C
         /      \
        3        E
 Servers: A, B, C, D, E Clients: 1, 2, 3, 4
 [ Fig. 2. Sample small IRC network ]
```
