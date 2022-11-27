# Laravel Orders

This is a package to handle the orders in your Laravel application, you can create, update and delete your orders with suitable events. Also you can manage the order lifecycle from being _initiated_ to the _completed_.

## Features
1. Create and Manage your orders easily
2. See Orders Reports and its Customers
3. Send notifications within order lifecycle
4. Fire events within order lifecycle

You can start from the [issues page](https://github.com/mgamal92/orders-laravel/issues) to work on the feature which you prefer.


## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Testing](#testing)
- [License](#license)

## Installation

```bash
composer require mgamal/laravel-orders
```

Optionally, you can publish the config file with:

```bash
php artisan vendor:publish --tag=config --provider="MG\LaravelOrder\OrderServiceProvider"
```

## Usage
- [Manage Orders](#manage-orders)
- [Order Status](#order-status)
- [Events](#events)
- [Custom Queries](#custom-queries)


### Manage Orders
- Create Order
```php
// Create Order
Order::create(OrderStatus status)
    ->withUser($user)
    ->withItems(...$items)
```

- Update Order
```php
// Update Order Status
$order->updateStatus(OrderStatus status)

// Update Order Items
$order->updateItems(...$items)
```

### Order Status

```php
enum OrderStatus
{
    case Initiated;
    case InProgress;
    case Completed;
    case Failed;
}
```
### Events

```php
Order::statusUpdate(function (Order $order) {
    // Do your work here!
});
```

### Custom Queries

### Testing
Running tests can be done either through composer, or directly calling the PHPUnit binary.
```bash
$ vendor/bin/phpunit test
```

### License
The MIT License (MIT). Please see [License File](LICENSE) for more information.