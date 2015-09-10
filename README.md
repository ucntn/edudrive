Edudrive - udostêpnianie plików z systemu OwnCloud na platformie Moodle
------

1. Wymagania wstêpne
  1. Platforma Moodle w wersji >2.3 (http://moodle.org)
  2. Owncloud w wersji >5.0.3 (https://owncloud.org/)
  3. Zainstalowane wtyczki do Apache'a:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  4. Zainstalowane rozsze¿enie php-mcrypt
 
2. Konfiguracja Apache pod wzglêdem XSendFile
  1. W konfiguracji Apache dodajemy linijki w Directory /:
    - XSendFile On
    - XSendFilePath <scie¿ka do katalogu owncloud/data>
	
    np.:
     <Directory />
     Options FollowSymLinks
     AllowOverride None
     XSendFilePath /var/www/html/owncloud/data
     </Directory> 

3. Instalacja wtyczki do Owncloud umo¿liwiaj¹cej udostêpnianie plików do zewnêtrznej platformy Moodle

4. Instalacja i konfiguracja wtyczki do Moodle
5. Uwagi
