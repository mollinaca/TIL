
# イテレータとかそういうオブジェクトとか

## list

```
list = []
```



## dict

```
dict = {}
```

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
date_list = [k for k, v in bloom.items() if v == max(bloom.values())]
```
dict: bloom の中で、要素の値が最大のもののリストを抽出する

## リスト内包表記

`[式 for 任意の変数名 in イテラブルオブジェクト]`
`[式 for 任意の変数名 in イテラブルオブジェクト if 条件式]`
`[真のときの値 if 条件式 else 偽のときの値 for 任意の変数名 in イテラブルオブジェクト]`


```
d_list = [int(input()) for d_list in range(n)]
```

```
count = len([x for x in data if x % 3 == 0]) # 3の倍数をカウント
```

```
d = {'key1': 'aaa', 'key2': 'aaa', 'key3': 'bbb'}
value = d['key1']
print(value)
 -> aaa
```

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