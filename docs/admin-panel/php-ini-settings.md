---
sidebar_position: 2
---

# PHP INI Settings

Set these values in your server's `php.ini` (or your hosting panel's PHP options) before you install eMarket. They let
the panel upload images and import files in bulk, and give longer jobs such as the installer's database setup and the
**System Updater** enough time and memory to finish.

## Recommended values

```ini
memory_limit = 512M
upload_max_filesize = 128M
post_max_size = 128M
max_execution_time = 300
max_input_time = 300
```

| Setting | Value | Why |
| --- | --- | --- |
| `memory_limit` | `512M` | Bulk uploads, reports, exports and updates load a lot of data at once. |
| `upload_max_filesize` | `128M` | Largest single file you can upload (media, bulk upload sheets, language files). |
| `post_max_size` | `128M` | Largest whole form submission. Keep it **equal to or larger than** `upload_max_filesize`, because the media library can upload several files in one go. |
| `max_execution_time` | `300` | Seconds a request may run; the installer and the System Updater need more than the usual 30. |
| `max_input_time` | `300` | Seconds PHP may spend reading an upload. |

Higher values are fine. Lower values can make large uploads or bulk imports fail, often with a "failed to upload" message or no clear error.

:::note
Neither the installer nor **System Status** reads these values. The installer's **Server requirements** step checks the
PHP version, the PHP extensions and the folder permissions; **System Status** (`/system_status`) shows the PHP version
(8.2 or newer passes, but eMarket needs **8.3** or newer, see [Server Requirements](./server-requirements.md)). Check
the values yourself as shown below.
:::

Also make sure `symlink` is **not** listed in `disable_functions`; the installer needs it to create the `public/storage`
link for uploaded images.

## Where to change them

- **cPanel**: **Software → Select PHP Version → Options**, or **MultiPHP INI Editor**. Pick the domain or subdomain the
  panel runs on.
- **Hostinger (hPanel)** and similar: **Advanced → PHP Configuration → PHP Options**.
- **Your own server or computer**: edit the `php.ini` file that PHP loads, then restart the web server (Apache,
  Nginx + PHP-FPM). Run `php --ini` to see which file is loaded. The command-line PHP and the web server's PHP can use
  different `php.ini` files; change the web server's one (and the CLI one too if you run `php artisan` commands with
  large imports). For a local setup see [Localhost Setup](./localhost-setup.md).

## Check the values

Create a temporary file `info.php` in the `public` folder with `<?php phpinfo();` in it, open
`https://yourdomain.com/info.php`, search for each setting in the **Local Value** column, and **delete the file** when
you are done.
