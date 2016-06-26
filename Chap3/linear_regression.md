# Linear Regression

Linear Regression 討論的問題在於 output 是屬於 $$\mathbb{R}$$ 實數空間

Linear Regression 的 Hypothesis (這僅是其中一種 H 的設計方式)

$$h(x)=\sum_{i={0}}^d w_ix_i= w^Tx$$

問題可以想像成是在求出一條/高維平面, 當 **x** 代入時可以與 $$y_n$$ 愈接近。 (紅色標出的距離稱作 residuals 餘數)
![](illustrationLR.jpg)
這邊 Error Measure 是使用這個問題傳統常用的 **Squared**
$$
\begin{matrix}
err(\hat{y}_n,y_n) = (\hat{y}_n-y_n)^2
\end{matrix}
$$How to minize $$E_{in}$$?