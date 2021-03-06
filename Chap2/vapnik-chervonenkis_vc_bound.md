# Vapnik-Chervonenkis (VC) bound (未完成)

$$
\mathbb{P}_\mathcal{D}[BAD\ D]\leq 2\cdot2m_{\mathcal{H}}(2 \cdot N)\cdot exp(-2 \cdot \frac{1}{16} \epsilon ^2N)
$$
這個章節要將 **壞事情發生的機率** 給出更為嚴謹的不等式 (上式) 來 bound 住。

## Proof
[參考課程影片](https://www.youtube.com/watch?v=GcxpsIvR7t8&index=25&list=PLXVfgk9fNX2I7tB6oIINGBmW50rrmFTqf)

$$
\mathbb{P}[\exists h \in H s.t. | E_{in}(h) - E_{out}(h) > \epsilon]
$$
壞事情發生的機率實際上還存在一個 ∞ 個的變因, 那就是 $$E_{out}$$, 所以第一步我們要先替換掉 $$E_{out}$$, 這邊假設的是我們做驗證的時候, **D**ata 不再從無限大的 outside 取了, 而是從我們的另一組 N 個 input 的 **D'ata** 去取, 而由於 D' 與 D 都是相同的機率分佈的 Sample, 所以當我們今天取得 $$E_{in}$$ 離 $$E_{out}$$ 很遠時, 有超過 $$\frac{1}{2}$$ 以上的機會離 $$E'_{in}$$很遠 (如下圖示)

![](pdf_of_ein.png)

由於
$$
\left.\begin{matrix}
|E_{in}^{'} - E_{out}|\leq \frac{\epsilon}{2}\\\
|E_{in}-E_{out}| \gt \epsilon
\end{matrix}\right\}
\Rightarrow
|E_{in}-E_{in}^{'}| \gt \frac{\epsilon}{2}
$$
可以得到
$$
\frac{1}{2}\mathbb{P}[\exists h \in H \ s.t. | E_{in}(h) - E_{out}(h) > \epsilon] \le \mathbb{P}[\exists h \in H \ s.t. | E_{in}(h) - E'_{in}(h)| > \frac{\epsilon}{2}]
$$
代換之後的不等式如上, 嚴謹數學證明參考自 [beader.me](http://beader.me/mlnotebook/section2/vc-dimension-two.html) (小弟實在還參不透)

$$
\begin{aligned}
\mathbb{P}[BAD\ D] &\le 2 \cdot \mathbb{P}[\exists h \in H \ s.t. | E_{in}(h) - E'_{in}(h) > \frac{\epsilon}{2}] \\
&\le 2m_{H}(2N)\mathbb{P} [fixed \ h \ s.t. | E_{in}(h) - E'_{in}(h)| > \frac{\epsilon}{2}]
\end{aligned}
$$
這邊使用 $$m_{H}(2N)$$ 來表示兩次 (D and D') 抽出的 input, Hypothesis 可以將它們分類的種類上限有幾種, ... (證明待補)

## Summary
雖然證明的部分尚未補完, 但在這裡我們先相信 VC bound 是已知且證明了, 那麼我們學到了什麼? 從一開始透過數學歸納法瞭解 Break Point 如何影響 Dichotomy 的上限函數 (Bounding Function), 然後知道這類的 Hypothesis 存在多項式關係的上限數量, 最後導回 Hoeffding's Inequality 中的 M, 得到當滿足 Hypothesis Set 具有 Break Point 時, 都可以透過夠多的 input 來達到 (**存在 Break Point** 且 **資料量夠多**)

* 降低 $$E_{in}$$
* 同時也使 $$E_{in}$$ 與 $$E_{out}$$ 接近