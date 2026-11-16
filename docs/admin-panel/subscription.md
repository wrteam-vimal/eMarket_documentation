---
sidebar_position: 17
sidebar_label: Subscription Settings
---

# Subscription

Subscriptions are paid **membership plans for customers**: a customer buys a plan for a number of days and, while it runs, gets **free delivery** on orders above the amount set in the plan. (These are not seller plans.) Plans are shared by all modules.

The menu is in the sidebar under **Subscriptions** (GENERAL group) with two pages: **Subscription Plans** (`/subscriptions`) and **Subscriptions FAQs** (`/subscriptions_faqs`).

## Subscription Plans

Open **Subscriptions → Subscription Plans** (page **Manage Subscriptions**).

![Manage Subscriptions](/img/detailed-documentation/subscriptions.webp)

- **Enter subscription name** with a save button: the name of your membership programme as customers see it (e.g. "eMarket Plus"). Set it once.
- Each plan is a card with its name, `#ID`, **Active** / **Deactive** badge, the price (the original price struck through when a discounted price is set) "/ N Days", **Days**, **Free Delivery Above**, an on/off switch, **Edit** and **Delete**.
- **Search**, **Refresh** and **Add Subscription** are at the top.

### Add a plan

Click **Add Subscription** and fill in:

| Field | Required | What it does | Example |
| :--- | :--- | :--- | :--- |
| **Plan Name** | Yes (default language) | Plan name shown to customers; one tab per language. | Monthly Saver |
| **Days** | Yes | Length of the plan in days. Each plan must have a different number of days. | 30 |
| **Price** | Yes | Regular price, at least 1. | 149 |
| **Discounted Price** | No | The price customers actually pay; must be lower than **Price**. | 99 |
| **Free Delivery Above** | No | Minimum order amount for free delivery while the plan is active. | 199 |
| **iOS Product ID** | For iOS | The in-app purchase product ID from App Store Connect (the iOS app sells plans as in-app purchases). | `emarket.plus.monthly` |
| **Status** | Yes | Active / Deactive. | Active |

Click **Save**.

![Add Subscription](/img/admin-panel/subscription-add.webp)

## Free delivery logic

While a customer has an active subscription, their orders above the plan's **Free Delivery Above** amount get free delivery. When the plan ends, the scheduler expires it automatically, so the Laravel scheduler (cron) must be running; without it, customers keep free delivery after their plan ends.

## Subscriptions and free-delivery time slots

Subscriptions and **free delivery on time slots** cannot be used together:

- If active time slots with **Enable Free Delivery** exist (with time slots switched on), adding a plan is refused with "Cannot Create Subscription Plan". Remove free delivery from those time slots in **Settings → Delivery Settings** first.
- While active subscription plans exist, **Free Delivery** cannot be turned on for a time slot.

See [Time Slots](./time-slots.md) and [Delivery Settings](../detailed-documentation/delivery.mdx#5-delivery-settings-delivery_settings).

## Subscription FAQs

Open **Subscriptions → Subscriptions FAQs** to manage the questions and answers shown to customers next to the plans. Click **Add Subscription FAQ** and enter the **Query**, **Answer**, a unique **Sort Order** and the **Status**. Turn on **Enable drag and drop** to reorder them. These FAQs are separate from the general FAQs page.

More details: [Subscription Plans](../detailed-documentation/content-blogs.mdx#9-subscription-plans-subscriptions) and [Subscription FAQs](../detailed-documentation/content-blogs.mdx#10-subscription-faqs-subscriptions_faqs).
