# How Can Machines Learn?
透過之前的章節, 我們已經瞭解到了機器學習上的一些 運作原理 以及 限制, 這邊做個 Summary, 從一開始的 Learning Model 出發, 假設我們的 input **x**  來自於一個機率函數產生 (inside 與 outside 皆是), 此時我們有了從 Hoeffding's Inequality 延伸推導的 VC bound, 告訴我們機器學習在某些條件底下, 訓練出來的誤差是會有上限的 (這中間使用了許多 union bound 來求出上限的上限, 所以這個 bound 其實是教為寬鬆的), 然後在上一節將目標函數轉為目標機率分佈來產生 output, 表明 VC bound 在存在 noise 的情況下仍可適用 (當然 noise 是會影響機器學習的誤差), 並說明了一些量測錯誤的方式 及 應用。

接下來我們要進一步去介紹 **機器學習的其他問題**。