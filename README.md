# PHP TURNSTILE

## Description
API Implementation of [CloudFlare turnstile](https://www.cloudflare.com/products/turnstile/) for PHP

## Installation

```bash
composer install fluxsoft/php-turnstile
```

## Usage
Here's an example of usage:

```php
// require vendor
use FluxSoft\Turnstile\Turnstile;

$turnstile = new Turnstile('secret key');
$verifyResponse = $turnstile->verify($_POST['cf-turnstile-response'], $_SERVER['REMOTE_ADDR']);

if ($verifyResponse->success) {
    // successfully verified captcha resolving
} else {
    if ($verifyResponse->hasErrors()) {
        foreach ($verifyResponse->errorCodes as $errorCode) {
            echo $errorCode . '\n'; 
        }
    } else {
        // unknown reason of failure resolving of captcha
    }
}
```

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <form action="" method="POST">
            <div class="cf-turnstile" data-sitekey="YOUR_PUBLIC_SITE_KEY"></div> 
            <button type="submit">check</button>
        </form>
        <script src="https://challenges.cloudflare.com/turnstile/v0/api.js" async defer></script>
    </body>
</html>
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.