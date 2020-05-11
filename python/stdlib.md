
# python の標準関数

3.7における標準関数の一覧
https://docs.python.org/ja/3.7/library/index.html

以下、メモ的なもの

## sys

再帰回数の上限設定
https://note.nkmk.me/python-sys-recursionlimit/

```
import sys
sys.setrecursionlimit(500000)
```

## collections

### deque

デックと読む  
キュー、スタック、両端キューを表現するのに使う  
https://docs.python.org/ja/3/library/collections.html#collections.deque  
https://note.nkmk.me/python-collections-deque/  

上3つのデータ構造を表現する場合は最も効率がいいが、中央の値を操作したい場合は list で実装したほうがよい  

* append: 末尾に要素を足す
* appendleft: 先頭に要素を足す
* pop: 末尾から要素を取りだす
* popleft: 先頭から要素を取り出す

キュー(FIFO)として使う場合は、エンキューとして `append()`、デキューとして `popleft()`    
スタック(LIFO)として使う場合は、プッシュとして `append()`、ポップとして `pop()`   
を使う  

## itertools

イテレータを生成する  
https://docs.python.org/ja/3/library/itertools.html  

### product()

nestしたループを作る
https://docs.python.org/ja/3/library/itertools.html#itertools.product

`product('ABCD', repeat=2)`
# => AA AB AC AD BA BB BC BD CA CB CC CD DA DB DC DD

### permutations()

https://docs.python.org/ja/3/library/itertools.html#itertools.permutations  
https://torina.top/detail/310/  

```
for i in itertools.permutations(['a', 'b', 'c']):
    print(i)

('a', 'b', 'c')
('a', 'c', 'b')
('b', 'a', 'c')
('b', 'c', 'a')
('c', 'a', 'b')
('c', 'b', 'a')
```

```
for i in itertools.permutations(range(3)):  # 0, 1, 2
    print(i)

(0, 1, 2)
(0, 2, 1)
(1, 0, 2)
(1, 2, 0)
(2, 0, 1)
(2, 1, 0)
```

```
origin_list = ['a', 'b', 'c']
for i, _ in enumerate(origin_list, 1):     
    for j in itertools.permutations(origin_list, r=i):  # rには1、2、3と渡される
        print(j)

('a',)
('b',)
('c',)
('a', 'b')
('a', 'c')
('b', 'a')
('b', 'c')
('c', 'a')
('c', 'b')
('a', 'b', 'c')
('a', 'c', 'b')
('b', 'a', 'c')
('b', 'c', 'a')
('c', 'a', 'b')
('c', 'b', 'a')
```
