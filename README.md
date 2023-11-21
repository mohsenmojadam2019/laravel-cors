# Laravel Cors
## CORS Middleware for Laravel

## Version Compatibility

| Laravel | Package      |
|:--------|:-------------|
| 9.0     | 0.1.0        |
| 10.0    | last version |

## Install
Via Composer

```php
composer remove barryvdh/laravel-cors timeshow/laravel-cors
composer require timeshow/laravel-cors
```

## Global usage
To allow CORS for all your routes, add the HandleCors middleware at the top of the $middleware property of app/Http/Kernel.php class:

```php   
protected $middleware = [
  \TimeShow\Cors\HandleCors::class,
    // ...
];
```

## Configuration
The defaults are set in config/cors.php. Publish the config to copy the file to your own config:

```php
php artisan vendor:publish --tag="cors"
```

Now update the config to define the paths you want to run the CORS service on, (see Configuration below):
```php
'paths' => ['api/*', 'admin/*'],
```

## Options
| Option                   | Description                                                              | Default value |
|--------------------------|--------------------------------------------------------------------------|---------------|
| paths                    | You can enable CORS for 1 or multiple paths, eg. `['api/*'] `            | `[]`          |
| allowed_methods          | Matches the request method.                                              | `['*']`       |
| allowed_origins          | Matches the request origin. Wildcards can be used, eg. `*.mydomain.com` or `mydomain.com:*`  | `['*']`       |
| allowed_origins_patterns | Matches the request origin with `preg_match`.                            | `[]`          |
| allowed_headers          | Sets the Access-Control-Allow-Headers response header.                   | `['*']`       |
| exposed_headers          | Sets the Access-Control-Expose-Headers response header.                  | `[]`       |
| max_age                  | Sets the Access-Control-Max-Age response header.                         | `0`           |
| supports_credentials     | Sets the Access-Control-Allow-Credentials header.                        | `false`       |
`allowed_origins`, `allowed_headers` and `allowed_methods` can be set to `['*']` to accept any value.