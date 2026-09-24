# Expense 💳

<p align="center">
  <img src="./icon/light_icon.png" width="128" height="128" alt="Expense App Icon" style="border-radius: 28px;" />
</p>

<p align="center">
  <strong>A lightweight, privacy-first, beautifully simple expense tracker for iOS.</strong><br>
  Completely offline. Zero tracking. Instant logging. Seamless Apple Pay automation.
</p>

<p align="center">
  <a href="https://swift.org"><img src="https://img.shields.io/badge/Swift-5.0-F05138.svg?style=flat&logo=swift" alt="Swift 5.0"></a>
  <a href="https://developer.apple.com/ios/"><img src="https://img.shields.io/badge/iOS-18.0+-007AFF.svg?style=flat&logo=apple" alt="iOS 18.0+"></a>
  <a href="https://github.com/WinchellWang/expense/releases"><img src="https://img.shields.io/badge/Size-<5_MB-success.svg?style=flat" alt="App Size"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-GPL_v3-blue.svg?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="README.md"><b>English</b></a> •
  <a href="doc/README.zh-Hans.md">简体中文</a> •
  <a href="doc/README.zh-Hant.md">繁體中文</a> •
  <a href="doc/README.ja.md">日本語</a> •
  <a href="doc/README.fr.md">Français</a> •
  <a href="doc/README.es.md">Español</a>
</p>

---

## ✨ Why Expense?

Most expense tracker apps nowadays are bloated with social feeds, complex financial account integrations, loan advertisements, subscription paywalls, and aggressive telemetry.

**Expense** goes back to the fundamentals: a distraction-free, elegant, lightning-fast ledger that respects your time and your personal privacy. Weighing in at **just a few megabytes**, Expense is a truly "small yet beautiful" native utility crafted purely with Swift & SwiftUI.

---

## 🌟 Key Highlights

### ⚡ Lightning-Fast & Intuitive Flow
- **One-tap entry**: Open the app, type the amount on a custom tactile keypad, tap a category icon, and you're done. No endless confirmation dialogs or clutter.
- **Fixed-decimal & flexible input modes**: Tailor the number entry to your preference, including fixed 2-decimal mode for rapid speed.
- **Smart Category Sorting**: Category icons dynamically reorder based on your real-world frequency of use, putting your favorite choices right under your thumb.

### 🎨 Fully Customizable Categories
- Build a ledger that mirrors your actual lifestyle.
- Assign any name and choose from hundreds of categorized native Apple emojis.
- Reorder, rename, or delete existing categories anytime. Renaming automatically cascades across past records seamlessly.

### 🍏 Zero-Touch Apple Pay Automation (Invisible Logging)
- Turn every transaction into an effortless, automatic ledger entry.
- Built with iOS **App Intents** and **Siri Shortcuts**, Expense integrates directly with Apple Wallet.
- Whenever you pay with Apple Pay, an iOS Personal Automation can instantly trigger in the background—logging the merchant, amount, and date without opening the app.
- Check out the [Automation Setup Guide](./doc/AUTOMATION_GUIDE.md) to set it up in under 2 minutes.

### 🔒 Privacy-First & 100% Local
- **Zero tracking**: No third-party SDKs, no ad frameworks, no analytics trackers, no account registration, and no remote backend servers.
- **Runs 100% locally**: All your financial entries live exclusively on your device's sandboxed storage.

### ☁️ Optional iCloud Backup & Full Data Sovereignty
- **You own your data**: Period.
- **iCloud sync & backup**: Keep your data safe across your Apple devices with private iCloud Documents & Key-Value storage. Auto-backup checks daily in the background.
- **One-click export**: Export clean, standard **CSV** spreadsheets (Excel/Numbers compatible) or human-readable **JSON** archives at any time.
- **Smart JSON Restore**: Seamlessly import backups from the iOS Files app or iCloud with intelligent deduplication and category merging.

### 🪶 Ultra-Lightweight ("Small & Beautiful")
- Built with pure native SwiftUI, with zero bulky third-party dependencies.
- The entire binary package is **under 5 MB**, conserving storage and launching virtually instantaneously.

---

## 📱 Screenshots & Overview

| Daily & Monthly Ledger | Tactile Keypad Entry | Category Customization | Data & iCloud Control |
|:---:|:---:|:---:|:---:|
| Calendar-style grouped expenses | Clean custom number pad & quick notes | Curated native Apple emoji catalog | CSV / JSON export & iCloud sync |

---

## 🚀 Getting Started

### Prerequisites
- macOS 15.0+ (Sequoia) with Xcode 27.0+ installed
- iOS 18.0+ device or simulator

### Build & Run
1. Clone this repository:
   ```bash
   git clone https://github.com/WinchellWang/expense.git
   cd expense
   ```
2. Open the project in Xcode:
   ```bash
   open Expense.xcodeproj
   ```
3. Select your target device or simulator and press `Cmd + R` to build and run.

---

## 🤖 Apple Pay Automation Guide

Expense supports native App Intents for background logging. To automate Apple Pay transactions:

1. Open the Apple **Shortcuts** app on your iPhone.
2. Go to the **Automation** tab and create a **Personal Automation**.
3. Choose **Transaction** (Apple Pay) as the trigger.
4. Add the Expense **"Add Expense"** action, mapping the transaction amount and merchant into the intent.
5. Set it to **Run Immediately** without confirmation.

For step-by-step instructions with localized screenshots and tips, please read the [Automation Guide](./doc/AUTOMATION_GUIDE.md).

---

## 🌐 Supported Languages

Expense automatically adapts to your system language with native translations:

- 🇺🇸 **English** (Default)
- 🇨🇳 **简体中文** (Simplified Chinese)
- 🇭🇰 / 🇹🇼 **繁體中文** (Traditional Chinese)
- 🇯🇵 **日本語** (Japanese)
- 🇫🇷 **Français** (French)
- 🇪🇸 **Español** (Spanish)

---

## 🤝 Contributing

Contributions, bug reports, and feature suggestions are warmly welcome! Feel free to:
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.
