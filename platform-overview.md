# Platform Overview

## What's it about?

How many times did you start your project from scratch, spent a few days setting up the basics, just to get your first output from your upcoming API? And what about your user interface? Backend app, frontend app \(or even a couple of them\), setting up authorization layer, password recovery, buid system, development\/production versions, deployment to remote server...

Well, the time has come to just deliver the project without all the pain that goes with it. We ourselves have struggled a long time before we finally managed to create a platform that is simply ready-to-go.  We offer you our approach to application development, be it just an API for another mobile app, or a bunch of web-apps connected to your API.

## API layer

The API layer is developed using [Webiny Framework](https://github.com/Webiny/Framework), powered by PHP7 and MongoDB. It is very simple, yet it provides many built-in tools for developers to do whatever they like. If you just use what it has to offer out of the box, you are already on your way to create user-friendly APIs , with auto-generated Postman collections for your mobile devs, clean URLs, authorization layer controllable through a user interface, API token control with access logs, etc.

### Entities

Entities are the main driving force of your business logic. We created a developer-friendly syntax to define your entity structure \(see our [Entity](http://github.com/Webiny/Entity) component for more info\). 90% of the time you will be dealing with entities so we wanted to make them as powerful as possible from the perspective of an API consumer but we also wanted to achieve as much as we can from customization point of view to make developer's life easier.

As soon as an entity is defined \(you create a class and add some attributes\) - it is available through an API. It is immediately controllable through authorization control module, it is discoverable through Postman \(with auto-generated collections\), it immediately supports all CRUD operations.

### Services

Services are used very rarely because during the years we have come to conclusion that creating a service just to call a method on your entity and return the result is as repetitive as it gets, adding files and unnecessary code to maintain. But sometimes you need to put some code somewhere, and it is not an entity - so there you have it.

