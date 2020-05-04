
# 問題解いてたらでてきた数学の知識

本質的に python とは無関係であるので、別ディレクトリにしたほうがよいかも。  
とりあえずメモ。  


## 二項係数を含む等式

```math
\sum_{i=0}^{N} {}_N \mathrm{C} _i=2^N
```
![math](./math/math_20200204.gif)

## 1 から P までの P 種類の目が等確率で出るサイコロの出目の期待値

そもそも期待値
http://w3e.kanazawa-it.ac.jp/math/category/kakuritu/kakuritu/henkan-tex.cgi?target=/math/category/kakuritu/kakuritu/kitaiti-no-teigi.html

```
def ex(p:int):
    return (1+p)/2
```

## 座標上の三角形の面積

3点 (0,0),(a,b),(c,d) で構成される三角形の面積は、 |ad-bc|/2  
3点 (x,y),(a,b),(c,d) で構成される三角形の面積は、 |(a-x)*(d-y)-(b-y)(c-x)|/2  
