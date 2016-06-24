# 機器學習可行嗎?
最根本的現實是機器學習即便挑選的演算法以及假說設定的再好, 最終也只能代表 inside **D**ata 能有不錯的表現, 關於 outside **D**ata 的一切我們都是未知, 接下來就是探討對於現實我們是否能增加一些假設條件, 來對於這些未知的結果得到較為可靠的預測 (透過數學的工具)。


## Topic I (Hoeffding's Inequality)
**Sample (取樣) 的代表性**, 假設取樣中某特徵呈現的機率為 ν, 而實際機率為 μ, 則兩者存在以下不等式的關係稱 Hoeffding's Inequality

P [|ν - μ| > ɛ] ≤ 2 exp (-2ɛ<sup>2</sup>N), ɛ 為誤差範圍、N 為取樣數

* 誤差愈大 或 取樣數愈大, 不等式右項就愈小, 表示發生的可能性愈低
* ν = μ 是 PAC (**P**robably **A**pproximately **C**orrect) 很大的機會是對的, 但還是有例外

## Topic II
將 Hoeffding's Inequality 導入 Learning Model 推敲 outside **D**ata, 假設產生 訓練資料(inside **D**) 及 測試資料(outside **D**) 是透過相同的 P 機率分佈 function, 這邊機率的意涵為 **D**ata 透過特定 **H**ypothesis 產生錯或對 (0/1) 的機率 (以下使用 **E**rror 表示錯誤的機率)。

P [|E<sub>in</sub>(h) - E<sub>out</sub>(h)| > ɛ] ≤ 2 exp (-2ɛ<sup>2</sup>N)

所以當取樣 (N) 夠多時

* E<sub>in</sub>(h) ≈ E<sub>out</sub>(h)
* 又當 E<sub>in</sub>(h) 夠小時, g = f is PAC (**P**robably **A**pproximately **C**orrect)
* 此評估 outside **D** 的方式, 說明了如何驗證單一一個 Hypothesis 的好壞, 但不保證此 Hypothesis 會被 Algorithm 挑選到

## Topic III (Pick Hypothesis Algorithm)
挑選 Hypothesis 的限制, E<sub>in</sub>(h) 最低不一定代表是最佳, 因為 sample 到不好的資料會讓 E<sub>in</sub>(h)、E<sub>out</sub>(h) 相距很遠, 當有選擇時, 會讓選出錯誤的 Hypothesis 機率增加 (更容易選到 overfitting 的假說, 只要某個 h 挑選到 bad sample data 時)。

####那究竟這個遇見 bad Sample 的機率有多高呢?
$$
\begin{aligned}
\ & \mathbb{P}_{\mathcal{D}}[BAD\ \mathcal{D}] \\\
\ & = \mathbb{P}_{\mathcal{D}}[BAD\ \mathcal{D}\ for\ h_1\ or\ BAD\ \mathcal{D}\ for\ h_2\ or\ ...\ or\ BAD\ \mathcal{D}\ for\ h_M]\\\
\ & \leq \mathbb{P}_{\mathcal{D}}[BAD\ \mathcal{D}\ for\ h_1] + \mathbb{P}_{\mathcal{D}}[BAD\ \mathcal{D}\ for\ h_2]+...+\mathbb{P}_{\mathcal{D}}[BAD\ \mathcal{D}\ for\ h_M] \\\
\ & \leq 2exp(-2\epsilon ^2N) + \leq 2exp(-2\epsilon ^2N) + ... + \leq 2exp(-2\epsilon ^2N) \\\
\ & = 2Mexp(-2\epsilon ^2N)
\end{aligned}
$$


**令有限 M 種的 Hypothesis**, 由 Topic I **Hoeffding's Inequality** 知道個別 Hypothesis 選中不好的資料 (E<sub>in</sub>(h)、E<sub>out</sub>(h) 相距很遠) 的機率不高, 所以 Σ <sub>(i=0~M) </sub>P<sub>D</sub>[BAD of D]≤ 2 M exp (-2ɛ<sup>2</sup>N), 可得知當

* 取樣個數夠多時
* 有限個數 M 的 **H**
 
E<sub>in</sub>(g) ≈ E<sub>out</sub>(g) is PAC 一樣會成立。

> Ｍ 的挑選是個取捨, 過小的話可以讓選中不好的 g 機會降低, 但是可以選的選項太少反而不一定存在可以挑出夠小的 E<sub>in</sub>(h), 太大的 M 則是讓選出不好的 g 機率增加。