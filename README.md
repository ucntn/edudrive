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
	
	
*Strona repozytorium w budowie*
Edudrive - udostêpnianie plików z systemu OwnCloud na platformie Moodle
------

1. #####Wymagania wstêpne
  1. Platforma **Moodle** w wersji >2.3 (http://moodle.org)
  2. System **OwnCloud** w wersji >5.0.3 (https://owncloud.org/)
  3. Zainstalowane wtyczki do **Apache'a**:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  4. Zainstalowane rozsze¿enie php-mcrypt
 
2. #####Konfiguracja Apache pod wzglêdem XSendFile
  1. W konfiguracji **Apache** dodajemy linijki w Directory /:
    - `XSendFile On`
    - `XSendFilePath <scie¿ka do katalogu OwnCloud/data>`
	
    np.:
    ```bash
	<Directory />
      Options FollowSymLinks
      AllowOverride None
	  XSendFile On
      XSendFilePath /var/www/html/OwnCloud/data
    </Directory>
	````

3. #####Instalacja wtyczki do OwnCloud umo¿liwiaj¹cej udostêpnianie plików do zewnêtrznej platformy Moodle
  1. Katalog **external_api** wraz z plikami umieszczamy w katalogu **OwnCloud/apps** 
  2. W pliku **external_api/settings.php** zmieniamy wartoœci *$OwnCloudWwwRoot* na adres URL OwnCloud'a oraz w tablicy *$api_keys* na w³asne, tak aby:
    - klucz (przyk³ad "abcdef") mia³ d³ugoœæ 6 znaków
    - wartoœæ mo¿e mieæ dowoln¹ iloœæ znaków
  3. Logujemy siê jako *admin* do **OwnCloud'a** i na stronie **"Aplikacji"** w³¹czamy **"External Api"**
  4. Dzia³anie wtyczki mo¿na sprawdziæ plikiem *client_sample.php*, powinien on wyœwietliæ zawartoœæ katalogu u¿ytkownika *admin*.
  5. Do pliku **.htaccess** w katalogu **OwnCloud** pod `<IfModule mod_rewrite.c>` nale¿y dopisaæ:
    ```bash
    RewriteRule ^file/download/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1&forcedownload=1 [L]
    RewriteRule ^file/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1 [L]
    RewriteRule ^thumb/([^-]*)/([^-]*) public.php?service=filesthumb&token=$1 [L]
	```
4. #####Instalacja i konfiguracja wtyczki do Moodle
  1. Katalog**edu3pl** umieszczamy w katalogu **moodle/repository**
  2. Logujemy siê do platformy Moodle jako administrator i instalujemy wykryt¹ wtyczkê (*np. w /admin/index.php*).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz¹dzaj repozytoriami"* pod pozycj¹ **"Edudrive"** wybieramy **"W³¹czone i widoczne"**
  4. W ustawieniach w³¹czonego repozytorium wybieramy **"Utwórz egzemplarz repozytorium"** i wype³niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego OwnCloud'a*
    - Identifikator klucza dostêpu i klucz dostêpu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u¿ytkownika*
  5. W tym momencie menad¿er plików (*"Wybór plików"*) powinien udostêpniæ opcjê **Edudrive**, która wyœwietli pliki zalogowanego u¿ytkownika.
	
5. #####Uwagi
  1. Nazwy u¿ytkowników **Moodle** oraz **OwnCloud** musz¹ byæ takie same, aby wtyczki pobiera³y dobre listy plików uzytkowników
  2. Wtyczka **Moodle** nie pozwala na udostêpnianie plików w aktywnoœciach (np. w odpowiedzi do zadañ, na forach), gdy¿ usuniêcie mog³oby spowodowaæ nie spójnoœæ np. odpowiedzi na zadania. 
	