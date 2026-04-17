# Changelog – SunGo Project Manager

[EN] All notable changes to the "SunGo Project Manager" extension are documented in this file.  
[PL] Wszystkie istotne zmiany w rozszerzeniu "SunGo Project Manager" są dokumentowane w tym pliku.


## [1.6.1] - 2026-04-17

### 🧰 Added / Dodano – Dual Repository Support / Obsługa Dual Repository
- Git Repository Module / Moduł repozytoriów Git: Added a dedicated module for managing multiple repositories without replacing native VS Code Git features / Dodano dedykowany moduł do zarządzania repozytoriami, który nie zastępuje systemowej obsługi Git w VS Code.
- Selective Deployment / Selektywne wysyłanie: Easily push selected files (via picker) to any external repository / Możliwość wysyłania wybranych plików (poprzez picker) do dowolnego zewnętrznego repozytorium.
- Binary Distribution / Publikacja binariów: Streamlined workflow for keeping source code in a private repository while publishing specific assets (like binaries) to a public one / Usprawniony proces utrzymywania kodu źródłowego w prywatnym repozytorium przy jednoczesnej publikacji wybranych zasobów (np. plików binarnych) w repozytorium publicznym.

---

## [1.5.5] - 2026-04-15

### 🛠️ Fixed / Naprawiono – Translation Fixes & Code Cleanup
- **38 UI & Content Changes / 38 zmian w UI i treści:** Refactored Snippet Manager library for professional consistency / Przebudowano bibliotekę Snippet Managera pod kątem spójności.
- **English Titles / Angielskie tytuły:** Snippet titles like "Custom Error Type", "Context with Timeout" are now standardized / Tytuły takie jak "Własny typ błędu" czy "Context z Timeout" zostały ujednolicone.
- **Code Harmonization / Harmonizacja kodu:** All `log.xxx`, `fmt.xxx`, and `errors.New` strings updated to English / Wszystkie stringi wewnątrz snippetów zmieniono na język angielski.
- **Comment Policy / Polityka komentarzy:** Source code comments unified to `// EN / PL` format / Komentarze w kodzie ujednolicono do formatu `// EN / PL` lub czystego angielskiego.
- **Code Cleanup / Porządki w kodzie:** General optimization of the internal logic / Ogólna optymalizacja logiki wewnętrznej.

### 📝 Added / Dodano – Snippet Editor / Edytor snippetów
- **New Category / Nowa kategoria:** Added "My Snippets" section at the end of the sidebar / Dodano sekcję "My Snippets" na końcu paska bocznego dla własnych wzorców.
- **Integrated UI / Zintegrowany interfejs:** New **+ Add Snippet** button opens a dedicated creation overlay / Nowy przycisk **+ Add Snippet** otwiera dedykowaną nakładkę tworzenia.
- **Custom Fields / Własne pola:** Support for Title, Description, Tags, and Go Code (green monospace) / Obsługa pól: Tytuł, Opis, Tagi oraz kod Go (zielony font monospace).
- **Persistence / Persystencja:** Snippets are saved to `globalStorage` (survive between sessions) / Snippety są zapisywane w `globalStorage` (dostępne między sesjami).
- **Management / Zarządzanie:** Implemented Delete functionality and background-click to close overlay / Wdrożono funkcję usuwania oraz zamykanie nakładki poprzez kliknięcie w tło.

---

## [1.5.0] - 2026-04-14

### Added / Dodano
- Snippet Manager: Organized code patterns (Goroutines, Context, etc.) with one-click insertion. / Manager Snippetów: Uporządkowane wzorce kodu z funkcją wstawiania jednym kliknięciem.

- Go Generate Runner: UI for scanning and running //go:generate with real-time output. / Go Generate Runner: Interfejs do skanowania i uruchamiania dyrektyw z podglądem na żywo.

### Fixed / Naprawiono
- Stability & Optimization: Resolved bugs from the test version and optimized tool performance. / Stabilność i optymalizacja: Naprawiono błędy wersji testowej i zoptymalizowano działanie narzędzi.

- UI & Focus: Fixed Webview focus issues in Snippet Manager and corrected message translations in both features. / UI i Focus: Naprawiono błędy z fokusem w Webview oraz poprawiono tłumaczenia komunikatów w obu nowych funkcjach.

---

## [1.4.0] - 2026-04-12

### Test version / Wersja testowa
- New features added (Experimental): Snippet Manager and Go Generate Runner for testing purposes. Note: This version contains several bugs as it is a snapshot of yesterday's tests. / Dodano nowe funkcje (Eksperymentalne): Manager Snippetów oraz Go Generate Runner w celu sprawdzenia działania. Uwaga: Wersja zawiera błędy, ponieważ pochodzi z wczorajszych testów.


## [1.2.2] - 2026-04-03
### Fixed / Naprawiono
- Message Translation Fixes – improved and corrected several UI message translations and notification strings to ensure better clarity in both English and Polish. / poprawki w tłumaczeniach komunikatów interfejsu oraz powiadomień, zapewniające większą spójność i jasność w języku polskim i angielskim.

## [1.1.1] - 2026-03-22
### Changed / Zmieniono
- **Optymize CODE**  - Code refaktor and function optymize header Generator/ refaktoryzacja kodu i optymalizacja funkcji generatora nagłówków.


## [1.1.1] - 2026-03-22

### Changed / Zmieniono
- **NLS Keys for SunGo Tools View** – added dedicated short-form translation keys for all items in the SunGo Tools View panel. Labels now respect the VS Code language setting: English or Polish . / dodano dedykowane krótkie klucze tłumaczeń dla wszystkich pozycji w panelu SunGo Tools View. Etykiety respektują teraz ustawienie języka VS Code.

## [1.1.0] – 2026-03-22

### Added / Dodano
- **SunGo Tools View** – new panel in the Explorer sidebar (below GO and PACKAGE OUTLINE) with a clickable list of all SunGo tools: Binary Analyzer, Go Vet, Build Diff, Dependencies, Profiler, Code Metrics, Project Notes, Header Generator. Accessible from any location in VS Code without switching to the SunGo project tree. / nowy panel w pasku eksploratora z klikalną listą wszystkich narzędzi SunGo. Dostępny z każdego miejsca w VS Code bez przełączania się do drzewa projektów.

### Changed / Zmieniono
- **Settings grouped into sections** – VS Code Settings (`Ctrl+,`) now shows SunGo configuration split into 4 dedicated sections: **SunGo – Build**, **SunGo – File Header**, **SunGo – Code Metrics**, **SunGo – Security**. Each section is independently expandable in the left panel. / ustawienia SunGo podzielone na 4 dedykowane sekcje w `Ctrl+,`: Build, File Header, Code Metrics, Security.
- **Active project icon** – the active project in the Tree View now shows a green `$(folder-active)` icon with `charts.green` color. Previously used `$(go-logo)` which did not support color theming. / aktywny projekt w drzewie pokazuje teraz zieloną ikonę `$(folder-active)`. Poprzednia ikona `$(go-logo)` nie obsługiwała kolorowania.
- **Inline icons reduced** – Tree View inline icons reduced from 7 to 3 (Binary Analyzer, Go Vet, Build Diff). Remaining tools available in the new SunGo Tools View. / ikony inline w drzewie projektów zredukowane z 7 do 3. Pozostałe narzędzia dostępne w nowym panelu SunGo Tools.
- **Dashboard icons unified** – Header Generator, Project Notes and Code Metrics icons in the Dashboard header now use Codicons (`settings-link` style) matching PAD Settings and VS Code Settings icons. / ikony Header Generator, Project Notes i Code Metrics w nagłówku Dashboardu używają teraz Codicons w stylu zgodnym z ikonami ustawień.

---


### This is v1.0.0 / To jest v1.0.0
After months of development SunGo Project Manager reaches its first stable milestone. The extension covers the full Go development lifecycle: project creation, build, run, test, analysis, profiling, dependency management, code quality metrics, cross-compilation, file headers and physical hardware feedback via SunGO PAD. / Po miesiącach rozwoju SunGo Project Manager osiąga pierwszy stabilny milestone. Wtyczka obejmuje pełny cykl życia projektu Go: tworzenie, build, run, testy, analizę, profilowanie, zarządzanie zależnościami, metryki jakości kodu, cross-compilation, nagłówki plików i fizyczny feedback przez SunGO PAD.

## [1.0.0] – 2026-03-22

### Added / Dodano
- **Project Notes** – new `SunGo: Open Project Notes` command accessible via the `$(notebook)` icon in the Tree View, Dashboard, and Command Palette. Creates `.vscode/sungo_notes.md` with a structured template (TODO, Ideas, Notes) on first use and opens it directly in the VS Code editor. / nowa komenda `SunGo: Open Project Notes` dostępna przez ikonę `$(notebook)` w drzewie projektów, Dashboardzie i palecie komend. Tworzy `.vscode/sungo_notes.md` z szablonem (TODO, Ideas, Notes) przy pierwszym użyciu i otwiera bezpośrednio w edytorze VS Code.
- **Code Metrics & Refactoring Hints** – new `metricsView.ts` panel accessible via the `$(dashboard)` icon in the Tree View and Dashboard. Recursively scans all `.go` files in the project (excluding `vendor/`, `bin/`, `.git/`) and displays: file/function count, total LOC, per-function metrics (LOC, parameters, nesting depth, godoc presence), and actionable refactoring hints with severity indicators 🟢🟡🔴. Clicking any function, file or hint navigates directly to that location in the editor. Thresholds configurable in `Ctrl+,`. / nowy panel `metricsView.ts` dostępny przez ikonę `$(dashboard)`. Rekurencyjnie skanuje pliki `.go` projektu i wyświetla metryki per plik i funkcja (LOC, parametry, zagnieżdżenie, godoc) oraz sugestie refaktoringu z nawigacją do kodu jednym kliknięciem.

---


## [0.9.0] – 2026-03-21

### Added / Dodano
- **File Header Generator** – new `headerGen.ts` module with 5 built-in styles: **Fancy Box** (Unicode border ╔═╗), **Box** (/****/), **Block** (/* */), **Line** (//), **Minimal** (single line), plus **Custom** (user-defined template with tokens) and **None**. / nowy moduł `headerGen.ts` z 5 wbudowanymi stylami: **Fancy Box** (ramka Unicode ╔═╗), **Box**, **Block**, **Line**, **Minimal**, **Custom** (szablon użytkownika z tokenami) i **None**.
- **Live Preview panel** – accessible via `SunGo: Header Generator` command. Shows a live preview of the header as style or settings change. Insert button wires directly into the active editor at line 0. / panel z podglądem live dostępny przez komendę `SunGo: Header Generator`. Podgląd aktualizuje się na żywo przy zmianie stylu lub ustawień. Przycisk Insert wstawia nagłówek do aktywnego edytora.
- **Insert Header command** – `SunGo: Insert File Header` available in the Command Palette and via right-click on any `.go` file in the Explorer. Inserts the header using the currently configured style. / komenda `SunGo: Insert File Header` dostępna w palecie komend i przez prawy klik na pliku `.go` w eksploratorze. Wstawia nagłówek zgodnie z aktualnie skonfigurowanym stylem.
- **Auto-insert on new file** – when `sungo.header.autoInsert` is enabled, SunGo automatically inserts the configured header whenever a new `.go` file is created. / gdy `sungo.header.autoInsert` jest włączone, SunGo automatycznie wstawia nagłówek przy każdym nowym pliku `.go`.
- **Header style in Project Creator** – the New Project wizard now includes a header style selector; the chosen style is applied to `main.go` immediately on project creation. / kreator nowego projektu zawiera teraz wybór stylu nagłówka; wybrany styl jest stosowany do `main.go` bezpośrednio przy tworzeniu projektu.
- **Custom template tokens** – the custom style supports tokens: `{project}`, `{file}`, `{author}`, `{team}`, `{website}`, `{forum}`, `{github}`, `{version}`, `{license}`, `{date}`, `{year}`. Tokens are clickable in the panel UI. / styl Custom obsługuje tokeny klikalne w panelu.
- **Global header settings** (`Ctrl+,`) – `sungo.header.author`, `sungo.header.team`, `sungo.header.website`, `sungo.header.forum`, `sungo.header.license`, `sungo.header.style`, `sungo.header.autoInsert`, `sungo.header.customTemplate`. GitHub/module path is read automatically from `go.mod`. / ustawienia globalne nagłówka w `Ctrl+,`. Ścieżka GitHub czytana automatycznie z `go.mod`.

---

## [0.8.1] – 2026-03-15

### Fixed / Naprawiono
- **SunGO PAD – Win+R → sungo not working after VS Code update** – `checkHardware()` now verifies whether `WindowsApps` is present in the user PATH after creating `sungo.cmd`. If missing, SunGo automatically adds the path permanently via `SetEnvironmentVariable` (User level, no admin required) and shows an informational notification. Fixes a regression caused by VS Code updates resetting the App Execution Aliases environment. / `checkHardware()` sprawdza teraz czy `WindowsApps` jest obecny w PATH użytkownika po utworzeniu `sungo.cmd`. Jeśli brakuje, SunGo automatycznie dodaje ścieżkę trwale przez `SetEnvironmentVariable` (poziom User, bez uprawnień administratora) i wyświetla powiadomienie. Naprawia regresję spowodowaną przez aktualizacje VS Code resetujące środowisko App Execution Aliases.

## [0.8.0] – 2026-03-14

### Added / Dodano
- **SunGo Profiler (pprof)** – new panel accessible via the `$(pulse)` icon in the Project Tree View (active project only). Analyzes CPU and memory profiles generated by the Go `runtime/pprof` package. / nowy panel dostępny przez ikonę `$(pulse)` w drzewie projektów (tylko aktywny projekt). Analizuje profile CPU i pamięci generowane przez pakiet `runtime/pprof`.
- **Auto-detection of profile files** – SunGo automatically detects `cpu.prof` and `mem.prof` in the project root and loads them on panel open. / SunGo automatycznie wykrywa pliki `cpu.prof` i `mem.prof` w katalogu projektu i ładuje je przy otwarciu panelu.
- **Top 20 table** – displays the top 20 functions by CPU time or memory allocation with visual percentage bars, flat and cumulative values. UI unified with Binary Analyzer style. / tabela top 20 funkcji według czasu CPU lub alokacji pamięci z wizualnymi paskami procentowymi, wartościami flat i cumulative. Styl ujednolicony z Binary Analyzer.
- **Flame Graph** – generates a call graph SVG via `go tool pprof -svg` (requires Graphviz). The graph is limited to nodes >1% (`-nodefraction=0.01`) for readability. Supports zoom (scroll wheel) and pan (drag) directly in the webview. / generuje graf wywołań SVG przez `go tool pprof -svg` (wymaga Graphviz). Graf ograniczony do węzłów >1% dla czytelności. Obsługuje zoom (kółko myszy) i przesuwanie (drag) bezpośrednio w webview.
- **Open in Browser** – button to open the flame graph SVG in the system browser for full-resolution viewing and saving. / przycisk otwierający flame graph SVG w przeglądarce systemowej dla pełnej rozdzielczości i możliwości zapisu.
- **Graphviz detection** – if Graphviz is not installed, SunGo shows a platform-specific installation hint (`winget` / `apt` / `brew`) instead of the flame graph section. / jeśli Graphviz nie jest zainstalowany, SunGo wyświetla wskazówkę instalacji per platforma zamiast sekcji flame graph.
- **Profiling snippets** – welcome screen displays ready-to-paste CPU and MEM code snippets with a one-click Copy button, guiding the user to instrument their `main.go`. / ekran powitalny wyświetla gotowe snippety CPU i MEM z przyciskiem kopiowania, prowadząc użytkownika przez instrumentację `main.go`.
- **File picker** – allows loading any `.prof` file from the project directory, not limited to the default filenames. / możliwość wczytania dowolnego pliku `.prof` z katalogu projektu, nie tylko domyślnych nazw.

### Fixed / Naprawiono
- **SunGo Terminal – yellow warning triangle** – added `env`, `strictEnv: false` and `hideFromUser: false` to `createTerminal()` options in `getSunGoTerminal()`. VS Code no longer flags the terminal as incomplete when Git and other extensions haven't injected their environment yet. Additionally unified `formatGoProject` to use `getSunGoTerminal()` instead of a direct `createTerminal()` call. / dodano `env`, `strictEnv: false` i `hideFromUser: false` do opcji `createTerminal()` w `getSunGoTerminal()`. VS Code nie flaguje już terminala jako niekompletnego gdy Git i inne rozszerzenia nie zdążyły wstrzyknąć swojego środowiska. Ujednolicono również `formatGoProject` do używania `getSunGoTerminal()` zamiast bezpośredniego `createTerminal()`.

---

## [0.7.2] – 2026-03-07

### Fixed / Naprawiono
- **CGO Detection during Cross-Compilation** – SunGo now scans `go.mod` for known CGO-dependent libraries (Raylib, Fyne, Qt, SDL2, OpenGL/GLFW, SQLite, GTK3) and additionally checks `src/*.go` files for `import "C"`. When CGO is detected, cross-compilation is blocked before the build starts and the user receives a platform-specific message explaining what toolchain is required (e.g. `mingw-w64` for Linux→Windows, `osxcross` for Linux→macOS). A button linking to setup documentation is provided. / SunGo skanuje teraz `go.mod` pod kątem znanych bibliotek wymagających CGO (Raylib, Fyne, Qt, SDL2, OpenGL/GLFW, SQLite, GTK3) oraz sprawdza pliki `src/*.go` pod kątem `import "C"`. Gdy CGO zostanie wykryte, cross-kompilacja jest blokowana przed startem builda, a użytkownik otrzymuje komunikat z informacją jakiego toolchaina potrzebuje dla danej kombinacji platform. Dostępny jest przycisk z linkiem do dokumentacji konfiguracji.

---
## [0.7.1] - 2026-03-07

### Fixed / Naprawiono
- **Cross-Compilation on Linux** – replaced relative output path (`./bin/cross/...`) with an absolute path built by `path.join()`; the relative path was causing `compilation error` on Linux when targeting any non-`auto` platform. Windows behavior is unchanged. / zastąpiono relatywną ścieżkę wyjściową (`./bin/cross/...`) ścieżką absolutną budowaną przez `path.join()`; relatywna ścieżka powodowała błąd kompilacji na Linuxie przy wyborze dowolnej platformy innej niż `auto`. Zachowanie na Windows pozostaje bez zmian.

---


## [0.7.0] – 2026-03-07

### Added / Dodano
- **Cross-Compilation Support** – new settings `sungo.build.targetOS` (`auto` / `windows` / `linux` / `darwin`) and `sungo.build.targetArch` (`amd64` / `arm64` / `arm`) in Extension Settings (`Ctrl+,`). When a non-`auto` OS is selected, SunGo sets `GOOS`, `GOARCH` and `CGO_ENABLED=0` in the build environment and outputs the binary to `bin/cross/` with a platform suffix (e.g. `MyApp_linux_amd64`). The native build path and behavior remain unchanged when `auto` is selected. / nowe ustawienia `sungo.build.targetOS` i `sungo.build.targetArch` w ustawieniach rozszerzenia (`Ctrl+,`). Przy wyborze konkretnego systemu SunGo ustawia `GOOS`, `GOARCH` i `CGO_ENABLED=0` i zapisuje binarkę do `bin/cross/` z sufiksem platformy. Natywny build pozostaje niezmieniony przy ustawieniu `auto`.
- **CGO Warning** – when cross-compiling, SunGo automatically checks for CGO usage (`go list -f '{{.CgoFiles}}'`) and displays a warning notification if CGO is detected, alerting the user that a cross-compiler toolchain may be required. / przy cross-kompilacji SunGo automatycznie sprawdza użycie CGO i wyświetla ostrzeżenie jeśli CGO zostało wykryte w projekcie.
- **Build Diff & Timeline** – new panel (`BuildDiffView`) accessible via the `$(git-compare)` inline icon in the Project Tree View (active project only). Allows selecting any two builds from history and comparing them: tables of Grown / Shrunk / Added / Removed symbols (top 20 each), summary bar with size delta and build times, and a scrollable Build Timeline showing the last 10 builds. UI unified with Binary Analyzer (dark theme, gold/green accents, `.card` layout). / nowy panel dostępny przez ikonę `$(git-compare)` w drzewie projektów. Porównuje dowolne dwa buildy: tabele symboli większych/mniejszych/nowych/usuniętych (top 20), pasek podsumowania z deltą rozmiaru i czasami buildów, oraz przewijana historia ostatnich 10 buildów.
- **Build Time Tracker** – every build now records its compilation duration in the history snapshot; build times are displayed in the Binary Analyzer history table, Build Diff summary bar, and Build Timeline. / każdy build zapisuje teraz czas kompilacji w historii; wyświetlany w Analizatorze, Build Diff i Timeline.
- **Symbol Snapshots** – after each successful build SunGo saves a symbol snapshot (`.vscode/.sungo_symbols_N.json`) enabling cross-build symbol-level diffing; up to 10 snapshots are retained automatically. / po każdym buildzie SunGo zapisuje snapshot symboli umożliwiający porównanie na poziomie symboli; przechowywanych jest maksymalnie 10 ostatnich.
- **Active Project Highlighting** – the active project in the Tree View now displays a green `$(go-logo)` icon instead of the default folder icon; inline action icons (`$(graph)`, `$(bug)`, `$(library)`, `$(git-compare)`) are visible only for the active project, keeping the tree clean for inactive ones. / aktywny projekt w drzewie wyróżniony jest teraz zieloną ikoną `$(go-logo)`; ikony akcji inline widoczne wyłącznie przy aktywnym projekcie.

---


## [0.6.0] – 2026-03-06

### Added / Dodano
- **Dependency Viewer** – a brand new dedicated panel (`DependenciesView`) accessible via the `$(library)` icon in the Project Tree View. Displays all project dependencies from `go.mod` with module path, installed version, available update, dependency type (direct/indirect), and one-click actions. / nowy dedykowany panel (`DependenciesView`) dostępny przez ikonę `$(library)` w drzewie projektów. Wyświetla wszystkie zależności projektu z `go.mod` wraz ze ścieżką modułu, zainstalowaną wersją, dostępną aktualizacją, typem zależności (direct/indirect) oraz akcjami jednym kliknięciem.
- **Update Detection** – the Dependency Viewer uses `go list -u -m -json all` to check for newer versions of every dependency; the Update column shows 🟢 when a package is current and 🔴 `vX.Y.Z` when a newer release is available on the registry. / panel zależności używa `go list -u -m -json all` do sprawdzania nowszych wersji każdej zależności; kolumna Update pokazuje 🟢 gdy pakiet jest aktualny i 🔴 `vX.Y.Z` gdy dostępna jest nowsza wersja w rejestrze.
- **One-Click Update** – each outdated dependency gets an ⬆️ button in the Actions column; clicking it runs `go get -u <module>` followed by `go mod tidy` automatically. The **Update All** button updates the entire dependency tree at once. / każda nieaktualna zależność otrzymuje przycisk ⬆️ w kolumnie Actions; kliknięcie uruchamia `go get -u <moduł>` a następnie automatycznie `go mod tidy`. Przycisk **Update All** aktualizuje całe drzewo zależności jednocześnie.
- **Binary Size Alert** – new configuration option `sungo.build.maxSizeMB` (default: `0` = disabled). When the compiled binary exceeds the defined threshold, SunGo displays a warning notification and flashes the SunGO PAD purple (3 times) as a physical alert signal. / nowa opcja konfiguracji `sungo.build.maxSizeMB` (domyślnie: `0` = wyłączona). Gdy skompilowana binarka przekroczy zdefiniowany próg, SunGo wyświetla powiadomienie ostrzegawcze i trzykrotnie miga PAD na fioletowo jako fizyczny sygnał alarmowy.
- **Go Vet Integration** – new `SunGo: Go Vet` command accessible via right-click on `main.go` in the Explorer and via the `$(bug)` icon in the Project Tree View. Runs `go vet ./...` across the entire project and reports results in a dedicated `SunGo: Go Vet` Output Channel; PAD flashes green on clean code, red on issues. / nowa komenda `SunGo: Go Vet` dostępna przez prawy klik na `main.go` w eksploratorze oraz przez ikonę `$(bug)` w drzewie projektów. Uruchamia `go vet ./...` dla całego projektu i raportuje wyniki w dedykowanym kanale `SunGo: Go Vet`; PAD miga zielono gdy kod jest czysty, czerwono gdy wykryto problemy.
- **PAD Flash API** – new `flash(command, times)` method on `PadDevice`; sends a color command N times with restore between each pulse. Used by Binary Size Alert and Go Vet for physical feedback without permanently changing the key colors. / nowa metoda `flash(command, times)` w `PadDevice`; wysyła komendę koloru N razy z przywróceniem kolorów między każdym pulsem. Używana przez alert rozmiaru i Go Vet do fizycznego feedbacku bez trwałej zmiany kolorów klawiszy.


## [0.5.6] – 2026-03-05

### Added / Dodano
- **Your Code Breakdown** – the Details panel in the Binary Analyzer now shows a granular breakdown of all functions and variables defined in your `main` package, sorted by size with visual bar indicators and byte-accurate measurements. / panel szczegółów w Analizatorze Binarnym prezentuje teraz szczegółowy rozkład wszystkich funkcji i zmiennych zdefiniowanych w pakiecie `main`, posortowanych według rozmiaru z wizualnymi paskami i dokładnymi wartościami w bajtach.
- **Analyzer on Status Bar Click** – clicking the binary size indicator in the Status Bar now opens both the `/bin` folder in the system explorer and the Binary Analyzer panel simultaneously. / kliknięcie wskaźnika rozmiaru binarki na pasku stanu otwiera teraz jednocześnie folder `/bin` w eksploratorze systemowym oraz panel Binary Analyzer.
- **Inverted Symbol Parser Logic** – rewrote the `go tool nm` symbol categorization engine using an inverted whitelist approach: only known Go symbols are classified explicitly; everything else falls into `External C / Libs`. This makes the analyzer future-proof for any C library (Raylib, Fyne, Ebitengine, SDL…) without manual updates. / przepisano silnik kategoryzacji symboli `go tool nm` na odwróconą logikę białej listy: tylko znane symbole Go są klasyfikowane wprost; reszta trafia do `External C / Libs`. Analyzer działa poprawnie z każdą biblioteką C bez konieczności ręcznych aktualizacji.

### Fixed / Naprawiono
- **Symbol Size Parser (PE Constants)** – fixed a critical bug where Windows PE constants such as `__size_of_stack_reserve__` (value: ~5 GB) were parsed as symbol sizes, causing `External C / Libs` to show 99–100% across all projects. / naprawiono krytyczny błąd, w którym stałe PE systemu Windows takie jak `__size_of_stack_reserve__` (wartość: ~5 GB) były parsowane jako rozmiary symboli, powodując wyświetlanie 99–100% dla `External C / Libs` we wszystkich projektach.
- **DWARF Debug Sections Excluded** – `.debug_info`, `.debug_line`, `.debug_loclists` and other DWARF sections are now properly skipped during analysis, eliminating multi-megabyte false positives in size calculations. / sekcje DWARF takie jak `.debug_info`, `.debug_line`, `.debug_loclists` są teraz poprawnie pomijane podczas analizy, eliminując fałszywe wielomegabajtowe wartości w obliczeniach rozmiaru.
- **Full i18n Coverage** – all hardcoded strings in the Analyzer panel and Status Bar tooltips are now routed through the NLS localization system with full Polish and English parity. / wszystkie zahardkodowane ciągi znaków w panelu Analyzera i tooltipach paska stanu są teraz obsługiwane przez system lokalizacji NLS z pełną obsługą języka polskiego i angielskiego.

## [0.5.5] - 2026-03-05

### Fixed / Poprawiono 
- **Chart Data Stream Integrity** – resolved issues with data transmission to charts, ensuring binary composition and history trends render correctly under all conditions. / naprawiono przesył danych do wykresów, zapewniając poprawne wyświetlanie składu binarki oraz trendów historii w każdych warunkach.

- **Missing Container Translations (i18n)** – integrated missing localization keys for UI containers and section headers, enabling full language parity between English and Polish. / uzupełniono brakujące tłumaczenia kontenerów oraz nagłówków sekcji, zapewniając pełną spójność językową między wersją angielską a polską.


## [0.5.3] – 2026-03-05

### Added / Dodano
- **Binary Optimization Toggle** – added a new configuration option in Extension Settings (`ctrl+,`) to enable/disable `-s -w` linker flags; allowing users to choose between minimal binary size and full symbol visibility for analysis. / dodano nową opcję konfiguracji w ustawieniach rozszerzenia (`ctrl+,`) do włączania/wyłączania flag linkera `-s -w`; pozwala to użytkownikom wybierać między minimalnym rozmiarem binarki a pełną widocznością symboli do analizy.
- **Detailed Component Breakdown** – implemented a  Details view in the Analyzer panel that provides a granular look at binary sections, libraries, and their percentage impact on the total file size. / zaimplementowano widok "Szczegóły" w panelu analizatora, który zapewnia szczegółowy wgląd w sekcje binarne, biblioteki i ich procentowy wpływ na całkowity rozmiar pliku.
- **Symbol Awareness & Warnings** – the UI now dynamically detects if a binary was stripped of symbols and displays a warning, guiding users to adjust their optimization settings if detailed data is unavailable. / interfejs dynamicznie wykrywa, czy binarka została oczyszczona z symboli i wyświetla ostrzeżenie, kierując użytkowników do zmiany ustawień optymalizacji w przypadku braku szczegółowych danych.

### Fixed / Naprawiono
- **Responsive "One-Column" Wrap** – optimized the grid to correctly drop the doughnut chart to a single column layout on narrow windows, ensuring full readability of the new details panel. / zoptymalizowano układ, aby wykres pierścieniowy poprawnie przeskakiwał do jednej kolumny na wąskich oknach, zapewniając pełną czytelność nowego panelu szczegółów.


## [0.5.0] – 2026-03-04

### Added / Dodano
- **Advanced Binary Analysis UI** – completely redesigned the Binary Analyzer panel with a modern, data-driven layout. Includes specialized sections for byte-watch reports and build history. / całkowicie przeprojektowany panel analizatora binarnego z nowoczesnym układem danych. Zawiera sekcje raportów "byte-watch" oraz pełną historię buildów.
- **Interactive Data Visualization** – integrated `Chart.js` to provide real-time visual feedback:
  - **Size History Trend**: A line chart visualizing binary size changes over time. / wykres liniowy wizualizujący zmiany rozmiaru binarki w czasie.
  - **Binary Composition**: A doughnut chart breaking down the executable into Runtime, Standard Libs, External Libs, and User Code. / wykres pierścieniowy pokazujący skład pliku (Runtime, biblioteki, kod użytkownika).

## [0.4.5] – 2026-03-03

### Added / Dodano
- **Binary Size Analyzer (Status Bar)** – real-time tracking of executable size after each successful build; includes trend indicators (▲/▼) to visualize code optimization or growth. / śledzenie rozmiaru pliku wykonywalnego w czasie rzeczywistym na pasku stanu; zawiera wskaźniki trendu (▲/▼) pozwalające wizualizować optymalizację lub wzrost kodu.
- **Smart Color Coding** – the status bar size info turns green when the binary is optimized (smaller) and orange/red when it grows, providing instant feedback for developers. / informacja o rozmiarze na pasku stanu zmienia kolor na zielony przy optymalizacji (zmniejszeniu) i pomarańczowy/czerwony przy wzroście, dając natychmiastowy feedback.
- **Quick Bin Access** – clicking the size indicator on the status bar now opens the project's `bin` folder directly in the system explorer. / kliknięcie wskaźnika rozmiaru otwiera folder `bin` projektu bezpośrednio w systemowym eksploratorze.

## [0.4.2] - 2026-03-02

### Fixed / Naprawiono
- **Dashboard Tool Detection Logic** – expanded the diagnostic engine to correctly recognize "No Finding..." status; this fix ensures the "Install GCC (MSYS2)" button appears reliably when the compiler is missing, regardless of the system's localization strings. / rozbudowano silnik diagnostyczny o poprawne rozpoznawanie statusu "No Finding..."; poprawka gwarantuje, że przycisk "Zainstaluj GCC (MSYS2)" pojawia się niezawodnie w przypadku braku kompilatora, niezależnie od lokalizacji systemowej.

## [0.4.1] – 2026-03-02

### Added / Dodano
- **Automated MinGW GCC Installation** – integrated MSYS2 environment setup directly from the Dashboard; users can now install the C compiler (required for CGO) with a single click if it is missing. / zintegrowano konfigurację środowiska MSYS2 bezpośrednio z poziomu Dashboardu; użytkownicy mogą teraz zainstalować kompilator C (wymagany dla CGO) jednym kliknięciem, jeśli go brakuje.
- **Enhanced `launch.json` Generator** – added new configurations to the project creator to support more precise debugger paths and better environment integration. /dodano nowe konfiguracje do kreatora projektów, wspierające precyzyjne ścieżki debuggera i lepszą integrację ze środowiskiem.

### Fixed / Naprawiono
- **Debug (F5) Stability** – optimized the launch sequence and path mapping to ensure that pressing F5 starts the debugging session reliably across different project structures. / zoptymalizowano sekwencję uruchamiania i mapowanie ścieżek, aby naciśnięcie klawisza F5 niezawodnie uruchamiało sesję debugowania w różnych strukturach projektów.

---

## [0.4.0] – 2026-03-01

### Added / Dodano
- **Dashboard Layout Redesign** – redesigned the main panel layout; Active Projects and Security & System are now stacked in the left column, while Installed Tools occupies the full right column for better use of screen space. / przeprojektowano układ głównego panelu; Active Projects i Security & System są teraz ułożone w lewej kolumnie, a Installed Tools zajmuje całą prawą kolumnę dla lepszego wykorzystania przestrzeni ekranu.

### Fixed / Naprawiono
- **PAD LED Brightness Persistence** – fixed an issue where the PAD would boot at full brightness regardless of the saved slider value; brightness is now restored from `globalState` immediately on panel open and on every PAD reconnect. / naprawiono problem, w którym PAD uruchamiał się z pełną jasnością niezależnie od zapisanej wartości suwaka; jasność jest teraz przywracana z `globalState` natychmiast po otwarciu panelu i przy każdym ponownym podłączeniu PAD-a.

## [0.3.12] – 2026-03-01
### Added / Dodano
- **Gopher Wisdom System** – integrated a professional Go tips engine. Click the blinking Gopher in the Dashboard to see expert advice in a dedicated "SunGo Gopher" Output channel. / zintegrowano silnik profesjonalnych porad Go. Kliknij mrugającego Gophera w Dashboardzie, aby zobaczyć rady eksperckie w dedykowanym kanale "SunGo Gopher".

## [0.3.11] – 2026-03-01
### Added / Dodano
- **Visual Demo (GIF)** – added a high-quality animated demonstration to the README to showcase the extension's core workflow instantly. / dodano wysokiej jakości animację demonstracyjną do pliku README, prezentującą kluczowe funkcje wtyczki.
- **Gopher Tips (Gopher Rules)** – introduced a new documentation section highlighting professional Go practices like binary headers and -s -w optimization. / wprowadzono nową sekcję dokumentacji "Porady Gofera", podkreślającą profesjonalne praktyki Go, takie jak binarne nagłówki i optymalizacja -s -w.
- **"Philosophy & JetBrains-like Experience"** - section to README. / Dodano sekcję filozofii i komfortu pracy do README.

### Changed / Zmieniono
- **Documentation Overhaul** – restructured the README for better scannability and clarity regarding standalone functionality versus optional hardware (SunGO PAD). / zreorganizowano plik README w celu poprawy czytelności i jasnego rozdzielenia samodzielnej funkcjonalności wtyczki od opcjonalnego sprzętu (SunGO PAD).

## [0.3.10] – 2026-02-27

### Fixed / Naprawiono
- **Path Case-Sensitivity** – fixed an issue where the README file could not be opened on Linux systems due to case-sensitivity / naprawiono problem z otwieraniem pliku README.
- **Layout Adjustments** – refined the position of the Linux configuration box for better visual hierarchy within the settings panel. / dopracowano położenie sekcji konfiguracji Linux w celu uzyskania lepszej hierarchii wizualnej w panelu ustawień.

## [0.3.9] – 2026-02-27

### Added / Dodano
- **Linux udev setup guide** – PAD color settings panel now includes a built-in Linux configuration guide with a direct link to README instructions / panel ustawień kolorów PAD zawiera teraz wbudowany przewodnik konfiguracji dla Linuxa z bezpośrednim linkiem do instrukcji w README

## [0.3.8] – 2026-02-26

### Added / Dodano
- **Full Linux PAD Support** – SunGO PAD now works natively on Linux via HID RAW / SunGO PAD działa teraz natywnie na Linuxie przez HID RAW
- **Linux keybindings (F13–F20)** – keys 2–9 send `Ctrl+Shift+F13–F20` on Linux to avoid terminal conflicts / klawisze 2–9 wysyłają `Ctrl+Shift+F13–F20` na Linuxie eliminując konflikty z terminalem

### Fixed / Naprawiono
- **Terminal crash on Linux** – removed forced `pwsh` shell path that caused terminal creation to fail silently on Linux / usunięto wymuszoną ścieżkę `pwsh` powodującą ciche błędy tworzenia terminala na Linuxie
- **LEDs not lighting on Linux** – fixed HID byte offset mismatch between Windows and Linux `hidraw` driver / naprawiono przesunięcie bajtów HID między sterownikiem Windows a Linux `hidraw`


## [0.3.6] – 2026-02-25

### Added / Dodano
- **Linux PAD Support** – SunGO PAD now fully supports Linux via firmware OS toggle / SunGO PAD obsługuje teraz w pełni system Linux dzięki przełącznikowi OS w firmware
- **OS Toggle (1+7+9)** – press keys 1+7+9 simultaneously to switch between Windows and Linux mode; setting is saved permanently in PAD flash memory / naciśnij jednocześnie klawisze 1+7+9 aby przełączyć między trybem Windows a Linux; ustawienie zapisywane trwale w pamięci flash PAD-a
  - 🔵 3 blue flashes = Windows mode (Win+R → `sungo.cmd`) / 3 niebieskie mignięcia = tryb Windows
  - 🔴 3 red flashes = Linux mode (Alt+F2 → `sungo`) / 3 czerwone mignięcia = tryb Linux
- **Auto script creation on Linux** – on first PAD connection the extension automatically creates `~/bin/sungo` launch script / przy pierwszym podłączeniu PAD-a wtyczka automatycznie tworzy skrypt startowy `~/bin/sungo`

### Changed / Zmieniono
- **Easter Egg** – now opens in the system browser instead of VS Code Webview panel / Easter Egg otwiera się teraz w przeglądarce systemowej zamiast w panelu Webview VS Code
- **`padDevice.ts`** – `checkHardware()` now detects OS and creates appropriate launch script (Windows: `sungo.cmd`, Linux: `~/bin/sungo`) / `checkHardware()` wykrywa system i tworzy odpowiedni skrypt startowy

### Fixed / Naprawiono
- **Cross-platform URI** – replaced `vscode.Uri.parse()` with `vscode.Uri.file()` for correct URI handling on Linux / zastąpiono `vscode.Uri.parse()` przez `vscode.Uri.file()` dla poprawnej obsługi URI na Linuxie


## [0.3.4] – 2026-02-24

### Fixed / Poprawiono
- **README.md** – updated and restructured documentation / aktualizacja i reorganizacja dokumentacji
- **Minor cosmetic fixes** – translation corrections in the codebase / drobne poprawki tłumaczeń w kodzie

---

## [0.3.3] – 2026-02-23

### Fixed / Poprawiono
- **PAD command handling** – fixed PAD commands on Linux / poprawiono obsługę komend PAD w systemie Linux
- **Code cleanup** – refactoring and performance improvements / refaktoryzacja kodu i poprawa wydajności

---

## [0.3.2] – 2026-02-22

### Changed / Zmieniono
- **Easter Egg** – replaced with a brand new demoscene-style Easter Egg / zastąpiono nowym, typowym dla demosceny Easter Eggiem

---

## [0.3.1] – 2026-02-21

### Added / Dodano
- **LED Brightness Control** – smooth brightness adjustment for PAD LEDs via a dedicated slider in the MacroPad settings panel; 0 turns off the LEDs, 100% is maximum (approximately 60% effective due to USB port power limits) / płynna regulacja jasności diod LED Pada przez suwak w panelu ustawień MakroPada; 0 wyłącza diody, 100% to maksimum (ok. 60% efektywne ze względu na limit mocy portu USB)

### Fixed / Poprawiono
- **HOME panel registration bug** – fixed an error in function registration that prevented the Home panel from opening correctly / poprawka błędu rejestracji funkcji uniemożliwiającego poprawne otwieranie panelu HOME

---

## [0.3.0] – 2026-02-20

### Added / Dodano
- **Intelligent PAD Color Management** – introduced a color priority system; the PAD first checks `globalState` cache and falls back to a new default palette (Indigo, White, Green…) if no stored state is found / wprowadzono system priorytetów kolorów; PAD najpierw sprawdza pamięć `globalState`, a w razie braku stosuje nową paletę domyślną
- **Color Persistence** – every color change made in the Webview is now permanently saved; the PAD restores its colors instantly after VS Code restarts, with no need for reconfiguration / każda zmiana koloru w Webview jest trwale zapisywana; PAD odzyskuje kolory natychmiast po restarcie VS Code
- **New Key Mapping System** – full synchronization with Firmware v2.3; fixed the one-key offset bug, restoring the correct layout (1: VSCode, 2: Creator, 3: Home, etc.) / pełna synchronizacja z Firmware v2.3; rozwiązano problem przesunięcia funkcji o jeden klawisz

### Fixed / Poprawiono
- **Ghost Colors eliminated** – removed hardcoded color definitions (purples/reds) from source and config files that caused a rainbow effect on startup / usunięto twardo zapisane definicje kolorów powodujące efekt tęczy przy starcie
- **"Command Already Exists" error** – complete refactoring of command registration in `extension.ts`; removed duplicates that blocked the extension on repeated reloads / całkowita refaktoryzacja rejestracji komend; usunięto duplikaty blokujące wtyczkę przy przeładowaniu
- **Registration stability** – moved command registration outside conditional blocks, ensuring the PAD interface is always ready immediately after extension initialization / przeniesiono rejestrację poza bloki warunkowe, gwarantując gotowość interfejsu PAD zaraz po inicjalizacji
- **`updateColors` optimization** – function in `padDevice.ts` rewritten to correctly handle the extension context and read user settings / funkcja przepisana dla poprawnej obsługi kontekstu i ustawień użytkownika

---

## [0.2.10] – 2026-02-17

### Fixed / Poprawiono
- **Info dialog** – fixed positioning of the PAD detection notification; now appears in the bottom-left corner as intended / poprawka pozycji okna informacyjnego o wykryciu PAD; teraz wyświetla się w lewym dolnym rogu
- **Typo in dialog** – fixed a minor text error in the notification message / poprawka literówki w komunikacie

---

## [0.2.9] – 2026-02-17

### Added / Dodano
- **Extended Action Colors** – added new action colors for the keypad: Blue, White, Yellow, Purple / dodano nowe kolory akcji dla keypada: niebieski, biały, żółty, fioletowy
- **Code refactoring** – further cleanup and optimization of the codebase / kolejne porządkowanie i optymalizacja kodu

### Fixed / Poprawiono
- **HID-RAW connection stability** – per-key state is now individually tracked; no more unintended color overwrites / indywidualne śledzenie stanu każdego klawisza; brak niezamierzonego nadpisywania kolorów
- **Typos** – corrected text errors in descriptions / poprawki literówek w opisach

---

## [0.2.8] – 2026-02-15

### Added / Dodano
- **SunGO PAD support** – integrated color schemes for RUN, BUILD, and full linter error handling / integracja schematów kolorów dla RUN, BUILD i pełna obsługa błędów lintera
- **Code refactoring** – KeyPAD and Security logic moved to dedicated source files / funkcje KeyPAD i Security przeniesione do osobnych plików
- **Improved button color persistence** – individual key state is remembered, preventing unintended overwrites / zapamiętywanie indywidualnego stanu klawiszy
- **Build/Run stability** – PAD colors now accurately reflect the process status (green for success, red for error) / kolory PAD dokładnie odzwierciedlają status procesu

---

## [0.2.6] – 2026-02-13

### Added / Dodano
- **SunGo PAD support** – full integration with the custom 9-key mechanical macro pad; enables physical control of Build, Run, Sign, and Dashboard navigation / pełna integracja z 9-przyciskową klawiaturą mechaniczną; fizyczne sterowanie procesami Build, Run, Sign i nawigacją po Dashboardzie
- **"Hide Console Window" option** – added support for the `-H=windowsgui` flag; allows compiling GUI apps (e.g. Raylib, Fyne) without a background terminal window on Windows / obsługa flagi `-H=windowsgui`; kompilacja aplikacji GUI bez zbędnego okna terminala w tle
- **"Force Rebuild" option** – implemented the `-a` flag to force a full rebuild of all packages, bypassing the Go cache / flaga `-a` wymuszająca pełne przebudowanie wszystkich pakietów z pominięciem cache Go
- **Dynamic flag builder** – improved `extension.ts` logic to intelligently combine size optimization flags (`-s -w`) with UI and cache flags based on user settings / inteligentne łączenie flag optymalizacji rozmiaru z flagami interfejsu i cache

### Fixed / Poprawiono
- **NLS localization** – added Polish and English descriptions for new build options in the VS Code settings menu / dodano opisy PL/EN dla nowych opcji kompilacji w ustawieniach
- **Overwrite logic** – synchronized file overwrite behavior with the new linker flags / zsynchronizowano nadpisywanie plików z nowymi flagami linkera

---

## [0.2.5] – 2026-02-09

### Added / Dodano
- **SunGo Test Engine** – brand new module integrating `go test` with a graphical UI / zupełnie nowy moduł integrujący `go test` z interfejsem graficznym
- **Interactive Test Dashboard** – dedicated Webview displaying real-time test results with a visual progress spinner / dedykowane Webview z wynikami testów w czasie rzeczywistym i wizualnym spinnerem
- **Automatic test file generation** – the project wizard now creates a default `main_test.go` for every new project, enabling TDD from the first second / kreator projektów tworzy domyślny `main_test.go`, zapewniając gotowość do TDD od pierwszej chwili
- **SunRiver Cow Says (ASCII Art)** – a signature notification system triggered on a 100% test pass rate / autorski system powiadomień ASCII uruchamiany po zdaniu wszystkich testów
- **Intelligent JSON parser** – the test engine parses the `go test -json` stream for precise pass/fail tracking without blocking the VS Code UI / silnik testowy analizuje strumień `go test -json` bez blokowania interfejsu

### Fixed / Poprawiono
- **`/src` path stability** – synchronized test paths to correctly detect `_test.go` files inside the project source folder / zsynchronizowano ścieżki testowe dla poprawnego wykrywania plików `_test.go`
- **TestView UI/UX** – refined the ASCII cow layout using monospace formatting and Flexbox to prevent rendering issues at different window widths / dopracowano layout krowy ASCII z użyciem monospace i Flexbox

---

## [0.2.1] – 2026-02-09

### Fixed / Poprawiono
- **Translations** – corrected several stylistic errors and typos in UI strings / poprawki błędów stylistycznych i literówek w interfejsie

---

## [0.2.0] – 2026-02-08

### Added / Dodano
- **Interactive Project Wizard** – brand new graphical Webview interface for creating projects, with visual selection of name, category, and template / nowy graficzny kreator projektów z wyborem nazwy, kategorii i szablonu
- **Project Template System** – ready-to-use starter templates for multiple app types:
  - **Console (CLI)**: Hello World and blank project / Hello World i pusty projekt
  - **Desktop (GUI)**: Fyne integration (example + blank) / integracja z Fyne (przykład + pusty)
  - **Games (2D)**: Ebitengine integration (example + blank) / integracja z Ebitengine (przykład + pusty)
  - **Servers / Microservices**: standard `net/http` and Gin framework templates / szablony dla `net/http` i Gin
- **Project categorization** – smart template filtering based on selected app type / inteligentne filtrowanie szablonów według typu aplikacji
- **Full Wizard localization (PL/EN)** – all labels, category descriptions, and progress messages are dynamically translated / wszystkie etykiety i komunikaty są dynamicznie tłumaczone

### Fixed / Poprawiono
- **Dashboard UI/UX** – wizard styling unified with the Dashboard (SunGo Green accents, VS Code system fonts) / styl kreatora ujednolicony z Dashboardem
- **Form layout** – fixed the "infinite width" input field bug; forms now have a defined max-width and are centered / naprawiono błąd nieskończonej szerokości pól; formularze mają teraz max-width i są wycentrowane
- **Build error handling** – improved messaging when a binary is locked (e.g. app already running) / lepsze komunikaty gdy plik binarny jest zablokowany
- **Path safety** – improved project name suggestion logic to avoid conflicts with existing folders / ulepszona logika sugestii nazwy projektu

---

## [0.1.10] – 2026-02-07

### Fixed / Poprawiono
- **Clear /bin function** – fixed incorrect behavior; now works correctly whether called on a `.go` file or the `/bin` folder directly / funkcja działa poprawnie niezależnie od tego, czy wywołana na pliku `.go` czy folderze `/bin`
- **Refactoring** – code split into functional blocks for easier maintenance / podział kodu na bloki funkcyjne ułatwiające utrzymanie

---

## [0.1.9] – 2026-02-07

### Fixed / Poprawiono
- **Localization mechanism (PL/EN)** – fixed a bug that prevented the Dashboard language from switching automatically when the VS Code language setting was changed; the SunGo interface now fully follows the user's language selection / naprawiono błąd uniemożliwiający automatyczną zmianę języka Dashboardu po zmianie ustawień VS Code

---

## [0.1.8] – 2026-02-07

### Added / Dodano
- **Full NLS localization for settings** – all Settings options now have Polish and English descriptions / wszystkie opcje ustawień mają opisy PL i EN
- **Command title localization** – action names in the Command Palette (Ctrl+Shift+P) and context menus are now dynamically translated / nazwy akcji w Palecie Komend i menu kontekstowym są dynamicznie tłumaczone
- **Language resources** – added and unified keys in `package.nls.json` and `package.nls.pl.json` / ujednolicono klucze w plikach NLS

---

## [0.1.7] – 2026-02-06

### Added / Dodano
- **Smart Version Detection** – SunGo now scans `main.go` for `ver` or `version` variables and automatically appends their value to the binary filename (e.g. `Project_v1.2.0.exe`) / SunGo skanuje `main.go` w poszukiwaniu zmiennych wersji i dodaje je do nazwy pliku binarnego
- **Professional build numbering** – changed suffix format from `_x` to `_build_x` for clearer iteration identification / zmieniono format sufiksu z `_x` na `_build_x`
- **"Version in Name" toggle** – new extension setting to enable or disable automatic version appending to binary filenames / nowa opcja włączania/wyłączania automatycznego dodawania wersji do nazwy pliku
- **Settings icon** – added an animated settings icon to the Dashboard (HOME) header / dodano animowaną ikonkę ustawień w nagłówku Dashboardu
- **Smart Clear /bin** – added a "SunGo: Clear /bin" action to the Explorer context menu; intelligently clears the output folder while keeping only the latest build / akcja w menu kontekstowym eksploratora; czyści folder /bin zachowując tylko ostatni build

### Fixed / Poprawiono
- **Naming consistency** – synchronized `getNextBinaryPath` to apply the `_build_` format from the very first copy / zsynchronizowano funkcję dla spójnego formatu od pierwszej kopii
- **Output path logic** – optimized filename generation to avoid conflicts when combining version and build numbering / optymalizacja generowania nazw plików
- **Dashboard UI (Perfect Alignment)** – refined the Dashboard header alignment using Flexbox / dopracowano wyrównanie nagłówka Dashboardu

---

## [0.1.6] – 2026-02-05

### Added / Dodano
- **Smart Overwrite Mode** – new `sungo.build.overwrite` setting allowing the user to choose between incremental binary versioning or overwriting the main file in `/bin` / nowa opcja pozwalająca wybrać między numerowaniem kolejnych binarek a nadpisywaniem głównego pliku w /bin

### Fixed / Poprawiono
- **StatusBar Spinner synchronization** – spinner now animates accurately, providing precise visual feedback during active operations / spinner animuje się precyzyjnie podczas aktywnych operacji
- **Asynchronous compilation (non-blocking)** – rebuilt the Build function to fully leverage async `exec`, eliminating UI freezes on large projects / przebudowano Build dla pełnej asynchroniczności, eliminując zamrażanie interfejsu
- **Binary path stability** – fixed path logic for publisher Thumbprints containing special characters or spaces / poprawiono logikę ścieżek dla wydawców ze znakami specjalnymi w nazwie

---

## [0.1.5] – 2026-02-05

### Added / Dodano
- **SunGo Security Suite** – new Dashboard module dedicated to application trust and security management / nowy moduł Dashboardu do zarządzania zaufaniem i bezpieczeństwem aplikacji
- **Dev Certificate (Self-Signed)** – one-click generation of a local publisher identity (`SunGo-Dev`) for signing `.exe` files professionally / błyskawiczne generowanie lokalnej tożsamości wydawcy do podpisywania plików .exe
- **Automatic certificate installation** – the script automatically adds the generated certificate to the system "Trusted Root Certification Authorities" store, bypassing Windows Defender blocks / automatyczne dodawanie certyfikatu do systemowego magazynu zaufanych certyfikatów
- **Sign Code function** – new gold `$(shield) Sign` button in the status bar and Dashboard for one-click signing of the latest build / złoty przycisk do podpisywania ostatniego buildu jednym kliknięciem
- **Unlock Folder** – tool for removing the "Mark of the Web" flag from files in the project folder, resolving permission issues when running binaries / narzędzie do usuwania flagi "Mark of the Web" z plików projektu

### Fixed / Poprawiono
- **Dashboard UI** – added a new highlighted "Security" card with gold visual accents / dodano kartę "Security" ze złotymi akcentami wizualnymi
- **Binary Signature** – updated the binary footer in the Dashboard to correctly identify version 0.1.5 / zaktualizowano stopkę binarną do wersji 0.1.5
- **Certificate error handling** – added administrator privilege verification when attempting to install a system certificate / dodano weryfikację uprawnień administratora przy instalacji certyfikatu

---

## [0.1.4] – 2026-02-01

### Added / Dodano
- **Binary Optimization** – automatic `-s -w` linker flags during build, reducing executable size and improving stability / automatyczne flagi `-s -w` podczas kompilacji, zmniejszające rozmiar pliku i poprawiające stabilność

### Fixed / Poprawiono
- **Critical Build Fix** – eliminated the "application will not run" error by preventing write process collisions during compilation / wyeliminowano błąd kolizji procesów zapisu podczas kompilacji
- **Smart Terminal Output** – improved terminal communication; SunGo now clearly reports build success or errors / poprawiono komunikację w terminalu — wyraźne raporty sukcesu lub błędów
- **StatusBar Logic** – fixed icon priority order on the status bar: Home > FMT > IMPORT > RUN > BUILD / poprawiono kolejność priorytetów ikon na pasku statusu

---

## [0.1.3] – 2026-02-01

### Added / Dodano
- **IMPORT ALL button** – new blue action on the status bar (between FMT and RUN) for instant project-wide dependency synchronization / nowa niebieska akcja na pasku statusu do błyskawicznej synchronizacji zależności całego projektu
- **Forced dependency fetch** – uses `go get -u -v ./...` to force-check and update every import in the code / wymusza sprawdzenie i aktualizację każdego importu
- **Intelligent module cleanup** – after each forced fetch, SunGo automatically runs `go mod tidy` to keep `go.mod` and `go.sum` clean / po każdym pobraniu automatycznie wykonuje `go mod tidy`
- **Editor context menu** – added "IMPORT ALL" and "Sync Tidy" options via right-click directly in the code editor (Go files only) / opcje dostępne pod prawym przyciskiem myszy w edytorze (tylko pliki Go)
- **Explorer context menu** – right-click on `main.go` in the file tree to instantly pull dependencies / prawy przycisk na `main.go` w drzewie plików

### Fixed / Poprawiono
- **Fetch stability** – added the `-u` (update) flag to resolve issues with missing or outdated libraries that were blocking the BUILD process / flaga `-u` rozwiązuje problemy z brakującymi bibliotekami blokującymi BUILD
- **Build stability** – automatic `go mod tidy` after each forced fetch eliminates "missing module" errors during BUILD / eliminacja błędów "missing module" podczas BUILD
- **Path logic (rootPath)** – added a guard against attempting synchronization when no project is open / zabezpieczenie przed synchronizacją gdy żaden projekt nie jest otwarty
- **Context menu UX** – SunGo commands grouped under `sungo_actions` to separate them from standard VS Code functions / komendy zgrupowane w `sungo_actions`

---

## [0.1.2] – 2026-01-30

### Added / Dodano
- **Automatic build numbering** – BUILD intelligently checks the `/bin` folder; if a file already exists, SunGo automatically increments the number / BUILD sprawdza folder /bin i automatycznie numeruje kolejne wersje
- **SunGo Spinner** – custom spinner mechanism on the status bar; animates in real time during RUN and BUILD / autorski spinner animujący się podczas RUN i BUILD
- **Asynchronous build monitoring** – BUILD tracks the compilation process via `child_process`; the spinner stops when Go generates the output file / śledzenie procesu kompilacji; spinner zatrzymuje się po wygenerowaniu pliku

### Fixed / Poprawiono
- **`/bin` folder management** – the extension automatically creates the `/bin` output folder before building if it does not exist / automatyczne tworzenie folderu /bin przed budowaniem
- **Visual consistency** – refined button color logic: orange for Build, yellow for Run / dopracowano logikę kolorów przycisków: pomarańczowy dla Build, żółty dla Run
- **Notification precision** – post-build system notifications now report the exact name of the newly created binary / powiadomienia po buildzie raportują dokładną nazwę nowego pliku binarnego

---

## [0.1.1] – 2026-01-30

### Added / Dodano
- **PowerShell Core (pwsh)** – SunGo now automatically opens a dedicated terminal based on `pwsh`, ensuring full compatibility with operators like `&&` regardless of the Windows version / SunGo automatycznie otwiera terminal oparty na `pwsh`, zapewniając pełną kompatybilność z operatorem `&&`
- **pwsh installation assistant** – an intelligent module checks for PowerShell Core at startup and notifies the user if it is missing / inteligentny moduł sprawdzający obecność PowerShell Core przy starcie
- **Dedicated "SunGo Terminal"** – the extension no longer uses the user's default terminal, instead creating its own clean process to eliminate conflicts with other extensions / wtyczka tworzy własny, czysty proces terminala eliminując konflikty z innymi rozszerzeniami

### Fixed / Poprawiono
- **ParserError eliminated** – permanently resolved the `InvalidEndOfLine` issue visible in older PowerShell (5.1) by moving execution logic to the modern `pwsh` environment / trwałe rozwiązanie problemu `InvalidEndOfLine` ze starszego PowerShell 5.1
- **Command separator simplification** – by standardizing on `pwsh`, all RUN and BUILD commands use the universal `&&` standard / ujednolicenie do `&&` we wszystkich komendach
- **Dashboard diagnostics** – the "Terminal VS Code" section in the Home panel now reports the actual installed `pwsh` version / sekcja terminala w panelu Home raportuje rzeczywistą wersję `pwsh`

---

## [0.1.0] – 2026-01-29

### Added / Dodano
- **Modern Home panel** – completely refreshed main panel serving as the project command center / całkowicie odświeżony panel główny jako centrum dowodzenia projektami
- **Interactive project list** – the Dashboard now displays the last 5 created projects as clickable chips for instant access / Dashboard wyświetla ostatnie 5 projektów jako klikalne chipy
- **Active project counter** – dynamic counter showing the total number of Go projects in the current Workspace in real time / dynamiczny licznik wszystkich projektów Go w Workspace
- **Quick create from Home** – added a button to start a new project directly from the main panel / przycisk tworzenia nowego projektu bezpośrednio z panelu głównego

### Fixed / Poprawiono
- **Diagnostics UI integration** – system check results (Go, GCC, Git) are now presented in a clearer card-based layout / wyniki diagnostyki prezentowane w czytelniejszym układzie kart
- **View synchronization** – fixed Webview data refresh after adding or removing a project / poprawiono odświeżanie Webview po dodaniu lub usunięciu projektu
- **General stability** – overall security and performance improvements / ogólna poprawa bezpieczeństwa i wydajności

---

## [0.0.9] – 2026-01-29

### Added / Dodano
- **Dynamic visual effects (Spinners)** – animated `$(loading~spin)` icons on the status bar during RUN and BUILD operations / animowane ikony `$(loading~spin)` na pasku statusu podczas RUN i BUILD
- **Intelligent Shell detection** – the extension automatically detects whether the user is running PowerShell, CMD, or Bash, and adjusts the command separator accordingly (`&&` vs `&`) / automatyczne wykrywanie shella i dobór separatora komend
- **Extended Dashboard** – the diagnostics section now includes active VS Code terminal detection with a warning system (especially useful for CMD users) / sekcja diagnostyki z wykrywaniem aktywnego terminala i systemem ostrzeżeń

### Fixed / Poprawiono
- **Diagnostics stability** – unified the tool version checking system (Go, GCC, Git), eliminating read errors on non-standard installations / ujednolicono system sprawdzania wersji narzędzi
- **Build UX** – the BUILD button now turns orange during compilation, clearly indicating an active build process / przycisk BUILD zmienia kolor na pomarańczowy podczas kompilacji
- **Code refactoring** – diagnostic functions moved outside the main extension lifecycle, speeding up plugin startup / przeniesienie funkcji diagnostycznych poza główny cykl życia wtyczki

---

## [0.0.8] – 2026-01-28

### Added / Dodano
- **Editor Title Menu** – added a set of icons (FMT, BUILD, RUN, SYNC) directly to the editor's top toolbar; available whenever a `.go` file is being edited / zestaw ikon na górnej belce edytora, dostępny podczas edycji plików `.go`
- **Smart context icons** – toolbar icons appear only in the context of Go files, keeping the interface clean for other file types / ikony pojawiają się tylko w kontekście plików Go
- **Universal SYNC (Tidy)** – `go mod tidy` now works intelligently from two locations: the project sidebar and the new editor toolbar icon / `go mod tidy` działa z dwóch miejsc: panelu bocznego i nowej ikonki nad kodem

### Fixed / Poprawiono
- **Smart CD paths** – eliminated the "go.mod not found" error; the extension now correctly performs `cd` to the project folder before every RUN, BUILD, and FMT operation / wyeliminowano błąd "go.mod not found"; poprawne `cd` przed każdą operacją
- **Path synchronization** – unified `rootPath` retrieval logic for 100% stability when working with multiple subfolders / ujednolicona logika pobierania `rootPath`
- **SYNC icon fix** – fixed the `syncImports` command registration that previously caused sluggish behavior and errors / poprawiono rejestrację komendy `syncImports`

---

## [0.0.7] – 2026-01-28

### Added / Dodano
- **BUILD function** – added the ability to compile a project to an executable with a single click / możliwość kompilacji projektu do pliku wykonywalnego jednym kliknięciem
- **Intelligent binary naming** – the extension automatically names the output file after the project folder (e.g. `MyApp.exe`) / automatyczne nadawanie nazwy pliku wyjściowego na podstawie folderu projektu
- **Windows support** – fixed the missing `.exe` extension so Windows correctly recognizes the built files / dodanie brakującego rozszerzenia `.exe` dla systemu Windows
- **Automatic `/bin` structure** – compiled files are placed in a dedicated `/bin` folder, separating the finished product from the source code / skompilowane pliki trafiają do dedykowanego folderu `/bin`
- **BUILD icon on the status bar** – added a new blue `$(package)` icon next to the FMT and RUN buttons / nowa niebieska ikona `$(package)` na pasku statusu

### Fixed / Poprawiono
- **Output path logic** – using the `path` module for dynamic path construction, eliminating errors with non-standard project names / dynamiczne budowanie ścieżek eliminuje błędy przy niestandardowych nazwach projektów
- **Icon and code optimization** – significantly reduced the extension package size from ~1 MB to ~50 KB / znaczna redukcja rozmiaru pakietu z ~1 MB do ~50 KB

---

## [0.0.6] – 2026-01-28

### Added / Dodano
- **Optimized status bar** – new priority layout: [SunGo] [Home] [FMT] [RUN] for better workflow ergonomics / nowy układ priorytetów dla lepszej ergonomii pracy
- **Critical error handling** – added missing command subscriptions and disposals, significantly improving extension stability / dodano brakujące subskrypcje i zamknięcia komend
- **"Buy me a coffee" button** – investing in a new cow for the Easter Egg 🐄 / inwestycja w nową krowę do Easter Egga 🐄

### Fixed / Poprawiono
- **Memory management** – proper registration of StatusBarItems and Webview instances, preventing memory leaks / poprawna rejestracja StatusBarItems i Webview zapobiegająca wyciekom pamięci
- **UI cleanup** – removed duplicate buttons from the project tree view, making the sidebar cleaner / usunięto duplikaty przycisków z widoku drzewa projektów
- **TypeScript typing** – eliminated errors related to potentially undefined `rootPath` values / usunięto błędy związane z potencjalnie niezdefiniowanym `rootPath`

---

## [0.0.5] – 2026-01-27

### Added / Dodano
- Go compiler presence check on startup to prevent errors for new users / sprawdzanie obecności kompilatora Go przy starcie
- Safe execution of system commands with support for spaces in project names / bezpieczne wykonywanie komend systemowych z obsługą spacji w nazwach projektów
- Code formatting action (`go fmt`) accessible via a status bar icon / formatowanie kodu dostępne przez ikonę na pasku statusu

---

## [0.0.4] – 2026-01-27

### Added / Dodano
- **Official launch on the Visual Studio Code Marketplace** / **Oficjalna premiera w Visual Studio Code Marketplace**
- **Localization system** – Polish and English language support / system lokalizacji z obsługą języka polskiego i angielskiego
- **SunGo icon** – PNG for Marketplace, SVG for the UI / ikona PNG dla Marketplace i SVG dla interfejsu
- **Core project management features:**
  - Go project structure creation / tworzenie struktury projektu Go
  - Library addition and import synchronization / dodawanie bibliotek i synchronizacja importów
  - Project removal and path reset / usuwanie projektów i resetowanie ścieżek
