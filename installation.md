# Installation

## Getting started

Create a project folder anywhere you like, enter the folder and execute the following commands:

```
npm install webiny
```

This will install a Webiny CLI tool you will use to setup everything else. After \`npm\` finishes the installation, run \`webiny\` file that is created in your project and follow the on-screen instructions that will guide you through the setup process of the platform

```
node webiny
```

### Dependencies

Webiny requires a web server with the following dependencies installed:
* PHP v7+
* MongoDb v3+
* Nginx v1.11+
* NPM v3+

#### Vagrant
If you don't want to hassle with installing the dependencies, you can use our Vagrant maching, which will get you up and running in few minutes.

First clone our vagrant git repo in one of your local folders:

```
git clone https://github.com/Webiny/WebinyDevVagrantBox.git
```

Inside the cloned folder, run:

```
vagrant box add webiny/webiny-dev
```

