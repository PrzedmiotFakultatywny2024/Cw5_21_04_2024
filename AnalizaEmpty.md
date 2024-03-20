# Analiza przykładowej wtyczki

![image](https://github.com/PrzedmiotFakultatywny2024/Cw5_21_04_2024/assets/24464854/69b6b42b-36e8-4c40-9124-c6af1d237fa7)

## `setup.php`

Ten plik `setup.php` jest częścią szablonu wtyczki dla systemu GLPI, który jest open-source'owym systemem zarządzania IT i serwisem helpdesk. Plik ten zawiera podstawowe definicje i funkcje niezbędne do zainicjowania i zarządzania wtyczką w systemie GLPI. 

### Nagłówek i Licencja
Na początku pliku znajduje się nagłówek z informacjami o prawach autorskich oraz tekstem licencji MIT, która jest stosunkowo luźną licencją pozwalającą na szerokie wykorzystanie oprogramowania, pod warunkiem zachowania informacji o prawach autorskich i tekstu licencji.

### Definicje Wersji GLPI
Następnie zdefiniowane są stałe określające wersję wtyczki (`PLUGIN_EMPTYPLG_VERSION`) oraz minimalną i maksymalną kompatybilną wersję GLPI (`PLUGIN_EMPTYPLG_MIN_GLPI_VERSION` i `PLUGIN_EMPTYPLG_MAX_GLPI_VERSION`). To ważne dla zapewnienia kompatybilności wtyczki z systemem GLPI i uniknięcia problemów związanych z różnicami w wersjach.

### Inicjalizacja Wtyczki
Funkcja `plugin_init_emptyplg()` jest używana do inicjalizacji wtyczki. W tym miejscu można zarejestrować różne haki (hooks) i funkcje callbackowe, które są wywoływane w określonych momentach działania systemu GLPI. Na przykład, w przykładowym kodzie, ustawione jest, że wtyczka ma być zgodna z mechanizmem ochrony przed atakami CSRF (`$PLUGIN_HOOKS['csrf_compliant']['emptyplg'] = true;`).

### Informacje o Wersji Wtyczki
Funkcja `plugin_version_emptyplg()` zwraca podstawowe informacje o wtyczce, takie jak nazwa, wersja, autor, licencja, strona domowa i wymagania w odniesieniu do wersji GLPI. Te informacje są wykorzystywane przez system GLPI do wyświetlania danych o wtyczce w interfejsie użytkownika.

### Sprawdzanie Przed Instalacją
Funkcja `plugin_emptyplg_check_prerequisites()` umożliwia sprawdzenie, czy spełnione są wszelkie wymagania przed instalacją wtyczki. Chociaż w tym przykładzie zawsze zwraca `true`, w praktyce może zawierać różne sprawdzenia, na przykład czy zainstalowane są niezbędne zależności czy też czy wersja GLPI jest odpowiednia.

### Sprawdzanie Konfiguracji
Funkcja `plugin_emptyplg_check_config($verbose = false)` służy do sprawdzania, czy wtyczka jest poprawnie skonfigurowana. Może to obejmować różnorodne testy w zależności od potrzeb wtyczki, a wynik może zależeć od tego, czy funkcja została wywołana z parametrem `$verbose` ustawionym na `true` (wypisywanie komunikatów o błędach) czy `false`.

## README

Zwyczajowe informacje o zarządzaniu kodem wtyczki.

## LICENSE

Tekst licencji.

##   `hook.php`

Plik `hook.php` w kontekście wtyczki GLPI, jak wskazuje jego nazwa, zawiera definicje funkcji hook (z ang. "haczyki"), które są wywoływane w określonych momentach procesu instalacji lub odinstalowywania wtyczki. Wtyczki do GLPI wykorzystują takie pliki, aby zintegrować się z systemem GLPI, modyfikując jego zachowanie lub dodając nowe funkcjonalności bez bezpośredniego ingerowania w kod źródłowy GLPI. Oto analiza głównych części kodu w `hook.php` dla pustej wtyczki `emptyplg`:

### Nagłówek i Licencja
Podobnie jak w innych plikach wtyczki, na początku pliku znajduje się nagłówek z informacjami o prawach autorskich i licencji MIT. Licencja MIT jest jedną z najbardziej liberalnych licencji oprogramowania, pozwalając na szerokie wykorzystanie kodu, pod warunkiem zachowania informacji o prawach autorskich i tekście licencji.

### Funkcja Instalacji
Funkcja `plugin_emptyplg_install()` jest wywoływana, gdy wtyczka jest instalowana. W tym miejscu powinny znajdować się wszelkie operacje niezbędne do przygotowania wtyczki do pracy, takie jak inicjalizacja schematu bazy danych, tworzenie niezbędnych tabel lub rekordów, ustawianie domyślnych opcji itp. W podanym przykładzie funkcja po prostu zwraca `true`, co oznacza, że proces instalacji przebiegł pomyślnie bez żadnych dodatkowych działań.

### Funkcja Deinstalacji
Funkcja `plugin_emptyplg_uninstall()` jest wywoływana podczas odinstalowywania wtyczki. Jej zadaniem jest odwrócenie wszelkich zmian wprowadzonych w systemie podczas instalacji wtyczki, takich jak usuwanie tabel z bazy danych, usuwanie rekordów czy czyszczenie ustawień. Podobnie jak funkcja instalacji, w tym przykładzie funkcja ta również zwraca `true`, co sugeruje, że odinstalowanie zostało wykonane pomyślnie, choć bez faktycznego wykonania jakichkolwiek operacji.

### Ogólne Przeznaczenie Pliku `hook.php`
Plik `hook.php` w kontekście wtyczek GLPI służy do definiowania, jak wtyczka powinna być zainstalowana i odinstalowana. Jest to kluczowy element, który pozwala na bezpieczne dodawanie i usuwanie wtyczek, zapewniając, że wszystkie niezbędne kroki konfiguracji i dekonfiguracji są wykonane odpowiednio. W praktycznym zastosowaniu, implementacje tych funkcji mogą być znacznie bardziej złożone, zależnie od specyfiki i wymagań danej wtyczki.


