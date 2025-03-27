---
layout: post
title:  "【個人專案】銷售分析儀表板"
date:   2025-03-25
categories: jekyll update
---

## **專案簡介**
> 專案程式碼請看 [GitHub][github-link]。

本專案使用銷售資料產生器建置的電商平台資料庫，實作銷售分析儀表板，
使用開源視覺化工具 Grafana 介接資料庫 PostgreSQL，
透過 SQL Query 查詢並計算多維度的銷售分析指標，以瞭解長短期銷售趨勢與客戶行為模式。

## **核心技術**
#### **資料庫查詢**
* 使用 [PostgreSQL][postgresql-link] 資料庫。
* 建立儀表板專用的資料庫使用者，設定唯讀權限，**<mark style="background-color: #ffff77; color: black;">提升資料庫操作安全性。</mark>**
* **<mark style="background-color: #ffff77; color: black;">透過SQL Query查詢資料表並計算指標。</mark>**

#### **資料視覺化**
* 使用開源軟體 [Grafana][grafana-link]。
* 資料庫介接與圖表製作。
* 儀表板使用者權限管理。

## **指標規劃**
#### **不分時間整體會員樣態**
不分時間的會員與商品統計資訊。**<mark style="background-color: #ffff77; color: black;">瞭解忠實客戶樣態與主力商品。</mark>**
* 註冊會員數
* 曾購買會員數
* 新註冊會員數月趨勢
* 購買會員數月趨勢
* 會員性別比例
* 會員年齡比例
* 通路轉換比例
* 各類商品購買次數比例
* 各類商品購買金額比例

#### **年度比較**
比較今年與去年的訂單量與客單價，呈現各類型商品的銷售佔比。
**<mark style="background-color: #ffff77; color: black;">以評估今年的銷售表現，並發現市場需求的變化</mark>**
，例如特定產品是否比去年更受歡迎。
* 今年訂單量
* 去年訂單量
* 訂單量月趨勢
* 今年客單價
* 去年客單價
* 客單價月趨勢
* 各通路轉換次數
* 各類商品購買次數
* 各類商品購買金額

#### **短期比較**
比較本周與上周的商品銷售情形，並呈現本周購買會員樣態與轉換率，
同時可以**<mark style="background-color: #ffff77; color: black;">透過篩選器查看不同性別、年齡級距會員的購買情形，評估促銷活動對各類型商品的業績影響。</mark>**
* 本周訂單數
* 購買會員性別年齡
* 會員購物歷程（轉換率）
* 各類商品購買情形
* 本周促銷活動
* 前周促銷活動

## **圖表設計**
根據各項指標要傳達的資訊，選擇合適且直觀的圖表類型。

以指標「客單價」為例，除呈現今年與去年的數字差異，結合趨勢圖找出造成差異的月份。
![Jekyll Logo](/assets/images/dashboard_value.jpg)

以指標「會員購物歷程」為例，使用funnel圖表，呈現不同階段流失的人數比例，以及最終購買的比例。
![Jekyll Logo](/assets/images/dashboard_funnel.jpg)

## **儀表板製作**
* 使用 APT 安裝儀表板工具 Grafana。
* 建立 Grafana 專用的資料庫唯讀使用者，以及儀表板的管理者與檢視者。
* SQL Query 撈取資料，進行指標計算。
* 設定圖表的資料欄位與樣式，例如：圖表類型、XY軸欄位、圖表顏色、字體大小等。
* **<mark style="background-color: #ffff77; color: black;">匯出儀表板設定檔，未來可透過此設定檔在其他主機復現儀表板的圖表設定。</mark>**

## **資料分析洞察**
專案使用銷售資料產生器建置的資料庫，雖然無法完全模擬真實的銷售狀況，但仍可
**<mark style="background-color: #ffff77; color: black;">針對隨機生成的資料樣態進行分析，示範儀表板的設計理念與資料解讀方式。</mark>**

**「整體會員樣態」頁面**
![Jekyll Logo](/assets/images/dashboard_page1.jpg)
* 雖會員人數達4000多人，但仍有很多會員從未購買過商品。
* 每月新註冊的會員人數相近。
* 每月購買商品的會員人數相近。
* 會員男女比例大致相同，以年齡60歲以上佔多數。
* 寵物零食被購買最多次，但因單價低，購買金額佔比不高。
* 寵物保健食品非購買次數最高，但因單價高，購買金額占比亦高。
* 狗飼料為必需品，購買次數與金額較高。

**「年度比較」頁面**
![Jekyll Logo](/assets/images/dashboard_page2.jpg)
* 去年訂單量可作為本年訂單量的目標值，截至三月底尚未達到去年業績的四分之一，如非受到銷售淡旺季的影響，應檢討年初促銷活動與銷售狀況。
* 今年平均客單價略低於去年，透過趨勢圖可以看到1-2月客單價較低。
* 去年各通路轉換次數相當，今年在收尋引擎與電子郵件廣告的成效略好。
* 比較今年與去年，各類商品購買次數相當，但金額佔比略有差異。
* 寵物保健食品金額佔比降低，顧客單次購買的數量可能降低，或偏好購買較低價的品牌。
* 狗罐頭金額佔比提高，顧客單次購買的數量可能提高，或偏好購買較高價的品牌。

**「短期比較」頁面**

[github-link]: https://github.com/hhhsiaooo/sales-dashboard-grafana
[postgresql-link]: https://www.postgresql.org/
[grafana-link]: https://grafana.com/oss/
