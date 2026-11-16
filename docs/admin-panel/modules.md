---
sidebar_position: 8
---

# Modules

Manage the business modules of the platform (for example Grocery, Pharmacy, Ecommerce, Food Delivery). Open **Modules** in the sidebar (General section), route `/modules`, permission `module_list`.

The module selected in the panel header decides which module's data you see and edit on module-wise pages (products, orders, time slots, theme colours and more).

![Modules](/img/detailed-documentation/modules.webp)

## Module Cards

Each module is shown as a card with:

- **Icon**, **name** and **ID** (for example `#1`).
- **Default** badge on the default module.
- **Description** (or "No Description").
- **Status switch** with an **Active** / **Inactive** badge.
- **Edit** (pencil) button.

Use the **Search** box to find a module and **Refresh** to reload the list.

## Enable or Disable a Module

- Turn the status switch on a card on or off. The change is saved at once.
- A disabled module is hidden from the storefront and the apps and can no longer be selected.
- At least one module must stay active, and the default module cannot be disabled.
- If you disable the module currently selected in the header, the panel switches to another active module.

## Reorder Modules

- Drag a card by its move handle (the arrows icon, top right of the card) to a new position. The new order is saved when you drop it.
- The default module is always first and cannot be moved.
- Reordering is only possible while the search box is empty.
- The order is used in the module switcher of the panel and in the apps.

## Edit a Module

Click the **Edit** (pencil) button to open **Edit Module**.

![Edit Module](/img/admin-panel/module-edit.webp)

| Field | Required | What it does |
| :--- | :--- | :--- |
| **Name** | Yes (default language) | Module name, per language. |
| **Slug** | Yes | URL name of the module (default language tab only). |
| **Description** | No | Short description, per language. |
| **Image** | No | Module icon. Single-colour SVG only, with a transparent background, up to 2 MB. A multi-colour SVG is shown in one colour (the module colour) in the app and website. |
| **Status** | Yes | **Activate** or **Deactivate**. |
| **Set as a default module** | No | Makes this module the default one. |

Other language tabs hold only Name and Description, with **Translate Empty Fields** and **Translate & Overwrite**. Click **Save**.

## Default Module

- Exactly one module is the default. Setting another module as default removes the badge from the old one; you cannot simply untick the current default.
- The default module must stay active.
- The **Status Colors** in [Theme Settings](./theme-settings.md) can only be edited while the default module is selected, and modules without their own theme colours use the default module's colours.

## Important Notes

- Many settings are per module: time slots, delivery boy assignment and theme colours. Set them up for every active module (see [Manage Time Slots](./time-slots.md)).
- The **Setup Checklist** card on the Settings hub shows what each module still needs before sellers and customers can use it.

## Support

For assistance with module configuration, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
