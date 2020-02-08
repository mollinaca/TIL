
# リスト内包表記によるリスト作成

※書く

# 約数のリストを返す関数

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

