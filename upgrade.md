# Upgrade Guide

- [Upgrading To 2.1](#upgrade-2.1)

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
