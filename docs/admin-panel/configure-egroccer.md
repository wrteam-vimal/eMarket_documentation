---
sidebar_position: 5
---

# Configure eMarket

After the [installation](./server-setup.md), configure your store from the admin panel. This page covers the first
login, where every setting lives, and the order in which to set things up. For a full step-by-step tutorial (from the
first login to a delivered test order) see
[Getting Started: Set Up Your Store Step by Step](../detailed-documentation/getting-started.mdx).

:::note
Log in with the **Super Admin** account you created in the installer's **Database & admin** step. Some settings (for
example **Demo Mode** and **Clear System Cache**) can only be changed by the Super Admin.
:::

## 1. Log in

1. Open `https://yourdomain.com/login` (or your admin subdomain). The **Admin** tab is selected.
2. Enter the **Email Address** and **Password** of the Super Admin account and click **Login**.

   ![Admin login](/img/admin-panel/admin-login.webp)

3. The panel opens on the **Dashboard** (`/dashboard`).

   ![Dashboard](/img/detailed-documentation/dashboard.webp)

Forgot the password? Click **Forgot Password?** on the login page (this needs working SMTP mail).

## 2. Get to know the panel

- **Module selector** (header): the active module, for example **Grocery**. Categories, products, orders, Home Builder
  and delivery settings show the selected module's data only, so check it before you add data.
- **Setup progress card** (Dashboard): shows how far setup is, with a **Set up now** button for the next missing step.
  **View checklist** opens the **Setup Checklist** (`/setup_checklist`), which lists every required setting per module.
  See [Setup Checklist](../detailed-documentation/intro.mdx#2-setup-checklist-setup_checklist).
- **Settings** (sidebar, **GENERAL** group) opens the **Settings hub** (`/system_settings`). Every configuration page is
  a card there, grouped as **Store**, **Selling**, **Delivery**, **Apps & Website**, **Content & Policies**,
  **Communication**, **Integrations** and **System**. Type in **Search settings…** to find a card, then click
  **Go to settings →**.
- **Search** in the header (<kbd>Ctrl</kbd> + <kbd>K</kbd>, or <kbd>⌘</kbd> + <kbd>K</kbd> on a Mac) jumps to any menu entry or setting by name.

![Settings hub](/img/detailed-documentation/settings-hub.webp)

Store Settings is split into sections (pills). The hub cards **Store Setting**, **Address Setting**, **Currency
Setting**, **Date, Time & Region**, **Cart Setting**, **Login Setting**, **SMTP Mail Setting** and others open
**Store Settings** (`/store_settings?section=...`) on the right section. Each section has its own **Update** button
that saves only that section. Details: [Settings Hub](../detailed-documentation/settings.mdx#1-settings-hub-system_settings)
and [Store Settings](../detailed-documentation/settings.mdx#2-store-settings-store_settings).

## 3. Recommended setup order

Work through these in order; the Setup Checklist marks most of them as done when they are saved.

| # | What | Where in the panel | Guide |
| :--- | :--- | :--- | :--- |
| 1 | Switch off modules you do not use | Sidebar **Modules** (`/modules`) | [Modules](./modules.md) |
| 2 | Store name, support contacts, logos | **Settings → Store Setting** (`/store_settings?section=store_setting`) | [Store Settings](./store-settings.md) |
| 3 | Store address, map provider and map keys | **Settings → Address Setting** (`/store_settings?section=address_setting`) | [Map API Key Settings](./map-api-key-settings.md) |
| 4 | Currency and decimal places | **Settings → Currency Setting** (`/store_settings?section=currency_setting`) | [Store Settings](./store-settings.md) |
| 5 | Time zone, date and time format, country code | **Settings → Date, Time & Region** (`/store_settings?section=regional_setting`) | [Store Settings](./store-settings.md) |
| 6 | Payment methods (Cash on Delivery plus one gateway in **Sandbox**) | **Settings → Payment Methods** (`/payment_methods`) | [Payment Gateway](./payment-gateway.md) |
| 7 | Delivery cities and areas, delivery charges, time slots | **Location → Cities**, **Settings → Delivery Settings** (`/delivery_settings`) | [Time Slots](./time-slots.md) |
| 8 | Customer sign-in methods | **Settings → Login Setting** (`/store_settings?section=login_setting`) | [Login Settings](./login-settings.md) |
| 9 | Firebase (push notifications, phone OTP) | **Settings → Firebase Settings** (`/firebase-settings`) | [Firebase Settings](./firebase-settings.md) |
| 10 | Email (SMTP) | **Settings → SMTP Mail Setting** (`/store_settings?section=smtp_mail_setting`) | [Email Settings](./email-settings.md) |
| 11 | SMS (optional) | **Settings → SMS Settings** (`/sms-settings`) | [Twilio Settings](./twilio-settings.md) |
| 12 | Brand colours | Sidebar **Theme Settings** (`/theme-settings`) | [Theme Settings](./theme-settings.md) |
| 13 | App versions and app links | **Settings → App Setting**, **Deeplink Settings** | [App Settings](./app-settings.md), [Deeplink Settings](./deeplink-settings.md) |
| 14 | Optional features | Self pickup, cart reminders, Gemini key, add-ons, subscriptions | [Self Pickup](./selfpickup-setting.md), [Cart Reminder](./cart-reminder.md), [Gemini Config](./gemini-config.md), [Addons](./addons.md), [Subscription](./subscription.md) |

Taxes, categories, sellers, products, delivery boys and the home page come next; the
[Getting Started](../detailed-documentation/getting-started.mdx) tutorial covers them in order.

:::tip
Mail, file storage and the realtime driver are set in the panel, not in `.env`: **SMTP Mail Setting**, **External
Storage** (`/external-storage`) and **Realtime Settings** (`/realtime-settings`). After saving settings that do not show
up right away, use **Settings → Clear System Cache**.
:::

## 4. Server-side configuration

A few things are set on the server, not in the panel.

1. **`.env` file** (project root), on a live server:

   ```env
   APP_ENV=production
   APP_DEBUG=false
   APP_URL=https://yourdomain.com
   ```

   `APP_URL` must be the address you open the panel on, or image and file links break. The database values
   (`DB_HOST`, `DB_PORT`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`) are written by the installer.

2. **Cron job** for Laravel's scheduler, every minute:

   ```bash
   * * * * * cd /path/to/emarket && php artisan schedule:run >> /dev/null 2>&1
   ```

   It credits seller earnings, sends abandoned-cart reminders, switches scheduled home pages and popups, and times out
   auto-assign offers.

3. **Storage link**, so uploaded images load: `php artisan storage:link` (the installer creates it when `symlink()` is
   allowed).

Then open **Settings → System Status** (`/system_status`). It checks the scheduler, queue, storage link, free disk space,
writable folders, mail, SMS, Firebase, PHP and Laravel versions, environment, `APP_URL`, cache driver and time zone, and
offers a link to fix each problem it can. See [System Status](../detailed-documentation/system-maintenance.mdx#1-system-status-system_status).

## 5. Before going live

- **System Status** shows no errors and the **Scheduler** card shows a recent run.
- Each payment gateway is switched from **Sandbox** to **Live** with live keys.
- **Demo Mode** is off (**Store Settings → Login Setting**, Super Admin only). With demo mode on, every role except the
  Super Admin is read-only. See [Demo Mode](../detailed-documentation/intro.mdx#6-demo-mode-read-only-panels).
- The purchase code is registered under **Settings → System Registration** (`/purchase_code`).
- The **Setup Checklist** is at 100% for every module you sell in.

The full list is in [Step 12: Go-live checklist](../detailed-documentation/getting-started.mdx#step-12-go-live-checklist).

## Maintenance mode

To take the site offline briefly (for example while you update the server), run over SSH:

```bash
php artisan down   # show the maintenance page
php artisan up     # bring the site back
```

To update eMarket itself, use **Settings → System Updater** (`/system_updater`); see
[System Updater](../detailed-documentation/system-maintenance.mdx#3-system-updater-system_updater).
