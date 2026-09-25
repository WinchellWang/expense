# 💳 Apple Pay 自動支出記録ガイド

> iOSの「ショートカット」でApple Payのタッチ決済を自動記録。固定カテゴリの対応付け、Generalへの一括記録と後からの編集、デバイス上のAI分類から選べます。

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 概要

iOSショートカットの「個人用オートメーション」を使用すると、iPhoneまたはApple WatchでApple Pay決済を行った瞬間に、**Expense**アプリへバックグラウンドで自動的に支出が記録されます。

### 自動化のメリット
- ⚡ **手入力の手間ゼロ**：タッチ決済が完了すると同時に、バックグラウンドで静かに記録されます。
- 🏷️ **カテゴリ設定を選択**：トリガーのカテゴリをExpenseに対応付けるほか、Generalへの一括記録やAIによる推定も可能です。
- 🏪 **店舗名の自動入力**：支払い先の店舗名（スターバックス、コンビニ、スーパー等）が自動的にメモに保存されます。
- 🔒 **デバイス上で処理**：通常の記録はiPhoneのApp Intentsで行います。AI分類はOn-Deviceを選択してください。銀行へのログインは不要です。

---

## 🛠️ 事前準備

- iOS 18.0以降を搭載した **iPhone**。
- Appleウォレットに登録済みの **Apple Pay** 対応カード。
- iPhoneにインストールされた **Expense** アプリ。
- Apple純正の **「ショートカット」** アプリ。

---

## 🚀 通常のショートカット：設定手順

ここでは、最も利用頻度の高い **「飲食 (Food & Drinks)」** カテゴリを例に解説します（他のカテゴリも同様の手順で設定可能です）：

### ステップ 1：ショートカットで新規オートメーションを作成
1. iPhoneで **「ショートカット」** アプリを開きます。
2. 画面下部の **「オートメーション」** タブをタップします。
3. 右上の **`+`** ボタンをタップして新規オートメーションを作成します。
4. リストから **「取引」**（一部のiOSバージョンでは **「ウォレット」**）を選択します。

---

### ステップ 2：トリガー条件の設定
設定画面で以下のように指定します：

1. **カード**：**「任意のカード」**（または特定のクレジットカードを選択）。
2. **カテゴリ**：
   - **「カテゴリ」** をタップ。
   - **「飲食 (Food & Drinks)」** にチェックを入れます。
   - 右上の青いチェックマーク `✓` をタップして保存します。
3. **加盟店**：**「任意の加盟店」** のままにします。
4. **実行オプション**：
   - **「すぐに実行」** を選択（スイッチが **緑色** になります）。
   - **「実行時に通知」** を **オフ** にします（毎回の決済通知ポップアップを防ぎます）。
5. 右上の **「次へ」** をタップします。

---

### ステップ 3：アクションの追加
**「新規の空のオートメーション」** を選択し、次の3つのアクションを順番に追加します：

#### アクション 1：金額から数値を抽出
Apple Payから渡される金額には通貨記号（例：`¥920`、`$15.00`）が含まれる場合があるため、数値のみを正確に抽出します：
1. **「アクションを追加」** をタップします。
2. **「入力から数値を抽出」**（英語：`Get numbers from`）を検索して追加します。
3. 入力欄をタップし、**「ショートカットの入力」**（または `取引 > 金額`）を選択します。
   - アクションには `[金額] から数値を抽出` と表示されます。
   - 出力変数名は **`数値`**（`# Numbers`）になります。

#### アクション 2：Expenseに支出を追加
1. 画面下の検索バーで **Expense** と入力します。
2. **「Add Expense」**（支出を追加）アクションを選択します。
3. 各項目を以下のように設定します：
   - **Amount（金額）**：項目をタップし、キーボード上の変数一覧からアクション1の出力である **`数値 (# Numbers)`** を選択します。
   - **Category（カテゴリ）**：項目をタップし、対応する **`🍱 飲食 (Food & Drinks)`** を選択します。
   - **Note（メモ）**：項目をタップし、**「ショートカットの入力」** を選択した後、挿入された青いカプセルをタップして属性を **`加盟店 (Pay Merchant)`** に切り替えます。
4. 「Add Expense」タイルの右側にある矢印 `>` をタップして詳細を開きます：
   - **「実行時に表示 (Show When Run)」** を **オフ** にします（これでバックグラウンド無音実行になります）。

#### アクション 3：ショートカットを停止
1. 下部の検索バーで **「このショートカットを停止」**（英語：`Stop this shortcut`）を検索して最後に追加します。
2. 右上の **「完了」** をタップしてオートメーションを保存します。

---

## 📸 オートメーション構成図

完成したオートメーションの構造は以下の通りです：

![shortcuts](./shortcuts.jpg)

---

## 💡 おすすめ設定：複数カテゴリのオートメーション

トリガーで選択できるカテゴリについて、上記の手順を繰り返します。以下は対応付けの例であり、すべてのApple Pay決済を網羅するものではありません：

| トリガーのカテゴリ | Expense の対応カテゴリ |
| :--- | :--- |
| **飲食 (Food & Drinks)** | `🍱 飲食` |
| **買い物 (Shopping)** | `🛍️ 買い物` |
| **交通 (Transportation)** | `🚗 交通` |
| **旅行 (Travel)** | `🏖️ 旅行` |
| **サービス (Services)** | `🛠️ サービス` |
| **娯楽 (Entertainment)** | `🎠 娯楽` |
| **健康 (Health)** | `💊 健康` |

---

## ⚠️ 通常のショートカットの制限とGeneralへの記録

Appleの「取引」オートメーションではカテゴリで絞り込めますが、ショートカットに渡される取引の入力には **Category（カテゴリ）が含まれません**。そのため、通常のショートカットではApple Payの元のカテゴリを読み取れません。これはiOSショートカットの設計上の制限であり、Expense側では解消できません。

- **1対1の対応付け**：トリガーでカテゴリを1つ選び、**Add Expense**で対応するExpenseのカテゴリを指定します。対応ごとに別のオートメーションが必要です。Apple Payのカテゴリにはトリガーの選択肢にないものもあり、選択したカテゴリに一致しない決済は記録されません。
- **すべてのカテゴリを記録**：トリガーを **Any Category（任意のカテゴリ）**、**Any Card（任意のカード）**、**Any Merchant（任意の加盟店）**にし、**Add Expense → Category**を **General（一般）**に固定します。選択できるカテゴリに該当しない決済も含め、カテゴリの絞り込みによる記録漏れを防げます。後からExpenseで各記録のカテゴリを手動編集してください。元のカテゴリをショートカットが判別できるようになるわけではありません。

同じ決済には1つの方式を使用してください。**Any Category**を有効にする際は、同じ決済を記録するカテゴリ別オートメーションを無効にして重複を防ぎます。「すべて」とは、iOSが「取引」トリガーに渡すApple Payのタッチ決済を指します。

---

## 🤖 AI補助ショートカット：全カテゴリの記録と自動分類

> **AIで自動分類を補えます：** Any Categoryですべてのカテゴリを対象にし、加盟店名から分類を推定します。すべてをGeneralに固定する必要がなくなり、幅広い決済を対象にしながら手動での整理を減らせます。

同じ **Any Category** トリガーでカテゴリによる絞り込みを避け、Apple Intelligenceが加盟店名からExpenseのカテゴリを推定します。Apple Payの欠けているCategoryフィールドを読み取る機能ではありません。提供するフローは **Add Expenseの前に**分類し、1回の決済につき1件を記録します。

### 必要な環境

- **iOS 26以降**と、**Apple Intelligence**に対応し有効化済みのiPhone。使用する言語と地域で機能が利用可能である必要があります。
- ショートカットの **モデルを使用（Use Model）** アクションで **デバイス上（On-Device）** を選択します。非対応機種ではiOSの更新だけでは使えません。[AppleのApple Intelligence入門ガイド](https://support.apple.com/en-ca/guide/iphone/iphc28624b81/ios)も参照してください。

---

## 📥 AIショートカットをダウンロード

<a href="https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d">
  <img src="https://cdn.jim-nielsen.com/ios/512/shortcuts-2018-10-03.png" alt="AIショートカットを追加" width="64" height="64">
</a>

[AIショートカットを追加](https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d)

---

## 🛠️ AIショートカットの設定

1. 上の専用ダウンロードセクションから共有AIショートカットを追加します。
2. 「取引」オートメーションを作成し、**Any Card → Any Category → Any Merchant**を選び、**すぐに実行**を有効、**実行時に通知**を無効にします。
3. オートメーションから読み込んだショートカットを実行し、**取引／ショートカットの入力**を渡して **Amount（金額）** と **Merchant（加盟店）** を取得できるようにします。
4. **Use Model**が **On-Device** に設定され、加盟店名を受け取ることを確認します。モデルが返すカテゴリ番号に対応する **If** 分岐で **Add Expense** を実行し、抽出した金額、対応カテゴリ、加盟店名のメモを記録します。各分岐のカテゴリをExpenseの設定に合わせ、**実行時に表示**を無効にします。
5. 同じ決済を記録する他のオートメーションを無効にし、初回の決済後に金額、メモ、カテゴリを確認します。

### 分類プロンプトとモデル設定

以下の英語プロンプトを **Use Model** にコピーしてください。最後の行の `Transaction (Merchant)` は変数のプレースホルダーです。「ショートカットの入力」の実際の **取引 → 加盟店（Merchant）** 変数に置き換え、通常の文字列のままにしないでください。カテゴリ番号を統一するため、すべての言語版で同じ英語プロンプトを使用します。

画像のとおり **Model → On-Device**、**Output → Number（数値）**、**Follow Up → オフ** に設定します。If分岐では数値の **Response** を `1` から `8` と比較し、`8` をGeneralに対応付けます。

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

### フローと制限

![AI補助ショートカットのフロー](./iOS_27_AI_Shortcuts.jpg)

AI分類は加盟店名からの推定であり、特に多種類の商品を扱う店舗では誤る場合があります。必要に応じてExpenseで確認・修正してください。分類が不明な場合は **General** を使用します。画像のフローは番号による分岐を使用しています。編集する際は、空の応答や想定外の応答もGeneralへ振り分け、一致する分岐がなく記録されない事態を防いでください。モデルの実行に失敗した場合は手動記録が必要になることがあります。

デバイス内処理の説明は **On-Device** を選択した場合に適用されます。Private Cloud ComputeやChatGPTに変更すると、分類の処理場所も変わります。

---

## ❓ よくある質問とトラブルシューティング

### Q1：金額が記録されない、または 0.00 になってしまう
**原因**：カード会社によって `Amount` に通貨記号（`¥`、`$` など）が含まれており、数値として正しく認識されない場合があります。  
**解決策**：必ず手順通りに **「入力から数値を抽出」** アクションを挟み、抽出された **`# 数値`** を `Add Expense` の Amount に渡してください。

### Q2：決済時に毎回確認ダイアログが表示されてしまう
**解決策**：
1. オートメーションのトリガー設定で、**「すぐに実行」** がオン、**「実行時に通知」** がオフになっていることを確認してください。
2. オートメーション内の `Add Expense` アクションの設定で、**「実行時に表示」** がオフになっていることを確認してください。

### Q3：自動記録後にカテゴリやメモを変更できますか？
**可能です。** ショートカットで記録されたデータは即座にExpenseアプリに反映されます。いつでもタップして修正や追記が可能です。

### Q4：取引データが外部サーバーに送信されることはありますか？
通常のショートカットはiOSのApp Intentsでローカルに記録します。AI版も **On-Device** を選択すれば分類をデバイス上で処理します。Private Cloud ComputeとChatGPTではリモート処理を使用します。Expenseの任意のiCloud同期・バックアップは別の設定です。
