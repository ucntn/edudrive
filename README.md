Edudrive - udost�pnianie plik�w OwnCloud na platformie Moodle
------

#####1. Wymagania wst�pne
  a. Platforma Moodle w wersji >2.3 (http://moodle.org)
  b. Owncloud w wersji >5.0.3 (https://owncloud.org/)
  c. Zainstalowane wtyczki do Apache'a:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  d. Zainstalowane rozsze�enie php-mcrypt
 
#####2. Konfiguracja Apache pod wzgl�dem XSendFile
  a. W konfiguracji Apache dodajemy linijki w Directory /:
    - XSendFile On
    - XSendFilePath <scie�ka do katalogu owncloud/data>
	
    np.:
     <Directory />
     Options FollowSymLinks
     AllowOverride None
     XSendFilePath /var/www/html/owncloud/data
     </Directory> 

#####3. Instalacja wtyczki do Owncloud umo�liwiaj�cej udost�pnianie plik�w do zewn�trznej platformy Moodle

#####4. Instalacja i konfiguracja wtyczki do Moodle

#####5. Uwagi
