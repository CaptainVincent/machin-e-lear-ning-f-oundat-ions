# Logistic Regression

'soft' binary classification:
$$f(x) = P(+1|x) \in [0, 1]$$

與一般的 binary classification 的問題不同, 今天想知道的是這 binary 結果發生的機率是多少? 但依據我們原先的資料, 我們並沒有方法得知這未知的機率, 我們僅有的是對某次 sample 到的 **x** 去計算出來的 y 各是多少, 所以從想像上這 N 次的結果 y 是隱含著雜訊的資料,