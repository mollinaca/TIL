# 深さ優先探索

参考:  
https://qiita.com/drken/items/4a7869c5e304883f539b  
https://qiita.com/drken/items/a803d4fc4a727e02f7ba  
https://qiita.com/takayg1/items/7008e4c9584e42ae13c7  

問題:  
https://atcoder.jp/contests/atc001/tasks/dfs_a  
#. で区画を表して、ゴールへたどり着けるか問題  

```atc001_a.py
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
import sys
sys.setrecursionlimit(500000)
h,w=map(int,input().split())
l=[list(input()) for _ in range(h)]

def dfs(r,c):
	if not(0<=c<w and 0<=r<h) or l[r][c]=="#":
		return
	if l[r][c]=="g":
		print("Yes")
		exit()
	l[r][c]="#"
	dfs(r+1,c)
	dfs(r-1,c)
	dfs(r,c+1)
	dfs(r,c-1)

for i,y in enumerate(l):
	if "s" in y:
		dfs(i,y.index("s"))
		break
print("No")
```  
dfs の再起で深さ優先探索を実現している


