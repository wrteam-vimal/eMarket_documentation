---
sidebar_position: 24
---

# Manage Time Slots

Choose whether customers pick a delivery time at checkout and which time slots they can pick. Open **Delivery Settings → Delivery Settings** in the sidebar, or click **Settings** and then the **Delivery Settings** card (group **Delivery**). The page is called **Manage Time Slots** (`/delivery_settings`, permission `delivery_settings`).

Time slots are **per module**: the config and the slots belong to the module selected in the panel header (Grocery, Pharmacy, Ecommerce, Food Delivery, and so on). Select the module first, then set it up; repeat for every module you use.

![Manage Time Slots](/img/detailed-documentation/delivery-settings.webp)

## Time Slot Config

"Turn delivery time slots on or off and choose how customers pick a delivery time."

- **Enable / Disable Time Slots**: off means customers get no time-slot choice. The other fields and the slot list appear only while it is on.
- **Slot Type**:
  - **Fixed Time Window**: customers pick a day and a delivery window from your list of slots.
  - **Quick Delivery**: the order is delivered within a set number of minutes. Requires **One Seller Cart** to be on in **Settings → Seller Setting**.
- **Delivery Estimate Days**: estimated number of days for delivery (Fixed Time Window only).
- **How many Days you want to allow?**: how many days ahead customers can book a slot (Fixed Time Window only; required).

Click **Save**.

## Time Slot List

Columns: ID, Title, Slot Type, From Time, To Time, Last Order Time, Status, Free Delivery and Actions (Edit, Delete). Only the slots of the selected **Slot Type** are listed; switching the type hides the other slots but does not delete them.

## Add New Time Slot

Click **Add New Time Slot**.

![Add New Time Slot](/img/detailed-documentation/time-slot-add.webp)

| Field | Fixed Time Window | Quick Delivery | What it does |
| :--- | :--- | :--- | :--- |
| **Title** | Required | Required | Slot name, per language, for example "Morning 9AM to 12PM". |
| **From Time** / **To Time** | Required | — | The delivery window. |
| **Last Order Time** (24 hrs format) | Required | Optional | Orders placed after this time cannot use the slot that day. |
| **Duration (minutes)** | — | Required | "Delivered within this many minutes of the order being placed." |
| **Free Delivery** | Optional | Optional | **Enable Free Delivery** for orders in this slot. |
| **Status** | Activate / Deactivate | Activate / Deactivate | Only active slots are shown to customers. |

The title can be filled per language, with **Translate Empty Fields** and **Translate & Overwrite**. Click **Save**.

Only one Quick Delivery slot can exist per module. **Add New Time Slot** is disabled while one exists; delete it first to add a new one.

## Configuration Steps

1. Select the module in the panel header (for example **Grocery**).
2. Open **Delivery Settings → Delivery Settings**.
3. Turn on **Enable / Disable Time Slots**, choose **Fixed Time Window**, enter **How many Days you want to allow?** (for example `7`) and click **Save**.
4. Click **Add New Time Slot**, enter **Title** `Morning`, **From Time** 07:00, **To Time** 10:00, **Last Order Time** 06:00, choose **Activate** and click **Save**.
5. Add the other windows of the day in the same way.
6. Repeat for every other module.

## Important Notes

- Slots made while one module is selected do not show in another module.
- **Free Delivery** cannot be enabled while active subscription plans exist. The form shows a note with a **Go to Subscriptions** link; remove the active plans first.
- Turning **One Seller Cart** off in Seller Setting switches every module that uses **Quick Delivery** back to **Fixed Time Window**.
- Time slots do not set delivery charges (except **Free Delivery** per slot). Delivery charges belong to each city's delivery zone.

More details: [Delivery Settings in the detailed documentation](../detailed-documentation/delivery.mdx#5-delivery-settings-delivery_settings).

## Support

For assistance with time slots, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
