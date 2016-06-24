## Perceptron Learning Algorithm
在開始用數學工具幫助我們理解為何可以學習前, 這裡先介紹一種簡單的機器學習演算法, 並透過這個例子來加入數學工具的分析。


這邊介紹一種簡單的 Hypothesis Set 的定義方式稱 **Perceptron** 來求一個是非題的解, 數學上的符號如下

令 **x** 為 d 維度的 input, **w** 為 d 維度的權重值

**H**ypothesis Set = {**w**<sub>1</sub>, **w**<sub>2</sub>, ... **w**<sub>∞</sub>}

Σ <sub>(i=1~n)</sub> w<sub>i</sub>x<sub>i</sub> (再定義出一個 threshold 來二分這是非題的結果, y = {+1 , -1})

h(x) = sign ( Σ <sub>(i=1~n)</sub> w<sub>i</sub>x<sub>i</sub> - threshold ) 

令 w<sub>0</sub> 為 -threshold、x<sub>0</sub> 為 1, 則化簡如下

h(x) = sign ( Σ <sub>(i=0~d)</sub> w<sub>i</sub>x<sub>i</sub> ) = sign (**w**<sup>T</sup>**x**)

> 相當於取 w 與 x 兩個 d+1 維的向量內積。