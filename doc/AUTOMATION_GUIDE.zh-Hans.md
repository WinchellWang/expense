# 💳 Apple Pay 自动记账指南

> 使用 iOS「快捷指令」自动记录 Apple Pay 轻触支付。可选择固定分类映射、统一记入 General 后手动整理，或通过设备端 AI 辅助分类。

[English](AUTOMATION_GUIDE.md) | [简体中文](AUTOMATION_GUIDE.zh-Hans.md) | [繁體中文](AUTOMATION_GUIDE.zh-Hant.md) | [日本語](AUTOMATION_GUIDE.ja.md) | [Français](AUTOMATION_GUIDE.fr.md) | [Español](AUTOMATION_GUIDE.es.md)

---

## 📌 概述

通过 iOS 快捷指令中的“个人自动化”，无论你使用 iPhone 还是 Apple Watch 刷卡付款，**Expense** 都能在刷卡完成的瞬间自动在后台记录下这笔消费。

### 为什么推荐使用自动化记账？
- ⚡ **无感自动记账**：刷卡完成即可放下手机离开，记账在后台静默自动完成。
- 🏷️ **多种分类方式**：预设类别一对一映射、统一记入 General，或由 AI 推断消费分类。
- 🏪 **自动填充商户名**：商家名称（如星巴克、山姆会员店等）会自动存入支出备注中。
- 🔒 **本地处理**：普通记账通过 iPhone 上的 App Intents 完成；AI 分类请选择 On-Device，无需绑定网银账号。

---

## 🛠️ 前提条件

- **iPhone** 运行 iOS 18.0 或更高版本。
- 手机“钱包”中已添加至少一张 Apple Pay 银行卡或交通卡。
- 已安装 **Expense** 记账 App。
- 系统自带的 **快捷指令** App。

---

## 🚀 传统快捷指令：详细配置教程

本教程以最常用的 **「餐饮 (Food & Drinks)」** 分类为例进行说明（配置其他分类方法完全一致）：

### 第一步：在快捷指令中新建自动化
1. 在 iPhone 上打开 **「快捷指令」** App。
2. 轻点屏幕底部的 **「自动化」** 标签页。
3. 轻点右上角的 **`+`** 号创建新自动化。
4. 向上滑动列表，找到并轻点 **「交易」**（部分 iOS 版本中显示为 **「钱包」**）。

---

### 第二步：配置触发条件（卡片与分类）
在触发器设置页面中：

1. **卡片**：选择 **「任一卡片」**（也可以指定特定的信用卡或借记卡）。
2. **类别 (Categories)**：
   - 轻点 **「类别」**。
   - 勾选 **「餐饮 (Food & Drinks)」**。
   - 轻点右上角的蓝色对勾按钮 `✓` 完成选择。
3. **商户**：保持为 **「任一商户」**。
4. **运行模式设置**：
   - 勾选 **「立即运行」**（开关变为 **绿色**）。
   - 关闭 **「运行时通知」**（保持为 **关闭** 状态，避免每次刷卡都弹出通知打扰）。
5. 轻点右上角的 **「下一步」**。

---

### 第三步：配置自动化操作流程
选择 **「新建空白自动化」**，依次添加以下 3 个操作：

#### 操作 1：从输入中获取纯数字金额
Apple Pay 传入的交易金额通常带有货币符号（如 `$9.21`、`¥15.00`），通过系统动作提取纯数字，可确保 100% 不出错：
1. 轻点 **「添加操作」**。
2. 搜索 **「从输入中获取数字」**（英文搜索 `Get numbers from`）并选中添加。
3. 轻点参数占位符，选择 **「快捷指令输入」**（或展开选择 `交易 > 金额`）。
   - 此时该卡片显示为：`从 [金额] 中获取数字`。
   - 其输出变量为 **`数字`**（`# Numbers`）。

#### 操作 2：添加支出到 Expense
1. 在屏幕底部的搜索栏中输入 **Expense**。
2. 找到并选择 **「Add Expense」**（添加支出）操作。
3. 依次配置各参数：
   - **Amount（金额）**：轻点输入框，在键盘上方变量栏中选择操作 1 的输出 **`数字 (# Numbers)`**。
   - **Category（分类）**：轻点分类，选择对应的 **`🍱 餐饮 (Food & Drinks)`**。
   - **Note（备注）**：轻点备注框，选择 **「快捷指令输入」**，轻点填入的蓝色胶囊气泡，将属性切换为 **`商户 (Pay Merchant)`**。
4. 轻点「Add Expense」卡片右上方的箭头 `>` 展开详细设置：
   - 将 **「运行时显示 (Show When Run)」** 设为 **关闭**（确保后台静默执行）。

#### 操作 3：停止快捷指令
1. 在底部搜索栏搜索 **「停止此快捷指令」**（英文搜索 `Stop this shortcut`）并添加。
2. 轻点右上角的 **「完成」** 保存自动化。

---

## 📸 完整自动化结构图

配置完成后的自动化结构如下：

![shortcuts](./shortcuts.jpg)

---

## 💡 进阶建议：按分类建立自动化

可为触发器中已有的类别重复上述步骤。下表仅为映射示例，不能覆盖所有 Apple Pay 消费：

| 触发器类别 (Trigger Category) | Expense 对应分类 |
| :--- | :--- |
| **餐饮 (Food & Drinks)** | `🍱 餐饮` |
| **购物 (Shopping)** | `🛍️ 购物` |
| **交通 (Transportation)** | `🚗 交通` |
| **旅行 (Travel)** | `🏖️ 旅行` |
| **服务 (Services)** | `🛠️ 服务` |
| **娱乐 (Entertainment)** | `🎠 娱乐` |
| **健康 (Health)** | `💊 健康` |

---

## ⚠️ 传统快捷指令的限制与 General 方案

苹果的「交易」自动化可以按类别筛选，但传入快捷指令的交易变量中**不包含 Category（分类）**，因此普通快捷指令无法读取 Apple Pay 的原始消费分类。这是 iOS 快捷指令的设计限制，Expense 无法从 App 端解决。

- **一对一分类映射**：在自动化触发条件中预选一个类别，再在 **Add Expense** 中明确指定对应的 Expense 分类。每组映射需要单独建立自动化。部分 Apple Pay 类别不在触发器的可选列表中，未匹配所选类别的消费不会被这些自动化记录。
- **记录所有类别的消费**：将触发条件设为 **任意类别（Any Category）**、**任一卡片（Any Card）** 和 **任一商户（Any Merchant）**，再将 **Add Expense → Category** 统一设为 **General（通用）**。这样可避免因类别筛选而漏记，包括没有对应可选类别的轻触支付。稍后进入 Expense，手动修改各条记录的分类。快捷指令本身仍无法识别原始类别。

同一笔消费应只使用一种方案。启用 **Any Category** 自动化时，请停用覆盖相同消费的分类自动化，避免重复记账。这里的「所有」指 iOS 会传给「交易」触发器的 Apple Pay 轻触支付。

---

## 🤖 AI 辅助快捷指令：全类别触发与自动分类

> **AI 可以补上自动分类这一环：** 用 Any Category 覆盖所有类别，再根据商户名推断分类，无需将每笔消费都固定记入 General，在保留全类别触发的同时减少手动整理。

沿用 **Any Category** 触发方式，避免按类别过滤消费，再由 Apple Intelligence 根据商户名推断 Expense 分类。AI 并非读取 Apple Pay 缺失的 Category 字段。所提供的流程会在 **Add Expense 之前**完成分类，每笔消费只记一次。

### 使用条件

- **iOS 26 或更高版本**，iPhone 必须支持并已启用 **Apple Intelligence**，且该功能在所用语言和地区可用。
- 快捷指令中的 **使用模型（Use Model）** 操作须选择 **设备端（On-Device）**。仅升级 iOS 无法让不支持的设备获得此功能。参见[苹果 Apple Intelligence 入门指南](https://support.apple.com/en-ca/guide/iphone/iphc28624b81/ios)。

---

## 📥 下载 AI 辅助快捷指令

<a href="https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d">
  <img src="https://cdn.jim-nielsen.com/ios/512/shortcuts-2018-10-03.png" alt="添加 AI 辅助快捷指令" width="64" height="64" style="border-radius: 14px;">
</a>

[添加 AI 辅助快捷指令](https://www.icloud.com/shortcuts/373d0c7f43aa49b6ae3eabe7dcd0c82d)

---

## 🛠️ AI 辅助快捷指令配置

1. 从上方独立的下载章节添加共享的 AI 辅助快捷指令。
2. 新建「交易」自动化，选择 **Any Card → Any Category → Any Merchant**，开启 **立即运行**，关闭 **运行时通知**。
3. 在自动化中运行导入的快捷指令，并将 **交易／快捷指令输入** 传给它，以便读取 **金额（Amount）** 和 **商户（Merchant）**。
4. 确认 **Use Model** 选择 **On-Device**，并接收商户名。模型返回分类编号，对应的 **If（如果）** 分支通过 **Add Expense** 写入提取后的金额、对应分类和商户备注。逐一检查各分支是否对应你的 Expense 分类，并关闭 **运行时显示**。
5. 停用会记录相同消费的其他自动化，首次支付后检查金额、备注和分类。

### 分类 Prompt 与模型设置

将以下英文 prompt 复制到 **Use Model**。最后一行的 `Transaction (Merchant)` 是变量占位说明，请替换为「快捷指令输入」中的真实 **交易 → 商户（Merchant）** 变量，不要保留为普通文字。各语言版本共用同一份英文 prompt，确保分类编号一致。

按截图将 **模型设为 On-Device**、**输出（Output）设为 Number（数字）**，并**关闭 Follow Up（跟进）**。在 If 分支中，将数字类型的 **Response** 与 `1` 至 `8` 比较，其中 `8` 对应 General。

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

### 流程截图与限制

![AI 辅助快捷指令流程](./iOS_27_AI_Shortcuts.jpg)

AI 根据商户名推断分类，可能判断错误，尤其是销售多类商品的商户。请按需在 Expense 中检查并修正。无法确定分类时，应以 **General** 兜底。截图采用编号分支；自行调整快捷指令时，还应将空白或非预期返回值导向 General，避免因未匹配分支而漏记。模型执行失败时仍可能需要手动补录。

本地处理的说明以选择 **On-Device** 为前提；切换为 Private Cloud Compute 或 ChatGPT 后，分类处理的位置也会改变。

---

## ❓ 常见问题与排错

### Q1：为什么记账金额为空或者显示为 0.00？
**原因**：不同国家和地区发行的银行卡传出的 `Amount` 变量可能包含货币符号（如 `$`, `€`, `¥`）。  
**解决办法**：请务必按照指南加入 **「从输入中获取数字」** 操作，并将提取出的 **`# 数字`** 传入 `Add Expense` 的金额栏。

### Q2：每次刷卡后依然会弹出询问确认的弹窗？
**解决办法**：
1. 检查自动化的触发器设置，确保 **「立即运行」** 为开启，**「运行时通知」** 为关闭。
2. 点进自动化操作，展开 `Add Expense` 卡片的详细属性，确保 **「运行时显示」** 已关闭。

### Q3：记完账后可以修改分类或备注吗？
**可以！** 所有自动化写入的记录会即时同步到 Expense 主界面。轻点任意一条记录即可重新选择分类、修改金额或编辑备注。

### Q4：Expense 会把我的交易记录上传到云端吗？
普通快捷指令通过 iOS App Intents 在本地记账。AI 版本选择 **On-Device** 时，分类也在设备端处理；Private Cloud Compute 和 ChatGPT 则涉及远程处理。Expense 中可选的 iCloud 同步与备份是独立设置。
