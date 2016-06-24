# When Can Machine Learn?

模仿人類學習的方式, 透過觀察 (data) 學習 (取出特徵、經過計算處理) 後得到有意義的技巧 (提升某項可以量化評估的表現)。

##### 一些應用機器學習的時機
* 過於複雜 (不預期的狀況) 的系統不容易轉化成程式來處理
* 不容易寫出判定規則的系統
* 人尚未或無法即時判定的行為
* 過分客製化 (數量過多) 的反應

##### 使用條件
* 具備 可理解的特徵 以及 可供量化評估改進的結果
* 不容易定義出規則 (容易定義則使用規則撰寫一般的程式處理即可)
* 有資料可供學習

## Model Component
* **A**lgorithm, learning algorithm 為挑選假說的演算法
* **D**ata Set, D: {(**X**<sub>1</sub>,Y<sub>1</sub>), (**X**<sub>2</sub>,Y<sub>2</sub>), ... (**X**<sub>N</sub>,Y<sub>N</sub>)}
* **X** 為 input 的特徵向量, Y 為 Output
* **H**ypothesis Set, 推論 **X** 與 Y 之間存在關係的假說集合
* **f** 理想上的 target function 可以完全地反應出所有的關係 (實際上 unknown), f: **X** → Y
* **g** 透過 algorithm 從 hypothesis set 中挑選出最接近 f 者
* **A** takes **D** and **H** to get **g** ≈ **f**, 機器學習是透過資料從假說中挑選最接近目標函式者, 用以推測訓練資料以外的其他資料結果
* Learning Model = **A** and **H**

> **Machine Learning vs Data Mining**

> 資料探勘通常是對大量的資料中尋找有用的性質, 如果這個性質的目標是找出更好的 hypothesis, 則兩者的差異不大 或是 可相互幫忙。

> **Machine Learning vs Artificial Intelligence**

> 人工智慧的目標在於經過計算之後可以得到具備智能的行為, 而機器學習是其中一種實現人工智慧的方法 (其他方法像是 決策數)。

> **Machine Learning vs Statistics**

> 統計學是用資料推論一些未知的結果, 所以統計是機器學習中會使用到的其中一種工具。