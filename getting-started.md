# Getting started

## Initial setup

For instructions on how to setup the platform please read the article on [Installation](/Docs/en/Guides/installation.md).

## Project structure overview

Once you finished the installation your project directory structure will look like this:

    .
    |-- Apps                    -->    All apps are located in this folder
    |   `-- Core                -->    Core app that handles everything
    |       |-- Js              -->    Folder for JS apps (there can be unlimited number of JS apps)
    |       |   |-- Backend     -->    App that serves as a skeleton for all other backend apps
    |       |   `-- Webiny      -->    This is the core of Webiny JS layer (all components, router, etc.)
    |       |-- Php             -->    Contains all server-side related processing, dev tools, etc.
    |       |-- Templates       -->    Smarty templates for app bootstrap, emails, reports, etc.
    |       `-- App.yaml        -->    App definition, configs, etc.
    |-- Configs                 -->    Configs for the Platform and Framework components
    |   |-- Development               
    |   |   |-- Application.yaml
    |   |   `-- Cache.yaml
    |   |-- Production                
    |   |   |-- Application.yaml
    |   |   |-- Cache.yaml
    |   |   |-- Database.yaml
    |   |   |-- Security.yaml
    |   |   `-- TemplateEngine.yaml
    |   `-- ConfigSets.yaml            -->    Maps domains to specific environments
    |-- public_html
    |   |-- build            -->    contains built JS apps and other assets
    |   `-- index.php        -->    system entry point (web-server should point here) 
    `-- webiny               -->    node cli tool to manage builds, deploys, etc.    

> NOTE: Some files and folders were omitted from the file tree as they are of no interest to us at this point.

## Bootstrap process

When a request arrives to **public\_html\/index.php**, the internal bootstrap process is triggered, which first tries to determine the configs that should be loaded. The requested domain is matched against entries in **ConfigSets.yaml** to find the appropriate environment. **Production** configs are always loaded, and if the detected environment is other than that, other config files are loaded and merged into the **Production** configs to override specific configuration parameters.

> NOTE: **Production** and **Development** environments are the only built-in environments. You can create other config sets and name them whatever you like \(e.g. Local, Staging,...\). Simply create a new folder inside **Configs** folder and add your own yaml files.

Once the platform config is loaded, the system begins to read apps from **Apps** folder and parse their **App.yaml** files.

After all app configs are loaded, the bootstrap process attempts to execute **Bootstrap.php** file located in the **Php** folder of each loaded app. More on this in [App Bootstrap](/app-bootstrap.md).

After all apps are bootstrapped, the system fires a **Core.Bootstrap.End** event without any parameters.

## Request Processing

Once the bootstrap process has finished, it is time to process the request. The platform is built in a way that can be completely customized at each stage of request processing, via event manager. The system fires an event **Core.Bootstrap.Request**, essentially saying: "Hey, I need someone to process the request, and I am expecting the result to be an instance of **\Apps\Core\Php\DevTools\Response\AbstractResponse**". If a valid result is received, it will be sent to the browser. If not, a 404 response will be sent.

The system provides 3 bult-in request handlers:

* **API** - checks if the request is an API request \(by checking the config **ApiPath**\) and if yes, starts its own logic for request processing. This event handler has a priority of **400.**

* **Routes** - checks if the request matches any of the static routes defined through [Webiny\/Router](https://github.com/Webiny/Router) component. This event handler has a priority of **390.**

* **Backend** - checks if request matches the prefix defined in **Application.yaml **for backend area and renders backend app. This event handler has a priority of **380.**


You can register your own handlers via your app's **App.yaml** or using [DevToolsTrait](/devtoolstrait.md)** **from PHP**.**

