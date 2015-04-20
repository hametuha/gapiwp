# gapiwp

Google API Library wrapper for WordPress.


## How to use

### Install

Install this libary in your theme or plugin via Composer.

To do so, you need write `repositories` section like below.

```json
{
  "name": "your-name/your-theme",
  "description": "WordPress theme",
  "repositories": [
    {
      "type": "vcs",
      "url": "git@github.com:hametuha/gapiwp.git"
    }
  ],
  "require": {
    "hametuha/gapiwp.git": "1.0.x"
  },
}
```

Now you can execute `composer install`. [Google API Client](https://github.com/google/google-api-php-client) is a bit bigger library, `--no-dev` option is recommended.

```
composer install --no-dev
```

### Load library

In your entry point( theme's functions.php or plugin's base file), initialize library.

```php
// Load auto loader.
include __DIR__.'/vendor/autoload.php';
// Initialize library
\Hametuha\GapiWP\Loader::load();
```

Now you can see setting screen on admin panel. Go to **Setting > Analytics Setting**.

After that, you can call api client library anywhere in your site.

```php
// Get Google Analytics client.
$ga = \Hametuha\GapiWP\Loader::analytics();
// Get top 100 pave views of this year.
$result = $ga->fetch('2015-01-01', date_i18n('Y-m-d'), 'ga:pageviews', array(
		'max-results' => 100,
		'dimensions'  => 'ga:pagePath',
		'sort' => '-ga:pageviews'
	));
	var_dump($result);
	exit;
```

## Lisence

Released under MIT lisence. See LISENCE.md.