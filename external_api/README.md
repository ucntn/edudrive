*Repository page under construction*

Owncloud external API plugin
------

#####Owncloud external sharing plugin installation:
  1. Put **extarnal_api** in Your *owncloud/apps* folder
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
