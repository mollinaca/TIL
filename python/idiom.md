
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

奇数なら "even" 偶数なら "odd" を出力する
```
n = int(input())
print ("even") if n%2 == 0 else print ("odd")
```

### 配列から要素が最大値の値を取り出す(pop)

```
l.pop(l.index(max(l)))
```
※破壊的操作であることに注意

## 関数

### 偶数ならTRUEを返す

```
def isEven (x:int):
    return TRUE if x%2 == 0 else return FALSE
```

### 奇数ならTRUEを返す

```
def isOdd (x:int):
    return TRUE if x%2 == 1 else return FALSE
```

### 偶数か奇数かを返す

```
def even_or_odd (x:int):
    return "Even" if x%2 == 0 else return "Odd"
```

### 素数のリストを作る

エラトステネスの篩による実装

```
import math
def eratosthenes(limit):
    A = [i for i in range(2, limit+1)]
    P = []
    
    while True:
        prime = min(A)
        
        if prime > math.sqrt(limit):
            break
            
        P.append(prime)
            
        i = 0
        while i < len(A):
            if A[i] % prime == 0:
                A.pop(i)
                continue
            i += 1
            
    for a in A:
        P.append(a)
            
    return P
```
素数のリスト P を返す


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

### 約数のリストを返す

```divs.py
def divs(n:int):
    divs = []
    for i in range(1, int(n**0.5)+1):
        if n % i == 0:
            divs.append(i)
            if i != n // i:
                divs.append(n//i)

    # divs.sort()
    return divs
```

### 二つの文字列がアナグラムかどうか

ソートして一致すればアナグラムである
```
def is_anagram(test:str original:str):
    if sorted(test) == sorted(original):
        return true
    return false
```

### 1 から P までの P 種類の目が等確率で出るサイコロの出目の期待値

そもそも期待値
http://w3e.kanazawa-it.ac.jp/math/category/kakuritu/kakuritu/henkan-tex.cgi?target=/math/category/kakuritu/kakuritu/kitaiti-no-teigi.html

```
def ex(p:int):
    return (1+p)/2
```
