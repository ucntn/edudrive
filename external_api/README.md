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

*Strona repozytorium w budowie*

Plugin zewnętrznego API dla Owncloud.
------

#####Instalacja wtyczki do OwnCloud umożliwiającej udostępnianie plików do zewnętrznej platformy Moodle
  1. Katalog **external_api** wraz z plikami umieszczamy w katalogu **OwnCloud/apps** 
  2. W pliku **external_api/settings.php** zmieniamy wartości *$OwnCloudWwwRoot* na adres URL OwnCloud'a oraz w tablicy *$api_keys* na własne, tak aby:
    - klucz (przykład "abcdef") miał długość 6 znaków
    - wartość może mieć dowolną ilość znaków
  3. Logujemy się jako *admin* do **OwnCloud'a** i na stronie **"Aplikacji"** włączamy **"External Api"**
  4. Działanie wtyczki można sprawdzić plikiem *client_sample.php*, powinien on wyświetlić zawartość katalogu użytkownika *admin*.
  5. Do pliku **.htaccess** w katalogu **OwnCloud** pod `<IfModule mod_rewrite.c>` należy dopisać:
    ```bash
    RewriteRule ^file/download/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1&forcedownload=1 [L]
    RewriteRule ^file/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1 [L]
    RewriteRule ^thumb/([^-]*)/([^-]*) public.php?service=filesthumb&token=$1 [L]
	```