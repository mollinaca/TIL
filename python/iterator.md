
# イテレータとかそういうオブジェクトとか

## list

```
list = []
```

リストの一部の値のみに操作を行う ⇒ enumrateを使う
```
for i, v in enumerate(l[s:e]):
    l[i] = v //操作
```

リストから重複する要素を削除したリストを作る(uniq)
```
set(l)
```
set はコンストラクタで set型のオブジェクトを生成する
リストやタプルを渡すと、重複する要素を除外したsetオブジェクトを生成する

二つのリストをまとめて1ループで処理する

```
for a,b in zip(list_a, list_b):
    print (a,b)
```

## dict

```
dict = {}
```

```
dict{key} = value
```
 -> dictに key,value を add する

```
for k in d:
    print(k)
```
 -> key が出力される

```
for k in d.keys():
    print(k)
```
 -> key が出力される

```
for v in d.values():
    print(v)
```
 -> value が出力される

```
for k, v in d.items():
    print(k, v)
```
 -> key, value の両方が出力される

```
max_d = max(d)
```
 -> dict の key の最大値

```
max_v = max(d.values())
```
 -> dict の value の最大値

```
max_k = max(d, key=d.get)
```
 -> dict の value が最大となる key ※順序は保証されない任意の一つ

```
date_list = [k for k, v in bloom.items() if v == max(bloom.values())]
```
dict: bloom の中で、要素の値が最大のもののリストを抽出する


dictから、特定の値に一致するvalueをもつkeyの数を数える
```
d = {'key1': 'aaa', 'key2': 'aaa', 'key3': 'bbb'}
print (list(d.values()).count('aaa'))
```
 -> 2


## リスト内包表記

`[式 for 任意の変数名 in イテラブルオブジェクト]`  
`[式 for 任意の変数名 in イテラブルオブジェクト if 条件式]`  
`[真のときの値 if 条件式 else 偽のときの値 for 任意の変数名 in イテラブルオブジェクト]`  


```
l = [int(input()) for l in range(n)]
```
 -> 1行ずつ合計n行の整数型の入力を受け取りリストlにしまう

```
l = list(map(int,input().split()))
A = ([i for i in l if i > 0])
```
 → 標準入力からスペース区切りの数字列を受け取り、そこから整数のみのリストを作る  

```
l = [0 for l in range(n)]
```
 -> 0で初期化したn個の要素数のリストを作る


```
count = len([x for x in d if x < 0]) # 負の数をカウント
count = len([x for x in d if x == 0]) # 0の数をカウント
count = len([x for x in d if x > 0]) # 正の数をカウント
count = len([x for x in d if x%3 == 0]) # 3の倍数をカウント
```

数値が入ったリスト l から、負の数のみを抽出したリストを作る
```
l_minus = [i for i in l if i < 0]
```

文字列が入ったリスト l から、数値型のリストに変換する
```
l_i = [int(i) for i in l]
```

dict から、keyのvaleuを取り出す
```
d = {'key1': 'aaa', 'key2': 'aaa', 'key3': 'bbb'}
value = d['key1']
print(value)
 -> aaa
```

dictから、valueに等しいkeyを取り出す
```
keys = [k for k, v in d.items() if v == 'aaa']
print(keys)
 -> ['key1', 'key2']

keys = [k for k, v in d.items() if v == 'bbb']
print(keys)
 -> ['key3']

keys = [k for k, v in d.items() if v == 'xxx']
print(keys)
 -> []
```

dictから、条件を満たすvalueをもつkeyを取り出す
```
d_num = {'key1': 1, 'key2': 2, 'key3': 3}

keys = [k for k, v in d_num.items() if v >= 2]
print(keys)
 -> ['key2', 'key3']

keys = [k for k, v in d_num.items() if v % 2 == 1]
print(keys)
 -> ['key1', 'key3']

d_str = {'key1': 'aaa@xxx.com', 'key2': 'bbb@yyy.net', 'key3': 'ccc@zzz.com'}

keys = [k for k, v in d_str.items() if v.endswith('com')]
print(keys)
 -> ['key1', 'key3']
```
