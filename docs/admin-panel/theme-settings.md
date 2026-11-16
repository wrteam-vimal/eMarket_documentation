---
sidebar_position: 10
---

# Theme Settings

Set the brand colours of the website, the customer app and the admin panel. Open **Theme Settings** in the sidebar (module section, below Withdrawal Requests), route `/theme-settings`, permission `theme_settings`.

The website and the customer app download the palette from the server, so changing a colour here does not require rebuilding or resubmitting the app.

![Theme Settings](/img/detailed-documentation/theme-settings.webp)

Each colour is generated from one seed colour: every card has a colour swatch (picker), a hex field and the generated shade row (50 to 950), and the panel previews the change while you pick.

## Admin Panel Colours

"Use each module's theme colours in the admin panel? Applies to every module."

- **Yes, module colours**: the admin panel follows the colours of the module selected in the header.
- **No, own colours**: the admin panel keeps its own colours in every module. Two cards appear: **Admin primary colour** and **Admin neutral colour**.

Click **Save** in this card.

![Theme Settings with own admin colours](/img/detailed-documentation/theme-settings-own-colours.webp)

With own colours, a note explains that the module colours below still apply to the website and the apps.

## Module Colours (per module)

Primary and Neutral colours are stored **per module**. Select the module in the panel header (Grocery, Pharmacy, Ecommerce, Food Delivery, and so on) before editing.

- **Primary Color**: "Used for main brand elements and actions" (buttons, links, active menu items).
- **Neutral Color**: "Used for text, backgrounds, borders, and neutral elements". A colour that is too light is refused, because borders and dividers would become invisible.

A module that has no colours of its own shows the default module's colours, with the note "This module uses the default module's colours. Change them and save to give it its own."

Click **Save** in this card.

## Status Colors (default module only)

The **Status Colors** section ("Used to represent different states and alerts in the system") is shown only while the **default module** is selected (set in [Modules](./modules.md)). These colours are shared by all modules.

- **Success Color**: success messages and valid states.
- **Error Color**: error messages and critical states.
- **Warning Color**: warning messages and alerts.
- **Info Color**: information messages and highlights.

Each has its own **Reset to Default** (asks for confirmation) and **Save** button.

## Configuration Steps

1. Select the module in the panel header.
2. Open **Theme Settings**.
3. Enter the **Primary Color** and **Neutral Color** hex values (or use the swatch) and click **Save** in the module colours card.
4. Repeat for every module that needs its own brand colour.
5. Select the default module to set the **Status Colors**, and click **Save** per colour.
6. In **Admin panel colours**, choose **Yes, module colours** or **No, own colours** (then set the two admin colours) and click **Save**.

More details and examples: [Theme Settings in the detailed documentation](../detailed-documentation/settings.mdx#11-theme-settings-theme-settings).

## Important Notes

- Changes apply to the website and customer app after save. The customer app picks up the new palette on its next launch and keeps the last palette for offline use.
- Light and dark mode share the same palette; they are not set separately.
- You enter one seed colour per card; the system generates the whole shade range from it.
- Use colours with enough contrast for readable text.

## Support

For assistance with theme configuration, contact our support team:

- **Email:** support@wrteam.in
- **Website:** [https://wrteam.in](https://wrteam.in)
- **Support Hours:** Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)
