---
sidebar_position: 15
---

# Deeplink Settings

The **Deeplink Schema** tells your website which app to open when a customer taps **Open in app**, and the apps use it to open the right in-app screen. It must be the same value as the scheme built into your customer app.

![Deeplink Settings](/img/detailed-documentation/deeplink-settings.webp)

1. In the admin panel, go to **Settings → Deeplink Settings** (card in the **Apps & Website** group of the Settings hub, route `/deeplink-settings`, permission `deeplink_settings`).
2. In **Deeplink Schema**, enter your app's scheme, for example `mystore`: lowercase letters, numbers, `+`, `.` or `-`, starting with a letter, without `://` and without spaces. It must match `DEEP_LINK_SCHEME` in the customer app's `config/deep_link.xcconfig`. See [Deep Links](../flutter-app/deep-links.md).
3. Click **Update**.

The field is required: an empty value, or one with capitals, spaces or `://`, is refused with "Deeplink schema must be lowercase, start with a letter and contain no "://" or spaces."

:::caution
Changing the scheme here alone breaks the app links until the apps are rebuilt with the same scheme. Change both together.
:::

More details: [Deeplink Settings](../detailed-documentation/settings.mdx#9-deeplink-settings-deeplink-settings) in the detailed documentation.
