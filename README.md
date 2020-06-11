<a href="https://aimeos.org/">
    <img src="https://aimeos.org/fileadmin/template/icons/logo.png" alt="Aimeos logo" title="Aimeos" align="right" height="60" />
</a>

# Aimeos shop system

[![License](https://poser.pugx.org/aimeos/aimeos/license.svg)](https://packagist.org/packages/aimeos/aimeos)

:star: Star us on GitHub — it helps!

## Requirements

The Aimeos shop distribution requires:
- Linus/Unix or WAMP/XAMP environment
- PHP >= 7.2
- MySQL >= 5.7
- Web server (Apache, Nginx or integrated PHP web server for testing)


## Installation

```
composer install
cp .env.example .env
php artisan serve
php artisan migrate
php artisan key:generate
php artisan serve
```


## Frontend

After the installation, you can test the Aimeos shop frontend by calling the URL of your
VHost in your browser. If you use the integrated PHP web server, you should browse
this URL: [http://127.0.0.1:8000](http://127.0.0.1:8000)

[![Aimeos frontend](https://aimeos.org/fileadmin/aimeos.org/images/aimeos-frontend.png)](http://laravel.demo.aimeos.org/)

## Backend

The Aimeos administration interface will be available at `/admin` in your VHost. When using
the integrated PHP web server, call this URL: [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

[![Aimeos admin backend](https://aimeos.org/fileadmin/aimeos.org/images/aimeos-backend.png)](http://admin.demo.aimeos.org/)

## Customize

Laravel and the Aimeos e-commerce package are extremely flexible and highly customizable.
A lot of documentation for the [Laravel framework](https://laravel.com) and the
[Aimeos e-commerce framework](https://aimeos.org/docs/Laravel) exists. If you have questions
about Aimeos, don't hesitate to ask in our [Aimeos forum](https://aimeos.org/help/).

For more details about Aimeos Laravel integration, please have a look at its
[repository](https://github.com/aimeos/aimeos-laravel).

## License

The Aimeos shop system is licensed under the terms of the MIT and LGPLv3 license and
is available for free.

## Links

* [Web site](https://aimeos.org/Laravel)
* [Documentation](https://aimeos.org/docs/Laravel)
* [Forum](https://aimeos.org/help/laravel-package-f18/)
* [Issue tracker](https://github.com/aimeos/aimeos/issues)
* [Composer packages](https://packagist.org/packages/aimeos/aimeos)
* [Source code](https://github.com/aimeos/aimeos)
