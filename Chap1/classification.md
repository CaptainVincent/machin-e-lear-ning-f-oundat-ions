# Classification 機器學習的分類
在整個學習的 Model 中針對控制變因的種類區分定義其特性。

##### 以提供不同 y<sub>n</sub> 形式區分的學習方式
* Supervised 監督式, 提供匹配的問題與解答來教學 (其他方式的基礎)
* Unsupervised 分群的問題, 不提供 y<sub>n</sub>
* Semi-supervised 數量多無法窮舉時, 部分標記剩餘透過機器學習分類
* Reinforcement 單筆單筆的告知系統反應是 好 或是 不好, 不一定精確知道其輸入對應的輸出為何, 但有輔助判定的資訊

##### 以提供資料方式區分的種類
* Batch 成批的資料訓練
* Online, sequentially 一個一個的逐步改善 
* Active, sequentially 機器主動的方式來自動挑出盲點 (應用於標記資料需要高成本)

##### 以資料內容區分的種類
* Concrete Features 具體有關聯性的特徵 (需有 domain knowledge)
* Raw Features 通常需要人或機器建立、抽取出具體的特徵, 以避免原始資料對於問題過於抽象
* Abstract Features 輸入資料完全不具任何意義, 同 raw features 一樣需要建立出特徵
