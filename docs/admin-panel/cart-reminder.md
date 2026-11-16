---
sidebar_position: 13
---

# Cart Reminder

Send push notifications to customers who add products to their cart but do not place an order. Click **Settings** in the sidebar, then the **Cart Setting** card (group **Selling**). It opens Store Settings on the **Cart Setting** pill (`/store_settings?section=cart_setting`); the reminders are in the **Cart reminders** group.

![Cart Setting](/img/admin-panel/cart_setting.webp)

## Cart Reminder Fields

| Field | Unit | What it does |
| :--- | :--- | :--- |
| **Cart Notification** | on/off | Turns cart reminders on. The three fields below appear only while it is on. |
| **Notification Delay After Cart Addition** | Minutes | How long after a product is added to the cart the first reminder is sent. |
| **Notification Interval** | Minutes | Time between the following reminders. |
| **Notification Stop Time** | Minutes | After this time (counted from when the product was added) no more reminders are sent for it if the order is still not placed. |

The same card also holds **Maximum Items Allowed In Cart**, **Minimum Order Amount** and **Is Delivery Charge Refundable?** (see [Store Settings](./store-settings.md#cart-setting)). Click **Update** to save the whole Cart Setting section.

## How Reminders Are Sent

- The scheduled command `cart:notification` runs every minute and checks every cart item that is not saved for later.
- First reminder: when **Notification Delay After Cart Addition** has passed since the product was added.
- Next reminders: every **Notification Interval** minutes, until **Notification Stop Time** is reached.
- Products a customer added within 10 minutes of each other get one reminder, not one each.
- Reminders are push notifications to the customer's registered devices. Customers without a registered device get nothing.

Example: with a delay of `30`, an interval of `120` and a stop time of `1440`, a customer gets the first reminder 30 minutes after adding a product, then one every 2 hours, and the reminders stop 24 hours after the product was added.

## Reminder Text

The title and message come from two push templates in **Settings → Notification Templates**:

- `cart_reminder_first`: the first reminder (placeholder `{{product_name}}`).
- `cart_reminder_interval`: the following reminders (placeholders `{{product_name}}` and `{{measurement}}`).

Edit them per language there. See [Notification Templates](../detailed-documentation/communications.mdx#2-notification-templates-notification-templates).

## See Abandoned Carts

The **Abandoned Carts** page in the sidebar (below Self Pickup Orders) lists every customer's cart for the selected module, with the items, cart value and last activity. Use it to follow up on large carts yourself. See [Abandoned Carts](../detailed-documentation/customer-finance.mdx#5-abandoned-carts-abandoned_carts).

![Abandoned Carts](/img/detailed-documentation/abandoned-carts.webp)

## Configuration Steps

1. Set up Firebase so push notifications can be sent (see [Firebase Settings](./firebase-settings.md)).
2. Make sure the server cron runs the Laravel scheduler every minute: `* * * * * php artisan schedule:run`.
3. Click **Settings** in the sidebar, then the **Cart Setting** card.
4. Turn on **Cart Notification**.
5. Enter **Notification Delay After Cart Addition**, **Notification Interval** and **Notification Stop Time** in minutes.
6. Click **Update**.
7. Optionally adjust the texts of `cart_reminder_first` and `cart_reminder_interval` in **Notification Templates**.

## Important Notes

- Without the scheduler cron, no reminders are sent. The **System Status** card on the Settings hub shows whether the scheduler is running.
- Keep the interval reasonable (for example 2 hours or more) so customers are not flooded.
- Reminders stop for a product once it is ordered or removed from the cart.

## Troubleshooting

1. **No reminders arrive**: check that **Cart Notification** is on, the scheduler cron is running, Firebase Settings are filled in and the customer allowed notifications in the app.
2. **Reminders never stop**: check that **Notification Stop Time** is larger than **Notification Delay After Cart Addition**.

## Support

For assistance with cart reminders, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
