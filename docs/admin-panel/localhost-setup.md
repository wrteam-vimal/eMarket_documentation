---
sidebar_position: 3
---

# Localhost Setup

You can install eMarket on your own computer for development and testing. The admin panel installs through the same
web installer as on a live server: once the tools below are installed and the project is prepared, open
**`http://localhost/install`** (or `http://127.0.0.1:8000/install`) and follow the same wizard steps as the
[Server Setup](./server-setup.md).

:::info In short
1. Install **PHP 8.3+**, **Composer**, **Node.js + npm**, **MySQL** and **phpMyAdmin** (plus a web server, or use `php artisan serve`).
2. Create an empty database in phpMyAdmin.
3. Prepare the project: `.env`, `composer install`, `php artisan key:generate`, `npm install`, `npm run build`.
4. Open `/install` in your browser and complete the wizard (Requirements → Purchase Code → Database → Finish).
:::

## 1. Install the required software

Install these before you open the `/install` route. The installer runs inside the eMarket app itself, so it cannot
load until PHP, the Composer packages and the built front end are in place.

| Software | Version | Why it is needed |
| --- | --- | --- |
| **PHP** | 8.3 or newer | Runs the eMarket admin panel (Laravel 13). |
| **Composer** | 2.x | Installs the PHP packages into the `vendor` folder. |
| **Node.js + npm** | Node 20.19+ or 22.12+ (npm comes with Node) | Builds the admin panel front end into `public/build`. |
| **MySQL** (or MariaDB) | MySQL 5.7+ / 8.x, or MariaDB 10.3+ | Stores all eMarket data. |
| **phpMyAdmin** | any recent version | Web tool to create the database and look at the data. |
| **Web server** | Apache (XAMPP/MAMP/Laragon) or `php artisan serve` | Serves the site at `http://localhost`. |

**Required PHP extensions:** `bcmath`, `ctype`, `curl`, `dom`, `fileinfo`, `gd`, `json`, `mbstring`, `openssl`,
`pdo_mysql`, `tokenizer`, `xml`, `zip`. Check them with `php -m`. On XAMPP for Windows, enable a missing one by
removing the `;` in front of its `extension=` line in `php.ini` and restarting Apache. Also apply the
[PHP INI settings](./php-ini-settings.md).

### Quick install per operating system

- **Windows**: install [XAMPP](https://www.apachefriends.org/download.html) with PHP 8.3 or newer. It includes Apache,
  PHP, MySQL (MariaDB) and phpMyAdmin (`http://localhost/phpmyadmin`). Then install
  [Composer](https://getcomposer.org/download/) (point it to `C:\xampp\php\php.exe`) and
  [Node.js LTS](https://nodejs.org/). Laragon is a good alternative that bundles the same tools.
- **macOS**: install [Homebrew](https://brew.sh), then run
  `brew install php composer node mysql phpmyadmin` and start MySQL with `brew services start mysql`.
  MAMP or Laravel Herd are alternatives that include PHP and MySQL.
- **Linux (Ubuntu/Debian)**: install PHP 8.3 with the extensions above
  (for example `php8.3 php8.3-{bcmath,curl,gd,mbstring,mysql,xml,zip}`), `mysql-server`, `phpmyadmin`,
  [Composer](https://getcomposer.org/download/) and Node.js 22 (for example from NodeSource or `nvm`).

Check everything from a terminal:

```bash
php -v          # PHP 8.3.x or newer
composer -V     # Composer 2.x
node -v         # v20.19+ or v22.12+
npm -v
mysql --version
```

:::tip Internet connection
Keep the computer online during installation: the **Purchase Code** step validates your code with the eMarket
licence server.
:::

## 2. Create the database

1. Start MySQL (and Apache, if you use XAMPP/MAMP).
2. Open phpMyAdmin (for example `http://localhost/phpmyadmin`).
3. Click **New**, enter a database name such as `emarket`, choose the collation **utf8mb4_unicode_ci** and click
   **Create**. Leave the database empty; the installer creates all tables.
4. Note the MySQL **host** (`127.0.0.1`), **port** (`3306`), **username** and **password**. XAMPP's default user is
   `root` with an empty password.

:::caution MySQL port vs. web server port
The database port is MySQL's port (usually **3306**), not the port in the phpMyAdmin address (for example 80 or
8080, which is the web server).
:::

## 3. Prepare the project

1. Copy the eMarket admin panel code to a folder, for example `C:\xampp\htdocs\emarket` (Windows) or
   `~/Sites/emarket` (macOS/Linux). Make sure hidden files such as `.env.example` and `.htaccess` are copied too.
2. In that folder create the environment file from the template:

   ```bash
   cp .env.example .env        # Windows: copy .env.example .env
   ```

3. Open `.env` and set:

   ```env
   APP_URL=http://localhost          # or http://127.0.0.1:8000 if you use php artisan serve
   INSTALL_MODE=server
   ```

   `INSTALL_MODE=server` lets the installer create the tables, seed the default data, set up API authentication
   (Passport) and the storage link for you. Without it the Database step stops with
   *"Installation failed: table "admins" was not created"*. You don't need to enter the database details in
   `.env`; the installer writes them.

4. Install the packages and build the front end:

   ```bash
   composer install
   php artisan key:generate
   npm install
   npm run build
   ```

## 4. Start the site and open /install

Use **one** of these:

- **XAMPP / MAMP / Laragon (Apache)**: point the site's document root to the project's **`public`** folder
  (for example `C:/xampp/htdocs/emarket/public` in Apache's `httpd.conf` / a virtual host), restart Apache and open
  **`http://localhost/install`**.
- **PHP's own server**: in the project folder run

  ```bash
  php artisan serve
  ```

  and open **`http://127.0.0.1:8000/install`**.

## 5. Complete the installation wizard

The wizard is the same as on a live server (see [Server Setup](./server-setup.md) for screenshots):

1. **Welcome**: click **Next**.
2. **Requirements**: the PHP version, extensions and folder permissions must all be green. Fix anything red (enable
   the extension or make `storage`, `bootstrap/cache` and `.env` writable) and try again.
3. **Purchase Code**: enter your purchase code. This registers the address you opened the installer from
   (for example `http://localhost`).
4. **Database**: enter **Database Host** `127.0.0.1`, **Database Port** `3306`, **Database Name** `emarket`, your
   MySQL **Username** and **Password**, and the **Admin Email** and **Admin Password** (at least 6 characters) for
   the Super Admin account. Click **Next** and wait while the tables and default data are created.
5. **Finish**: "Congratulations!" means the panel is installed. Open `/login` (for example
   `http://localhost/login`) and sign in with the admin email and password you just entered.

After installation, continue with [Configure eMarket](./configure-egroccer.md) or the
[Getting Started tutorial](../detailed-documentation/getting-started.mdx).

:::note Scheduled tasks
Seller earnings, scheduled home pages, auto-assign time-outs and log clean-up run on Laravel's scheduler. On a
local machine keep it running in a separate terminal with `php artisan schedule:work` while you test those features.
:::

## Troubleshooting

| Problem | Fix |
| --- | --- |
| **"Vite manifest not found"** or a blank page at `/install` | The front end is not built. Run `npm install` and `npm run build`. |
| **"No application encryption key has been specified"** | Run `php artisan key:generate`. |
| **`composer install` fails with "requires ext-gd / ext-zip"** | Enable the missing PHP extension in `php.ini`, restart, and run `composer install` again. |
| **"Could not connect to the database"** or a port error | Check that MySQL is running and use port `3306` (not the phpMyAdmin/web port). Check the username and password in phpMyAdmin. |
| **"Installation failed: table "admins" was not created"** | Add `INSTALL_MODE=server` to `.env`, run `php artisan config:clear`, and run the Database step again. |
| **"Could not reach the purchase code validator"** | Connect to the internet and retry the Purchase Code step. |
| **"Application is already installed"** | The installer only runs once (the file `storage/installed` marks it). Use the existing login, or reinstall with a fresh empty database. |
| **Images do not show** | Run `php artisan storage:link`. If it says the link exists, delete `public/storage` and run it again. |
| **Composer runs out of memory** | `COMPOSER_MEMORY_LIMIT=-1 composer install` |
| **Permission errors (macOS/Linux)** | `chmod -R 775 storage bootstrap/cache` |

## Development tips

- Show detailed errors while developing: set `APP_DEBUG=true` in `.env` (never on a live server).
- Clear cached settings after changing `.env`: `php artisan config:clear` and `php artisan cache:clear`.
- Rebuild the front end automatically while you edit Vue files: `npm run watch`.
- Application logs are in `storage/logs/` and on the panel's **Logs** page.
