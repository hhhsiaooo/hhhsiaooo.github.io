---
layout: post
title:  "【公司專案】採購資料開放應用分析"
date:   2025-02-28
categories: jekyll update
---

## **專案背景**
**<mark style="background-color: #ffff77; color: black;">為推動採購資料的開放與應用</mark>**，並與國際標準接軌，
專案參考 Open Contracting Partnership 所訂定之**<mark style="background-color: #ffff77; color: black;">Open Contracting Data Standard（OCDS）</mark>**，
將電子採購網資料進行轉換，使其符合國際開放採購資料標準，促進公開透明與跨國合作。
未來可提供更具結構化、標準化的採購資訊，讓個人、學術機構、民間團體及企業等使用者更容易存取與分析資料，
透過專案產出的採購管理儀表板，展現了資料應用的可能性。

## **實作流程**
> 我擔任**<mark style="background-color: #ffff77; color: black;">專案經理</mark>**，負責客戶溝通、進度掌控及資料分析實作。

#### 1.管理指標設計
參考**<mark style="background-color: #ffff77; color: black;">Open Contracting Partnership 所建議之風險管理指標</mark>**，
與客戶討論並根據國內法律規定進行調整，訂出合適的管理指標清單與衡量標準。

#### 2.資料蒐集
盤點管理指標清單所需資料欄位，使用**<mark style="background-color: #ffff77; color: black;">「中華民國政府電子採購網」</mark>**
之招標公告與決標公告，取得標案相關資訊。
例如：標的分類、招標方式、決標方式、決標金額、招標日期等資訊。

#### 3.資料轉換
使用 Open Contracting Partnership 提供之資料轉換程式，將電子採購網資料對應至 OCDS 規範的資料階層，
並使用官方工具驗證檔案符合 OCDS 資料標準，產出資料交換格式 JSON 檔案。
* 資料階層對照：將電子採購網的資料欄位，對應Open Contracting Data Standard（OCDS）資料階層。

![Jekyll Logo](/assets/images/ocds_mapping.jpg)

* OCDS轉換程式：填寫 Open Contracting Partnership 提供的資料轉換工作表。

![Jekyll Logo](/assets/images/ocds_transformation.jpg)

* 資料驗證：將資料轉換工作表上傳至官方驗證工具 Data Review Tool。

![Jekyll Logo](/assets/images/ocds_validation.jpg)

* 產製JSON檔案與說明文件。

![Jekyll Logo](/assets/images/ocds_json.jpg)

#### 4.儀表板建置
使用 **<mark style="background-color: #ffff77; color: black;">Google Looker Studio</mark>** 進行開發，包含兩種指標構面：
* 採購案件現況：標案類型佔比、決標金額佔比、標案地區分布等統計資訊。
* 招標與決標階段的管理指標：投標廠商家數、等標期分布等指標。

儀表板圖表示意圖

![Jekyll Logo](/assets/images/ocds_chart1.jpg)

![Jekyll Logo](/assets/images/ocds_chart2.jpg)

![Jekyll Logo](/assets/images/ocds_chart3.jpg)

## **專案成就與自我成長**
> 原先的圖表設計專注於管理指標，但在儀表板初稿完成後，客戶才定義了儀表板的主要目標對象，
> 要求將重點放在採購案件現況的呈現，並強調簡單清晰的統計圖表，而不是複雜的風險管理指標。
> 這讓我意識到專案初期**<mark style="background-color: #ffff77; color: black;">設定目標對象</mark>**的重要性，
> 同時也需要與客戶保持密切聯繫，**<mark style="background-color: #ffff77; color: black;">採用敏捷式專案管理，提供最小可見的專案成果</mark>**，
> 確保後續實作方向與客戶需求一致。
> 
> 此外，這次專案讓我參與了**<mark style="background-color: #ffff77; color: black;">資料標準化的全流程實作</mark>**，
> 包含原始資料盤點、格式規範研究、資料轉換與驗證，學習識別指標所需資料欄位，
> 根據國際規範進行資料轉換，並使用專業工具進行自動化處理與驗證。
> 這些經驗不僅提升了我的資料處理能力，也確保了資料的準確性與合規性。

