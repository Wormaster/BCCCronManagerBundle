# Intro to CronManager

It is a bundle that provides a web interface for managing cron table.

[![Build Status](https://secure.travis-ci.org/michelsalib/BCCCronManagerBundle.png?branch=master)](http://travis-ci.org/michelsalib/BCCCronManagerBundle)

## Features:

- Displays cron table with time expression, command, output file, error file and comment
- Can guess last execution time and status (based on log files)
- Can display log files
- Support edit/add cron entry
- Includes shortcuts to easily get common time expression, symfony command and symfony log directory
- Translated in english, french and german

## Screenshots
### Cron list
![](https://github.com/michelsalib/BCCCronManagerBundle/raw/master/Resources/screens/cron-list.png)
### Cron form
![](https://github.com/michelsalib/BCCCronManagerBundle/raw/master/Resources/screens/cron-form.png)
### Cron output
![](https://github.com/michelsalib/BCCCronManagerBundle/raw/master/Resources/screens/cron-file.png)

## Installation and configuration:

### Get the bundle

#### If you are using Symfony 2.1 and more

Add BCCCronManagerBundle to your composer.json:

In 2.1/2.2 :

``` js
    "bcc/cron-manager-bundle": "2.2.*@dev"
```

In 2.3 :

``` js
    "bcc/cron-manager-bundle": "v2.3.0"
```

In 2.4 (Twitter Bootrap 2.*) :

``` js
    "bcc/cron-manager-bundle": "v2.4.0"
```

In 2.4 (Twitter Bootrap 3.*) :

``` js
    "bcc/cron-manager-bundle": "v2.4.1"
```

In 2.6 and more :

``` js
    "bcc/cron-manager-bundle": "v2.6.*"
```

For Bootstrap 3 and symfony less than 2.6, do not forget to add your own Less filter like this in your config.yml :
```
    filters:
        less:
            node:       %node%
            node_paths: [%node_paths%]
            apply_to: "\.less$"
```

Now tell composer to download the bundle by running the command:
``` bash
php composer.phar update bcc/cron-manager-bundle
```

#### If you are using Symfony 2.0.x
Add to your `/deps` file :

```
[BCCCronManagerBundle]
    git=http://github.com/michelsalib/BCCCronManagerBundle.git
    target=/bundles/BCC/CronManagerBundle
    version=origin/2.0
```

And make a `php bin/vendors install`.

##### Register the namespace (only for Symfony 2.0.x)

``` php
<?php

    // app/autoload.php
    $loader->registerNamespaces(array(
        'BCC' => __DIR__.'/../vendor/bundles',
        // your other namespaces
    ));
```

### Add BCCCronManagerBundle to your application kernel

``` php
<?php

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new BCC\CronManagerBundle\BCCCronManagerBundle(),
            // ...
        );
    }
```

### Import the routing configuration

Add to your `routing.yml`:

``` yml
#BCCCronManager routing
BCCCronManagerBundle:
    resource: "@BCCCronManagerBundle/Resources/config/routing.xml"
    prefix:   /cron-manager
```
You can customize the prefix as you wish.

### Import the Assetic configuration

Add the Assetic configuration file to the `imports` section of your `config.yml`:

``` yml
imports:
    - { resource: "@BCCCronManagerBundle/Resources/config/assetic.yml" }
```

