# WP Migrate DB PRO Installer

[![Packagist](https://img.shields.io/packagist/v/philippbaschke/acf-pro-installer.svg?maxAge=3600)](https://packagist.org/packages/philippbaschke/acf-pro-installer)
[![Packagist](https://img.shields.io/packagist/l/philippbaschke/acf-pro-installer.svg?maxAge=2592000)](https://github.com/PhilippBaschke/acf-pro-installer/blob/master/LICENSE)
[![Travis](https://img.shields.io/travis/PhilippBaschke/acf-pro-installer.svg?maxAge=3600)](https://travis-ci.org/PhilippBaschke/acf-pro-installer)
[![Coveralls](https://img.shields.io/coveralls/PhilippBaschke/acf-pro-installer.svg?maxAge=3600)](https://coveralls.io/github/PhilippBaschke/acf-pro-installer)

A composer plugin that makes installing [WPM PRO] with [composer] easier.

It reads your :key: WPM PRO key from the **environment** or a **.env file**.

[WPM PRO]: hhttps://deliciousbrains.com/wp-migrate-db-pro/
[composer]: https://github.com/composer/composer

## Usage

**1. Add the package repository to the [`repositories`][composer-repositories] field in `composer.json` 
   (based on this [gist][package-gist]):**

```json
{
      "type": "package",
      "package": {
        "name": "deliciousbrains/wp-migrate-db-pro",
        "type": "wordpress-plugin",
        "version": "1.8.1",
        "dist": {
          "type": "zip",
          "url": "https://deliciousbrains.com/dl/wp-migrate-db-pro-latest.zip?"
        },
        "require": {
          "igniteonline/wpm-pro-installer": "^1.0.2",
          "composer/installers": "^1.0"
        }
      }
    },
    {
      "type": "package",
      "package": {
        "name": "deliciousbrains/wp-migrate-db-pro-media-files",
        "type": "wordpress-plugin",
        "version": "1.4.9",
        "dist": {
          "type": "zip",
          "url": "https://deliciousbrains.com/dl/wp-migrate-db-pro-media-files-latest.zip?"
        },
        "require": {
          "igniteonline/wpm-pro-installer": "^1.0.2",
          "composer/installers": "^1.0"
        }
      }
    }
```
Replace `"version": "*.*.*"` with your desired version.

**2. Make your WPM PRO key available**

Set the environment variable **`WPM_PRO_KEY`** to your [WPM PRO key][wpm-account].

Alternatively you can add an entry to your **`.env`** file:

```ini
# .env (same directory as composer.json)
WPM_PRO_KEY=Your-Key-Here
```

**3. Require WPM PRO**

```sh
composer require deliciousbrains/wp-migrate-db-pro:*
```

**4. Require WPM PRO Media Files**

```sh
composer require deliciousbrains/wp-migrate-db-pro-media-files:*
```

Unfortunately, DeliciousBrains is not exposing a way of retrieving different versions of their plugin.
Because of this, changing the version in the package section will download the latest version regardless.
You have to manually change the version in your `composer.json` file to manually trigger composer to download a new package.
[composer-repositories]: https://getcomposer.org/doc/04-schema.md#repositories
[composer-versions]: https://getcomposer.org/doc/articles/versions.md
[package-gist]: https://gist.github.com/dmalatesta/4fae4490caef712a51bf
[wpm-account]: https://deliciousbrains.com/signin/
