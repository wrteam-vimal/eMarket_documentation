---
sidebar_position: 23
---

# Addons

Addons let customers customize an order item (e.g. extra cheese, dip, size). They are available only in the **Food Delivery** module.

## Admin Panel

Switch the module in the header to **Food Delivery** and open **Products → Addons** (route `/addons`, permission `addons`). Opening the page in another module redirects to the dashboard.

![Addons — Admin Panel](/img/admin-panel/addons_admin.webp)

- The list shows add-on groups from **all sellers**: **ID**, **Name** (with "Used in N products" and "In carts or orders" notes), **Selection Type**, **Options**, **Owner** (Mine, the seller's name, or Global), **Status** (Active / Deactive) and **Actions**.
- **Filter by seller**: All sellers, **Global (admin)** or one seller. A **Search** box and **Refresh** button are also available.
- The admin can **view and delete** add-on groups. There is no Add or Edit button here: sellers create and edit their add-ons in the seller panel.
- A group that is used in products, carts or orders cannot be deleted; a "Cannot delete" dialog explains why. Ask the seller to remove it from those products first.

## Seller Panel

Sellers manage their own add-ons from **Products → Addons** in the seller panel (`/seller/addons`).

1. Click **Add Addon Group**.
2. Fill in the group:
   - **Name** (required, per language) and optional **Sub title**.
   - **Type**: **Free** or **Paid**.
   - **Selection Type**: **Single** or **Multiple**.
   - **Required**: Yes / No (whether the customer must pick an option).
   - **Max Select**: how many options can be picked; keep `0` for unlimited.
   - **Status**: Activate / Deactivate.
3. Under **Options**, click **Add Option** for each choice and enter the option name (e.g. "Extra Cheese"), **Price** and an optional **Discounted Price** (it must be lower than the price). Paid groups need a price for every option.
4. Click **Save**, then attach the group to products in the product form.


Global add-ons (not owned by a seller) show **Managed by admin** in the seller panel and cannot be edited or deleted by the seller.

## Important Notes

- The Addons menu appears only when the **Food Delivery** module is selected.
- The admin sees and can delete every seller's add-ons; sellers see and manage only their own (plus global add-ons, which are locked).
- More details: [Add-ons](../detailed-documentation/settings.mdx#15-add-ons-addons) and [Addons in the catalog guide](../detailed-documentation/catalog.mdx#12-addons-addons).
