# VC Dimension
VC Dimension ($$V_{dc}$$) = 'minimum K' -1

![](dc_dimension.jpg)
$$
\begin{aligned}
\\m_{\mathcal{H}}(N)\leq \sum_{i=0}^{d_{vc}}\binom {N}{i}\leq N^{d_{vc}} \\\
\textit{( for }N\geq 2, d_{vc}\geq 2\textit{ )}
\end{aligned}
$$
透過上圖可以簡化我們的式子
$$
\begin{aligned}
&\;\;\;\,\mathbb{P}[|E_{in}(g) - E_{out}(g)\gt \epsilon|] \\\
&= \mathbb{P}[BAD]\\\
&\leq \mathbb{P}[\exists h \in \mathcal{H}\text{ s.t. } |E_{in}(h)-E_{out}(h)|\gt \epsilon] \\\
&\leq 4m_{\mathcal{H}}(2N)exp(-\frac{1}{8}\epsilon^2N) \\\
&\leq 4(2N)^{d_{vc}}exp(-\frac{1}{8}\epsilon^2N) \\\
&\textit{( if }d_{vc}\textit{ is finite = k is exists)}
\end{aligned}
$$

## 機器學習的條件
* Good Hypothesis Set (有 Break Point)
* Good Data (N 夠大)
* Good Algorithm (可以挑到夠小的 $$E_{in}$$)
* Good Luck

## VC Dimension for d-D Perceptron 
* 1-D perceptron: $$d{vc} = 2$$
* 2-D perceptron: $$d{vc} = 3$$
* d-D perceptron: $$d{vc} =^? d + 1$$

### Proof
設計
$$
x =
 \left[
 \begin{matrix}
   - x_1^T - \\
   - x_2^T - \\
   - x_3^T - \\
   : \\
   - x_{d+1}^T - 
 \end{matrix}
 \right]
 =
 \left[
 \begin{matrix}
   1&0&0&...&0 \\
   1&1&0&...&0 \\
   1&0&1&...&0 \\
   : \\
   1&0&0&...&1 \\
 \end{matrix}
 \right]
$$