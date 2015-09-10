*Strona repozytorium w budowie*

Plugin do Moodle do ³¹czenia z zewnêtrznym repozytorium Owncloud.
------

#####Instalacja i konfiguracja wtyczki do Moodle
  1. Katalog**edu3pl** umieszczamy w katalogu **moodle/repository**
  2. Logujemy siê do platformy Moodle jako administrator i instalujemy wykryt¹ wtyczkê (*np. w /admin/index.php*).
  3. W *"Administracja serwisu"* -> *"Wtyczki"* -> *"Repozytoria"* -> *"Zarz¹dzaj repozytoriami"* pod pozycj¹ **"Edudrive"** wybieramy **"W³¹czone i widoczne"**
  4. W ustawieniach w³¹czonego repozytorium wybieramy **"Utwórz egzemplarz repozytorium"** i wype³niamy formularz:
    - Nazwa
    - Bazowy URL repozytorium - 8adres URL zainstalowanego OwnCloud'a*
    - Identifikator klucza dostêpu i klucz dostêpu API - *dane podane w external_api/settings.php*
    - Typ repozytorium - *osobiste zalogowanego u¿ytkownika*
  5. W tym momencie menad¿er plików (*"Wybór plików"*) powinien udostêpniæ opcjê **Edudrive**, która wyœwietli pliki zalogowanego u¿ytkownika.
	