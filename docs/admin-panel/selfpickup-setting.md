---
sidebar_position: 7
---

# Self Pickup Settings

Self pickup lets customers collect their orders from the seller's store instead of having them delivered. The admin turns the feature on for the whole platform; each seller then decides whether their own store offers it and sets the pickup address and opening hours.

## Admin: Turn On Self Pickup

Click **Settings** in the sidebar, then the **Seller Setting** card (group **Selling**). It opens Store Settings on the **Seller Setting** pill (`/store_settings?section=seller_setting`).

![Seller Setting with Self Pickup Mode](/img/admin-panel/selfpickup.webp)

- **One Seller Cart**: must be on. Self pickup works only when a cart holds products from one seller.
- **Self Pickup Mode**: appears only while **One Seller Cart** is on. Turn it on to allow self pickup on the platform.

Click **Update**.

Turning **One Seller Cart** off also turns **Self Pickup Mode** off.

## Seller: Configure the Store for Pickup

Each seller's self-pickup options are in the seller's profile:

- **Admin**: sidebar **Sellers → Manage Sellers**, **Edit** on the seller (`/sellers/edit/:id`).
- **Seller**: in the seller panel, the profile menu (top right) → **My Profile** (`/seller/profile`).

![Seller self pickup configuration](/img/admin-panel/seller-selfpickup.webp)

In the **Other Setting** card:

- **Door Step Mode**: Yes / No, the seller delivers to the customer's door.
- **Self Pickup Mode**: Yes / No, customers can collect orders at the store. At least one of the two modes must stay on.

With **Self Pickup Mode** set to Yes, the **Self Pickup Configuration** section appears. All its fields are required:

- Search the pickup location on the map to fill **Latitude** and **Longitude**.
- **Pickup Store Address**: the address customers come to.
- **Store Timings**: **Opening time** and **Closing time**.

Click **Update** to save the seller. See also [Add / Edit Seller](../detailed-documentation/sellers.mdx#3-add--edit-seller-sellerscreate-sellerseditid).

## When Customers See Self Pickup

Customers are offered self pickup at checkout only when:

1. **Self Pickup Mode** is on in **Seller Setting** (admin), and
2. **Self Pickup Mode** is Yes for the seller whose products are in the cart.

If the seller has also kept **Door Step Mode** on, customers can choose between home delivery and self pickup.

## Self Pickup Orders

Orders placed for pickup are listed in the sidebar under **Self Pickup Orders** (`/self_pickup_orders`), with their own statuses: Pending, Ready for Pickup, Picked Up and Cancelled. Mark an order **Ready for Pickup** to tell the customer to come to the store, then **Picked Up** when they collect it. See [Self Pickup Orders](../detailed-documentation/orders.mdx#4-self-pickup-orders-self_pickup_orders).

## Configuration Steps

1. Admin: open **Settings → Seller Setting**, turn on **One Seller Cart** and **Self Pickup Mode**, and click **Update**.
2. Admin or seller: open the seller's profile, set **Self Pickup Mode** to Yes, fill in the location, **Pickup Store Address**, **Opening time** and **Closing time**, and click **Update**.
3. Place a test order in the customer app and check that the self pickup option appears.

## Support

For assistance with self pickup settings, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
