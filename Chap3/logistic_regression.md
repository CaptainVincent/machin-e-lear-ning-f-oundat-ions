# Logistic Regression

'soft' binary classification:
$$f(x) = P(+1|x) \in [0, 1]$$

與一般的 binary classification 的問題不同, 今天想知道的是這 binary 結果發生的機率各是多少? 但依據我們手上有的資料跟以前 binary classification 並無不同, 所以我們並不知曉這未知的機率, 我們僅有的是對某次 sample 到的 **x** 去計算出來的 y 各是多少, 所以從想像上這 N 次 Sample 的結果 y 其實是隱含著雜訊的資料 (預期是落在 0~1 的 $$\mathbb{R}$$, 但實際觀察到的僅是 0(-1) 或 1)。