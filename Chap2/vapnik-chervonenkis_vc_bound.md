# Vapnik-Chervonenkis (VC) bound

$$
\mathbb{P}_\mathcal{D}[BAD\ D]\leq 2\cdot2m_{\mathcal{H}}(2 \cdot N)\cdot exp(-2 \cdot \frac{1}{16} \epsilon ^2N)
$$
這個章節要將 **壞事情發生的機率** 給出更為嚴謹的不等式 (上式) 來 bound 住。

## Proof

$$
\mathbb{P}[\exists h \in H s.t. | E_{in} - E_{out} > \epsilon]
$$壞事情發生的機率還存在一個 ∞ 個的變因, 那就是 