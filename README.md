Edudrive - udostêpnianie plików z systemu OwnCloud na platformie Moodle
------

1. #####Wymagania wstêpne
  1. Platforma **Moodle** w wersji >2.3 (http://moodle.org)
  2. System **Owncloud** w wersji >5.0.3 (https://owncloud.org/)
  3. Zainstalowane wtyczki do **Apache'a**:
    - mod_rewrite
    - mod_xsendfile (https://tn123.org/mod_xsendfile/) 
  4. Zainstalowane rozsze¿enie php-mcrypt
 
2. #####Konfiguracja Apache pod wzglêdem XSendFile
  1. W konfiguracji **Apache** dodajemy linijki w Directory /:
    - `XSendFile On`
    - `XSendFilePath <scie¿ka do katalogu owncloud/data>`
	
    np.:
    ```bash
	<Directory />
      Options FollowSymLinks
      AllowOverride None
	  XSendFile On
      XSendFilePath /var/www/html/owncloud/data
    </Directory>
	````

3. #####Instalacja wtyczki do Owncloud umo¿liwiaj¹cej udostêpnianie plików do zewnêtrznej platformy Moodle
  1. Pliki z **external_api** umieszczamy w katalogu **owncloud/apps/external_api** 
  2. W pliku **external_api/settings.php** zmieniamy wartoœci *$owncloudWwwRoot* na adres URL Owncloud'a oraz w tablicy *$api_keys* na w³asne, tak aby:
    - klucz (przyk³ad "abcdef") mia³ d³ugoœæ 6 znaków
    - wartoœæ mo¿e mieæ dowoln¹ iloœæ znaków
  3. Logujemy siê jako *admin* do **Owncloud'a** i na stronie **"Aplikacji"** w³¹czamy **"External Api"**
  4. Dzia³anie wtyczki mo¿na sprawdziæ plikiem *client_sample.php*, powinien on wyœwietliæ zawartoœæ katalogu u¿ytkownika *admin*.
  5. Do pliku **.htaccess** w katalogu **owncloud** pod `<IfModule mod_rewrite.c>` nale¿y dopisaæ:
  ```bash
    RewriteRule ^file/download/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1&forcedownload=1 [L]
    RewriteRule ^file/([^-]*)/([^-]*) public.php?service=filesforapp&token=$1 [L]
    RewriteRule ^thumb/([^-]*)/([^-]*) public.php?service=filesthumb&token=$1 [L]
	```
4. #####Instalacja i konfiguracja wtyczki do Moodle
  1. Wtyczkê rozpakowujemy (edu3pl.zip) do katalogu moodle/repository
  2. Logujemy siê do platformy Moodle jako administrator i instalujemy wykryt¹ wtyczkê (/admin/index.php).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz¹dzaj repozytoriami"* pod pozycj¹ **"Edudrive"** wybieramy **"W³¹czone i widoczne"**
  4. W ustawieniach w³¹czonego repozytorium wybieramy **"Utwórz egzemplarz repozytorium"** i wype³niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego Owncloud'a*
    - Identifikator klucza dostêpu i klucz dostêpu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u¿ytkownika*
  5. W tym momencie menad¿er plików ("Wybór plików") powinien udostêpniæ opcjê **Edudrive**, która wyœwietli pliki zalogowanego u¿ytkownika.
	
5. #####Uwagi
  1. Nazwy u¿ytkowników **Moodle** oraz **OwnCloud** musz¹ byæ takie same, aby wtyczki pobiera³y dobre listy plików uzytkowników
  2. Wtyczka **Moodle** nie pozwala na udostêpnianie plików w aktywnoœciach (np. w odpowiedzi do zadañ, na forach), gdy¿ usuniêcie mog³oby spowodowaæ nie spójnoœæ np. odpowiedzi na zadania. 
	