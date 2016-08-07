# WebinyTrait

When you want to access system resources, like loaded configs, request, database, storage, router, event manager, etc., you need to use **WebinyTrait**. Below is a stripped out version of this trait to give you an overview of methods available to you when using it:

```php
trait WebinyTrait
{
    /**
     * Get access to AnalyticsDb
     */
    static protected function wAnalytics();

    /**
     * Get access to database
     */
    static protected function wDatabase($database = 'Webiny');

    /**
     * Get access to storage
     */
    static protected function wStorage($name = null);

    /**
     * Get access to class loader
     */
    static protected function wClassLoader();

    /**
     * Get access to caching system
     */
    static protected function wCache();

    /**
     * Get access to system configuration
     */
    static protected function wConfig();

    /**
     * Get current request
     */
    static protected function wRequest();

    /**
     * Get event manager
     */
    static protected function wEvents();

    /**
     * Get router
     */
    static protected function wRouter();

    /**
     * Get service manager
     */
    static protected function wService($name = null);

    /**
     * Get template engine
     */
    static protected function wTemplateEngine();

    /**
     * Get production flag
     */
    static protected function wIsProduction();

    /**
     * Get validation instance
     */
    static protected function wValidation();

    /**
     * Get Authorization
     */
    static protected function wAuth();

    /**
     * Get Apps container or App instance
     */
    static protected function wApps($app = null);
}
```

