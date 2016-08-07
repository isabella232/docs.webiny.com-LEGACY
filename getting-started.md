# Project structure

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

