Edudrive - udostêpnianie plików z systemu OwnCloud na platformie Moodle
------

1. #####Wymagania wstêpne
  1. Platforma Moodle w wersji >2.3 (http://moodle.org)
  2. Owncloud w wersji >5.0.3 (https://owncloud.org/)
  3. Zainstalowane wtyczki do Apache'a:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  4. Zainstalowane rozsze¿enie php-mcrypt
 
2. #####Konfiguracja Apache pod wzglêdem XSendFile
  1. W konfiguracji Apache dodajemy linijki w Directory /:
    - XSendFile On
    - XSendFilePath <scie¿ka do katalogu owncloud/data>
	
    np.:
    `<Directory />
    Options FollowSymLinks
    AllowOverride None
    XSendFilePath /var/www/html/owncloud/data
    </Directory>`

3. #####Instalacja wtyczki do Owncloud umo¿liwiaj¹cej udostêpnianie plików do zewnêtrznej platformy Moodle
  1. Pliki z extarnal_api.zip rozpakowujemy do katalogu owncloud/apps 
  2. W pliku external_api/settings.php zmieniamy wartoœci $owncloudWwwRoot na adres URL Owncloud'a oraz w tablicy $api_keys na w³asne, tak aby:
    - klucz (przyk³ad "mdlTST") mia³ d³ugoœæ 6 znaków
    - wartoœæ mo¿e mieæ dowoln¹ iloœæ znaków
  3. Logujemy siê jako admin do Owncloud'a i na stronie "Aplikacji" w³¹czamy "External Api"
  4. Dzia³anie wtyczki mo¿na sprawdziæ plikiem client_sample.php, powinien on wyœwietliæ zawartoœæ katalogu u¿ytkownika admin.
  5. Do pliku .htaccess w katalogu owncloud pod "<IfModule mod_rewrite.c>" nale¿y dopisaæ:
    - RewriteRule ^file/download/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1&forcedownload=1 [L]
    - RewriteRule ^file/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1 [L]
    - RewriteRule ^thumb/([^-]*)/([^-]*) public.php?service=filesthumb&token=$1 [L]
4. #####Instalacja i konfiguracja wtyczki do Moodle
5. #####Uwagi
