
# 正規表現ライブラリと使い方

`import re`  
https://docs.python.org/ja/3/library/re.html  

## 使い方

https://note.nkmk.me/python-re-match-search-findall-etc/  
* 正規表現パターンをコンパイル: compile()
* 文字列の先頭がマッチするかチェック、抽出: match()
* 先頭に限らずマッチするかチェック、抽出: search()
* 文字列全体がマッチするかチェック: fullmatch()
* マッチする部分すべてをリストで取得: findall()
* マッチする部分すべてをイテレータで取得: finditer()
* マッチする部分を置換: sub(), subn()
* 正規表現パターンで文字列を分割: split()

## fullmatch

https://atcoder.jp/contests/abc049/tasks/arc065_a  

```
if re.fullmatch(r"(dream|dreamer|erase|eraser)+", s):
    print("YES")
else:
    print("NO")
```

