# Release Notes

- [Botble 2.3.1](#version_2_3_1)
- [Botble 2.3](#version_2_3)
- [Botble 2.2.1](#version_2_2_1)
- [Botble 2.2](#version_2_2)
- [Botble 2.1](#version_2_1)
- [Botble 2.0](#version_2_0)
- [Botble 1.0](#version_1_0)

<a name="version_2_3_1"></a>
## Botble 2.3.1
    - Fix create a Category.
    - Move analytics JSON config file to storage path.
    - Move repositories, criteria to support module.
    - Optimize media module.
    
<a name="version_2_3"></a>
## Botble 2.3
    - Apply new media management. There is many change on media on this version so the document for Media will be update later.
    - Add shortcode button above editor to easy add shortcode.
    - Allow switch between Ckeditor and Tinymce.
    - Fix bug when create new role.
    - Fix bug activate/deactivate user.
    - Add create user in admin area, now we have 2 options: create user and invite user.
    - Remove function get_file_by_size(). Now you can use get_image_url($post->image, 'thumb') instead of get_file_by_size.
    - Add front site users area.

<a name="version_2_2_1"></a>
## Botble 2.2.1
    - Add post format (Default, gallery, video...)
    - Fix bug in plugin language when default language is not set.
    - Change route name of post, page, category in front site from "public.view" to "public.single.detail"
    - Fix counter in Dashboard.
    - Refactor admin breadcrumb.
    - Set page title for each page in admin area.
    - Add new demo theme
    - Refactor show category list, theme list...
    - Remove admin bar config in theme
<a name="version_2_2"></a>
## Botble 2.2
    - Easier theme breadcrumbs. Now you can use Theme::breadcrumb()->add('label', 'http://...')->add('label2', 'http:...');
    - Fix invite user
    - Fix reset password
    - Update email template and send mail function.
    Now you can send mail by: `EmailHandler::send('Hello there', 'Test email', ['name' => 'Sang Nguyen', 'to' => 'sangit7b@gmail.com']);`
    - Remove laroute package.
    Please remove LarouteServiceProvider on /config/app.php and laroute package on composer.json.
    
<a name="version_2_1"></a>
## Botble 2.1

    - Upgrade to Laravel 5.4.
    - Upgrade custom field plugin
    - Refactor assets structure
    - Fix error when installing.
    - Fix analytics plugin after installation.

<a name="version_2_0"></a>
## Botble 2.0
### 11-09-2016
    - Fix https://github.com/botble/issues/issues/1: Media upload error
    - Please see image attachment in this issue to update your code.
    
### 11-08-2016
    - Fix installation script.

### 10-22-2016
    Release Botble version 2.0

<a name="version_1_0"></a>
## Botble 1.0 

### 09-13-2016
     - Fix folders in media is not accessible: To update, you just need update two files:
          + /resources/views/files/partials/folder-row.blade.php
          + /resources/views/files/partials/uplevel.blade.php
     - Fix Menu management: 
        Run "composer update" to update menu package or replace /vendor/botble/menu folder.

### 08-31-2016
    - Fix menu module (just run "composer update" to update menu module)
    - Fix media uploads:
        Replace botbe/repositories/feature, 
        app/http/controllers/features 
        and app/http/endpoints/feature, media.js in assets.

### 08-24-2016
    - Upgrade to Laravel 5.3

### 08-11-2016
    - Update routes and media

###  08-01-2016
    - Add social login (login to admin page via facebook, github, google...

### 07-16-2016
    - Add contact form support, fix some small bugs.

### 07-09-2016
    - Fix dashboard widget, custom field and media management.

### 07-08-2016
    - Initial release Version 1.0