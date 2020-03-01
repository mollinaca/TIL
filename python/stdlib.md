
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

