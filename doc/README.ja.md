# Expense 💳

<p align="center">
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="../icon/light_icon.png" width="128" height="128" alt="Expense App Icon" style="border-radius: 28px;" />
  <a align="center" href="https://testflight.apple.com/join/Ea4FgKEF">
  <img src="https://testflight.apple.com/images/testflight-iOS-400x400_1x_40.png" width="48" height="48" alt="Expense App Icon" />
  </a>
</p>

<p align="center">
  <strong>プライバシーを最優先にした、軽量で洗練されたシンプルな iOS 家計簿アプリ。</strong><br>
  完全オフライン動作 · トラッキングゼロ · 素早い記帳 · Apple Pay 連携によるシームレスな自動記録
</p>

<p align="center">
  <a href="https://swift.org"><img src="https://img.shields.io/badge/Swift-5.0-F05138.svg?style=flat&logo=swift" alt="Swift 5.0"></a>
  <a href="https://developer.apple.com/ios/"><img src="https://img.shields.io/badge/iOS-18.0+-007AFF.svg?style=flat&logo=apple" alt="iOS 18.0+"></a>
  <a href="https://github.com/WinchellWang/expense/releases"><img src="https://img.shields.io/badge/サイズ-<5_MB-success.svg?style=flat" alt="App Size"></a>
  <a href="../LICENSE"><img src="https://img.shields.io/badge/ライセンス-GPL_v3-blue.svg?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="../README.md">English</a> •
  <a href="README.zh-Hans.md">简体中文</a> •
  <a href="README.zh-Hant.md">繁體中文</a> •
  <a href="README.ja.md"><b>日本語</b></a> •
  <a href="README.fr.md">Français</a> •
  <a href="README.es.md">Español</a>
</p>

---

## ✨ なぜ Expense なのか？

現代の多くの家計簿アプリは、不要なソーシャル機能、金融商品の広告、複雑な口座連携、高額なサブスクリプション課金、そして過剰なトラッキングで肥大化しています。

**Expense** は原点に立ち返り、ノイズがなく、直感的で、瞬時に記録できるシンプルなツールを目指しました。アプリのサイズは**わずか数メガバイト（< 5MB）**。純粋な Swift と SwiftUI で丹念に作られた、まさに真の「小さく美しい」実用ツールです。

---

## 🌟 主な特長

### ⚡ 驚くほど快適で直感的な記帳フロー
- **1タップで即完了**：アプリを開いて独自の数字キーパッドで金額を入力し、カテゴリーをタップするだけ。煩わしい確認手順は一切不要です。
- **柔軟な小数入力モード**：通常の入力モードに加え、高速入力が可能な「小数点2桁固定モード」もサポート。
- **スマートな自動並び替え**：カテゴリーアイコンは実際の利用頻度に応じて自動的にソートされ、よく使う項目が常に押しやすい位置に表示されます。

### 🎨 自由自在にカスタマイズできるカテゴリー
- あなたのライフスタイルに合わせたカテゴリー構成を簡単に作れます。
- カテゴリー名は自由に変更可能。数百種類の厳選された Apple ネイティブ絵文字（Emoji）からアイコンを選べます。
- 並び替え・編集・削除も自由自在。カテゴリー名を変更しても、過去の支出履歴にも自動で反映されます。

### 🍏 Apple Pay 連携による無感（自動）記帳
- お支払いの瞬間がそのまま支出記録に。記録忘れを完全に防ぎます。
- iOS ネイティブの **App Intents** および **ショートカット（Siri Shortcuts）** を活用。
- Apple Pay で決済すると、バックグラウンドの個人用オートメーションが自動で起動し、アプリを開くことなく店舗名や金額を記録します。
- 詳しい設定方法は [オートメーション設定ガイド](AUTOMATION_GUIDE.ja.md) をご覧ください。

### 🔒 徹底したプライバシー保護・完全ローカル動作
- **トラッキングゼロ**：サードパーティ製分析 SDK、広告フレームワーク、データ収集コードは一切含まれていません。アカウント登録も不要で、外部サーバーとの通信もありません。
- **サンドボックス内完結**：すべての支出データはお使いのデバイス内にのみ安全に保存されます。

### ☁️ 自らのデータを完全管理：iCloud バックアップとエクスポート
- **データはすべてあなたのもの**：ロックインは一切ありません。
- **iCloud バックアップ**：プライベートな iCloud 領域に安全にデータを保管。毎日の自動バックアップにも対応しています。
- **ワンクリック書き出し**：標準的な **CSV** 形式（Excel や Numbers 対応）および構造化された **JSON** 形式でいつでも全データをエクスポート可能。
- **スマートな復元機能**：ファイル App や iCloud からいつでもバックアップを復元。重複自動排除とカテゴリー自動統合に対応しています。

### 🪶 極めて軽量（「小さく美しい」体験）
- 純粋なネイティブ SwiftUI 設計により、肥大化したライブラリ依存はゼロ。
- インストールサイズは **5MB 未満**。ストレージを圧迫せず、起動も瞬時です。

---

## 🚀 ビルドと実行

### 動作要件
- macOS 15.0+（Sequoia）、Xcode 16.0+
- iOS 18.0+ 実機またはシミュレータ

### 手順
1. リポジトリをクローン：
   ```bash
   git clone https://github.com/WinchellWang/expense.git
   cd expense
   ```
2. Xcode でプロジェクトを開く：
   ```bash
   open Expense.xcodeproj
   ```
3. 実行先を選択し、`Cmd + R` でビルドして実行します。

---

## 🤖 Apple Pay オートメーション設定

Expense はネイティブのショートカットアクションに対応しています：

1. iPhone の **ショートカット** App を開きます。
2. **オートメーション** タブで「新規個人用オートメーション」を作成します。
3. トリガーとして **「トランザクション（Apple Pay）」** を選択します。
4. アクションとして Expense の **「支出を追加（Add Expense）」** を追加し、金額と加盟店名を設定します。
5. 「すぐに実行」を選択し、「実行時に通知」をオフにします。

画像付きの詳細な手順は [自動記帳ガイド](AUTOMATION_GUIDE.ja.md) をご覧ください。

---

## 🌐 対応言語

システムの言語設定に応じて自動で切り替わります：

- 🇺🇸 **English**（英語）
- 🇨🇳 **简体中文**（簡体字中国語）
- 🇭🇰 / 🇹🇼 **繁體中文**（繁体字中国語）
- 🇯🇵 **日本語**
- 🇫🇷 **Français**（フランス語）
- 🇪🇸 **Español**（スペイン語）

---

## 📄 ライセンス

本プロジェクトは GNU General Public License v3.0 (GPL v3) の下で公開されています。詳細は [LICENSE](../LICENSE) をご確認ください。
