---
sidebar_position: 16
---

# Need Support?

If something does not work as described in this documentation, the WRTeam support team will help you.

## Contact

Head of Customer Support: Vrajeshwari Parmar  
Teams: [Vrajeshwari Parmar](https://teams.live.com/l/invite/FDAoEdGkqMcYb5JLg?v=g1)

- **Email:** [support@wrteam.in](mailto:support@wrteam.in)
- **Website:** [https://wrteam.in](https://wrteam.in)

Support hours: **Monday to Friday, 9:00 AM to 6:00 PM IST (GMT +5:30)**. We are a team based in India. We usually reply
to every question within 24 hours (working days).

More ways to reach WRTeam are on the [Contact Us](../contact.md) page.

## Before you contact support

Many problems can be found in the panel itself:

1. **Settings → System Status** (`/system_status`): checks the scheduler, queue, storage link, disk space, writable
   folders, mail, SMS, Firebase, PHP version, environment and `APP_URL`, with a fix link where possible. See
   [System Status](../detailed-documentation/system-maintenance.mdx#1-system-status-system_status).
2. **Settings → Setup Checklist** (`/setup_checklist`): shows which required settings or data are still missing for
   each module.
3. **Settings → Logs** (`/logs`, Super Admin only): the application log per day, with errors such as a failed SMS or
   payment. See [Logs](../detailed-documentation/system-maintenance.mdx#2-logs-logs).
4. **Settings → Clear System Cache**: try this first when a saved setting or an uploaded translation does not show up.
5. Check the FAQs: [Admin Panel FAQs](../detailed-documentation/admin-faqs.mdx).

## What to include in your message

- Your **purchase code** (the one registered under **Settings → System Registration**).
- The eMarket **version** (shown on **Settings → System Updater**).
- Which part is affected: admin panel, seller or delivery boy panel, website, or which app.
- What you did, what you expected, and what happened instead (steps to reproduce).
- Screenshots or a screen recording, and any error message.
- The matching log lines from **Settings → Logs** (or `storage/logs/laravel-YYYY-MM-DD.log` on the server).
- Server details if the problem is with installation: hosting type, PHP version, and the
  [System Status](../detailed-documentation/system-maintenance.mdx#1-system-status-system_status) results.

:::caution
Never send passwords or live payment keys in a public place. If support needs access to your server or panel, share it
privately and change the passwords afterwards.
:::
