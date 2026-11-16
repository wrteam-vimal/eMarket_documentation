---
sidebar_position: 6
---

# Store Settings

Store Settings holds the platform-wide business settings for the store, the panels and all apps. Click **Settings** in the sidebar (General section) to open the Settings hub (`/system_settings`), then click the card of the section you need, for example **Store Setting**, **Cart Setting** or **Login Setting**. Each card opens Store Settings directly on that section (`/store_settings?section=...`).

![Settings hub](/img/detailed-documentation/settings-hub.webp)

A row of pills at the top of the page switches between sections. Each section is one card with grouped fields and its own **Update** button, and **Update** saves only that section. The page title follows the open section, and the **← Settings** link above the title takes you back to the hub.

![Store Settings](/img/detailed-documentation/store-settings.webp)

For a field-by-field reference with examples, see [Store Settings in the detailed documentation](../detailed-documentation/settings.mdx#2-store-settings-store_settings).

:::info Who can change these settings
All sections need the `manage_store_settings` permission. While demo mode is on, only the Super Admin can save; other roles get a "Demo mode" message.
:::

## Sections

| Pill | Link | What it holds |
| :--- | :--- | :--- |
| Store Setting | `?section=store_setting` | App name, support contacts, copyright text, logos and images |
| Address Setting | `?section=address_setting` | Store address and location, map provider and map API keys |
| Currency Setting | `?section=currency_setting` | Currency symbol, currency code, decimal places |
| Date, Time & Region | `?section=regional_setting` | Time zone, date and time format, default country code |
| Product & Stock Setting | `?section=product_setting` | Low stock limit, few-quantity alert, category levels, product rating |
| Delivery Boy Setting | `?section=delivery_boy_setting` | Default delivery boy bonus, delivery OTP |
| App Setting | `?section=app_setting` | App maintenance mode, store links, version control |
| SMTP Mail Setting | `?section=smtp_mail_setting` | Mail server and test email |
| Third Party API Credentials | `?section=third_party_api_credentials` | Gemini key |
| Seller Setting | `?section=seller_setting` | One Seller Cart, Self Pickup Mode, seller commission |
| Login Setting | `?section=login_setting` | Customer sign-in methods, panel login page tabs, Demo Mode |
| Cart Setting | `?section=cart_setting` | Cart limits, delivery charge refunds, cart reminders |
| Refer & Earn Setting | `?section=refer_earn_setting` | Referral rewards |
| Announcement Banner | `?section=announcement_setting` | Scrolling notice at the top of the admin and seller panels |

Payment gateways, additional charges, tax, Firebase, SMS and theme colours have their own pages, also opened from the Settings hub. See [Settings Hub](../detailed-documentation/settings.mdx#1-settings-hub-system_settings).

## Store Setting

Store name, support contacts, logos and copyright text.

**Store details** (per language; use **Translate Empty Fields** or **Translate & Overwrite** to fill the other languages):

- **App Name**: the store name used in the panels, website, apps and emails.
- **Support Number**: contact number shown to customers (digits only, at most 16).
- **Support Email**: contact address shown to customers.
- **Copyright Details**: footer text of the panels, website and apps. Click the **Current year** chip to insert `{{current_year}}`, which is replaced with the current year. The **Preview** line under the box shows the result.

**Logos & images**:

- **Logo**: logo for the light theme.
- **Dark Logo**: logo for the dark theme.
- **Invoice Logo**: logo printed on invoices.
- **Panel Login Background Image**: background of the panel login page.
- **Placeholder Image**: shown wherever an image is missing.

Click **Update**.

## Address Setting

![Address Setting](/img/admin-panel/store-settings-address.webp)

- **Address & location**: **Address** (per language), **Default City**, **Latitude** and **Longitude**.
- **Map Provider**: **Google Maps (Paid)** or **OpenStreetMap (Free)**. With Google Maps, enter the **Place Api Key** and **Map Api Key** (see [Map API Key Settings](./map-api-key-settings.md)). OpenStreetMap needs no key.

The address card and the Map Provider card each have their own **Update** button.

## Currency Setting

- **Store Currency**: symbol or code shown next to prices, for example `₹` or `USD`.
- **Currency Code**: the ISO currency code, for example `INR`.
- **Decimal Places**: digits shown after the decimal point in prices, a whole number from 0 to 6 (2 shows 10.50).

Payment gateway currencies are set per gateway on **Payment Methods**, not here.

## Date, Time & Region

- **System Timezone**: time zone used for all dates and times. Type a city or an offset to search.
- **Date Format** and **Time Format**: how dates and times are shown everywhere.
- **Country Code**: default country code for phone numbers.

## Product & Stock Setting

![Product & Stock Setting](/img/admin-panel/store-settings-product-stock.webp)

- **Low stock limit**: a product counts as low stock when its stock goes below this number.
- **Few Quantity Left Alert**: shows "few quantity left" on a product when its quantity is below this number.
- **Allow Products on All Category Levels**: when off, products can only be assigned to an end-level category (the last node).
- **Product Rating**: turns the product rating system on or off.

## Delivery Boy Setting

![Delivery Boy Setting](/img/admin-panel/store-settings-delivery-boy.webp)

- **Bonus**: **Bonus Settings** (on/off) and **Bonus Type** (**Commission** or **Fixed/Salaried**). For Commission, also **Delivery Boy Bonus Percentage**, **Minimum bonus amount** and **Maximum bonus amount** (set 0 to remove a limit). These are the defaults that **Add Default Bonus** fills in on the Add Delivery Boy form.
- **Delivery confirmation**: **Order Delivery OTP System**. When on, an OTP is generated for each order, and the delivery boy needs the customer's OTP to confirm delivery.

## App Setting

Maintenance mode, store links and version control for the customer, seller and delivery boy apps. See [App Settings](./app-settings.md).

## SMTP Mail Setting

The mail server used to send emails, with a test email. See [Email Settings](./email-settings.md).

## Third Party API Credentials

![Third Party API Credentials](/img/admin-panel/store-settings-third-party.webp)

- **Gemini Key**: the AI content key used to write product descriptions and translations (the **Translate Empty Fields** and **Translate & Overwrite** buttons). See [Gemini Config](./gemini-config.md).

The Google map keys are no longer in this section; they are in **Address Setting**.

## Seller Setting

- **One Seller Cart**: customers can only have products from one seller in the cart.
- **Self Pickup Mode**: shown only while **One Seller Cart** is on. Lets customers collect orders from the seller's store. See [Self Pickup Settings](./selfpickup-setting.md).
- **Seller Commission (%)**: the default platform commission on seller orders.

Turning **One Seller Cart** off also turns **Self Pickup Mode** off, and on save every module that uses **Quick Delivery** time slots is switched back to **Fixed Time Window** (see [Manage Time Slots](./time-slots.md)).

## Login Setting

Customer sign-in methods, phone authentication, the tabs of the panel login page and the Demo Mode switch. See [Login Settings](./login-settings.md).

## Cart Setting

![Cart Setting](/img/admin-panel/cart_setting.webp)

- **Cart limits**: **Maximum Items Allowed In Cart** (required) and **Minimum Order Amount**.
- **Refunds**: **Is Delivery Charge Refundable?**. When **Yes**, the delivery charge is included in the refund of a cancelled or returned order; when **No**, only the product amount is refunded. It applies to all orders.
- **Cart reminders**: **Cart Notification** and its timing fields. See [Cart Reminder](./cart-reminder.md).

## Refer & Earn Setting

![Refer & Earn Setting](/img/admin-panel/store-settings-refer-earn.webp)

- **Minimum Order for Referral**: the minimum amount the referred customer's first order must reach.
- **Referral Credit First Order**: the credit given for the referred customer's first order.

## Announcement Banner

![Announcement Banner](/img/admin-panel/store-settings-announcement.webp)

- **Show announcement banner**: when on, every admin and seller sees the message scrolling at the top of the panel.
- **Message**: one per language, up to 500 characters. The default-language message is required while the banner is on; languages left empty show the default-language message. A **Preview** shows how the banner looks.

## Configuration Steps

1. Click **Settings** in the sidebar, then the **Store Setting** card.
2. Enter **App Name**, **Support Number**, **Support Email** and **Copyright Details**.
3. Upload the **Logo**, **Dark Logo**, **Invoice Logo**, **Panel Login Background Image** and **Placeholder Image**, then click **Update**.
4. Click the **Address Setting** pill, fill in the address and location, choose the **Map Provider** and click **Update** in each card.
5. Click the **Currency Setting** pill, set the currency and decimal places and click **Update**.
6. Click the **Date, Time & Region** pill, choose the time zone, formats and country code and click **Update**.
7. Go through the other pills you need in the same way. Each pill is saved on its own.

## Important Notes

- Each section saves only its own fields. Click **Update** before you switch to another pill, or the changes in that section are lost.
- A link such as `/store_settings?section=cart_setting` opens a section directly.
- If a saved change does not show up right away, use the **Clear System Cache** card on the Settings hub.
- Additional charges (packaging, handling, service fees) are no longer part of Store Settings; they are on their own page. See [Additional Charges](../detailed-documentation/settings.mdx#4-additional-charges-additional_charges).
- The Demo Mode switch (Login Setting) can only be changed by the Super Admin account (user ID 1).

## Troubleshooting

1. **Logo not uploading**: use an image file (PNG, JPG, WEBP or SVG) and check the upload size limit of your server (see [PHP INI Settings](./php-ini-settings.md)).
2. **Settings not saving**: check that your role has `manage_store_settings` and that demo mode is off (or that you are the Super Admin). Read the error message: for example, **Support Number** must be at most 16 digits and **Decimal Places** at most 6.

## Support

For assistance with store settings, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
