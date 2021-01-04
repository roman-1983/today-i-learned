# Access Shopware config

Off course it is possible to access the Shopware config, which is composed by the config-parameters from the `config.php` and `config_*.php` files.

Inside a controller i use the following command:
```php
$config = $this->get('config');
```

It is also possible to retrieve the config using the global `Shopware()` object:
```php
$config = Shopware()->Config();
```