# Serializable Closure

<a href="https://github.com/laravel/serializable-closure/actions">
    <img src="https://github.com/laravel/serializable-closure/workflows/tests/badge.svg" alt="Build Status">
</a>
<a href="https://packagist.org/packages/laravel/serializable-closure">
    <img src="https://img.shields.io/packagist/dt/laravel/serializable-closure" alt="Total Downloads">
</a>
<a href="https://packagist.org/packages/laravel/serializable-closure">
    <img src="https://img.shields.io/packagist/v/laravel/serializable-closure" alt="Latest Stable Version">
</a>
<a href="https://packagist.org/packages/laravel/serializable-closure">
    <img src="https://img.shields.io/packagist/l/laravel/serializable-closure" alt="License">
</a>

## Introduction

> This project is a fork of the excellent [opis/closure: 3.x](https://github.com/opis/closure) package. At Laravel, we decided to fork this package as the upcoming version [4.x](https://github.com/opis/closure) is a complete rewrite on top of the [FFI extension](https://www.php.net/manual/en/book.ffi.php). As Laravel is a web framework, and FFI is not enabled by default in web requests, this fork allows us to keep using the `3.x` series while adding support for new PHP versions.

Laravel Serializable Closure provides an easy and secure way to **serialize closures in PHP**.

## Installation / Usage

> **Requires [PHP 7.4+](https://php.net/releases/)**

First, install Laravel Serializable Closure via the [Composer](https://getcomposer.org/) package manager:

```bash
composer require laravel/serializable-closure --dev
```

Then, you may serialize a closure this way:

```php
use Laravel\SerializableClosure\SerializableClosure;

$closure = fn () => 'james';

// Recommended
SerializableClosure::setSecretKey('secret');

$serialized = serialize(new SerializableClosure($closure));
$closure = unserialize($serialized)->getClosure();

echo $closure(); // james;
```

## Caveats

- Creating **anonymous classes** within closures is not supported.

## License

Seriazable Closure is open-sourced software licensed under the [MIT license](LICENSE.md).
