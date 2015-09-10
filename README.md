Edudrive - udost�pnianie plik�w z systemu OwnCloud na platformie Moodle
------

1. #####Wymagania wst�pne
  1. Platforma **Moodle** w wersji >2.3 (http://moodle.org)
  2. System **Owncloud** w wersji >5.0.3 (https://owncloud.org/)
  3. Zainstalowane wtyczki do **Apache'a**:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  4. Zainstalowane rozsze�enie php-mcrypt
 
2. #####Konfiguracja Apache pod wzgl�dem XSendFile
  1. W konfiguracji **Apache** dodajemy linijki w Directory /:
    - `XSendFile On`
    - `XSendFilePath <scie�ka do katalogu owncloud/data>`
	
    np.:
    ```bash
	<Directory />
      Options FollowSymLinks
      AllowOverride None
	  XSendFile On
      XSendFilePath /var/www/html/owncloud/data
    </Directory>
	````

3. #####Instalacja wtyczki do Owncloud umo�liwiaj�cej udost�pnianie plik�w do zewn�trznej platformy Moodle
  1. Pliki z **external_api** umieszczamy w katalogu **owncloud/apps/external_api** 
  2. W pliku **external_api/settings.php** zmieniamy warto�ci *$owncloudWwwRoot* na adres URL Owncloud'a oraz w tablicy *$api_keys* na w�asne, tak aby:
    - klucz (przyk�ad "abcdef") mia� d�ugo�� 6 znak�w
    - warto�� mo�e mie� dowoln� ilo�� znak�w
  3. Logujemy si� jako *admin* do **Owncloud'a** i na stronie **"Aplikacji"** w��czamy **"External Api"**
  4. Dzia�anie wtyczki mo�na sprawdzi� plikiem *client_sample.php*, powinien on wy�wietli� zawarto�� katalogu u�ytkownika *admin*.
  5. Do pliku **.htaccess** w katalogu **owncloud** pod `<IfModule mod_rewrite.c>` nale�y dopisa�:
  ```bash
    RewriteRule ^file/download/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1&forcedownload=1 [L]
    RewriteRule ^file/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1 [L]
    RewriteRule ^thumb/([^-]*)/([^-]*) public.php?service=filesthumb&token=$1 [L]
	```
4. #####Instalacja i konfiguracja wtyczki do Moodle
  1. Wtyczk� rozpakowujemy (edu3pl.zip) do katalogu moodle/repository
  2. Logujemy si� do platformy Moodle jako administrator i instalujemy wykryt� wtyczk� (/admin/index.php).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz�dzaj repozytoriami"* pod pozycj� **"Edudrive"** wybieramy **"W��czone i widoczne"**
  4. W ustawieniach w��czonego repozytorium wybieramy **"Utw�rz egzemplarz repozytorium"** i wype�niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego Owncloud'a*
    - Identifikator klucza dost�pu i klucz dost�pu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u�ytkownika*
  5. W tym momencie menad�er plik�w ("Wyb�r plik�w") powinien udost�pni� opcj� **Edudrive**, kt�ra wy�wietli pliki zalogowanego u�ytkownika.
	
5. #####Uwagi
  1. Nazwy u�ytkownik�w **Moodle** oraz **OwnCloud** musz� by� takie same, aby wtyczki pobiera�y dobre listy plik�w uzytkownik�w
  2. Wtyczka **Moodle** nie pozwala na udost�pnianie plik�w w aktywno�ciach (np. w odpowiedzi do zada�, na forach), gdy� usuni�cie mog�oby spowodowa� nie sp�jno�� np. odpowiedzi na zadania. 
	