# Virtual host

- [Windows (Xampp)](#windows)
- [Linux or OSX](#linux_osx)

<a name="windows"></a>
## Windows (Xampp)

**- Add domain in your hosts file. Go to `Windows/system32/drivers/etc/hosts`**

    127.0.0.1 your-domain.local

**- Then go to `<xampp installation folder>/apache/config/extra/httpd-vhosts.conf`**

    #your-domain.local
    <VirtualHost *:80>
      ServerName your-domain.local
      DocumentRoot "**your-project-folder/public**"
      <Directory "**your-project-folder/public**">
        AllowOverride All
        Require all granted
      </Directory>
    </VirtualHost>

**- Example:**

    #cms.local
    <VirtualHost *:80>
      ServerName cms.local
      DocumentRoot "D:\Projects\botble\public"
      <Directory "D:\Projects\botble\public">
        AllowOverride All
        Require all granted
      </Directory>
    </VirtualHost>

**- After that, restart apache.**

Well done! Now, you can access the project by go to `http://your-domain.local`

<a name="linux_osx"></a>
## Linux or OSX

Please use this package to easy create Virtualhost: https://github.com/RoverWire/virtualhost