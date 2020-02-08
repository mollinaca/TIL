
# よく使うイディオム、関数など

## イディオム

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

## 関数

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

