
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

### 素数判定

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