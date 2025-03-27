---
layout: post
title:  "【個人專案】銷售資料產生器"
date:   2025-03-25
categories: jekyll update
---

## **專案簡介**
> 專案程式碼請看 [GitHub][github-link]。

顧客行為資料和銷售記錄對於市場分析與促銷策略研擬至關重要，但受限於隱私問題無法取得真實資料，為模擬真實電商平台運作，
本專案以作者感興趣的寵物用品作為示範，
**<mark style="background-color: #ffff77; color: black;">使用 Python 生成有邏輯性且自動更新的交易資料，建立電商銷售資料庫，作為未來分析應用的資料來源。</mark>**

## **核心技術**
#### **爬蟲** 
* 使用**<mark style="background-color: #ffff77; color: black;">requests + BeautifulSoup</mark>**，從 [MOMO購物網][momo-link] 取得寵物相關商品資訊。
* 清理資料以取得商品名稱、品牌與價格等資訊。

#### **資料驗證**
* 使用**<mark style="background-color: #ffff77; color: black;">Pydantic</mark>**進行資料驗證，確保爬取與生成的資料格式符合資料表規範。

#### **資料庫操作**
* **<mark style="background-color: #ffff77; color: black;">PostgreSQL</mark>**資料庫安裝與設定。
* 設計並建立資料表。
* 使用**<mark style="background-color: #ffff77; color: black;">SQLAlchemy ORM</mark>**操作資料庫，避免 SQL Injection 攻擊，解決不同資料庫間 SQL 語法差異的問題。

#### **自動化測試**
* 使用**<mark style="background-color: #ffff77; color: black;">pytest</mark>**進行自動化測試並計算覆蓋率。

#### **系統服務管理**
* 使用 Linux 系統服務管理工具**<mark style="background-color: #ffff77; color: black;">systemd</mark>**，定期執行資料產生器，以更新銷售資料庫。

#### **環境管理**
* 使用**<mark style="background-color: #ffff77; color: black;">Poetry</mark>**建立虛擬環境，進行套件管理，並將程式碼打包成可執行的指令。
* 在**<mark style="background-color: #ffff77; color: black;">Linux環境部署</mark>**系統服務。

## **資料設計**
#### **顧客資料表**
* 使用 Python 套件 [Faker][faker-link] 生成顧客資料。
* 顧客資料包含姓名、性別、生日、聯絡資訊、居住地等資訊。
* **<mark style="background-color: #ffff77; color: black;">設定排程每日06:00生成隨機筆數的顧客資料，模擬前一天新會員註冊之情境。</mark>**

#### **商品資料表**
* 爬取購物網站的寵物用品資訊。
* 商品資料包含商品名稱、品牌、價格、資料更新時間等資訊。
* **<mark style="background-color: #ffff77; color: black;">設定排程每週一04:00爬取最新商品資訊與價格。</mark>**

#### **促銷檔期表**
* 促銷活動類型包含：滿額折扣、多件優惠、免運滿額贈。
* **<mark style="background-color: #ffff77; color: black;">根據消費者心理與平假日的購買行為差異，指定一週七天適用的促銷活動類型，並設定各類型商品的購買機率、購買數量、每日交易數量。</mark>**
  * 週二至週四為工作日，購買低峰，推出多件優惠引導消費者囤貨，單一商品購買數量較高，且偏好購買必需品或消耗品，例如：飼料、罐頭及尿布墊。
  * 週六與週日為假日，消費者出門遊玩逛街較少線上購物，推出滿額贈及免運活動，減少購買猶豫時間，單一商品購買數量較低，但交易筆數較高，消費者偏好購買非必需品或低價商品，例如：零食及潔牙骨。
  * 憂鬱週一購物紓解壓力，快樂週五迎接假日犒賞自己，購買高峰，推出滿額折扣，用高額折扣刺激購物，消費者偏好購買單價較高的商品，以達折扣門檻，例如：保健食品及凍乾零食。

#### **促銷活動表**
* **<mark style="background-color: #ffff77; color: black;">基於三種促銷活動類型（滿額折扣、多件優惠、免運滿額贈），設定活動內容、折扣門檻與贈品。</mark>**
* 促銷活動包含活動名稱、活動類型、折扣門檻值、折扣比率、贈品等資訊。

#### **顧客行為資料表**
* **<mark style="background-color: #ffff77; color: black;">設定排程每日06:00隨機選取資料庫中的顧客資料與產品資料，產生顧客行為資料。</mark>**
* 顧客行為包含瀏覽商品、加入購物車及購買商品。
* 確保顧客行為發生時間，**<mark style="background-color: #ffff77; color: black;">遵守瀏覽商品->加入購物車->購買商品的順序。</mark>**

#### **交易資料表**
* 儲存顧客行為資料中的購買資料。
* **<mark style="background-color: #ffff77; color: black;">選擇當天適用的折扣活動，並計算折扣後的結帳金額。</mark>**

[github-link]: https://github.com/hhhsiaooo/company-operations-data-gen
[momo-link]: https://www.momoshop.com.tw/main/Main.jsp
[faker-link]: https://faker.readthedocs.io/en/master
