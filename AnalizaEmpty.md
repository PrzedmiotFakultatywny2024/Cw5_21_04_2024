# Analiza przykładowej wtyczki

![image](https://github.com/PrzedmiotFakultatywny2024/Cw5_21_04_2024/assets/24464854/69b6b42b-36e8-4c40-9124-c6af1d237fa7)

*Dalszy tekst częściowo generowany autoamtycznie.*

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

##   `emptyplg.xml`

Plik `emptyplg.xml` jest plikiem konfiguracyjnym dla pustej wtyczki (`emptyplg`) do systemu GLPI, który służy do definiowania metadanych wtyczki. Ten format pliku jest typowy dla wtyczek GLPI, umożliwiając łatwe zarządzanie i dystrybucję wtyczek. Oto omówienie głównych sekcji i elementów tego pliku XML:

### Elementy Główne
- **`<name>` i `<key>`**: Te elementy określają nazwę wtyczki (`emptyplg`). Nazwa i klucz są tutaj identyczne i służą do jednoznacznej identyfikacji wtyczki w systemie GLPI.
- **`<state>`**: Określa stan rozwoju wtyczki (`stable` w tym przypadku), co informuje użytkowników o gotowości i stabilności wtyczki. Możliwe wartości to między innymi `stable`, `beta`, `development`, `alpha`.
- **`<logo>`**: Adres URL do logotypu wtyczki, który może być wyświetlany w interfejsie użytkownika GLPI lub na stronach poświęconych wtyczce.

### Opis
- **`<description>`**: Zawiera krótki i długi opis wtyczki w różnych językach (`<en>` dla angielskiego, `<fr>` dla francuskiego). Pozwala to na dostarczenie użytkownikom informacji o celu i funkcjach wtyczki w ich ojczystym języku.

### Linki
- **`<homepage>`, `<download>`, `<issues>`, `<readme>`**: Te elementy zawierają linki do strony domowej wtyczki, strony pobierania, śledzenia błędów i pliku README. Są to kluczowe zasoby dla użytkowników i programistów, oferujące informacje, wsparcie i aktualizacje.

### Autorzy
- **`<authors>`**: Lista autorów wtyczki. Daje to uznanie osobom odpowiedzialnym za rozwój wtyczki.

### Wersje
- **`<versions>`**: Sekcja ta zawiera informacje o różnych wersjach wtyczki oraz o kompatybilności każdej z nich z wersjami GLPI. Umożliwia to użytkownikom identyfikację, która wersja wtyczki jest odpowiednia dla ich instalacji GLPI.

### Języki
- **`<langs>`**: Określa języki, dla których dostępne są tłumaczenia wtyczki, co ułatwia międzynarodowe użycie.

### Licencja
- **`<license>`**: Typ licencji, na której udostępniona jest wtyczka (`GPL V3+` w tym przypadku). Jest to ważne dla użytkowników i programistów, aby zrozumieć, jak mogą używać i modyfikować wtyczkę.

### Komentarze
- Sekcje zakomentowane (`<!--tags>` i `<!--screenshots>`): Choć aktualnie zakomentowane, mogą zostać użyte do dodania tagów opisowych i zrzutów ekranu dla wtyczki. Tagi pomagają w kategoryzacji i wyszukiwaniu wtyczki, a zrzuty ekranu mogą zapewnić wizualną prezentację funkcjonalności.


## `composer.json`

Plik `composer.json` jest plikiem konfiguracyjnym używanym przez Composer, który jest systemem zarządzania zależnościami dla PHP. Umożliwia on definiowanie bibliotek, od których zależy Twój projekt PHP, oraz zarządzanie nimi. W kontekście pustej wtyczki do GLPI, `composer.json` określa wymagania dotyczące środowiska oraz narzędzia potrzebne do rozwoju i testowania wtyczki. Oto omówienie głównych sekcji tego pliku:

### `require`
Sekcja `require` określa zależności, które są niezbędne do działania projektu w środowisku produkcyjnym. W tym przypadku jedyną zależnością jest wersja PHP – wymagana jest wersja 7.4 lub nowsza. To oznacza, że wtyczka nie będzie działać na starszych wersjach PHP, co jest istotne przy planowaniu wdrożenia lub aktualizacji środowiska.

### `require-dev`
Sekcja `require-dev` zawiera zależności, które są potrzebne tylko do rozwoju i testowania projektu, a nie są wymagane w środowisku produkcyjnym. Tutaj zależność `glpi-project/tools` w wersji co najmniej `^0.4` wskazuje na narzędzia deweloperskie specyficzne dla projektów GLPI, które mogą obejmować linter, formatowanie kodu, narzędzia do testowania itp. To pomaga w utrzymaniu jakości kodu i ułatwia współpracę między deweloperami.

### `config`
Sekcja `config` umożliwia dostosowanie różnych aspektów zachowania Composera:

- **`optimize-autoloader`**: Ustawienie to na `true` optymalizuje proces autoloadingu dla lepszej wydajności. To szczególnie ważne w produkcji, gdzie każda optymalizacja może przyczynić się do szybszego ładowania się strony.
- **`platform`**: Określa platformę docelową dla zależności. Tutaj wersja PHP jest ustawiona na `7.4.0`, co oznacza, że Composer będzie rozwiązywał zależności tak, jakby był uruchomiony na PHP 7.4.0, niezależnie od faktycznej wersji PHP używanej przez dewelopera. To zapewnia spójność zależności między różnymi środowiskami deweloperskimi.
- **`sort-packages`**: Gdy ustawione na `true`, polecenia takie jak `require` czy `update` będą dodawać i aktualizować zależności w `composer.json` w kolejności alfabetycznej, co poprawia czytelność i ułatwia zarządzanie zależnościami.

## `.gitignore`

Plik do ingorowanie niektórych rzeczy na githubie.

## `tools`

Dodatkowe narzędzia.
