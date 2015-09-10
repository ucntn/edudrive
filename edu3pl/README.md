*Repository page under construction*

Moodle plugin for connecting to external OwnCloud repository.
------

#####Moodle plugin installation and configuration
  1. Put **edu3pl** to Your **moodle/repository** folder
  2. Login to Moodle as admin and install the plugin (*e.g. via /admin/index.php*).
  3. In *"Site administration"* -> *"Plugins"* -> *"Repositories"* -> *"Manage repositories"*, select **"Enabled and visible"** for **"Edudrive"**
  4. In repository configuration select **"Create a repository instance"**. Fill in the configuration form with:
    - Name
    - Repository root URL - *Owncloud's URL*
    - Label key name and API acess key - *set in external_api/settings.php*
    - Repository type - *personal*
5. At this point the Moodle filepicker should have additional repository option called **"Edudrive"** while selecting files. When selected it should list all user external files.
	
	
Plugin do Moodle do ³¹czenia z zewnêtrznym repozytorium Owncloud.
------

#####Instalacja i konfiguracja wtyczki do Moodle
  1. Katalog **edu3pl** umieszczamy w katalogu **moodle/repository**
  2. Logujemy siê do platformy Moodle jako administrator i instalujemy wykryt¹ wtyczkê (*np. w /admin/index.php*).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz¹dzaj repozytoriami"* pod pozycj¹ **"Edudrive"** wybieramy **"W³¹czone i widoczne"**
  4. W ustawieniach w³¹czonego repozytorium wybieramy **"Utwórz egzemplarz repozytorium"** i wype³niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego OwnCloud'a*
    - Identifikator klucza dostêpu i klucz dostêpu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u¿ytkownika*
  5. W tym momencie menad¿er plików (*"Wybór plików"*) powinien udostêpniæ opcjê **Edudrive**, która wyœwietli pliki zalogowanego u¿ytkownika.
	