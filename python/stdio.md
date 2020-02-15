# memo

## 参考

https://qiita.com/_-_-_-_-_/items/34f933adc7be875e61d0
https://qiita.com/y-tsutsu/items/aa7e8e809d6ac167d6a1
https://qiita.com/kyuna/items/8ee8916c2f4e36321a1c
https://note.nkmk.me/python-str-extract/

## 標準入力を受け取る

### 一つの文字列

```
str=input().rstrip()
n=int(input().rstrip())
```

### 複数の文字列

* 個数がわかる → それぞれの変数
```
a, b = map(str, input().split())
a, b = map(int, input().split())
```

* 個数がわかるがたくさん → list
```
n = int(input())
d_list = [int(input()) for d_list in range(n)]
```

* 個数がわからない → list
```
str_list = input().split()
int_list = list(map(int,input().split()))
```

* n回の繰り返しで複数の文字列を取得しながら処理
```
n = int(input())
for _ in range(n):
    a, b = map(str, input().split())
    d = [int(input()) for d in range(n)]
    # 処理...
```

* 0埋めした a*b の2次元配列を作る
```
a, b = map(int, input().split())
arr = [[0 for i in range(a)] for j in range(b)]
```

* n行の2次元配列（1行当たりの要素数に制約なし）
```
n = int(input())
grid = []
for _ in range(n):
    array = list(map(int, input().strip().split()))
    grid.append(array)
```

## 標準出力

```
print (n)
 → n を出力

print ('test', str)
 → test という文字列に続いて str の中身

print (a+b, str)
 → aとbの和に続いて str の中身

print ("x"*n)
 → xをn個続けて出力する

print (''.join(sorted(x)))
文字列をソートして文字列として出力する
joinをしないと、sortedの結果のリストで1文字ずつリストの要素として出力される

print (sum(list[i:i+n]))
 → list[i:i+1]の要素の和を出力

print(' '.join(map(str, a_list)))
 → リストの要素をスペース区切りで出力する。末尾にはスペースが入らず、改行される
```

