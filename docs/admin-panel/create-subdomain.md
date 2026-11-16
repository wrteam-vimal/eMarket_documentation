---
sidebar_position: 2
---

# Create Subdomain

To keep the admin panel apart from the customer website, run it on a subdomain such as `admin.yourdomain.com`. The main
domain `yourdomain.com` then stays free for the public website, and the subdomain serves only the admin panel (and the
seller and delivery boy panels, which use the same installation).

## Steps

1. In your hosting control panel (cPanel, hPanel, Plesk, etc.) open **Domains → Subdomains** and create the subdomain,
   for example `admin`.
2. Set the subdomain's **document root** to the `public` folder of the eMarket admin panel, for example
   `/home/youruser/emarket/public`. Do not point it at the project root.
3. Enable **SSL** (HTTPS) for the subdomain, for example with the free Let's Encrypt certificate most hosts offer.
4. Wait for DNS to update (usually a few minutes, up to 24 hours), then open `https://admin.yourdomain.com/install` to
   run the web installer. See [Server Setup](./server-setup.md).
5. Make sure `APP_URL` in the `.env` file is the subdomain address, for example `APP_URL=https://admin.yourdomain.com`.
   If it does not match, **Settings → System Status** shows an **App URL** warning and image links can break.

:::tip
Use the subdomain address everywhere the apps and website need the panel's URL (the admin/API base URL in the Flutter
apps and in the website's environment variables).
:::

## Hosting references

- [Hostinger: how to create and delete subdomains](https://support.hostinger.com/en/articles/1583405-how-to-create-and-delete-subdomains)
