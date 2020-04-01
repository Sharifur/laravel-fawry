Laravel Fawry
==============

[![Latest Stable Version](https://poser.pugx.org/maherelgamil/laravel-fawry/version)](https://packagist.org/packages/maherelgamil/laravel-fawry)
[![Total Downloads](https://poser.pugx.org/maherelgamil/laravel-fawry/downloads)](https://packagist.org/packages/v/laravel-fawry)
[![Latest Unstable Version](https://poser.pugx.org/maherelgamil/laravel-fawry/v/unstable)](//packagist.org/packages/maherelgamil/laravel-fawry)
[![License](https://poser.pugx.org/maherelgamil/laravel-fawry/license)](https://packagist.org/packages/maherelgamil/laravel-fawry)
[![StyleCI](https://styleci.io/repos/61923982/shield)](https://styleci.io/repos/61923982)

[AtFawry](https://www.atfawry.com/) interface for laravel

# Installation

Install via composer  
```bash
composer require maherelgamil/laravel-fawry

```

And then publish config

```bash
php artisan vendor:publish --tag="fawry-config"
```

Add `merchant_code` , `security_key` that's provided from Atfawry account

Now, Run migration

```bash
php artisan migrate
```

# Usage

## Create Card Token:

```php
// Get user
$user = App\User::find(1);

$tokenResponse = Fawry::createCardToken($cardNumber, $expiryYear, $expiryMonth, $cvv, $user);
```

## Get List Of Customer Tokens:

```php
// Get user
$user = App\User::find(1);

Fawry::listCustomerTokens($user);
```

## Delete Customer Token
```php
// Get user
$user = App\User::find(1);

Fawry::deleteCardToken($user);
```

## Charge:

### Charge Via Card:
```php
// Get user
$user = App\User::find(1);

Fawry::chargeViaCard($merchantRefNum, $user, $amount, $chargeItems = [], $description = null )
```

### Charge Via Fawry
```php
// Get user
$user = App\User::find(1);

Fawry::chargeViaFawry($merchantRefNum, $user, $paymentExpiry, $amount, $chargeItems = [], $description = null )
```

## Refund
```php
Fawry::refund($fawryRefNumber, $refundAmount, $reason = null)
```

Enjoy!
