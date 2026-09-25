# 💳 Apple Pay 自動記帳設定指南

> 使用 iOS「捷徑」自動記錄 Apple Pay 感應付款。可選擇固定類別對應、統一記入 General 後手動整理，或透過裝置端 AI 輔助分類。

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 概述

透過 iOS 捷徑的「個人自動化」功能，無論你使用 iPhone 還是 Apple Watch 感應付款，**Expense** 都能在感應完成的瞬間，於背景無感記錄該筆消費。

### 為什麼推薦使用自動化記帳？
- ⚡ **零阻力記帳**：感應付款後即可收起手機，記帳在背景安靜自動完成。
- 🏷️ **多種類別設定**：預設類別一對一對應、統一記入 General，或由 AI 推斷消費類別。
- 🏪 **自動帶入商家名稱**：消費店家（如星巴克、全聯、超商等）會自動記錄在備註欄中。
- 🔒 **本機處理**：一般記帳透過 iPhone 上的 App Intents 完成；AI 分類請選擇 On-Device，不需綁定銀行帳密。

---

## 🛠️ 事前準備

- **iPhone** 運行 iOS 18.0 或以上版本。
- 錢包中已加入至少一張支援 Apple Pay 的信用卡或簽帳金融卡。
- 已於 iPhone 上安裝 **Expense** App。
- 系統內建的 **「捷徑」** App。

---

## 🚀 傳統捷徑：完整設定步驟

本教學以最常見的 **「餐飲 (Food & Drinks)」** 類別為例（設定其他類別步驟完全相同）：

### 步驟 1：在捷徑中建立新自動化
1. 在 iPhone 上開啟 **「捷徑」** App。
2. 點擊螢幕下方的 **「自動化」** 標籤頁。
3. 點擊右上角的 **`+`** 號新增自動化。
4. 向下滑動並選擇 **「交易」**（部分 iOS 版本名稱為 **「錢包」**）。

---

### 步驟 2：設定觸發條件（卡片與類別）
在自動化設定畫面中：

1. **卡片**：選擇 **「任何卡片」**（亦可指定特定信用卡）。
2. **類別 (Categories)**：
   - 點擊 **「類別」**。
   - 勾選 **「餐飲 (Food & Drinks)」**。
   - 點擊右上角藍色打勾圖示 `✓` 確認。
3. **特約商**：維持為 **「任何特約商」**。
4. **執行模式**：
   - 勾選 **「立即執行」**（開關顯示為 **綠色**）。
   - 關閉 **「執行時通知」**（避免每次感應付款都跳出系統通知干擾）。
5. 點擊右上角 **「下一步」**。

---

### 步驟 3：建立自動化動作流程
選擇 **「新增空白自動化」**，依序新增以下 3 個動作：

#### 動作 1：從輸入擷取純數字金額
由於 Apple Pay 傳入的金額通常帶有幣別符號（例如 `$9.21`、`NT$150`），透過系統動作提取純數字能確保 100% 順暢：
1. 點擊 **「加入動作」**。
2. 搜尋 **「從輸入取得數字」**（英文搜尋 `Get numbers from`）並加入。
3. 點擊參數欄位，選擇 **「捷徑輸入」**（或點開選擇 `交易 > 金額`）。
   - 該動作卡片將顯示：`從 [金額] 取得數字`。
   - 其輸出變數為 **`數字`**（`# Numbers`）。

#### 動作 2：新增支出至 Expense
1. 在下方搜尋欄輸入 **Expense**。
2. 點選 **「Add Expense」**（新增支出）動作。
3. 設定各欄位：
   - **Amount（金額）**：點擊欄位，在鍵盤上方的變數選單選取動作 1 的輸出 **`數字 (# Numbers)`**。
   - **Category（類別）**：點擊欄位，選取對應的 **`🍱 餐飲 (Food & Drinks)`**。
   - **Note（備註）**：點擊欄位，選取 **「捷徑輸入」**，點一下填入的藍色標籤，將屬性切換為 **`特約商 (Pay Merchant)`**。
4. 點擊「Add Expense」卡片右上角箭頭 `>` 展開進階選項：
   - 將 **「執行時顯示 (Show When Run)」** 設為 **關閉**（達成全背景靜默記帳）。

#### 動作 3：結束此捷徑
1. 在搜尋欄搜尋 **「停止此捷徑」**（英文搜尋 `Stop this shortcut`）並加入至最後。
2. 點擊右上角的 **「完成」** 儲存自動化。

---

## 📸 完整流程示意圖

完成後的自動化架構如下：

![shortcuts](./shortcuts.jpg)

---

## 💡 進階技巧：依類別建立自動化

可為觸發器中已有的類別重複上述步驟。下表僅為對應範例，無法涵蓋所有 Apple Pay 消費：

| 觸發器類別 (Trigger Category) | Expense 對應類別 |
| :--- | :--- |
| **餐飲 (Food & Drinks)** | `🍱 餐飲` |
| **購物 (Shopping)** | `🛍️ 購物` |
| **交通 (Transportation)** | `🚗 交通` |
| **旅遊 (Travel)** | `🏖️ 旅遊` |
| **服務 (Services)** | `🛠️ 服務` |
| **娛樂 (Entertainment)** | `🎠 娛樂` |
| **健康 (Health)** | `💊 健康` |

---

## ⚠️ 傳統捷徑的限制與 General 方案

Apple 的「交易」自動化可以依類別篩選，但傳入捷徑的交易變數中**不包含 Category（類別）**，因此一般捷徑無法讀取 Apple Pay 的原始消費類別。這是 iOS 捷徑的設計限制，Expense 無法從 App 端解決。

- **一對一類別對應**：在自動化觸發條件中預選一個類別，再於 **Add Expense** 明確指定對應的 Expense 類別。每組對應需要單獨建立自動化。部分 Apple Pay 類別不在觸發器的可選清單中，未符合所選類別的消費不會被這些自動化記錄。
- **記錄所有類別的消費**：將觸發條件設為 **任何類別（Any Category）**、**任何卡片（Any Card）** 和 **任何特約商（Any Merchant）**，再將 **Add Expense → Category** 統一設為 **General（一般）**。如此可避免因類別篩選而漏記，包括沒有對應可選類別的感應付款。稍後進入 Expense，手動修改各筆紀錄的類別。捷徑本身仍無法識別原始類別。

同一筆消費應只使用一種方案。啟用 **Any Category** 自動化時，請停用涵蓋相同消費的類別自動化，避免重複記帳。此處的「所有」指 iOS 會傳給「交易」觸發器的 Apple Pay 感應付款。

---

## 🤖 AI 輔助捷徑：全類別觸發與自動分類

> **AI 可以補上自動分類這一環：** 用 Any Category 涵蓋所有類別，再根據特約商名稱推斷類別，不必將每筆消費固定記入 General，在保留全類別觸發的同時減少手動整理。

沿用 **Any Category** 觸發方式，避免依類別過濾消費，再由 Apple Intelligence 根據特約商名稱推斷 Expense 類別。AI 並非讀取 Apple Pay 缺少的 Category 欄位。提供的流程會在 **Add Expense 之前**完成分類，每筆消費只記一次。

### 使用條件

- **iOS 26 或以上版本**，iPhone 必須支援並已啟用 **Apple Intelligence**，且該功能在使用的語言及地區可用。
- 捷徑中的 **使用模型（Use Model）** 動作須選擇 **裝置端（On-Device）**。僅升級 iOS 無法讓不支援的裝置取得此功能。請參閱 [Apple Intelligence 入門指南](https://support.apple.com/en-ca/guide/iphone/iphc28624b81/ios)。

---

## 📥 下載 AI 輔助捷徑

<a href="https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d">
  <img src="https://cdn.jim-nielsen.com/ios/512/shortcuts-2018-10-03.png" alt="加入 AI 輔助捷徑" width="64" height="64">
</a>

[加入 AI 輔助捷徑](https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d)

---

## 🛠️ AI 輔助捷徑設定

1. 從上方獨立的下載章節加入共享的 AI 輔助捷徑。
2. 建立「交易」自動化，選擇 **Any Card → Any Category → Any Merchant**，開啟 **立即執行**，關閉 **執行時通知**。
3. 在自動化中執行匯入的捷徑，並將 **交易／捷徑輸入** 傳給它，以便讀取 **金額（Amount）** 和 **特約商（Merchant）**。
4. 確認 **Use Model** 選擇 **On-Device**，並接收特約商名稱。模型傳回類別編號，對應的 **If（如果）** 分支透過 **Add Expense** 寫入擷取後的金額、對應類別及特約商備註。逐一確認各分支是否對應你的 Expense 類別，並關閉 **執行時顯示**。
5. 停用會記錄相同消費的其他自動化，首次付款後檢查金額、備註及類別。

### 分類 Prompt 與模型設定

將以下英文 prompt 複製到 **Use Model**。最後一行的 `Transaction (Merchant)` 是變數佔位說明，請替換為「捷徑輸入」中的實際 **交易 → 特約商（Merchant）** 變數，不要保留為一般文字。各語言版本共用同一份英文 prompt，確保類別編號一致。

依照截圖將 **模型設為 On-Device**、**輸出（Output）設為 Number（數字）**，並**關閉 Follow Up（跟進）**。在 If 分支中，將數字類型的 **Response** 與 `1` 至 `8` 比較，其中 `8` 對應 General。

```text
You are a transaction classification assistant.

Your task is to classify the given merchant/business name into exactly one of the following 8 categories:

1: Food & Drinks (e.g., restaurants, cafes, bars, supermarkets, food delivery)

2: Shopping (e.g., clothing, electronics, home goods, general retail)

3: Transportation (e.g., public transit, gas stations, ride-hailing/Uber/Lyft, tolls, parking)

4: Travel (e.g., airlines, hotels, Airbnb, car rentals, booking agencies)

5: Services (e.g., utilities, phone bills, insurance, subscriptions, repairs, professional services)

6: Entertainment (e.g., movies, streaming, gaming, concerts, museums, clubs)

7: Health (e.g., pharmacies, doctors, dentists, gyms, wellness)

8: General (other expense that is hard to classify into the above 7 categories)

Rules:
- Output ONLY the single category number (from 1 to 8).
- Do not include any explanations, punctuation, spaces, or extra text.

Here is Merchant Name: Transaction (Merchant)
```

### 流程截圖與限制

截圖錄製於 **iOS 27**，已展開模型的詳細設定；上方 AI 功能的使用要求仍為 **iOS 26+** 且裝置支援相關功能。

![AI 輔助捷徑流程](./iOS_27_AI_Shortcuts.jpg)

AI 根據特約商名稱推斷類別，可能判斷錯誤，尤其是販售多類商品的商家。請視需要在 Expense 中檢查並修正。無法確定類別時，應以 **General** 作為備用類別。截圖採用編號分支；自行調整捷徑時，也應將空白或非預期的回應導向 General，避免因未符合分支而漏記。模型執行失敗時仍可能需要手動補登。

本機處理的說明以選擇 **On-Device** 為前提；切換為 Private Cloud Compute 或 ChatGPT 後，分類處理的位置也會改變。

---

## ❓ 常見問題與疑難排解

### Q1：為什麼金額沒有記錄到或顯示為 0.00？
**原因**：部分銀行卡傳入的 `Amount` 帶有貨幣符號（如 `$`, `NT$`）。  
**解決方式**：請確認已加入 **「從輸入取得數字」** 動作，並將該動作輸出的 **`# 數字`** 傳遞給 `Add Expense` 的金額欄位。

### Q2：每次付款後依然會跳出確認視窗？
**解決方式**：
1. 檢查自動化觸發器設定，確認 **「立即執行」** 為開啟，**「執行時通知」** 為關閉。
2. 進入自動化動作編輯，展開 `Add Expense` 卡片，確認 **「執行時顯示」** 已關閉。

### Q3：自動記錄後可以修改類別或備註嗎？
**可以！** 所有透過捷徑寫入的帳目均會立即同步於 Expense 主畫面上，隨時點擊即可編輯類別、金額與備註。

### Q4：Expense 會將交易紀錄傳送至雲端嗎？
一般捷徑透過 iOS App Intents 在本機記帳。AI 版本選擇 **On-Device** 時，分類也在裝置端處理；Private Cloud Compute 與 ChatGPT 則涉及遠端處理。Expense 中選用的 iCloud 同步與備份是獨立設定。
