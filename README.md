# Webloyer

[![Latest Stable Version](https://poser.pugx.org/ngmy/webloyer/v/stable)](https://packagist.org/packages/ngmy/webloyer)
[![Total Downloads](https://poser.pugx.org/ngmy/webloyer/downloads)](https://packagist.org/packages/ngmy/webloyer)
[![Latest Unstable Version](https://poser.pugx.org/ngmy/webloyer/v/unstable)](https://packagist.org/packages/ngmy/webloyer)
[![License](https://poser.pugx.org/ngmy/webloyer/license)](https://packagist.org/packages/ngmy/webloyer)

[![Build Status](https://travis-ci.org/ngmy/webloyer.svg?branch=master)](https://travis-ci.org/ngmy/webloyer)
[![Coverage Status](https://coveralls.io/repos/ngmy/webloyer/badge.svg?branch=master)](https://coveralls.io/r/ngmy/webloyer?branch=master)

Webloyer is a Web UI for managing [Deployer](https://github.com/deployphp/deployer) deployments.

## Features

Webloyer has the following features:

* Project management

 * Managing deployment settings on a project-by-project basis

* Deployment management on a project-by-project basis

 * 1-click deploying and rolling back

 * Keeping a log of every deployments

 * E-mail notifications can be sent when a deployment finishes

* Recipe management

 * Creating, editing, deleting and listing recipe files

* Server management

 * Creating, editing, deleting and listing server list files

* User management

 * Authentication with e-mail address and password

 * Role-based access control to features

## Screenshots

See [screenshots](/SCREENSHOTS.md).

## Requirements

Webloyer has the following requirements:

* PHP >= 5.5.9

* OpenSSL PHP Extension

* PDO PHP Extension

* Mbstring PHP Extension

* Tokenizer PHP Extension

## Installation

1. Download the application source code by using the Composer `create-project` command:

 ```
 composer create-project ngmy/webloyer
 ```

2. Give write permission to the `storage` directory and the `bootstrap/cache` directory for your web-server user by running the following command:

 ```
 chmod -R 777 storage
 chmod -R 777 bootstrap/cache
 ```

3. Run the installer by using the Artisan `webloyer:install` command:

 ```
 php artisan webloyer:install
 ```

4. Start the queue listener as a background process by using the Artisan `queue:listen` command:

 ```
 nohup php artisan queue:listen --timeout=0 &
 ```

 **Note:** You must be running this command as your deployment-user.

5. Add the following Cron entry to your server:

 ```
 * * * * * php /path/to/webloyer/artisan schedule:run >> /dev/null 2>&1
 ```

## Usage

### Step 1: Login to Webloyer

1. Go to the Login page by click the "Login" link.

2. Enter the e-mail address and password.

3. Click the "Login" button to login to Webloyer.

### Step 2: Create your project

1. Go to the Create Project page by click the "Create" button in the Projects page.

2. Enter your project information.

 **Note:** For now, Webloyer only supports the `deploy` task and the `rollback` task. Therefore, you must define these tasks in your Deployer recipe file.

 **Note:** If you want to use the e-mail notification, you need to enter your e-mail settings from the E-Mail Settings page.

3. Click the "Store" button to finish project creation process.

### Step 3: Managing deployments

1. Go to the Deployments page by click the "Deployments" button.

2. Run the `deploy` task by click the "Deploy" button. Or run the `rollback` task by click the "Rollback" button.

3. After the task of execution has been completed, it is possible to go to the Deployment Detail page by click the "Show" button, you can see the details of the task execution results.

## Foundation library

Webloyer uses [Laravel](http://laravel.com/) as a foundation PHP framework.

## License

Webloyer is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT).
