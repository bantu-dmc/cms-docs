# Upgrade Guide

- [Upgrade To 2.2.1](#upgrade-2.2.1)
- [Upgrade To 2.2](#upgrade-2.2)
- [Upgrading To 2.1](#upgrade-2.1)

<a name="upgrade-2.2.1"></a>
## Upgrade To 2.2.1

Remove admin bar configuration in your theme

    class="{{ admin_bar_class() }}"
    {!! admin_bar() !!}
    
Remove admin breadcrumb in your plugin if it is exists.

    {!! Breadcrumbs::render('pageTitle', trans('download::category.create'), Route::currentRouteName()) !!}
    <div class="clearfix"></div>

<a name="upgrade-2.2"></a>
## Upgrade To 2.2

Remove this line on `/config/app.php`
    
    Lord\Laroute\LarouteServiceProvider::class,
    
Remove laroute on `composer.json`
    
    "lord/laroute": "~2.4",

There are many changes on `gulpfile.js` so if you don't change anything on this file. Please replace it with new `gulpfile.js`.

Then, if you are using `Linux` or `OSX`, you can use `upgrade.sh` to continue upgrade to version 2.2.

    $ sudo chmod -R 777 upgrade.sh
    $ ./upgrade.sh

Upgrade script for Windows OS will be update soon. From now, you can follow `upgrade.sh` content to upgrade your source code.

<a name="upgrade-2.1"></a>
## Upgrading To 2.1

> {note} This version using Laravel Framework 5.4 so if you are working on Laravel 5.3, please override all default files and folders of Laravel version 5.4 before upgrade.

### Core and plugins
Override folder `/core` and `/plugins` from new version.

### Public resource
Replace `public/vendor` folder.

### Check and update manually
- composer.json
- gulpfile.js
- .env
