*Strona repozytorium w budowie*

Plugin do Moodle do ��czenia z zewn�trznym repozytorium Owncloud.
------

#####Instalacja i konfiguracja wtyczki do Moodle
  1. Katalog**edu3pl** umieszczamy w katalogu **moodle/repository**
  2. Logujemy si� do platformy Moodle jako administrator i instalujemy wykryt� wtyczk� (*np. w /admin/index.php*).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz�dzaj repozytoriami"* pod pozycj� **"Edudrive"** wybieramy **"W��czone i widoczne"**
  4. W ustawieniach w��czonego repozytorium wybieramy **"Utw�rz egzemplarz repozytorium"** i wype�niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego OwnCloud'a*
    - Identifikator klucza dost�pu i klucz dost�pu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u�ytkownika*
  5. W tym momencie menad�er plik�w (*"Wyb�r plik�w"*) powinien udost�pni� opcj� **Edudrive**, kt�ra wy�wietli pliki zalogowanego u�ytkownika.
	