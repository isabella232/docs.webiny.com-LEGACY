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
If you don't want to hassle with installing the dependencies, you can use our Vagrant machine, which will get you running in few minutes.

First clone our vagrant git repo in one of your local folders:

```
git clone https://github.com/Webiny/WebinyDevVagrantBox.git
```

Make sure you have [vagrant](https://www.vagrantup.com/downloads.html) and [VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed. Inside the cloned folder, run:

```
vagrant box add webiny/webiny-dev
```

Once the box is installed:

```
vagrant up
```

and then use the following command to ssh into your vagrant machine.

```
vagrant ssh
```

Now you can run the upper `npm` command from vagrant and install Webiny.

Note that our vagrant box by default maps the vagrant `/home/vagrant/Code` folder to the `Code` folder on your local drive. The folder on the local drive is located in the folder where you cloned the `WebinyDevVagrantBox` repo.

> **Warning**: Lorem ipsum dolor sit amet, consectetur adipisicing elit, > sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. > velit esse cillum dolore eu fugiat.


