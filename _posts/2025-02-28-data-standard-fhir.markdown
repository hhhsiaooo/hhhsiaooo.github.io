---
layout: post
title:  "【公司專案】醫院評鑑分析儀表板"
date:   2025-02-28
categories: jekyll update
---

## **專案背景**
目前台灣醫院各自開發自有的醫療資訊系統，醫院評鑑中的醫療品質指標資料未進行標準化，
無法滿足智慧醫療發展的需求。

為解決此問題，本專案協助盤點醫療品質指標相關資料，
基於**<mark style="background-color: #ffff77; color: black;">FHIR（Fast Healthcare Interoperability Resources）及 TW Core IG</mark>**進行規範，
並透過示範儀表板，驗證標準化資料的應用可行性。

## **實作流程**
> 此為團隊合作專案，我負責的項目為**<mark style="background-color: #ffff77; color: black;">「FHIR資料標準」</mark>**
> 與**<mark style="background-color: #ffff77; color: black;">「儀表板建置」</mark>**。
> 因專案時程有限，在團隊成員研究資料分布、尚未產出合成資料前，
> 我先使用測試資料繪製圖表，供客戶確認，確保指標設計符合需求，減少後續調整時間。
> 此外，我也利用測試資料建立符合FHIR標準的資料模板，讓負責合成資料的同仁可依此轉換資料。
> 我們透過緊密合作與事前規劃，提升執行效率，確保專案按時交付。

#### 1.指標設計
領域專家參考國內外論文，並根據美國醫學研究院提出的**<mark style="background-color: #ffff77; color: black;">六大醫療品質核心構面</mark>**，
進行指標評估與設計，釐清計算所需的資料欄位，並建立概念性定義。
該階段定義出本專案使用的品質指標，包含存活出院比率、出院時意識清楚比率等。

![Jekyll Logo](/assets/images/fhir_core.jpg)

#### 2.資料合成
基於品質指標所需資料欄位，**<mark style="background-color: #ffff77; color: black;">與領域專家討論資料合成邏輯，使模擬資料貼近實際情況。</mark>**
* 資料合成比例：病患性別比例；出院動向比例；大腦表現功能分類比例等。
* 欄位間關係：身分證第一碼數字與性別相關；急診轉歸為死亡的病患，出院動向也會是死亡等。

#### 3.FHIR資料標準
將合成資料欄位對應至FHIR資源類型，轉換為JSON格式，
並利用HL7提供的驗證器進行驗證，確保資料檔案**<mark style="background-color: #ffff77; color: black;">符合 FHIR 規範</mark>**。
* FHIR階層對照：以CPR處置為例，原始資料欄位「CPR」，對應至FHIR資源類型 Procedure，需填入規範的值集。

![Jekyll Logo](/assets/images/fhir_mapping.jpg)

* 檔案完整階層：使用資料交換基本單位「Bundle」，打包每筆病患就醫歷程所涉及之資源類型，產出JSON檔案。

![Jekyll Logo](/assets/images/fhir_bundle.jpg)

![Jekyll Logo](/assets/images/fhir_json.jpg)

* 檔案驗證結果：使用命令提示字元驗證JSON檔案，若驗證通過，可看到「Information: All OK」。

![Jekyll Logo](/assets/images/fhir_validation.jpg)

#### 4.儀表板建置
使用**<mark style="background-color: #ffff77; color: black;">Grafana</mark>**進行開發，包含兩種分析構面：
* 品質指標：瞭解品質指標每月趨勢變化，並可篩選不同病患屬性，進行比較。
* 統計資訊：病患性別比例、年齡級距比例、離院狀況比例、各項處置比例等。

![Jekyll Logo](/assets/images/fhir_dashboard.jpg)

## **專案成就與自我成長**
> 在此專案中，我對**<mark style="background-color: #ffff77; color: black;">FHIR與TW Core IG規範</mark>**有了進一步的認識，
> 與領域專家及技術團隊緊密合作，
> **<mark style="background-color: #ffff77; color: black;">將醫療品質指標的概念性定義，轉化為結構化可交換的資料格式</mark>**，
> 並運用驗證工具確保資料合規。此外，團隊之間保持緊密溝通，
> 靈活調整專案執行方式與順序，這也是專案能夠如期交付的關鍵。

