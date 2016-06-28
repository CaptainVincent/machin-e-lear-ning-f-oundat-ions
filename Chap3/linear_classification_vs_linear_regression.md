# Linear Classification vs. Linear Regression
![](lc_compare_lr.jpg)
今天 Linear Classification 的問題, 我們在介紹 PLA 的時候有提到是 NP-hard, 但是今天 y output {-1,+1} 也都是 ∈ $$\mathbb{R}$$, 那我們是否能夠拿解 Linear Regression 的演算法來做 Linear Classification 的問題呢?

## Yes!
從兩者錯誤的衡量方式來觀察 $$\color{blue}{err_{0/1} = \left[ sign(w^\intercal x) \ne y \right]}$$ , $$\color{red}{err_{sqr} = (w^\intercal x) - y)^2}$$
![](error_measure_compare.jpg)
左圖所示, 當今天 y = 1 時, 預測的 y 對於兩種錯誤衡量方式計算出的結果, 右圖則是當 y = -1 的 case, 所以今天不論 y 為何 $$\color{blue}{err_{0/1}} < \color{red}{err_{sqr}}$$ 皆成立, 如下式我們知道之前 VC dimension 特性帶給我們的已知
$$
\begin{aligned}
\color{blue}{\text{classification} E_{out}} &\overset{VC}{\le} \color{blue}{\text{classification}\ E_{in}} + \text{Penalty for Model Complexity}\\\
&\le \color{red}{\text{regression}\ E_{in}} + \text{Penalty for Model Complexity}
\end{aligned}
$$
所以我們今天只要能保證紅色的 $$\color{red}{E_{in}}$$ 夠小, 就能保證 classification 的問題 $$E_{out} \approx E_{in}$$, 所以我們最後這邊可以用較寬鬆的 bound 但較為好解的方法。

## Advanced
大部分的時候我們使用 Linear Regression 的演算法來解 Binary Classification 已經夠好, 如果想要更好的話可以使用 $$w_{LIN}$$ 來作為 PLA/pocket 的 initial value。