
# よく使うイディオム、関数など

## イディオム

### shebang & magic comment

```
#!/usr/bin/env python3
# coding: utf-8
```

なお、PEP-8では非推奨なのでそのうち書くのやめる  
https://pep8-ja.readthedocs.io/ja/latest/#id12  


### リスト内包表記によるリスト作成

```
l = list(map(lambda x: x, range(10)))
l = [x for x in range(10)]
 -> [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

```
squares = list(map(lambda x: x**2, range(10)))
squares = [x**2 for x in range(10)]
 -> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### 三項演算子

```
if n == 10:
    x = "OK"
else :
    x = "NG"
```
は
```
x = "OK" if n == 10 else "NG"
```
と書ける。

### 奇数なら "even" 偶数なら "odd" を出力する
```
n = int(input())
print ("even") if n%2 == 0 else print ("odd")
```

### 配列から要素が最大値の値を取り出す(pop)

```
l.pop(l.index(max(l)))
```
※破壊的操作であることに注意

### 少数の四捨五入

```
round(i)
```

### 切り捨て
```
a = b//c
```

### 切り上げ
```
a = -(-b//c)
```

### IPアドレスのフォーマットかどうか

IPv4アドレスのフォーマットであるかどうか、のみを考える
つまり、 0.0.0.0 ~ 255.255.255.255 の間であればよい※実際に存在しうるIPv4アドレスかどうかまでは考慮しない

```
import re
def isIpv4addressFormat (x:str):
    ※ To be written...
```

https://qiita.com/mklot/items/dc5826c8b610e31275cc
https://qiita.com/dongri/items/2a0a18e253eb5bf9edba#python

