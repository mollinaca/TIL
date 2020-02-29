
# よく使う関数群


## 偶数ならTRUEを返す

```
def isEven (x:int):
    return TRUE if x%2 == 0 else return FALSE
```

## 奇数ならTRUEを返す

```
def isOdd (x:int):
    return TRUE if x%2 == 1 else return FALSE
```

## 偶数か奇数かを返す

```
def even_or_odd (x:int):
    return "Even" if x%2 == 0 else return "Odd"
```

## 約数のリストを返す

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

## 最大公約数

python3.5以前なら fractions.gcd()
https://docs.python.org/ja/3/library/fractions.html#fractions.gcd
python3.5以降なら math.gcd()
https://docs.python.org/ja/3/library/math.html#math.gcd

```
import fractions
gcd(a,b)
```

複数の値の最大公約数を求める場合は、reduce()を使って以下のように再帰的に求める
```
import math
from functools import reduce

def gcd_list(numbers):
    return reduce(math.gcd, numbers)
```
numbersは数値が入ったリスト

## 最小公倍数


```
import factions/math
def lcm(a:int,b:int):
    return a // math.gcd(a, b) * b
```

複数の値の最小公倍数
```
import math
from functools import reduce

def lcm_list(numbers):
    return reduce(lcm, numbers)
```

## 素数かどうか判定する

O(n)
```
def isPrime(x:int):
    for i in range(2,n):
        if x%i == 0:
            return False
    else:
        return True
```

O(sqrt(n))
```
import math

def isPrime(x:int):
    if x < 2 or x == 9:
        return False
    if x == 2:
        return True
    if x%2 == 0:
        return False
    for i in range(3,int(math.sqrt(x)),2):
        if x%i == 0:
            return False
    else:
        return True
```

O(sqrt(n)) math を使わない
```
def isPrime(x:int):
    if x < 2 or x == 9:
        return False
    if x == 2:
        return True
    if x%2 == 0:
        return False
    i = 2
    while True:
        i += 1
        if x%i == 0:
            print (i)
            return False
        if i*i >= x:
            return True
```

## 素数のリストを作る

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

## 桁和

```
def digsum(a:int):
    res = 0
    while a>0:
        res += a%10
        a //= 10
    return res
```
桁数は `len(a)` のみでおｋ

## 二つの文字列がアナグラムかどうか

ソートして一致すればアナグラムである
```
def is_anagram(test:str original:str):
    if sorted(test) == sorted(original):
        return true
    return false
```

### 10進数からN進数へ基数変換したら何桁になる？

つまり、元の数を何回Nで割れるかということ
```
def n_keta(n:int, k:int):
    while True:
        n = n//k
        count += 1
        if n == 0:
            return count
```
