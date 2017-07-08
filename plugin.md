#Plugin

- [Create plugin](#create-plugin)
- [Activate plugin](#activate-plugin)
- [Deactivate plugin](#deactivate-plugin)
- [Remove plugin](#remove-plugin)

> In version 2.1, command name is changed from `cms:create` to `plugin:create`. Please run `php artisan --help` to see all commands

<a name="create-plugin"></a>
## Create a plugin
**- Open CMD or Terminal then run:**

     php artisan plugin:create <plugin name>

> {video} You can see more detail here: [Create a plugin](https://www.youtube.com/watch?v=8F4wfrS9svs)

<a name="activate-plugin"></a>
## Activate a plugin
**- Open CMD or Terminal then run:**

     php artisan plugin:activate <plugin name>

<a name="deactivate-plugin"></a>
## Deactivate a plugin
**- Open CMD or Terminal then run:**

     php artisan plugin:deactivate <plugin name>
     
<a name="remove-plugin"></a>
## Remove a plugin
**- Command:**

    php artisan cms:remove demo

> {note} `demo` is a plugin

When you run this command. It will do:

+ Deactivate `demo` plugin.

+ It will be remove `demo` table and its permissions

+ Delete folder demo in `/plugins` and delete `/plugins` directory if it's empty

> {video} See video for more detail: [Delete a plugin](https://www.youtube.com/watch?v=jmex2G4eC18)