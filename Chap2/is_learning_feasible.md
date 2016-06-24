# 機器學習可行嗎?
最根本的現實是機器學習即便挑選的演算法以及假說設定的再好, 最終也只能代表 inside **D**ata 能有不錯的表現, 關於 outside **D**ata 的一切我們都是未知, 接下來就是探討對於現實我們是否能增加一些假設條件, 來對於這些未知的結果得到較為可靠的預測 (透過數學的工具)。


## Topic I (Hoeffding's Inequality)
**Sample (取樣) 的代表性**, 假設取樣中某特徵呈現的機率為 ν, 而實際機率為 μ, 則兩者存在以下不等式的關係稱 Hoeffding's Inequality

P [|ν - μ| > ɛ] ≤ 2 exp (-2ɛ<sup>2</sup>N), ɛ 為誤差範圍、N 為取樣數

* 誤差愈大 或 取樣數愈大, 不等式右項就愈小, 表示發生的可能性愈低
* ν = μ 是 PAC (**P**robably **A**pproximately **C**orrect) 很大的機會是對的, 但還是有例外

## Topic II
將 Hoeffding's Inequality 導入 Learning Model, 推敲 outside **D**ata, 假定透過相同的 P 機率分佈作為產生 訓練資料(inside **D**) 及 測試資料(outside **D**) 的樣本, 這邊機率的意涵為 **D**ata 透過特定 **H**ypothesis 產生對或錯的機率 (使用 **E**rror 作為錯誤的機率)。

P [|E<sub>in</sub>(h) - E<sub>out</sub>(h)| > ɛ] ≤ 2 exp (-2ɛ<sup>2</sup>N)

所以當取樣 (N) 夠多時

* E<sub>in</sub>(h) ≈ E<sub>out</sub>(h)
* 又當 E<sub>in</sub>(h) 夠小時, g = f is PAC (**P**robably **A**pproximately **C**orrect)
* 說明了如何驗證一個 Hypothesis 的好壞, 但不保證被 Algorithm 挑選到