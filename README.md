*Repository page under construction*
Edudrive - sharing external OwnCloud files in Moodle
------

1. #####Requirements:
  1. **Moodle** version >2.3 (http://moodle.org)
  2. **OwnCloud** version >5.0.3 (https://owncloud.org/)
  3. **Apache** plugins installed:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  4. **Php-mcrypt** extension installed
 
2. #####Apache XSendFile configuration:
  1. Add additional lines to **Apache** *<Directory />* configuration:
    - `XSendFile On`
    - `XSendFilePath <path to owncloud/data>`

    e.g.:
    ```bash
    <Directory />
     Options FollowSymLinks
     AllowOverride None
	 XSendFile On
     XSendFilePath /var/www/html/owncloud/data
    </Directory> 
    ```
	   
3. #####Owncloud external sharing plugin installation:
  1. Put **external_api** in Your *owncloud/apps* folder
  2. In **external_api/settings.php** file, change variable *$owncloudWwwRoot* to URL address of Your Owncloud server and set *$api_keys* so that:
    - key (e.g. "abcdef") had 6 character length
    - value can have any length
  3. Login as *admin* to OwnCloud and activate **"Extranal Api"** in **"Applications"**
  4. To check if the plugin is working, use the *client_sample.php* file, which should show the content of admin user folder
  5. To the **.htaccess** file in Your **OwnCloud** folder under `<IfModule mod_rewrite.c>` add:
    ```bash
	RewriteRule ^file/download/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1&forcedownload=1 [L]
    RewriteRule ^file/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1 [L]
    RewriteRule ^thumb/([^-]*)/([^-]*) public.php?service=filesthumb&token=$1 [L] 
	```

4. #####Moodle plugin installation and configuration
  1. Put **edu3pl** to Your **moodle/repository** folder
  2. Login to Moodle as admin and install the plugin (*e.g. via /admin/index.php*).
  3. In *"Site administration"* -> *"Plugins"* -> *"Repositories"* -> *"Manage repositories"*, select **"Enabled and visible"** for **"Edudrive"**
  4. In repository configuration select **"Create a repository instance"**. Fill in the configuration form with:
    - Name
    - Repository root URL - *Owncloud's URL*
    - Label key name and API acess key - *set in external_api/settings.php*
    - Repository type - *personal*
5. At this point the Moodle filepicker should have additional repository option called **"Edudrive"** while selecting files. When selected it should list all user external files.

5. Note
	a. Usernames in Moodle and Owncloud should be the same, if the installed plugins were to list appriopriate users files.
	b. Moodle Edudrive plugin does not allow to share files in activities (e.g. in assignments, forums), because deleting a file in Owncloud would lead to file inconsitency on the Moodle side.
