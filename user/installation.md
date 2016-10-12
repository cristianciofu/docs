## Requirements

There are a few things that you will need to have set up in order to run Flarum:

* A web server: **Apache** (with mod_rewrite), **Nginx**, or **Lighttpd**
* **PHP 5.5+** with the following extensions: mbstring, pdo_mysql, openssl, json, gd, dom, fileinfo
* **MySQL 5.5+**
* **SSH (command-line) access**

<a name="installing-flarum"></a>
## Installation

### With composer

Flarum utilizes Composer to manage its dependencies and extensions. So, before installing Flarum, you will need to install [Composer](https://getcomposer.org) on your machine. Then run this command in the location where Flarum should be installed:

```bash
composer create-project flarum/flarum . --stability=beta
```

While this command is running, you can configure [URL rewriting](/user/configuration.md#url-rewriting) on your web server. Finally, navigate to your forum in a browser and follow the instructions to complete the installation.

((future))
### With installer

((endfuture))

## Migration

