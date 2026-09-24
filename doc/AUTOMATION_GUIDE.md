# 💳 Apple Pay Automatic Expense Logging Guide

> Seamlessly track your expenses in real-time when paying with Apple Pay using iOS Shortcuts automations. 100% private, on-device, and zero manual input required.

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 Overview

With iOS Shortcuts Personal Automations, you can automatically log purchases into **Expense** the instant you tap your iPhone or Apple Watch to pay with Apple Pay.

### Why use this automation?
- ⚡ **Zero-effort tracking**: The moment your card is tapped, the transaction is logged silently in the background.
- 🏷️ **Smart Categorization**: Map Apple Pay's built-in transaction categories (Food & Drinks, Shopping, Transportation, etc.) directly to your Expense categories.
- 🏪 **Merchant Name Included**: Automatically records the store or merchant name into the expense note.
- 🔒 **100% Private & Local**: Runs entirely on your iPhone. No bank login, no API credentials, and no financial data ever leaves your device.

---

## 🛠️ Prerequisites

- **iPhone** running iOS 18.0 or later (iOS 27+ recommended).
- **Apple Pay** configured with at least one card in Apple Wallet.
- **Expense** app installed on your iPhone.
- Apple's built-in **Shortcuts** app.

---

## 🚀 Step-by-Step Setup Guide

Follow these steps to set up automatic logging for a category (using **Food & Drinks** as the primary example):

### Step 1: Create a New Automation in Shortcuts
1. Open the **Shortcuts** app on your iPhone.
2. Tap the **Automation** tab at the bottom of the screen.
3. Tap the **`+`** button in the top-right corner to create a new automation.
4. Scroll down and select **Transaction** (in some iOS versions, this trigger is named **Wallet**).

---

### Step 2: Configure the Transaction Trigger
On the automation configuration screen:

1. **Card**: Set to **Any Card** (or select specific credit/debit cards).
2. **Categories**:
   - Tap **Categories**.
   - Check **Food & Drinks** (or whichever category you want this automation to handle).
   - Tap the blue checkmark button `✓` in the top right to confirm.
3. **Merchants**: Set to **Any Merchant**.
4. **Execution Mode**:
   - Select **Run Immediately** (toggle switch turns **Green**).
   - Turn **Notify When Run** **OFF** (prevents popup notifications for every tap).
5. Tap **Next** in the top right.

---

### Step 3: Build the Automation Actions
Choose **New Blank Automation**, then assemble the following actions in order:

#### Action 1: Extract Clean Numbers
Apple Pay provides transaction amounts formatted with currency symbols (e.g., `$9.21`, `15,50 €`). Extracting the pure numeric value ensures seamless, error-free recording:
1. Tap **Add Action**.
2. Search for **"Get numbers from"** (Scripting action) and select it.
3. Tap the parameter placeholder, then choose **Shortcut Input** (or tap `Transaction` and choose `Amount`).
   - The action tile will display: `Get numbers from [Amount]`.
   - Its output variable is **`Numbers`** (`# Numbers`).

#### Action 2: Add Expense to App
1. Tap the search bar at the bottom and search for **Expense**.
2. Select the **Add Expense** action.
3. Configure the fields:
   - **Amount**: Tap the field, then select the **`Numbers`** variable (the output from Action 1).
   - **Category**: Tap the Category field and select your matching category: **`🍱 Food & Drinks`**.
   - **Note**: Tap the Note field, select **Shortcut Input** (or `Transaction`), tap on the blue bubble, and select **Merchant** (`Pay Merchant`).
4. Tap the down chevron or arrow icon `>` on the **Add Expense** tile to expand its options:
   - Turn **Show When Run** **OFF** (this enables silent background logging).

#### Action 3: Stop Shortcut Cleanly
1. In the search bar at the bottom, search for **"Stop this shortcut"**.
2. Tap to add it to the end of the action sequence.
3. Tap **Done** in the top-right corner to save your automation.

---

## 📸 Automation Overview

Your completed automation will look like this:

![shortcuts](./shortcuts.jpg)

---

## 💡 Recommended Setup: Multi-Category Automations

To categorize all your spending automatically, repeat the steps above to create dedicated automations for each of your common spending categories:

| Automation Trigger Category | Expense App Category | Example Purchases |
| :--- | :--- | :--- |
| **Food & Drinks** | `🍱 Food & Drinks` | Restaurants, cafes, supermarkets, delivery |
| **Shopping** | `🛍️ Shopping` | Retail, clothing, department stores, electronics |
| **Transportation** | `🚗 Transportation` | Gas stations, metro, subway, taxi, parking |
| **Travel** | `🏖️ Travel` | Airlines, hotels, train tickets |
| **Services** | `🛠️ Services` | Haircuts, repairs, laundry, cleaning services |
| **Entertainment** | `🎠 Entertainment` | Movies, concerts, museums, arcade |
| **Health** | `💊 Health` | Pharmacies, clinics, doctors, fitness |

### 🌟 Catch-All Automation (Optional Fallback)
Create one final automation with:
- **Categories**: **Any Category**
- **Expense Category**: `🏷️ General`

> This acts as a safety net for any unclassified card taps so no transaction ever slips through unrecorded!

---

## ❓ Troubleshooting & FAQs

### Q1: The Amount is empty or logs as 0.00?
**Cause**: In some regions, the `Amount` property carries currency symbols (such as `$`, `£`, `€`, `¥`) that strict numeric parsers cannot parse directly.  
**Fix**: Ensure you have inserted the **`Get numbers from [Amount]`** action first, and then passed its **`# Numbers`** variable into the `Amount` parameter of `Add Expense`.

### Q2: A confirmation banner or dialog appears every time I tap?
**Fix**:
1. In the automation trigger settings, verify that **Run Immediately** is turned **ON** and **Notify When Run** is turned **OFF**.
2. Tap into the automation actions, expand `Add Expense` by tapping `v`, and ensure **Show When Run** is toggled **OFF**.

### Q3: Can I edit the expense category or note later?
**Yes!** All transactions recorded via Shortcuts appear immediately on the **Expense** home screen and timeline. You can tap on any record at any time to adjust its category, amount, date, or note.

### Q4: Does Expense upload my transactions to any server?
**No.** All operations are performed strictly on your device via iOS App Intents. Expense does not have backend servers, does not require an account, and never collects or transmits your financial data.
