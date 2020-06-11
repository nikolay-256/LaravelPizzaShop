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

## Backend

The Aimeos administration interface will be available at `/admin` in your VHost. When using
the integrated PHP web server, call this URL: [http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

[![Aimeos admin backend](https://aimeos.org/fileadmin/aimeos.org/images/aimeos-backend.png)](http://admin.demo.aimeos.org/)

## Admin

To use the admin interface, you have to set up Laravel authentication first:

### Laravel 7

```
composer require laravel/ui:^2.0
php artisan ui vue --auth
npm install && npm run dev
```

For more information, please follow the Laravel documentation:
* [Laravel 7.x](https://laravel.com/docs/7.x/authentication)

### Laravel 6

```
composer require laravel/ui:^1.0
php artisan ui vue --auth
npm install && npm run dev
```

For more information, please follow the Laravel documentation:
* [Laravel 6.x](https://laravel.com/docs/6.x/authentication)

### Laravel 5.x

```php artisan make:auth```

For more information, please follow the Laravel documentation:
* [Laravel 5.8](https://laravel.com/docs/5.8/authentication)
* [Laravel 5.7](https://laravel.com/docs/5.7/authentication)
* [Laravel 5.6](https://laravel.com/docs/5.6/authentication)
* [Laravel 5.5](https://laravel.com/docs/5.5/authentication)

### Create account

Test if your authentication setup works before you continue. Create an admin account
for your Laravel application so you will be able to log into the Aimeos admin interface:

```php artisan aimeos:account --super <email>```

The e-mail address is the user name for login and the account will work for the
frontend too. To protect the new account, the command will ask you for a password.
The same command can create limited accounts by using "--admin", "--editor" or "--api"
instead of "--super" (access to everything).

### Configure authentication

As a last step, you need to extend the `boot()` method of your
`App\Providers\AuthServiceProvider` class and add the lines to define how
authorization for "admin" is checked in `app/Providers/AuthServiceProvider.php`:

```php
    public function boot()
    {
        // Keep the lines before

        Gate::define('admin', function($user, $class, $roles) {
            if( isset( $user->superuser ) && $user->superuser ) {
                return true;
            }
            return app( '\Aimeos\Shop\Base\Support' )->checkUserGroup( $user, $roles );
        });
    }
```

### Test

If your `./public` directory isn't writable by your web server, you have to create these
directories:
```
mkdir public/files public/preview public/uploads
chmod 777 public/files public/preview public/uploads
```

In a production environment, you should be more specific about the granted permissions!
If you've still started the internal PHP web server (`php artisan serve`)
you should now open this URL in your browser:

http://127.0.0.1:8000/index.php/admin

Enter the e-mail address and the password of the newly created user and press "Login".
If you don't get redirected to the admin interface (that depends on the authentication
code you've created according to the Laravel documentation), point your browser to the
`/admin` URL again.

**Caution:** Make sure that you aren't already logged in as a non-admin user! In this
case, login won't work because Laravel requires to log out first.

[![Aimeos backend](https://aimeos.org/fileadmin/aimeos.org/images/aimeos-backend.png)](http://127.0.0.1:8000/index.php/admin)

## Hints

To simplify development, you should configure to use no content cache. You can
do this in the `config/shop.php` file of your Laravel application by adding
these lines at the bottom:

```php
    'madmin' => array(
        'cache' => array(
            'manager' => array(
                'name' => 'None',
            ),
        ),
    ),
```

## License

The Aimeos Laravel package is licensed under the terms of the MIT license and
is available for free.

## Links

* [Web site](https://aimeos.org/Laravel)
* [Documentation](https://aimeos.org/docs/Laravel)
* [Forum](https://aimeos.org/help/laravel-package-f18/)
* [Issue tracker](https://github.com/aimeos/aimeos-laravel/issues)
* [Composer packages](https://packagist.org/packages/aimeos/aimeos-laravel)
* [Source code](https://github.com/aimeos/aimeos-laravel)
