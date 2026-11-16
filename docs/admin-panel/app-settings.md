---
sidebar_position: 14
---

# App Settings

Put the customer, seller and delivery boy apps into maintenance, set the store links and control which app versions must update. Click **Settings** in the sidebar, then the **App Setting** card (group **Apps & Website**). It opens Store Settings on the **App Setting** pill (`/store_settings?section=app_setting`).

![App Setting](/img/admin-panel/app_settings.webp)

## App Availability (maintenance mode)

"In this mode you can set your app in Maintenance and that Application will not work till not disabled from here."

| Switch | Extra field when on | Effect |
| :--- | :--- | :--- |
| **Customer App** | **Customer App Remark** | Puts the customer app into maintenance. |
| **Seller App** | **Seller App Remark** | Puts the seller app into maintenance. |
| **Delivery Boy App** | **Delivery Boy App Remark** | Puts the delivery boy app into maintenance. |

The remark is the message users see while the app is in maintenance. It can be entered per language (with **Translate Empty Fields** / **Translate & Overwrite**). Turn the switch off again to bring the app back.

## Store Links

- **Play Store Url**: link to your app on Google Play.
- **App Store Url**: link to your app on the Apple App Store.

## Android Version Control

- **Android Version System Status**: turns version checking on for the Android app. The fields below appear when it is on.
- **Android Required Force Update**: when on, users on an older version must update before they can continue.
- **Android Current Version Of App**: the latest version number you published, for example `1.0.5`.

## iOS Version Control

- **IOS Version System Status**
- **IOS Required Force Update**
- **IOS Current Version Of App**

These work the same way as the Android fields.

## Configuration Steps

1. Click **Settings** in the sidebar, then the **App Setting** card.
2. Enter the **Play Store Url** and **App Store Url**.
3. After you publish a new app version, turn on **Android Version System Status** / **IOS Version System Status**, enter the new version in **Current Version Of App**, and turn on **Required Force Update** if old versions must not be used.
4. To put an app into maintenance, turn on its switch under **App availability** and write the remark users should see.
5. Click **Update**.

## Important Notes

- Maintenance mode stops the app for all its users until you turn the switch off. Use it only during real maintenance.
- Enter the version exactly as it is set in the app build, or every user may be asked to update.
- App-side setup (package name, Firebase files, API URL) is done in the app source code, not here. See the app documentation.
- Other app-related settings are elsewhere: sign-in methods in [Login Settings](./login-settings.md), map keys in **Address Setting** ([Store Settings](./store-settings.md)), push notifications in [Firebase Settings](./firebase-settings.md), deep links in [Deeplink Settings](./deeplink-settings.md), and app colours in [Theme Settings](./theme-settings.md).

## Troubleshooting

1. **App shows the maintenance message**: check that the matching switch under **App availability** is off and click **Update**.
2. **Users keep being asked to update**: check that **Current Version Of App** matches the version in the store, or turn **Required Force Update** off.

## Support

For assistance with app settings, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
