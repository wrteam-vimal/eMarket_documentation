---
sidebar_position: 4
---

# Server Setup

The admin panel is installed with a web installer at **`https://yourdomain.com/install`**. The same installer is used
on a live server and on [localhost](./localhost-setup.md).

## Before you start

1. Check the [Server Requirements](./server-requirements.md) and [PHP INI settings](./php-ini-settings.md).
2. Create an empty MySQL database (and a database user with full rights on it) in your hosting panel or phpMyAdmin.
3. Upload and extract the eMarket admin panel files on the server, and point the domain's document root to the
   project's **`public`** folder (for example `public_html/emarket/public`).
4. In the project folder, create `.env` from `.env.example` (if it is not there yet) and set:

   ```env
   APP_URL=https://yourdomain.com
   INSTALL_MODE=server
   ```

   `INSTALL_MODE=server` lets the installer create the database tables, default data, API authentication (Passport)
   and the storage link. If `.env` is hidden in your file manager, turn on "Show hidden files".
5. If your package does not include the `vendor` and `public/build` folders, run these in the project folder
   (SSH/terminal):

   ```bash
   composer install --no-dev
   php artisan key:generate
   npm install
   npm run build
   ```

## Installation steps

Open `https://yourdomain.com/install` and go through the five steps.

1. **Welcome**: lists what you need (your Envato purchase code, the MySQL database name, username and password, and an
   email and password for the admin account). Click **Next**.

   ![Installer – Welcome](/img/admin-panel/install-1-welcome.webp)

2. **Requirements**: every PHP extension and folder permission must show a green tick ("Your server meets all
   requirements."). If something is red, enable the extension or fix the folder permission, then try again.

   ![Installer – Server requirements](/img/admin-panel/install-2-requirements.webp)

3. **Purchase Code**: enter your purchase code and click **Next**. This registers the domain you are installing on
   (taken from the browser address). Use **Where do I find my purchase code?** if you need help finding it.

   ![Installer – Purchase code](/img/admin-panel/install-3-purchase-code.webp)

4. **Database**: enter **Database Host** (usually `127.0.0.1` or `localhost`), **Database Port** (`3306`),
   **Database Name**, **Database Username** and **Database Password**, then the **Admin Email** and **Admin Password**
   (at least 6 characters) for the Super Admin account. Click **Next** and wait: the installer creates all tables and
   the default data.

   ![Installer – Database](/img/admin-panel/install-4-database.webp)

5. **Finish**: "Congratulations! Your website is ready." The install link is removed automatically. Open
   `https://yourdomain.com/login` and sign in with the admin email and password from step 4.

After installation, add the cron job from [Server Requirements](./server-requirements.md#other-requirements) and
continue with [Configure eMarket](./configure-egroccer.md).

## Common installation errors

| Error | What to do |
| --- | --- |
| **"Could not connect to the database. Maybe your Database is not available."** | Check host, port, name, username and password. Make sure the user is assigned to the database with all privileges. Some hosts require a strong database password (upper- and lower-case letters, a number and `@` or `_`). |
| **The installer explains a wrong port** | Use MySQL's port (usually `3306`), not your website's port. |
| **"Installation failed: table "admins" was not created"** | Add `INSTALL_MODE=server` to `.env` and run the Database step again. |
| **Images do not show after installation** | `symlink` is disabled on the server. Remove it from `disable_functions` (in your hosting panel's PHP settings) and run `php artisan storage:link`. |
| **"Could not reach the purchase code validator"** | The server needs outgoing internet access during installation. |
| **"Vite manifest not found"** | Build the front end with `npm install && npm run build`, or upload the `public/build` folder from the package. |
| **"Application is already installed"** | The installer runs only once. Log in at `/login`. |

![Disable symlink in disable_functions](/img/admin-panel/disable_sys_link.webp)
