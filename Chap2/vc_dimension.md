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
* Good Algorithm (可以挑到夠小 $$E_{in}$$ 的 Hypothesis)
* Good Luck

## VC Dimension for d-D Perceptron 
* 1-D perceptron: $$d{vc} = 2$$
* 2-D perceptron: $$d{vc} = 3$$
* d-D perceptron: $$d{vc} =^? d + 1$$

### Proof

##### Step 1. 證明 $$d_{vc} \ge d+1$$
> 證明的方式就是要證明當 **x** 為 d 維度時, d + 1 個 output 可以被 shattered

設計一個特殊矩陣, 表示將 d+1 個 input 組成一個 **X** 矩陣 (**X** 反矩陣存在 **invertible**)
$$
X =
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
   &&:&& \\
   1&0&0&...&1 \\
 \end{matrix}
 \right]
$$
根據定義

For any **y**, sign (**Xw**) = **y**, 那我們試著找一個 **w** 使得 **Xw** = **y** (假設存在這麼剛好的 **X**)

由前提知設計出的**X** 反矩陣存在, 所以 **w** = **X<sup>-1</sup>y** 也會存在, 得證存在某個 hypothesis **w** 使得任意 **y** 都可以被產生出來 (Shattered)。

##### Step 2. 證明 $$d_{vc} \le d+1$$
> 證明的方式就是要證明當 **x** 為 d 維度時, d + 2 個以上的 output 都不能被 shattered

$$
X =
 \left[
 \begin{matrix}
   - x_1^T - \\
   - x_2^T - \\
   - x_3^T - \\
   : \\
   - x_{d+1}^T - 
   - x_{d+2}^T - 
 \end{matrix}
 \right]
$$