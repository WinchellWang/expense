# Expense 💳

<p align="center">
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="../icon/light_icon.png" width="128" height="128" alt="Expense App Icon" style="border-radius: 28px;" />
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="https://testflight.apple.com/images/testflight-iOS-400x400_1x_40.png" width="48" height="48" alt="Expense App Icon"/>
  </a>
</p>

<p align="center">
  <strong>一款轻量、注重隐私、极简优雅的 iOS 个人记账应用。</strong><br>
  完全离线运行 · 零隐私追踪 · 秒级极速记账 · 搭配 Apple Pay 实现无感自动记账
</p>

<p align="center">
  <a href="https://swift.org"><img src="https://img.shields.io/badge/Swift-5.0-F05138.svg?style=flat&logo=swift" alt="Swift 5.0"></a>
  <a href="https://developer.apple.com/ios/"><img src="https://img.shields.io/badge/iOS-18.0+-007AFF.svg?style=flat&logo=apple" alt="iOS 18.0+"></a>
  <a href="https://github.com/WinchellWang/expense/releases"><img src="https://img.shields.io/badge/体积-<5_MB-success.svg?style=flat" alt="App Size"></a>
  <a href="../LICENSE"><img src="https://img.shields.io/badge/License-GPL_v3-blue.svg?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="../README.md">English</a> •
  <a href="README.zh-Hans.md"><b>简体中文</b></a> •
  <a href="README.zh-Hant.md">繁體中文</a> •
  <a href="README.ja.md">日本語</a> •
  <a href="README.fr.md">Français</a> •
  <a href="README.es.md">Español</a>
</p>

---

## ✨ 为什么选择 Expense？

如今市面上的多数记账软件充斥着复杂的理财推荐、社交动态、借贷广告、繁重账户绑定与冗长的付费订阅，甚至在后台收集上传用户隐私数据。

**Expense** 选择回归初心：打造一款无干扰、设计纯粹、响应迅捷的原生轻量记账工具。安装包**体积仅数兆字节（< 5MB）**，由纯原生 Swift & SwiftUI 精雕细琢而成，是真正意义上的“小而美”。

---

## 🌟 核心特色

### ⚡ 极简直观的记账流程
- **一步记录**：打开即记，定制的触觉反馈数字键盘，点选分类即刻入账，无需繁琐确认步骤。
- **灵活输入模式**：支持固定两位小数与自由小数模式，满足不同记账手感需求。
- **智能频次排序**：分类图标根据你的真实使用频率动态排序，常用的分类始终在最顺手的位置。

### 🎨 深度自定义分类
- 随心构建贴合个人日常习惯的账本分类体系。
- 自由设定分类名称，并提供数以百计精选的原生 Apple Emoji 图标。
- 支持随时重命名与删除分类，重命名自动级联更新过往所有关联账单。

### 🍏 搭配 Apple Pay 实现无感自动记账
- 刷卡即记账，彻底摆脱漏记困扰。
- 基于 iOS 原生 **App Intents** 与 **快捷指令（Siri Shortcuts）** 架构。
- 每次刷 Apple Pay 消费时，手机后台自动化静默触发记账，无需手动打开应用即可完成金额与备注记录。
- 查看详细的 [快捷指令与自动化配置教程](AUTOMATION_GUIDE.zh-Hans.md)。

### 🔒 坚守隐私，100% 本地运行
- **零网络追踪**：无任何第三方统计 SDK、无广告代码、无分析打点、无需注册账号、无云端自建服务器。
- **沙盒本地存储**：所有财务账目与分类数据仅存在于你手中的 iPhone 本地沙盒。

### ☁️ 随心掌控数据：iCloud 备份与多格式导出
- **真正掌控自己的数据**：你的财务账目完全归你所有。
- **iCloud 安全备份**：支持通过 Apple 私有 iCloud Documents 及 Key-Value 储存跨设备备份数据，支持每日自动增量更新。
- **一键双格式导出**：随时导出标准 **CSV** 表格（兼容 Excel / Numbers）与结构化 **JSON** 全量备份。
- **智能去重导入**：从 iOS 文件 App 或 iCloud 随时恢复备份，内置智能去重与分类合并算法。

### 🪶 极致轻量（真正的“小而美”）
- 纯原生 SwiftUI 开发，无任何臃肿第三方依赖。
- 整体编译包体积仅 **几兆字节**，不仅极大节约存储空间，冷启动更能做到毫秒级秒开。

---

## 🚀 源码编译与运行

### 环境要求
- macOS 15.0+（Sequoia），安装 Xcode 16.0+
- iOS 18.0+ 真机或模拟器

### 构建步骤
1. 克隆代码仓库：
   ```bash
   git clone https://github.com/WinchellWang/expense.git
   cd expense
   ```
2. 使用 Xcode 打开工程：
   ```bash
   open Expense.xcodeproj
   ```
3. 选择目标设备或模拟器，按下 `Cmd + R` 即可编译运行。

---

## 🤖 Apple Pay 自动化配置简介

Expense 内置原生快捷指令操作，支持 Apple 钱包交易触发：

1. 打开 iPhone 上的 **快捷指令** App。
2. 切换至 **自动化** 标签页，点击右上角新建 **个人自动化**。
3. 选取 **交易**（Apple Pay 刷卡）作为触发条件。
4. 添加 Expense 的 **「记账 / Add Expense」** 操作，将交易金额与商户名称填入操作参数。
5. 勾选 **立即运行** 并关闭运行前询问。

图文详细教程请参阅：[自动化使用指南](AUTOMATION_GUIDE.zh-Hans.md)。

---

## 🌐 多语言支持

Expense 原生适配系统语言，支持以下语言自由切换：

- 🇺🇸 **English**（英语）
- 🇨🇳 **简体中文**（Simplified Chinese）
- 🇭🇰 / 🇹🇼 **繁體中文**（Traditional Chinese）
- 🇯🇵 **日本語**（日语）
- 🇫🇷 **Français**（法语）
- 🇪🇸 **Español**（西班牙语）

---

## 📄 开源许可

本项目遵循 GNU General Public License v3.0 (GPL v3) 开源协议 - 详情请参阅 [LICENSE](../LICENSE) 文件。
