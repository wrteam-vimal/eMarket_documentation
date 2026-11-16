---
sidebar_position: 9
---

# Login Settings

Choose how customers sign in to the customer app and website, which tabs the panel login page shows, and whether demo mode is on. Click **Settings** in the sidebar, then the **Login Setting** card (group **Selling**). It opens Store Settings on the **Login Setting** pill (`/store_settings?section=login_setting`).

![Login Setting](/img/detailed-documentation/store-settings-login.webp)

## Sign-in Methods

Switches for the sign-in options the customer app and website offer:

- **Phone Login**
- **Google Login**
- **Apple Login**
- **Email Login**

At least one of **Phone Login** or **Google Login** must stay enabled.

## Phone Authentication

- **Phone Auth OTP**: customers sign in with their phone number and a one-time password.
- **Phone Auth Password**: customers sign in with their phone number and a password.
- **Firebase Authentication**: OTPs are sent and checked by Firebase. Set up Firebase first (see [Firebase Settings](./firebase-settings.md)).
- **Custom SMS Gateway OTP based**: shown only while **Phone Auth OTP** or **Phone Auth Password** is on. OTPs are sent through your own SMS gateway (Twilio, see [Twilio Settings](./twilio-settings.md)) and the SMS text comes from the SMS templates.

When **Phone Login** is enabled, **Firebase Authentication** or **Custom SMS Gateway OTP based** must also be enabled, otherwise the section is not saved.

## Panel Login Page

![Panel login page and Demo Mode](/img/admin-panel/login-settings-panel-demo.webp)

- **Seller tab**: shows the Seller tab on the panel login page. The seller login page itself stays available.
- **Delivery Boy tab**: shows the Delivery tab on the panel login page. With both tabs off, the tab bar is hidden.

## Demo Mode

- **Demo Mode**: when on, the apps pre-fill the default login credentials and the panels become read-only for every role except the Super Admin. Keep it off on a live store.
- Only the Super Admin account (user ID 1) can change this switch; for everyone else it is greyed out.
- Demo mode is stored in the `.env` file as `DEMO_MODE`. If the `.env` file is not writable, the other login settings are saved but Demo Mode is not changed. You can also switch it off by setting `DEMO_MODE=0` in `.env`.

More details: [Login Setting and the Demo Mode Toggle](../detailed-documentation/settings.mdx#login-setting-and-the-demo-mode-toggle).

## Configuration Steps

1. Click **Settings** in the sidebar, then the **Login Setting** card.
2. Under **Sign-in methods**, enable the methods you want to offer.
3. If you enable **Phone Login**, also enable **Phone Auth OTP** or **Phone Auth Password**, and choose **Firebase Authentication** or **Custom SMS Gateway OTP based** for sending OTPs.
4. Under **Panel login page**, choose whether the **Seller tab** and **Delivery Boy tab** are shown.
5. As the Super Admin, check that **Demo Mode** is off on a live store.
6. Click **Update**.

## Important Notes

- **Google Login** and **Apple Login** also need the Firebase project and the app-side setup to be completed (see [Firebase Settings](./firebase-settings.md)).
- **Custom SMS Gateway OTP based** only works when SMS Settings are filled in (see [Twilio Settings](./twilio-settings.md)).
- Changes apply to the customer app and website at the next sign-in.

## Troubleshooting

1. **"At least one of phone login or google login must be enabled."**: turn on **Phone Login** or **Google Login**.
2. **"When phone login is enabled, either Firebase Authentication or Custom SMS Gateway OTP Based must be enabled."**: turn on one of the two.
3. **"Only the main admin can change Demo Mode."**: log in as the Super Admin (user ID 1) to change Demo Mode.
4. **Customers do not receive an OTP**: check Firebase Settings (Firebase Authentication) or SMS Settings (Custom SMS Gateway).

## Support

For assistance with login configuration, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
