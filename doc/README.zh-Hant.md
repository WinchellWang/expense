# Expense 💳

<p align="center">
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="../icon/light_icon.png" width="128" height="128" alt="Expense App Icon" style="border-radius: 28px;" />
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="https://testflight.apple.com/images/testflight-iOS-400x400_1x_40.png" width="48" height="48" alt="Expense App Icon" />
  </a>
</p>

<p align="center">
  <strong>一款輕量、極度重視隱私、簡潔優雅的 iOS 個人記帳應用程式。</strong><br>
  完全離線運作 · 零隱私追蹤 · 秒級極速記帳 · 搭配 Apple Pay 實現無感自動記帳
</p>

<p align="center">
  <a href="https://swift.org"><img src="https://img.shields.io/badge/Swift-5.0-F05138.svg?style=flat&logo=swift" alt="Swift 5.0"></a>
  <a href="https://developer.apple.com/ios/"><img src="https://img.shields.io/badge/iOS-18.0+-007AFF.svg?style=flat&logo=apple" alt="iOS 18.0+"></a>
  <a href="https://github.com/WinchellWang/expense/releases"><img src="https://img.shields.io/badge/容量-<5_MB-success.svg?style=flat" alt="App Size"></a>
  <a href="../LICENSE"><img src="https://img.shields.io/badge/License-GPL_v3-blue.svg?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="../README.md">English</a> •
  <a href="README.zh-Hans.md">简体中文</a> •
  <a href="README.zh-Hant.md"><b>繁體中文</b></a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.fr.md">Français</a> •
  <a href="README.es.md">Español</a>
</p>

---

## ✨ 為什麼選擇 Expense？

現今市面上多數記帳軟體充斥著金融理財廣告、社群動態、借貸推銷、冗長付費訂閱，並在後台收集用戶隱私數據。

**Expense** 選擇回歸純粹：打造一款毫無干擾、介面直覺、流暢迅捷的記帳工具。應用程式**大小僅數 MB**，由純原生 Swift & SwiftUI 精心構建，是真正意義上的「小而美」。

---

## 🌟 核心特色

### ⚡ 簡潔直覺的記帳流程
- **一步完成**：開啟即記，配備觸覺回饋數字鍵盤，點選類別立即入帳，省去所有繁瑣確認步驟。
- **彈性輸入模式**：支援固定兩位小數與自由小數點模式，滿足不同記帳手感習慣。
- **智慧頻率排序**：類別圖示依據真實使用頻率自動排列，常用類別隨手可得。

### 🎨 深度自訂類別
- 打造完全契合個人日常生活型態的類別架構。
- 自由設定類別名稱，並精選數百款原生 Apple Emoji 圖示。
- 支援隨時編輯與刪除類別，修改名稱自動聯動更新歷來所有關聯消費明細。

### 🍏 搭配 Apple Pay 實現無感自動記帳
- 感應付款即時記帳，徹底告別漏記困擾。
- 採用 iOS 原生 **App Intents** 與 **捷徑（Siri Shortcuts）** 技術。
- 每次使用 Apple Pay 感應交易時，系統在後台靜默觸發記帳，無需開啟 App 即可自動記錄金額與店家備註。
- 詳情請參閱 [捷徑與自動化設定教學](AUTOMATION_GUIDE.zh-Hant.md)。

### 🔒 守護隱私，100% 本機端運作
- **零網路追蹤**：無任何第三方追蹤 SDK、無廣告推播、無數據分析回傳、免註冊帳號、無後端伺服器。
- **沙盒本機儲存**：所有消費流水帳與自訂資料僅安全儲存於你手中的 iPhone 沙盒空間內。

### ☁️ 真正掌控資料：iCloud 備份與多元匯出
- **你的資料完全屬於你**：無任何資料鎖定。
- **iCloud 安全備份**：透過個人私有 iCloud Documents 與 Key-Value 儲存跨裝置備份，支援每日背景自動增量更新。
- **一鍵雙格式匯出**：隨時匯出標準 **CSV** 試算表（相容 Excel / Numbers）或結構化 **JSON** 完整備份。
- **智慧去重回復**：從 iOS 檔案 App 或 iCloud 隨時回復備份，具備智慧去重與類別自動合併機制。

### 🪶 極致輕量（真正的「小而美」）
- 純原生 SwiftUI 開發，零肥大第三方框架依賴。
- 編譯後安裝包體積極小（**< 5 MB**），大幅節省儲存空間，享受毫秒級啟動速度。

---

## 🚀 原始碼編譯與執行

### 環境需求
- macOS 15.0+（Sequoia），安裝 Xcode 16.0+
- iOS 18.0+ 實體裝置或模擬器

### 建置步驟
1. 複製專案庫：
   ```bash
   git clone https://github.com/WinchellWang/expense.git
   cd expense
   ```
2. 以 Xcode 開啟專案：
   ```bash
   open Expense.xcodeproj
   ```
3. 選取目標裝置或模擬器，按快捷鍵 `Cmd + R` 即可編譯運行。

---

## 🤖 Apple Pay 自動化設定簡介

Expense 深度整合 iOS 捷徑：

1. 開啟 iPhone 上的 **捷徑** App。
2. 切換至 **自動化** 分頁，點擊右上角新增 **個人自動化操作**。
3. 選取 **交易**（Apple Pay 刷卡）作為觸發條件。
4. 加入 Expense 的 **「記帳 / Add Expense」** 動作，將交易金額與特店名稱帶入參數。
5. 勾選 **立即執行** 並關閉「執行前詢問」。

詳細圖文說明請參閱：[自動化指南](AUTOMATION_GUIDE.zh-Hant.md)。

---

## 🌐 支援語言

Expense 完美支援多語言環境，隨系統語言自動切換：

- 🇺🇸 **English**（英文）
- 🇨🇳 **简体中文**（簡體中文）
- 🇭🇰 / 🇹🇼 **繁體中文**（繁體中文）
- 🇯🇵 **日本語**（日文）
- 🇫🇷 **Français**（法文）
- 🇪🇸 **Español**（西班牙文）

---

## 📄 開源授權

本專案採用 GNU General Public License v3.0 (GPL v3) 授權條款釋出 - 完整內容請查閱 [LICENSE](../LICENSE) 檔案。
