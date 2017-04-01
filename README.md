長庚大學 大數據分析方法 作業三
================

網站資料爬取
------------

``` r
library(Rfacebook)
```

    ## Loading required package: httr

    ## Loading required package: rjson

    ## Loading required package: httpuv

    ## 
    ## Attaching package: 'Rfacebook'

    ## The following object is masked from 'package:methods':
    ## 
    ##     getGroup

``` r
library(rvest) 
```

    ## Loading required package: xml2

``` r
Teco_job <-NULL
for (i in 1:6){
ppturl = paste("https://www.ptt.cc/bbs/Tech_Job/index",i,".html",sep="")
post_title <-read_html(ppturl) %>% 
html_nodes(".title") %>% 
html_text()
post_pushNum <- read_html(ppturl) %>% 
html_nodes(".nrec") %>% 
html_text()
post_author <- read_html(ppturl) %>% 
html_nodes(".author") %>% 
html_text()
Teco_job <- rbind(Teco_job,data.frame(Title = post_title,Author = post_author,PushNum = post_pushNum))
}

##read_html
##html_nodes
##html_text
```

爬蟲結果呈現
------------

``` r
knitr::kable(Teco_job) 
```

| Title                                                 | Author       | PushNum |
|:------------------------------------------------------|:-------------|:--------|
| \[公告\]有關本板                                      | Rooney       | 1       |
| \[轉錄\]職位中英文                                    | Rooney       | 5       |
| Re: \[轉錄\]\[就可\] 嫁給工程師的好處多?! ^\_^        | azer         | 69      |
| \[公告\] 發文類別新增　\[國防\] 選項                  | Rooney       | 2       |
| \[Tech\_Job\] 看板 選情報導                           | \[馬路探子\] | 2       |
| \[公告\] 投票結果與新板主志工報名                     | Rooney       |         |
| Re: \[公告\] 投票結果與新板主志工報名                 | Rooney       | 3       |
| Re: \[問題\] 科技人的另一半                           | Irisyeh      | 爆      |
| \[心得\] 請大家注意身體健康噢!                        | chienyu211   | 28      |
| \[公告\] 板規修改                                     | Rooney       | 6       |
| Re: \[心得\] 竹朝科技---一個讓我失望+後悔的公司       | bear3        | XX      |
| Re: \[無關\]boylover兄臺                              | Rooney       | 4       |
| \[公告\] 發文限制問題                                 | Rooney       | 5       |
| Re: \[問題\] 為什麼分紅費用化對員工不好呢?            | LKO          | 80      |
| \[公告\] 食衣住行與內幕文問題                         | Rooney       | 5       |
| \[公告\] 常見問題整理                                 | Rooney       | 2       |
| \[閒聊\] 被資遣注意事項!!!                            | oca          | 20      |
| Re: \[問題\] 上夜班如何調整作息?                      | tatibana31   | 5       |
| \[公告\] Tech\_Job板規                                | DEERETTE     | 4       |
| \[公告\] 新的標題分類                                 | layachang    | 1       |
| Re: \[新聞\] 我專利申請量 全球排名第七                | yaudeh       | 6       |
| Re: \[問題\] SSD出來以後,以後主機板會不會內建硬碟     | shter        | 10      |
| Re: \[討論\] 工程師們大多怎麼規劃人生呢               | deadly       | 22      |
| Re: \[新聞\] 索愛慘賠 本土代工廠很剉                  | shter        | 40      |
| \[分享\] 「求去者」所為何事？                         | VarX         | 3       |
| Re: \[問題\] 公司要求加班                             | spritecat    |         |
| Re: \[問題\] 關於研發替代役 錄取的關鍵是?!            | AixStyle     | 4       |
| \[心情\]大家加油不要灰心                              | mazerlin     | 24      |
| Re: \[面試\] 最近面試常被這個問題打敗...              | smalloc      | 2       |
| Re: 忽然覺得 讀書跟賺錢不怎麼成正比                   | g8330330     | 15      |
| Re: 忽然覺得 讀書跟賺錢不怎麼成正比                   | fbgae        | 16      |
| Re: 忽然覺得 讀書跟賺錢不怎麼成正比                   | hamk5202     | 44      |
| Re: \[心得\] offer被取消 沒想到我們也被耍了           | yuujang      | 5       |
| \[面試\] 心得分享                                     | tojump       | 5       |
| \[心得\] 硬體類研發替代役面試心得                     | blueangel629 | 3       |
| \[問題\] 面試自我介紹該講些什麼                       | ALiGoo       | 7       |
| 失業給付的申請 11                                     | WRITERT1NA   |         |
| \[公告\] 感謝sevencolor                               | layachang    | 11      |
| \[心得\] 如何寫份好履歷？從主管的角度看起！           | autumnbreeze | 8       |
| Re: \[問題\] 當找不到工作時，會不會有一種想輕生的 …   | Jongny       | 爆      |
| \[情報\] 台積電受害員工自救會                         | layachang    |         |
| \[公告\] 問卷規範                                     | layachang    |         |
| \[小小分享\] 面試中曾經被問過的問題～                 | winnie02022  | 30      |
| \[公告\] Tech\_Job版版規 0904                         | layachang    |         |
| Re: \[問題\] 請問讀交大電子博班畢業會不會加分呀?      | whni         | 5       |
| 職場求生術與政治學                                    | karlhsu      | 23      |
| \[公告\] 暫停回文                                     | layachang    |         |
| \[公告\] 討論串"台清交博士畢選六萬的工研院還<U+AC20>… | layachang    | 5       |
| \[公告\] 討論串"學歷重要嗎"                           | layachang    | 3       |
| Re: 進入哪家公司 才能夠擁有美好的人生?                | tyu26        | 7       |
| \[公告\] 暫停回覆                                     | layachang    |         |
| \[公告\] 討論串"\[長恨\] 無奈呀 職場如戰場 人生 …     | layachang    |         |
| \[公告\] 請暫停回覆討論串                             | layachang    | 6       |
| \[公告\] 討論串"\[閒聊\] 唸了這麼多書要做什麼??"      | layachang    | 8       |
| \[公告\] 討論串"\[問題\] 有人請教我如何進mtk?"        | layachang    | 7       |
| \[公告\] 誠徵副版主                                   | layachang    |         |
| \[公告\] 懇請熟識板主的板友代為通知                   | longbow2     | 6       |
| \[公告\] 本板暫由小組長接管，徵求新任板主             | longbow2     | 5       |
| \[公告\] 板主選舉投票開始                             | longbow2     | 1       |
| \[公告\] 板主票選提早開票                             | longbow2     |         |
| \[公告\] 解除 fdj 板主職位                            | longbow2     | 2       |
| \[公告\] 徵選本板板主一名                             | longbow2     | 3       |
| Re: \[政見\] illywu(ilsobeit) 競選 Tech\_Job 新版主   | longbow2     | 5       |
| \[公告\] 2009驚夏第一彈 討論串                        | longbow2     | 5       |
| \[政見\] 幫忙一下 若是有機會替大家服務                | harrygp      | 19      |
| \[公告\] achii 警告一次 及板主選舉事項                | longbow2     | 10      |
| Re: \[檢舉\] 鬧板                                     | longbow2     | 9       |
| \[公告\] 物價與薪資 文刪文， SmallJohn 警告一次       | longbow2     | 6       |
| \[公告\] 板主選舉開始                                 | longbow2     | 2       |
| \[公告\] 刪文及水桶（achii）                          | longbow2     | 18      |
| Re: \[討論\] 問一個問題 版主真抱歉                    | longbow2     |         |
| \[公告\] 刪文、水桶、劣退（goosey、dkenvy）           | longbow2     | 4       |
| \[公告\] 投票即將截止，請板友踴躍投票                 | longbow2     | 2       |
| \[公告\] harrygp 就任本板板主                         | longbow2     | 6       |
| \[面試\] 友達光電面試心得                             | Sunghui      | 9       |
| \[討論\] 威盛在臺灣那邊的工資開到多少                 | qiantangchao | 7       |
| Re: \[討論\] 威盛在臺灣那邊的工資開到多少             | twwo         | 3       |
| Re: \[討論\] 威盛在臺灣那邊的工資開到多少             | qiantangchao |         |
| Re: 台積12廠奈米技術整合工程師                        | powerme      | 49      |
| \[面試\] 面試分享                                     | mythlove     | 9       |
| Re: \[討論\] 請教harrygp板主 這樣該給桶嗎?            | harrygp      | 16      |
| Re: \[公告\]徵求另外一位板主共同管理                  | cloud7515    | 17      |
| \[政見\] shaffer 應徵版主                             | shaffer      | 4       |
| Re: \[公告\]徵求另外一位板主共同管理                  | ShortestPath | 8       |
| Re: \[公告\]徵求另外一位板主共同管理                  | glo6e        | 3       |
| \[面試\] 面試心得 凌陽多 宇潤數位 台積 晨星 智源      | ross999      | 7       |
| Re: \[公告\]徵求另外一位板主共同管理                  | glo6e        | 1       |
| \[面試\] 面試心得分享: Google                         | waitrop      | 21      |
| \[公告\]本版有設定發文與推文限制                      | harrygp      | 1       |
| 我天天上班都在玩RPG                                   | stpippen     | 43      |
| \[面試\] Garmin顯示技術面試分享                       | pinch        | 7       |
| \[面試\] 艾克爾面試心得                               | teanchun     | 5       |
| Re: \[討論\] 待業的日子怎麼過                         | shaffer      | 28      |
| \[討論\] 最近來interview的條件都很棒                  | freeread     | X4      |
| \[面試\] 面試後主動與主管會HR連絡會加深印象嗎??       | freedom70516 | 9       |
| \[公告\]邀請ShortestPath就任精華文章面試區及<U+A420>… | harrygp      | 6       |
| Re: Re:工作心得分享(協調會結果)                       | paleshelter  | 10      |
| \[轉錄證明\]\[申請\] Tech\_Job板申請新增板主          | harrygp      |         |
| \[公告\] pangyu 警告一次                              | shaffer      |         |
| \[公告\] wonderfulkid 警告一次                        | shaffer      |         |
| \[公告\] wrltertina 警告一次                          | cloud7515    | 3       |
| \[公告\] 版規增訂 2009.10.17                          | shaffer      |         |
| \[新聞\] 無塵室裡昏倒 工程師缺氧不治                  | belleville2  | 44      |
| \[公告\] jingruhuang cestsophia 警告一次              | cloud7515    |         |
| \[心得\] 面試心得                                     | essanthony   | 6       |
| \[心得\] 不景氣時代下的面試心得                       | blueway1222  | 33      |
| \[公告\] 關於ECFA討論串                               | cloud7515    | 7       |
| \[公告\] 洗版文相關規定投票                           | shaffer      | 6       |
| Re: \[討論\] 如果還能重新選擇 你還會走科技業嗎        | exclamation  | 22      |
| \[公告\] 版規增訂 2009.10.27                          | shaffer      |         |
| \[公告\] 閒聊/較激烈討論之洗版文章規定 投票開始       | shaffer      |         |
| \[公告\] 洗版文章相關規定投票結果及板規修訂           | shaffer      |         |
| Re: \[討論\] 女友說她想要離開                         | Irisyeh      | 46      |
| \[心得\] 我畫的網誌                                   | goofyman     | 14      |
| \[討論\] 有 pm 幹你去不去                             | Gyroball     | 36      |
| \[面試\] 友達中科廠 工業工程/生管工程師 面<U+B820>…   | Allentzeng   | 8       |
| Re: \[請益\] 台灣或美國的offer選擇                    | dameinui     | 21      |
| \[心得\] 新人學習所提問的問題                         | kng          | 32      |
| Re: \[請益\] 我不喜歡我徒弟.....該怎麼辦              | MaligB       | 13      |
| \[論卦\] 通膨經濟學、兩萬二、與台灣人大滅絕           | genome       | 62      |

解釋爬蟲結果
------------

``` r
dim(Teco_job)
```

    ## [1] 120   3

使用dim()執行結果顯示120與3，表示row:120、col:3 因此可知道有120個標題(title)

``` r
table(Teco_job$Author)
```

    ## 
    ##   [馬路探子]         azer        bear3   chienyu211     DEERETTE 
    ##            1            1            1            1            1 
    ##      Irisyeh    layachang          LKO          oca       Rooney 
    ##            2           14            1            1           10 
    ##   tatibana31     AixStyle       ALiGoo autumnbreeze blueangel629 
    ##            1            1            1            1            1 
    ##       deadly        fbgae     g8330330     hamk5202       Jongny 
    ##            1            1            1            1            1 
    ##     mazerlin        shter      smalloc    spritecat       tojump 
    ##            1            2            1            1            1 
    ##         VarX   WRITERT1NA       yaudeh      yuujang      karlhsu 
    ##            1            1            1            1            1 
    ##     longbow2        tyu26         whni  winnie02022      harrygp 
    ##           17            1            1            1            5 
    ##     mythlove      powerme qiantangchao      Sunghui         twwo 
    ##            1            1            2            1            1 
    ##    cloud7515 freedom70516     freeread        glo6e  paleshelter 
    ##            4            1            1            2            1 
    ##        pinch      ross999      shaffer ShortestPath     stpippen 
    ##            1            1            9            1            1 
    ##     teanchun      waitrop   Allentzeng  belleville2  blueway1222 
    ##            1            1            1            1            1 
    ##     dameinui   essanthony  exclamation       genome     goofyman 
    ##            1            1            1            1            1 
    ##     Gyroball          kng       MaligB 
    ##            1            1            1

藉由$Author篩選出"作者"的欄位，從結果可看出longbow2這位作者的出現次數為17次,是最高的。

人工結論:我發現longbow2這位作者極有可能是高階管理員,因為他的PO文90%以上都是「公告」類的 而且發文也很頻繁,是個活躍的管理員。
