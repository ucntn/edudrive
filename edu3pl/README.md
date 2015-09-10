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
	
	
Plugin do Moodle do ��czenia z zewn�trznym repozytorium Owncloud.
------

#####Instalacja i konfiguracja wtyczki do Moodle
  1. Katalog **edu3pl** umieszczamy w katalogu **moodle/repository**
  2. Logujemy si� do platformy Moodle jako administrator i instalujemy wykryt� wtyczk� (*np. w /admin/index.php*).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz�dzaj repozytoriami"* pod pozycj� **"Edudrive"** wybieramy **"W��czone i widoczne"**
  4. W ustawieniach w��czonego repozytorium wybieramy **"Utw�rz egzemplarz repozytorium"** i wype�niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego OwnCloud'a*
    - Identifikator klucza dost�pu i klucz dost�pu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u�ytkownika*
  5. W tym momencie menad�er plik�w (*"Wyb�r plik�w"*) powinien udost�pni� opcj� **Edudrive**, kt�ra wy�wietli pliki zalogowanego u�ytkownika.
	