# 台南主題地圖
用各種統計資料以地圖視覺化的方式呈現
讓人可以比較直觀的方式來一目瞭然事情與情況的輕重分布
以下為我們各自的主題：
>1.台南空氣品質
>[name=資訊系108謝宗祐]
>2.台南交通事故情況
>[name=資訊系108李翊倫]
>3.台南市公車圖
>[name=測量系110林彥呈(組長)]
---
---
## 專案一
>[name=謝宗祐]

### 動機:
近年來，PM2.5的問題越來越多人去注意到，空氣污染的問題可說是越來越嚴重，於是我就想要做一個能把台南空氣品質標示出來的主題地圖，除了讓自己明白台南空氣品質現況，也能讓更多人看見台南的空氣品質可能會有甚麼問題。

### 起初構想：
首先希望能做出2017年的地圖，接著再去做前幾年的地圖，進一步做比對，看哪些區的空氣品質是越來越嚴重，或是有改善了。最後，根據做出來的地圖比對，試著去預測2018年的空氣品質。

### 最後實作:
沒想到整個台南市竟然只有4個測量站，因此最後我只做了2017年的地圖，除了將幾項數據標示在點上外，也附上超連結能直接了解現在該站空氣品質的情況。最後，原本我想做出近幾年的空氣品質地圖，但想想那應該都會是差不多的東西，於是我就在收集完數據後，將近三年的數據做整理比對，並觀察有何重大改變，最後把我觀察到的結果給紀錄在點上。所有的動作都是透過臺南文史資源地圖協作平臺來完成，只要先將資料整理好，透過csv檔匯入，即可快速又方便的把數據呈現在圖上。

[臺南文史資源地圖協作平臺](http://hpgis.rchss.sinica.edu.tw/tncr/mapsites/)
資料例圖(整理前)
![](https://i.imgur.com/ybkqn37.png)

資料例圖(整理後)
![](https://imgur.com/VVpeLGK.png
)

實際結果
![](https://imgur.com/fcyd72L.png
)

### 心得:
這次的地圖讓我明白其實台南的空氣品質有越來越進步的情況，不過懸浮微粒(也就是我們所知的PM2.5及PM10)卻有不減反升的結果，值得我們注意。最後希望關心這個議題的人能提供一些意見來讓這張地圖更好，呈現更完整的資訊，也歡迎大家一起協作這張台南空氣品質地圖。

---
---
## 專案二
>[name=李翊倫]
### 專案主軸：
根據台南市警局的轄區來劃出地圖的分布
並列出交通事故資料。



如下圖為台南市警局轄區
![轄區](https://www.tnpd.gov.tw/chinese/file/map1.jpg)
![轄區](https://i.imgur.com/DFv5GLW.png)


如下圖為台南市交通事故資料
![106資料](https://i.imgur.com/WPyUino.png)
>有如底下的各種事故原因的資料：
>1.汽（機、慢）車駕駛人過失
>2.機件
>3.行人（或乘客）過失
>4.交通管制（設施）缺陷
>5.其他

另外還有列出死亡與受傷的人數
可以看出道路交通事故的高風險區域

再用人口和地籍資料把資料整理一下
[台南市民政局107年5月份人口資料](http://web.tainan.gov.tw/agr/population.asp?nsub=I4A100)
![](https://i.imgur.com/GLRWx2F.png)
[臺南市行政區規劃_wiki](https://zh.wikipedia.org/wiki/%E8%87%BA%E5%8D%97%E5%B8%82%E8%A1%8C%E6%94%BF%E5%8D%80%E5%8A%83)
![](https://i.imgur.com/faQEmby.png)
人口資料為107年4月
(取維基百科內的行政區域面積和台南市民政局的107年5月人口資料)


>列出如下列各種資料
>1.事故人數/地區總人口
>2.事故人數/地區面積
>3.事故人數/地區人口密度

**把資料加權之後更能明確指出實際地區上交通的危險程度**

![](https://i.imgur.com/WfNVrIR.png)

![](https://i.imgur.com/ByFzQvE.png)
如上圖 為整理後的資料

### [臺南文史資源地圖協作平臺](http://hpgis.rchss.sinica.edu.tw/tncr/mapsites/)
把資料上傳到這個分享平台之後
可以看到各個分局的所在位置
還有其轄區的相關事故資料

![](https://i.imgur.com/iQT6pZC.jpg)

![](https://i.imgur.com/nQxYTRB.jpg)

![](https://i.imgur.com/19twCcL.png)
### 實做python小程式
但是這很明顯沒有發揮地圖的視覺化功用
網路上又找不到公開的有明確地點的資料
因此用了一個比較偷吃步的方法是說
為了要顯示事故事件的密集度
假設事件是平均分佈在轄區之中
那麼把一個轄區裡有幾次事故拆成幾筆資料
其中的X、Y分別是：
分局的座標+sqrt(轄區面積)*(0~1的浮點數亂數)*0.0008
即可把資料視覺化再呈現在地圖上
(雖然和事實只是巨觀上相同，微觀上資料是錯的)

使用Python 2.7.14 寫了一個小程式
能把資料拆成很多項
![](https://i.imgur.com/F7IY3Me.png)
![](https://i.imgur.com/YMop92e.png)
![](https://i.imgur.com/DvaDyKq.png)

並且每一筆資料的經度、緯度都不太一樣
![](https://i.imgur.com/lrhWrre.png)
以Excel開起來的樣子


但是 實際上傳到平台的時候
卻顯示資料過多 伺服器處理得很慢
本機端也負荷不了
(總共18443筆資料)

![](https://i.imgur.com/LCoVLvO.png)

因此把資料換成1:25看看
每25筆資料則新增一個點
XY座標為：
分局的座標+sqrt(轄區面積)*(0~1的浮點數亂數)*0.0008

看出來點還是相當密集 不夠貼近事實
![](https://i.imgur.com/wktPrdW.png)



再把XY座標公式改為：
分局的座標+sqrt(轄區面積)*(0~1的浮點數亂數)*0.005
![](https://i.imgur.com/5LmtBUP.jpg)
再用平台內建的叢集模式觀看
![](https://i.imgur.com/SeurQ2n.jpg)
當縮放不一樣的時候顯示叢集的也不一樣
![](https://i.imgur.com/jTJzBjE.jpg)

因此能把「轄區事件/轄區面積」的資料視覺化



---
---
## 專案三
### 1.構想素材
> 依照現有的台南公車圖來描繪出更簡化的全圖，圖上會呈現路線的頻繁度、設站方向、附近TBike站點，主要目標在繪製出更一目了然的公車路線圖。
> **目前以台南市區為主，若有餘力會再做其他區。**
> 
> ![台南公車](https://i.imgur.com/de4oREm.jpg)

> 構想來源為南極冰魚交通地圖系列，台中市公車圖：
> 
> ![台中公車](https://i.imgur.com/9XYVhLY.png)

### 2.使用工具
> 使用Inkscape繪製向量圖型，方便未來修改，以及瀏覽縮放不失真。

### 3.目前進度
> [Finish](https://ncku365-my.sharepoint.com/:b:/g/personal/f64066096_ncku_edu_tw/EfWCxA5dZvVIim-YC6mf4NMBM6NGcKotjBNlvF5-g3SP0Q?e=R8zqQn)


## 資料來源
### 專案一
[台南空氣污染即時監測](http://aqicn.org/city/taiwan/tainan/hk/)
[行政院環保署空氣品質監測網](https://taqm.epa.gov.tw/taqm/tw/YearlyDataDownload.aspx)
[環保署環境資源資料庫](https://erdb.epa.gov.tw/DataRepository/EnvMonitor/AirQualityMonitorMonData.aspx?topic1=%E5%A4%A7%E6%B0%A3&topic2=%E7%92%B0%E5%A2%83%E5%8F%8A%E7%94%9F%E6%85%8B%E7%9B%A3%E6%B8%AC&subject=%E7%A9%BA%E6%B0%A3%E5%93%81%E8%B3%AA)
### 專案二
[臺南市道路交通事故原因傷亡統計](http://data.tainan.gov.tw/dataset/policedata016)
[台南警局轄區](https://www.tnpd.gov.tw/chinese/home.jsp?serno=201012130011&mserno=201012130002&menudata=TncgbMenu&contlink=content/org04.jsp&level2=Y)
### 專案三
[TBike站點分布圖](http://tbike.tainan.gov.tw/Portal/zh-TW/Station/Map)
