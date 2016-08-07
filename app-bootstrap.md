# App Bootstrap

When you create your own app, you can define an optional **Bootstrap.php** file in case you want to execute some custom code during system bootstrap. Create a new **Bootstrap.php** file in your **Php** folder and paste the following code inside:

```php
<?php
namespace Apps\{YourApp}\Php;

use Apps\Core\Php\DevTools\BootstrapTrait;

class Bootstrap
{
    use BootstrapTrait;

    public function run(PackageManager\App $app)
    {
        // Your code goes here
    }
}
```

> NOTE: make sure you replace {YourApp} in the namespace with the actual name of your folder

The **$app** parameter is an instance of your app and exposes some useful methods for accessing your app's version, entities, services, build paths, etc.

