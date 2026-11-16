---
sidebar_position: 11
---

# Twilio Setting

eMarket sends SMS messages (OTP codes and order updates) through **Twilio**. The Twilio credentials are entered on the **SMS Gateways & Methods Settings** page: **Settings → SMS Settings** (card in the **Communication** group of the Settings hub, route `/sms-settings`, permission `sms_settings`). The text of each SMS is edited on **Settings → SMS Templates**.

## 1. Get your Twilio credentials

1. Create an account at [Twilio](https://www.twilio.com) (or sign in) and open the [Twilio Console](https://console.twilio.com/).
2. On the console dashboard, under **Account Info**, copy the **Account SID** and the **Auth Token**.
3. Buy or choose a Twilio phone number that can send SMS, and copy it with its country code (e.g. `+14155550123`).

![Twilio Dashboard](/img/admin-panel/twilio_dashboard.webp)

## 2. Enter them in the admin panel

1. Open **Settings → SMS Settings**. The page title is **SMS Gateways & Methods Settings**.
2. Turn on **Twilio [ Enable / Disable ]**. The three fields appear.
3. Fill in:

| Field | What to enter |
| :--- | :--- |
| **Twilio SID** | Account SID from the Twilio console (starts with `AC`). |
| **Twilio Auth Token** | Auth Token from the Twilio console. |
| **Twilio Phone Number** | The Twilio number SMS are sent from, with country code. |

4. Click **Update**.

![SMS Gateways & Methods Settings](/img/detailed-documentation/sms-settings.webp)

## 3. Send OTP codes through Twilio

Twilio sends order SMS as soon as it is enabled. To also send **login OTP codes** through Twilio instead of Firebase:

1. Open **Settings → Login Setting** (`/store_settings?section=login_setting`).
2. Under *Phone authentication*, turn on **Phone Auth OTP** or **Phone Auth Password**, then turn on **Custom SMS Gateway OTP based** (it appears only while one of those two is on).
3. Click **Update**.

See [Login Setting](../detailed-documentation/settings.mdx#login-setting-and-the-demo-mode-toggle) for every switch on that section.

## 4. SMS Templates

Open **Settings → SMS Templates** (page **Manage SMS Templates**, route `/sms-templates`) to change the text of the SMS sent on order events.

![SMS Templates](/img/detailed-documentation/sms-templates.webp)

- The list shows **ID**, **Type**, **Message**, **Last Updated** and **Actions** (edit and **Send test to me**).
- There are 11 types, from `customer_place_order` to `customer_order_reject_return_request` (placed, payment pending, received, processed, shipped, out for delivery, delivered, cancelled, and the return request steps).
- Click edit to change the **Title** and **Message**. Placeholders are written in square brackets, e.g. `[Customer Name]`, `[Order ID]`, `[Store Name]`. Keep them spelled exactly as in the original text.
- Click **Send test to me**, enter your number with country code (e.g. `+919876543210`) and send. The saved message arrives with sample values and **[TEST]** in front.

Which order statuses actually send an SMS is chosen in **Account Settings** (`/settings`, Order Mail Settings). More details: [SMS Templates](../detailed-documentation/communications.mdx#6-sms-templates-sms-templates).

## Troubleshooting

- **"Twilio SID is required when Twilio is enabled."** – with Twilio on, all three fields are required.
- **Twilio cannot be switched off** while phone login sends OTP through the SMS gateway and Firebase OTP is off. Turn on **Firebase Authentication** in Login Setting first.
- **"SMS is not set up yet"** on a test – the Twilio SID, Auth Token or Phone Number is missing.
- **"Twilio did not accept the message"** – usually a wrong number format, or a Twilio **trial** account sending to a number that is not verified in Twilio.
- Check your Twilio balance and the Twilio console **Monitor → Logs → Messaging** for delivery errors.

More details: [SMS Settings](../detailed-documentation/settings.mdx#7-sms-settings-sms-settings) in the detailed documentation.
