# 💳 Apple Pay Automatic Expense Logging Guide

> Automatically record Apple Pay tap payments with iOS Shortcuts. Choose fixed category mapping, General with later review, or on-device AI classification.

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 Overview

With iOS Shortcuts Personal Automations, you can automatically log purchases into **Expense** the instant you tap your iPhone or Apple Watch to pay with Apple Pay.

### Why use this automation?
- ⚡ **Zero-effort tracking**: The moment your card is tapped, the transaction is logged silently in the background.
- 🏷️ **Category options**: Map a preset trigger category to Expense, record everything as General, or use AI to infer a category.
- 🏪 **Merchant Name Included**: Automatically records the store or merchant name into the expense note.
- 🔒 **Local processing**: Standard logging uses App Intents on your iPhone. For AI classification, select On-Device; no bank login is required.

---

## 🛠️ Prerequisites

- **iPhone** running iOS 18.0 or later.
- **Apple Pay** configured with at least one card in Apple Wallet.
- **Expense** app installed on your iPhone.
- Apple's built-in **Shortcuts** app.

---

## 🚀 Standard shortcut: step-by-step setup

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

Repeat the steps above for categories available in your automation trigger. The table shows example mappings; this does not cover every Apple Pay payment.

| Automation Trigger Category | Expense App Category |
| :--- | :--- |
| **Food & Drinks** | `🍱 Food & Drinks` |
| **Shopping** | `🛍️ Shopping` |
| **Transportation** | `🚗 Transportation` |
| **Travel** | `🏖️ Travel` |
| **Services** | `🛠️ Services` |
| **Entertainment** | `🎠 Entertainment` |
| **Health** | `💊 Health` |

---

## ⚠️ Standard shortcut limitations and the General workaround

Apple’s Transaction automation can filter by category, but the transaction input passed to a shortcut does **not include Category**. A standard shortcut therefore cannot read the original Apple Pay category. This is an iOS Shortcuts design limitation that Expense cannot fix.

- **One-to-one mapping**: Select one category in the automation trigger, then explicitly select its matching Expense category in **Add Expense**. Create a separate automation for each mapping. Some Apple Pay categories are not available in the trigger’s category list, so transactions outside your selected categories will not be recorded by these automations.
- **Record all categories**: Set the trigger to **Any Category**, **Any Card**, and **Any Merchant**, then set **Add Expense → Category** to **General**. This avoids missing tap payments because of category filters, including payments with no matching selectable category. Later, open Expense and edit each record’s category manually. The shortcut still cannot determine the original category.

Use one strategy for the same payments. Disable overlapping category-specific automations when enabling an **Any Category** automation to avoid duplicate records. “All” here means Apple Pay tap payments delivered by iOS to the Transaction trigger.

---

## 🤖 AI-assisted shortcut: all categories with automatic classification

> **AI addresses the classification gap:** use Any Category to include all categories, then infer a category from the merchant name instead of leaving every expense in General. This reduces manual sorting while preserving broad trigger coverage.

Use the same **Any Category** trigger to avoid category filtering, then let Apple Intelligence infer an Expense category from the merchant name. AI does not recover Apple Pay’s missing Category field. In the supplied workflow, classification happens **before** Add Expense, so each payment is recorded once.

### Requirements

- **iOS 26 or later**, on an iPhone that supports **Apple Intelligence**, with Apple Intelligence enabled and available for your language and region.
- The Shortcuts **Use Model** action, set to **On-Device**. Updating iOS alone does not enable this on unsupported hardware. See [Apple’s Apple Intelligence getting-started guide](https://support.apple.com/en-ca/guide/iphone/iphc28624b81/ios).

---

## 📥 Download the AI shortcut

<a href="https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d">
  <img src="https://cdn.jim-nielsen.com/ios/512/shortcuts-2018-10-03.png" alt="Add the AI shortcut" width="64" height="64" style="border-radius: 14px;">
</a>

[Add the AI shortcut](https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d)

---

## 🛠️ AI shortcut setup

1. Add the shared AI shortcut from the dedicated download section above.
2. Create a **Transaction** automation with **Any Card → Any Category → Any Merchant**, select **Run Immediately**, and turn off **Notify When Run**.
3. Run the imported shortcut from the automation, passing the **Transaction / Shortcut Input** through to it so it can access **Amount** and **Merchant**.
4. Check that **Use Model** uses **On-Device** and receives the merchant name. The model returns a category number; the matching **If** branch runs **Add Expense** with the extracted amount, mapped category, and merchant note. Check each branch’s category against your Expense categories and turn off **Show When Run**.
5. Disable other automations that log the same payments. Verify the amount, note, and category after your first payment.

### Classification prompt and model settings

Copy the following English prompt into **Use Model**. In the last line, replace `Transaction (Merchant)` with the actual **Transaction → Merchant** variable from Shortcut Input; do not leave it as literal text. All language editions use the same prompt to keep the category numbers consistent.

Set **Model → On-Device**, **Output → Number**, and **Follow Up → Off**, as shown in the screenshot. Compare the numeric **Response** with `1` through `8` in the If branches; `8` maps to General.

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

### Workflow and limitations

![AI-assisted shortcut workflow](./iOS_27_AI_Shortcuts.jpg)

AI classification is an estimate based on the merchant name and can be wrong, especially for merchants selling different kinds of goods. Review and correct records in Expense when needed. Keep **General** as the fallback for uncertain classifications. The screenshot uses numbered branches: when adapting the shortcut, also route empty or unexpected responses to General so an unmatched response does not skip logging. Model execution failures may still require a manual entry.

The local-processing description applies when **On-Device** is selected. Choosing Private Cloud Compute or ChatGPT changes where classification is processed.

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
The standard shortcut records expenses locally through iOS App Intents. The AI version also processes classification locally when **On-Device** is selected; Private Cloud Compute and ChatGPT use remote processing. Optional iCloud sync and backup in Expense are separate settings.
