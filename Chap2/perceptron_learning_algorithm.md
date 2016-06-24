## Perceptron Learning Algorith

在開始用數學工具幫助我們理解為何可以學習前, 這裡先介紹一種簡單的機器學習演算法, 並在後續透過這個例子來加入數學工具分析 Machine Learning 的限制。


首先介紹一組 Hypothesis Set 的定義方式稱作 **Perceptron** 來求一個是非題的解, 數學上的符號如下

(令 **x** 為 d 維度的 input, **w** 為 d 維度的權重值)

**H**ypothesis Set = {**w**<sub>1</sub>, **w**<sub>2</sub>, ... **w**<sub>∞</sub>}

Σ <sub>(i=1~d)</sub> w<sub>i</sub>x<sub>i</sub> (再定義出一個 threshold 來二分這是非題的結果, y = {+1 , -1})

h(x) = sign ( Σ <sub>(i=1~d)</sub> w<sub>i</sub>x<sub>i</sub> - threshold ) 

令 w<sub>0</sub> 為 -threshold、x<sub>0</sub> 為 1, 則化簡如下

h(x) = sign ( Σ <sub>(i=0~d)</sub> w<sub>i</sub>x<sub>i</sub> ) = sign (**w**<sup>T</sup>**x**)

> 相當於取 w 與 x 兩個 d+1 維的向量內積。

目標是從 **H**ypothesis Set 中挑選出最接近 f 的 g, 而這最接近的定義為在已經看過的資料中可以產出愈相同的 output , 但實際上整個 H 是一個無限大的集合, 所以 **PLA** (Perceptron Learning Algorithm) 的想法是嘗試先從中挑選出第一個 g<sub>0</sub> (或稱 **w**<sub>0</sub>), 並不斷的在錯誤中修正。

### 演算法

If, sign (**w**<sup>T</sup>**x**<sub>n(t)</sub>) ≠ y<sub>n(t)</sub>

> hypothesis 計算的結果於資料中的不符, y<sub>n(t)</sub> = {+1,-1}

Let, **w**<sub>t+1</sub> = **w**<sub>t</sub> + y<sub>n(t)</sub> **x**<sub>n(t)</sub>

> 如果預期結果是正時, 因內積的兩個向量夾角過大才會是負, 所以修正方式是要往 **x** 方向靠近, 反之則要遠離 **x**

Until no more mistakes.

<img src="2DPLA.jpg" width="237" height="218"/>

(以二維(2D)的 input 為例做想像)

> sign (**w**<sup>T</sup>**x**) 中, **w**<sup>T</sup>**x** = 0 在二維中是一條法相量為 **w**<sup>T</sup> 的直線二分其結果 y, 在高維度時則是劃分結果 y 的則是法相量 **w**<sup>T</sup> 的高維平面。

### 是否會終止 ?
* Linear Separability 線性可分
> PLA 會終止的條件在於可以找到一個 **w**, 使得所有 sign (**w**<sup>T</sup>**x**<sub>n(t)</sub>) = y<sub>n(t)</sub>, 所以最根本的條件在於存在一條分割線/平面可以將所有 input **x** 根據 ouput y 劃分開來, 此特性稱作線性可分。
> 
> 同時 y<sub>n(t)</sub> **w**<sub>f</sub><sup>T</sup>**x**<sub>n(t)</sub> (所有 input 包含發生錯誤的點) ≥ min( y<sub>n</sub> **w**<sub>f</sub><sup>T</sup>**x**<sub>n</sub> ) > 0
* PLA 在線性可分的情況下, 每次的修正是否有朝更好的方向前進
> **w**<sub>f</sub><sup>T</sup> **w**<sub>t+1</sub> = **w**<sub>f</sub><sup>T</sup> (**w**<sub>t</sub> + y<sub>n(t)</sub> **x**<sub>n(t)</sub>) >= **w**<sub>f</sub><sup>T</sup> **w**<sub>t</sub> + min( y<sub>n</sub> **w**<sub>f</sub><sup>T</sup>**x**<sub>n</sub> ) > **w**<sub>f</sub><sup>T</sup> **w**<sub>t</sub>
>
> 上式僅證明了一半, 因為內積愈大有可能是因為 **角度愈靠近**, 卻也有可能是因為 **向量長度** 所造成
>
><div> 
\begin{equation}
  \begin{split}
  w_f^Tw_T &\geq w_f^Tw_{T-1} + min\ {y_nw_f^Tx_n} \\\
           &\geq ... \\\
           &\geq w_f^Tw_0 + T\cdot min\ {y_nw_f^Tx_n} = T\cdot min\ {y_nw_f^Tx_n}
  \end{split}
  \end{equation}
</div>
透過前式, 我們可以一路推導做了 T 次修正後如上的結果

<div> 
\begin{equation}
\begin{split}
||w_{t+1}||^2 &=    ||w_t + y_{n(t)}x_{n(t)}||^2 \\\
              &=    ||w_t||^2 + 2y_{n(t)}w_t^Tx_{n(t)} + ||y_{n(t)}x_{n(t)}||^2\\\
              &\leq ||w_t||^2 + 0 + ||y_{n(t)}x_{n(t)}||^2 \\\
              &\leq ||w_t||^2 + max\ {||x_n||^2}
\end{split}
\end{equation}
</div>
因為我們僅在錯誤的時候做修正, 所以中間項的乘積會 < 0, 上式就是我們得到的向量長度 Upper bound

<div> 
\begin{equation}
\begin{split}
  ||w_T||^2 &\leq ||w_{T-1}||^2 + max\ {||x_n||^2} \\\
            &\leq ... \\\
            &\leq ||w_0||^2 + T\cdot max\ {||x_n||^2} = T\cdot max\ {||x_n||^2}
\end{split}
\end{equation}
</div>
接著一樣透過前式, 我們可以一路推導做了 T 次修正後如上的結果

<div>
\begin{equation}  
\begin{split}   
1 &\geq \frac{w_f^Tw_T}{||w_f||||w_T||} &\geq \frac{T\cdot min\ y_nw_f^Tx_n}{||w_f||||w_T||} \ &\geq \frac{T\cdot min\ y_nw_f^Tx_n}{||w_f||\cdot \sqrt{T}\cdot max\ {||x_n||^2}}  = \frac {\sqrt{T}\rho}{R}   
\end{split}    
\end{equation}
</div>
最後可以求出 cos θ 經過 T 次迭代後的收斂式子 (ρ 與 R 皆是我們導出的常數), 因此我們可知當今天的資料是 Linear Separability 時

* PLA 確實可修正 **W**<sub>t</sub> 使其更加靠近 **W**<sub>f</sub>
* 由 lower bound 可以知道經過有限次的迭代後, 此演算法會中止
* 綜合以上兩點所以 PLA 可以找到一條完美的分割線

得到以上的結果後, 對於 PLA 還是存在一些疑問, 包括了如何知道資料是線性可分 (**W**<sub>f</sub> 存在), 如果是已知那實際上我們也就不需要做 PLA, 所以這部分通常是未知, 另一個問題是怎麼知道要做多久才會結束?
