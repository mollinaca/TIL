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

個数がわかる → それぞれの変数
```
a, b = map(str, input().split())
a, b = map(int, input().split())
```

個数がわからない、たくさん → list
```
str_list = [str(i) for i in input().split()] 
n_list = [int(i) for i in input().split()] 
```

## 標準出力

```
print (n) → n の中身
print ('test',str) → test という文字列に続いて str の中身
print (a+b,str) → aとbの和に続いて str の中身
```
