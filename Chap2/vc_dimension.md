# VC Dimension
VC Dimension ($$V_{dc}$$) = 'minimum K' -1

![](dc_dimension.jpg)
透過上圖可以簡化我們的式子
$$
\begin{aligned}
\\m_{\mathcal{H}}(N)\leq \sum_{i=0}^{d_{vc}}\binom {N}{i}\leq N^{d_{vc}} \\\
\textit{( for }N\geq 2, d_{vc}\geq 2\textit{ )}
\end{aligned}
$$
## 機器學習的條件
* Good Hypothesis Set (有 Break Point)
* Good Data (N 夠大)
* Good Algorithm (可以挑到夠小的 $$E_{in}$$)
* Good Luck
