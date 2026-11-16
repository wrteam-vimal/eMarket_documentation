---
sidebar_position: 1
---

# Server Requirements

Make sure your server (or local computer) meets these requirements before you install the eMarket admin panel.

## Software

| Software | Version | Notes |
| --- | --- | --- |
| **PHP** | 8.3 or newer | The admin panel runs on Laravel 13. |
| **MySQL** or **MariaDB** | MySQL 5.7+ / 8.x, or MariaDB 10.3+ | Database with `utf8mb4` support. |
| **Web server** | Apache (with `mod_rewrite`) or Nginx | Point the domain's document root to the project's `public` folder. |
| **Composer** | 2.x | Needed if the `vendor` folder is not included in your package, and for updates. |
| **Node.js + npm** | Node 20.19+ or 22.12+ | Needed to build the admin panel front end (`npm run build`) if `public/build` is not included. |

## PHP extensions

- BCMath
- Ctype
- cURL
- DOM
- Fileinfo
- GD
- JSON
- Mbstring
- OpenSSL
- PDO (with the MySQL driver, `pdo_mysql`)
- Tokenizer
- XML
- Zip

Also apply the recommended [PHP INI settings](./php-ini-settings.md).

## Other requirements

- **Writable folders**: `storage/`, `bootstrap/cache/` and the `.env` file must be writable by the web server. The
  installer's **Requirements** step checks this.
- **`symlink()` allowed**: the installer creates the `public/storage` link for uploaded images. If your host lists
  `symlink` under `disable_functions`, remove it there.
- **Cron job**: Laravel's scheduler must run every minute after installation
  (`* * * * * cd /path/to/emarket && php artisan schedule:run >> /dev/null 2>&1`). It credits seller earnings,
  switches scheduled home pages, times out auto-assign offers and prunes old logs.
- **Internet access** during installation: the **Purchase Code** step validates your code with the eMarket licence server.

## Local computer

To install on your own computer for development or testing, see [Localhost Setup](./localhost-setup.md). It lists how to
install PHP, Composer, Node.js, MySQL and phpMyAdmin on Windows, macOS and Linux.
