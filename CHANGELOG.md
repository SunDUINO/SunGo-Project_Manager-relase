# Changelog – SunGo Project Manager

[EN] All notable changes to the "SunGo Project Manager" extension are documented in this file.  
[PL] Wszystkie istotne zmiany w rozszerzeniu "SunGo Project Manager" są dokumentowane w tym pliku.

---

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
