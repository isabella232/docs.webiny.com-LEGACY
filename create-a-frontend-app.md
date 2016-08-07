# Creating a frontend app

## Setting up the basic app structure

* Create a **MyApp** folder in the Apps folder and create the following file structure:

      .
      |-- Js
      |   `-- Frontend
      |       |-- Modules
      |       `-- App.js
      |-- Php
      |   `-- Bootstrap.php
      |-- Templates
      |   `-- MyApp.tpl
      `-- App.yaml


* In **App.yaml**, enter the following info:
* ```
  Name: MyApp
  Version: 0.1.0
  Link: http://myapp.com
  Description: Enter your app description here

  AuthorName: Webiny LTD
  AuthorLink: http://www.webiny.com
  AuthorEmail: info@webiny.com
  ```

* In **Bootstrap.php**, paste the following code and uncomment the appropriate route definition:

* ```
  <?php
  namespace Apps\MyApp\Php;

  use Apps\Core\Php\DevTools\BootstrapTrait;
  use Apps\Core\Php\PackageManager\App;

  class Bootstrap
  {
     use BootstrapTrait;

     public function run(App $app)
     {
         // Domain root launches the app, but we need to set it to lower priority because of greedy regex
         // $this->addAppRoute('/^\//', 'MyApp:Templates/MyApp.tpl', 200);

         // Or set an app prefix, which will not be so greedy, then we don't need priority
         // $this->addAppRoute('/^\/my-app/', 'MyApp:Templates/MyApp.tpl');
     }
  }
  ```


* In **MyApp.tpl**, paste the following code to bootstrap your app \(change the **baseUrl** to match your app route\):
* ```
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="utf-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <title>MyApp</title>
      <meta name="viewport" content="width=device-width, initial-scale=1, minimum-scale=1, maximum-scale=1">
      <link href="http://fonts.googleapis.com/css?family=Source+Sans+Pro:400,700,300" rel="stylesheet" type="text/css">
      <script type="text/javascript">
          function Webiny(run) {
              run({
                  app: 'MyApp.Frontend',
                  router: {
                      baseUrl: '/',
                      title: '%s | MyApp',
                      defaultRoute: 'Dashboard'
                  },
                  authentication: 'MyApp.Frontend'
              });
          }
      </script>
      {webiny}
  </head>
  <body>
  <webiny-app/>
  </body>
  </html>
  ```

  * **&lt;webiny-app\/&gt;** - is the element that will be used to mount the actual app.

  * **{webiny}** - is the smarty plugin that includes some key resources required for Webiny to run.

  * **function Webiny\(run\){...}** - is the function that is executed once the **vendors.js** file included by **{webiny}** has finished loading. A callback is passed to it and you need to execute it with an app config as first parameter to start the bootstrap process. The config consists of the following:

  * ```
    {
        app: 'MyApp.Frontend',            -->    The name of the JS app you want to run
        router: {
            baseUrl: '/',                 -->    Base URL for the app router
            title: '%s | MyApp',          -->    Window title pattern to render when routes change
            defaultRoute: 'Dashboard'     -->    Default route to render when route is not specified
        },
        authentication: 'MyApp.Frontend'  -->    JS app containing Authentication module (Optional)
    }
    ```



* Paste the following code into your App.js file:
* ```
  import Webiny from 'Webiny';

  export default new Webiny.App('MyApp.Frontend');
  ```

  This simply defines an app and the platform knows what to do with it. There are more things that can be done here, but that is out of the scope of this tutorial.

* Enable the app in **Configs\/Production\/Application.yaml** under **Apps** key:

* ```
  Apps:
     MyApp: true
  ```


## Creating your first JS module

Ok, now that we have the skeleton for our new app, we need to add a couple more things to get some output.

* We need to create our layout, a UI structure, that will be rendered when the app is run. To achieve this, we simply define a new module called **Layout **\(you can name it whatever you like\):


*     .
      `-- Frontend
          |-- Modules
          |   `-- Layout
          |       |-- Main.jsx
          |       `-- Module.js
          `-- App.js

  Paste the following code into **Module.js**:

* ```
  import Webiny from 'Webiny';
  import Main from './Main';

  class Module extends Webiny.Module {

      init() {
          this.registerDefaultComponents({MasterLayout: Main});
      }
  }

  export default Module;
  ```

  This tells the system that whenever a route is rendered, **MasterLayout** placeholder should render the **Main** component. **MasterLayout** is a built-in placeholder which serves as an entry point for rendering.

  Now, we will create our layout, paste the following code into **Main.jsx**:

* ```
  import Webiny from 'Webiny';
  const Ui = Webiny.Ui.Components;

  /**
   * Create your app layout here. "MasterContent" is the default container the Router uses for rendering content.
   */
  class Main extends Webiny.Ui.View {
      render() {
          return (
              <div>
                  <h2>Main Header</h2>
                  <Webiny.Ui.Placeholder name="MasterContent"/>
              </div>
          );
      }
  }

  export default Main;
  ```

* Ok, now we have our main layout, but we still haven't created our first route and the actual content to render when somebody runs our app. Let's create a **Dashboard** module. Now our folder structure look like this:


*     .
      `-- Frontend
          |-- Modules
          |   |-- Dashboard
          |   |   `-- Module.js
          |   `-- Layout
          |       |-- Main.jsx
          |       `-- Module.js
          `-- App.js

  Paste the following code into **Dashboard\/Module.js**:

* ```
  import Webiny from 'Webiny';

  class DummyView extends Webiny.Ui.View {
      render() {
          const user = Webiny.Model.get('User');
          return <p>Hello there, {_.get(user, 'firstName', 'Guest')}!</p>;
      }
  }

  class Module extends Webiny.Module {
      init() {
          this.registerRoutes(
              new Webiny.Route('Dashboard', '/', DummyView, 'Dashboard')
          );
      }
  }

  export default Module;
  ```

  In the **Module** class we simply registered a route called **Dashboard**, passed a pattern, defined a view component for it, called **DummyView** \(usually you would put it in a separate file, just like Main.jsx, but for the sake of brevity I included it inline\) and gave it a title that will be rendered using the title pattern defined in app config.

* You can now run your watch, include **Core.Webiny** and **MyApp.Frontend**, and navigate to your development domain. You should see your Dashboard content rendered, and the window title should say "Dashboard \| MyApp"


