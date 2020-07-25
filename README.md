# PayWithBank3D PHP

[![Latest Version on Packagist](https://img.shields.io/packagist/v/parkwayprojects/paywithbank3d-php.svg?style=flat-square)](https://packagist.org/packages/parkwayprojects/paywithbank3d-php)
[![Build Status](https://img.shields.io/travis/parkwayprojects/paywithbank3d-php/master.svg?style=flat-square)](https://travis-ci.org/parkwayprojects/paywithbank3d-php)
[![Quality Score](https://img.shields.io/scrutinizer/g/parkwayprojects/paywithbank3d-php.svg?style=flat-square)](https://scrutinizer-ci.com/g/parkwayprojects/paywithbank3d-php)
[![Total Downloads](https://img.shields.io/packagist/dt/parkwayprojects/paywithbank3d-php.svg?style=flat-square)](https://packagist.org/packages/parkwayprojects/paywithbank3d-php)

PayWithBank3D PHP is a library for using the PayWithBank3D API from PHP.

## Installation

You can install the package via composer:

```bash
composer require parkwayprojects/paywithbank3d-php
```

## Usage
First you initialize the library with your  public key, secret key and option(live or staging)

``` php
$bank3d = (new PayWithBank3D('Secret Key', 'Public Key', 'Options'))
```

## Transaction
initialize a transaction

```php
$bank3d->addBody('reference', time())
                   ->addBody('amount', '100000')
                   ->addBody('currencyCode', 'NGN')
                   ->addBody('customer', [
                       'name' => 'Edward Paul',
                       'email' => 'infinitypaul@live.com',
                       'phone' => '070064566'
                   ])
                   ->addBody('returnUrl', 'https://infinitypaul.com')
                   ->addBody('color', '#FF0000')
                   ->addBody('metadata', [
                       'orderId'=> '1234'
                   ]);
$bank3d->getAuthorizationUrl()->redirectNow();
```
This will automatically take you to secure payment page on PayWithBank3D, Once payment is completed, you are redirected to the url you specify in the returnURL

## Verify Transaction

```php
$bank3d->verify();
```
This return the status of the payment you just made and some other values of the transaction

### Testing

``` bash
composer test
```



## Credits

- [Paul Edward](https://github.com/infinitypaul)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

