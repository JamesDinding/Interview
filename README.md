# Interview

解題方向
用fakeData來假裝是接收到的資料，用遞迴的方始寫setTimeout限時1秒讓頁面轉跳，如過list中的url都無法在1秒內轉跳完成，
最後會導回一開始初始的頁面，並顯示無法提供服務。因為會重新導回原本的頁面，所以設變數用localStorage存，表示有無訪問
過原本的頁面，不然會變成無限迴圈。
為了方便測試，點擊"無法提供服務"會清除localStorage並重新載入。

作法導致的問題點，以b-domain.com來說，會轉跳過去，This site can’t be reached，去devtool上去看，status會是(failed)net::ERR_NAME_NOT_RESOLVED，
不太確定怎麼處理，畢竟轉跳過去後就沒辦法執行剩下的code了。(在fakeData中註解掉了)
再來是像c-domain.com轉跳時，有時會顯示連結不安全是否要前往之類的。(測試時我是先將時限縮小到0.1秒)

總的來說就是沒有辦法事先確認要訪問的網站是否存在或安全，就只是在1秒內能轉跳就轉跳，而導致的問題點。
