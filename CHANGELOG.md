# Changelog – SunGo Project Manager

[EN] All notable changes to the "SunGo Project Manager" extension are documented in this file.  
[PL] Wszystkie istotne zmiany w rozszerzeniu "SunGo Project Manager" są dokumentowane w tym pliku.

---


## [2.13.0] - 2026-08-21

### Added / Dodano -- Splash Screen / Ekran Powitalny

- **[EN]** Added a splash screen shown automatically after installing or updating the extension, displaying the SunGo Project Manager banner, the current version number, and a short tagline. A new setting, **SunGo – Splash Screen › Show On Every Startup**, lets you switch it to appear on every VS Code startup instead of only once per install/update.
- **[PL]** Dodano ekran powitalny wyświetlany automatycznie po instalacji lub aktualizacji rozszerzenia, prezentujący baner SunGo Project Manager, aktualny numer wersji oraz krótkie hasło. Nowe ustawienie **SunGo – Splash Screen › Show On Every Startup** pozwala przełączyć go na wyświetlanie przy każdym uruchomieniu VS Code zamiast tylko raz po instalacji/aktualizacji.

### Changed / Zmieniono -- Gopher Assistant Redesign / Przeprojektowanie Asystenta Gopher

- **[EN]** Redesigned the Gopher Assistant character to match the official Go gopher mascot: a teal, capsule-shaped body, small side ears, and a cream snout with visible front teeth, replacing the previous mouse-like look.
- **[PL]** Przeprojektowano postać Asystenta Gopher, dopasowując ją do oficjalnej maskotki Go: turkusowe, kapsułowe ciało, małe boczne uszy oraz kremowy pyszczek z widocznymi przednimi zębami, w miejsce poprzedniego, bardziej mysiego wyglądu.
- **[EN]** The idle animation now blinks and rolls its eyes in a small circular motion instead of staying static.
- **[PL]** Animacja stanu bezczynności teraz mruga i "przewraca" oczami po małym okręgu zamiast pozostawać statyczna.
- **[EN]** The error state now shows the gopher's eyes turning red and pulsing, along with a small animated flame above its head, instead of just the previous static red tint.
- **[PL]** Stan błędu pokazuje teraz pulsujące, czerwone oczy gophera oraz mały animowany płomień nad głową, zamiast samego wcześniejszego statycznego czerwonego poblasku.
- **[EN]** The build/compile state now fills the gopher's body with a falling stream of binary digits (0s and 1s) in the extension's brand color, alongside the existing spinning gear.
- **[PL]** Stan buildu/kompilacji wypełnia teraz ciało gophera opadającym strumieniem cyfr binarnych (0 i 1) w kolorze marki rozszerzenia, uzupełniając dotychczasowe obracające się koło zębate.

### Removed / Usunięto -- Dead "Release Assistant" Entry / Martwy wpis "Release Assistant"

- **[EN]** Removed an orphaned "Release Assistant" item from the SunGo Tools panel that pointed to a command which was never implemented.
- **[PL]** Usunięto osierocony wpis "Release Assistant" z panelu SunGo Tools, wskazujący na nigdy niezaimplementowaną komendę.

---


## [2.12.1] - 2026-08-20

### Added / Dodano -- SunGO Tools Documentation / Dokumentacja SunGO Tools

- **[EN]** Added comprehensive instructions and usage guides for the **SunGO Tools** suite directly within the documentation.
- **[PL]** Dodano szczegółowe instrukcje oraz przewodniki użytkowania dla zestawu narzędzi **SunGO Tools** bezpośrednio w dokumentacji.

### Changed / Zmieniono -- UI Refinements & Performance Improvements / Drobne poprawki interfejsu i optymalizacja wydajności

- **[EN]** Applied cosmetic and visual refinements to the user interface to ensure a more consistent look and improved overall user experience.
- **[PL]** Wprowadzono poprawki wizualne i kosmetyczne w interfejsie użytkownika, zapewniając większą spójność wyglądu oraz wyższy komfort użytkowania.
- **[EN]** Implemented key performance optimizations and code enhancements, resulting in a faster, smoother, and more responsive extension interface.
- **[PL]** Przeprowadzono optymalizacje wydajnościowe oraz usprawnienia kodu, co przekłada się na szybsze, płynniejsze i bardziej responsywne działanie interfejsu rozszerzenia.

---


## [2.12.0] - 2026-08-13

### Added / Dodano -- Fuzz Testing / Testowanie Fuzz

- **[EN]** Added a **Fuzz Testing** panel powered by Go's native fuzzer (`go test -fuzz`): pick any `FuzzXxx` function found in your project, choose how long to run it for, and start a single, time-bounded run — no background processes left running after you close the panel. On success you get an execution-count summary; if a crash is found, you get the path to the saved failing input, a ready-to-copy command to re-run just that case, and the extracted failure detail.
- **[PL]** Dodano panel **Fuzz Testing** oparty na natywnym fuzzerze Go (`go test -fuzz`): wybierz dowolną znalezioną w projekcie funkcję `FuzzXxx`, ustaw czas trwania i uruchom jeden, ograniczony czasowo przebieg — żadnych procesów w tle po zamknięciu panelu. Przy sukcesie dostajesz podsumowanie liczby wykonań; jeśli fuzzer znajdzie awarię, dostajesz ścieżkę do zapisanego wejścia, gotową do skopiowania komendę do odtworzenia tylko tego przypadku oraz wyciągnięty szczegół błędu.
- **[EN]** The Fuzz Testing panel can generate an example fuzz test for you, the same way Coverage and Benchmarks already do — pick an open `.go` file, click "Generate Example Fuzz Test", and get a ready-to-fill skeleton with seed values and assertions marked as TODO.
- **[PL]** Panel Fuzz Testing potrafi wygenerować przykładowy test fuzz, tak samo jak już robią to Coverage i Benchmarks — wybierz otwarty plik `.go`, kliknij "Generate Example Fuzz Test" i dostań gotowy do uzupełnienia szkielet z wartościami seed i asercjami oznaczonymi jako TODO.
- **[EN]** Fuzz Testing can be assigned to a MacroPAD key, just like Coverage and Benchmarks — opening the panel with a key press works the same way; the fuzz run itself always starts manually from inside the panel.
- **[PL]** Fuzz Testing można przypisać do klawisza MacroPAD, tak samo jak Coverage i Benchmarks — otwarcie panelu wciśnięciem klawisza działa tak samo; sam przebieg fuzzingu zawsze startuje ręcznie z poziomu panelu.

---


## [2.11.0] - 2026-08-09

### Added / Dodano -- Test Coverage, Benchmarks & Dependency Graph / Pokrycie Testami, Benchmarki i Graf Zależności

- **[EN]** Added a **Test Coverage Viewer**: runs your project's tests with coverage tracking, highlights covered and uncovered lines directly in the editor, and shows a sortable per-file coverage summary — so you can see at a glance which parts of your codebase still need tests.
- **[PL]** Dodano **Test Coverage Viewer**: uruchamia testy projektu ze śledzeniem pokrycia, podświetla pokryte i niepokryte linie bezpośrednio w edytorze oraz pokazuje sortowalne podsumowanie pokrycia per plik — dzięki czemu od razu widać, które fragmenty kodu wciąż potrzebują testów.

- **[EN]** Added a **Benchmark Runner** with persistent run history: execute your project's benchmarks with one click, compare any two past runs side by side (faster/slower/new/removed), and follow a chosen benchmark's performance trend over time on a chart.
- **[PL]** Dodano **Benchmark Runner** z trwałą historią przebiegów: uruchamiasz benchmarki projektu jednym kliknięciem, porównujesz dowolne dwa wcześniejsze przebiegi obok siebie (szybciej/wolniej/nowy/usunięty) oraz śledzisz na wykresie trend wydajności wybranego benchmarku w czasie.

- **[EN]** Added an **Interactive Dependency Graph**: visualizes your external module dependencies (click a node to reveal its own dependencies, double-click to open it on pkg.go.dev) side by side with your internal package structure. For smaller, single-package projects it automatically falls back to a file-level view, showing how your individual `.go` files relate to each other.
- **[PL]** Dodano **Interaktywny Graf Zależności**: wizualizuje zewnętrzne zależności modułów (kliknięcie węzła odsłania jego własne zależności, podwójne kliknięcie otwiera go na pkg.go.dev) obok struktury wewnętrznych pakietów projektu. Dla mniejszych, jednopakietowych projektów automatycznie przełącza się na widok na poziomie plików, pokazując jak poszczególne pliki `.go` się ze sobą łączą.

- **[EN]** Both the Coverage Viewer and Benchmark Runner can now generate example test/benchmark skeletons for you: pick an open `.go` file and click "Generate Example Tests" (or "...Benchmarks") to get ready-to-fill stubs for a couple of your functions, complete with TODO markers — a quick way to get started when a project has no tests yet.
- **[PL]** Zarówno Coverage Viewer, jak i Benchmark Runner potrafią teraz wygenerować przykładowe szkielety testów/benchmarków: wybierz otwarty plik `.go` i kliknij "Generate Example Tests" (lub "...Benchmarks"), aby dostać gotowe do uzupełnienia szkielety dla kilku funkcji, ze znacznikami TODO — szybki start, gdy projekt nie ma jeszcze żadnych testów.

- **[EN]** Added ready-made Benchmark and edge-case testing patterns to the Snippet Manager's Testing category — a basic benchmark, side-by-side sub-benchmark comparisons, and a nil/empty/error-path test pattern for quickly raising coverage.
- **[PL]** Dodano gotowe wzorce benchmarków i testów przypadków brzegowych do kategorii Testing w Snippet Managerze — podstawowy benchmark, porównanie kilku implementacji obok siebie oraz wzorzec testu nil/pusty/ścieżka błędu do szybkiego podnoszenia pokrycia.

### Fixed / Poprawiono -- Project Switching / Przełączanie Projektów

- **[EN]** Fixed the Explorer view not reliably reappearing after selecting a project from the SunGo Projects list — it now switches back to the Explorer every time, regardless of what was previously visible.
- **[PL]** Naprawiono niekonsekwentne pojawianie się widoku Explorera po wybraniu projektu z listy SunGo Projects — teraz zawsze przełącza z powrotem na Explorer, niezależnie od tego, co było wcześniej widoczne.

---

## [2.10.6] - [2.10.8] - 2026-07-

### ⚠️ Test Build (Pre-release)
### ⚠️ Wersje Testowe (Pre-release)

---

[2.10.5] - 2026-08-08

### Changed / Zmieniono -- Bundled Build for Faster Startup / Zbundlowany build dla szybszego startu

[EN] Switched the extension's build process to bundling: instead of shipping hundreds of separate JavaScript files, the entire extension now compiles down to a single optimized file. This resolves VS Code's "too many files" performance warning, noticeably reduces the installed extension's footprint, and speeds up how quickly the extension becomes ready after VS Code starts.
[PL] Zmieniono proces budowania rozszerzenia na bundlowany: zamiast setek osobnych plików JavaScript, całe rozszerzenie kompiluje się teraz do jednego, zoptymalizowanego pliku. Rozwiązuje to ostrzeżenie VS Code o zbyt dużej liczbie plików, zauważalnie zmniejsza rozmiar zainstalowanego rozszerzenia i przyspiesza moment, w którym rozszerzenie jest gotowe do pracy po starcie VS Code.
[EN] USB/MacroPAD hardware communication continues to work exactly as before — the low-level device driver was deliberately kept outside the bundle to preserve full compatibility across Windows, macOS, and Linux.
[PL] Komunikacja z MacroPAD przez USB działa dokładnie tak samo jak wcześniej — sterownik niskopoziomowy został celowo pozostawiony poza bundlem, aby zachować pełną kompatybilność na Windows, macOS i Linuksie.

---

## [2.10.4] - 2026-08-07

### Added / Dodano -- Saved Repository List for Publish Any Files to Any Repo / Lista zapisanych repozytoriów dla Publish Any Files to Any Repo

- **[EN]** Added a saved repositories list to the **Publish Any Files to Any Repo** tool, letting you store up to 10 frequently used destinations and switch between them with a single click, while still being able to type a custom URL at any time. Repositories you successfully publish to are remembered automatically.
- **[PL]** Dodano listę zapisanych repozytoriów do narzędzia **Publish Any Files to Any Repo**, pozwalającą zachować do 10 najczęściej używanych adresów docelowych i przełączać się między nimi jednym kliknięciem, z zachowaniem możliwości wpisania własnego adresu w dowolnej chwili. Repozytoria, do których udało się opublikować pliki, są zapamiętywane automatycznie.

### Fixed / Poprawiono -- Isolated Working Folders & Automatic Cleanup / Izolowane foldery robocze i automatyczne czyszczenie

- **[EN]** Fixed an issue where switching between repository URLs in **Publish Any Files to Any Repo** could leave behind a stale working folder tied to a previously used address. Each repository now uses its own dedicated, isolated working folder, which is automatically cleaned up after every publish attempt — eliminating any conflict or leftover state when moving between repositories.
- **[PL]** Naprawiono problem, w którym przełączanie się między adresami repozytoriów w narzędziu **Publish Any Files to Any Repo** mogło pozostawiać nieaktualny folder roboczy powiązany z wcześniej użytym adresem. Każde repozytorium korzysta teraz z własnego, odizolowanego folderu roboczego, automatycznie czyszczonego po każdej próbie publikacji — co eliminuje ryzyko konfliktu lub pozostałości przy przełączaniu się między repozytoriami.

- **[EN]** Further hardened the Project Notes single-instance safeguard on MacroPAD II so it now also recognizes notes already open in a background tab, not just the currently active one — fully eliminating any remaining edge case of duplicate windows.
- **[PL]** Dodatkowo wzmocniono zabezpieczenie pojedynczej instancji Project Notes na MacroPAD II, tak aby rozpoznawało również notatki otwarte w tle, a nie tylko w aktywnej zakładce — całkowicie eliminując pozostałe przypadki powielania okien.


---
## [2.10.3] - 2026-08-07

### Performance & Optimization / Wydajność i optymalizacja

- **[EN]** Significantly improved the refresh speed of the Tools tab through targeted code refactoring and performance optimizations. Streamlined execution logic to enhance overall system responsiveness.
- **[PL]** Znacząco przyspieszono odświeżanie zakładki Tools dzięki głębokiej refaktoryzacji kodu oraz optymalizacjom wydajnościowym. Zoptymalizowano logikę wykonywania operacji, poprawiając ogólną responsywność aplikacji.

---

## [2.10.2] - 2026-08-07

### Fixed / Poprawiono -- MacroPAD II Hardware Detection & Settings Access / Wykrywanie sprzętu MacroPAD II i dostęp do ustawień

- **[EN]** Fixed an issue where MacroPAD II was not properly detected by the extension and the Pad Settings panel became inaccessible following bundle configuration changes in the previous build. Restored full native HID detection and seamless access to hardware configuration views.
- **[PL]** Naprawiono problem, w którym MacroPAD II nie był prawidłowo wykrywany przez rozszerzenie, a panel ustawień pada pozostawał niedostępny po zmianach w konfiguracji bundlera z poprzedniej kompilacji. Przywrócono pełne natywne wykrywanie HID oraz bezproblemowy dostęp do widoków konfiguracji sprzętu.

---

## [2.10.1] - 2026-08-07

### Fixed / Poprawiono -- Project Notes Multi-Launch Guard on MacroPAD II / Zabezpieczenie przed wielokrotnym uruchamianiem Project Notes z MacroPAD II

- **[EN]** Resolved a issue where invoking the **Project Notes** tool via any hardware key (A, B, C, S1, or S2) on MacroPAD II caused the notes view to launch multiple times or spawn duplicate panel instances. Key press handling for Project Notes now enforces a strict single-instance debounce and focus check, ensuring smooth, predictable navigation without window clutter.
- **[PL]** Rozwiązano problem, w którym wywołanie narzędzia **Project Notes** za pomocą dowolnego klawisza fizycznego (A, B, C, S1 lub S2) na MacroPAD II powodowało wielokrotne uruchamianie widoku notatek lub tworzenie zduplikowanych instancji panelu. Obsługa naciśnięcia klawisza dla Project Notes wymusza teraz rygorystyczną kontrolę pojedynczej instancji oraz wyciszanie powtórzeń (debounce), co gwarantuje płynne i przewidywalne działanie bez powielania okien.

---

## [2.10.0] - 2026-08-05

### Added / Dodano -- Unique Key Assignment & Adaptive Label Styles / Unikalne przypisania klawiszy i adaptacyjny styl etykiet

- **[EN]** Introduced unique tool-to-key assignment for the MacroPAD: as soon as a tool is bound to key A, B, C, S1 or S2, it automatically disappears from the other keys' selection lists, making duplicate assignments impossible to create directly from the UI.
- **[PL]** Wprowadzono unikalne przypisania narzędzi do klawiszy MacroPAD: gdy narzędzie zostanie przypisane do klawisza A, B, C, S1 lub S2, automatycznie znika z list wyboru pozostałych klawiszy, co eliminuje możliwość przypadkowego zdublowania przypisania.

- **[EN]** Added automatic conflict resolution with a friendly notification: if a duplicate assignment is ever detected (e.g. carried over from an older configuration), SunGo clears the outdated one and informs you which key was affected.
- **[PL]** Dodano automatyczne rozwiązywanie konfliktów wraz z czytelnym powiadomieniem: jeśli kiedykolwiek wykryty zostanie zdublowany przydział (np. z wcześniejszej konfiguracji), SunGo porządkuje starsze przypisanie i informuje, którego klawisza to dotyczyło.

- **[EN]** Added a new "Tools label style" option in Pad Settings, letting you choose how the assigned key marker is displayed next to each entry in the SunGo Tools panel: plain text, text with an emoji marker, or text with a colored icon.
- **[PL]** Dodano nową opcję "Styl etykiety w Tools" w ustawieniach pada, pozwalającą wybrać sposób wyświetlania znacznika przypisanego klawisza obok narzędzia w panelu SunGo Tools: sam tekst, tekst ze znacznikiem emoji lub tekst z kolorową ikoną.

### Fixed / Poprawiono -- Cross-Platform Label Rendering & Full Tool Coverage / Renderowanie etykiet na różnych platformach i pełne pokrycie narzędzi

- **[EN]** Fixed the key-assignment marker rendering incorrectly on some platforms (appearing as a blank square on Linux or as literal placeholder text on Windows) by introducing a colored-icon indicator that renders reliably across Windows, macOS, and Linux.
- **[PL]** Naprawiono nieprawidłowe wyświetlanie znacznika przypisanego klawisza na niektórych platformach (puste kwadraty na Linuksie lub dosłowny tekst zastępczy na Windows), wprowadzając wskaźnik w postaci kolorowej ikony, który renderuje się poprawnie na Windows, macOS i Linuksie.

- **[EN]** Expanded the tool selection lists in Pad Settings to cover all 14 available SunGo Tools (previously only 10 were selectable), and completed the remaining English/Polish translation entries for full localization coverage.
- **[PL]** Rozszerzono listy wyboru narzędzi w ustawieniach pada o wszystkie 14 dostępnych narzędzi SunGo (wcześniej dostępnych było tylko 10) oraz uzupełniono brakujące wpisy tłumaczeń angielskich i polskich dla pełnego pokrycia lokalizacji.

---

## [2.9.2] - 2026-08-05

### Fixed / Poprawiono
- **[EN]** Fixed live refresh of SunGo Tools Explorer entries so MacroPAD key prefix labels update immediately after assignment changes.
- **[PL]** Naprawiono odświeżanie panelu SunGo Tools na żywo, dzięki czemu prefiksy przypisanych klawiszy MacroPAD aktualizują się od razu po zmianie funkcji.

---

## [2.9.1] - 2026-08-05

### Added / Dodano
- **[EN]** Displayed assigned SunGO MacroPAD II key markers (`A`, `B`, `C`, `S1`, `S2`) next to SunGo Tools panel entries for instant hardware mapping visibility.
- **[PL]** Wyświetlanie przypisango klawisza SunGO MacroPAD II (`A`, `B`, `C`, `S1`, `S2`) przy pozycjach panelu SunGo Tools, umożliwiając szybkie rozpoznanie przypisania.

### Changed / Zmieniono
- **[EN]** Aligned tool labels with fixed-width key prefixes in the Explorer tree view for a cleaner and more consistent layout.
- **[PL]** Wyrównano etykiety narzędzi w widoku drzewa Explorera za pomocą stałych prefiksów klawiszy, poprawiając czytelność układu.

---

## [2.9.0] - 2026-07-29

### Added / Dodano -- Built-in Documentation Generator / Wbudowany Generator Dokumentacji

- **[EN]** Added an automated Documentation Generator module in Webview that scans project architecture, parses headers via `headerGen.ts`, inspects `go.mod` (module name and Go version), executes `go list -json ./...` with a custom stream parser, and builds a clean workspace directory tree.
- **[PL]** Dodano zautomatyzowany moduł Generatora Dokumentacji w Webview, który skanuje strukturę projektu, analizuje nagłówki przez `headerGen.ts`, odczytuje `go.mod` (nazwę modułu i wersję Go), uruchamia `go list -json ./...` z własnym parserem strumienia oraz generuje czyste drzewo katalogów obszaru roboczego.

- **[EN]** Implemented structured document generation (`Docs/README.<LANG>.md`, `ARCHITECTURE`, `API`, `CONTRIBUTING`) following the "README = index + links" architectural rule, with automatic EN/PL cross-linking support.
- **[PL]** Zaimplementowano generowanie ustrukturyzowanych dokumentów (`Docs/README.<LANG>.md`, `ARCHITECTURE`, `API`, `CONTRIBUTING`) zgodnie z zasadą „README = indeks + odnośniki”, wraz z automatycznym podlinkowaniem wersji językowej EN/PL.

### Changed & Optimized / Zmieniono i Zoptymalizowano -- Webview UI Alignment / Spójność UI Webview

- **[EN]** Unified Generator UI with dark theme styling matching `PadSettingsViewNoDevice` (`#1e1e1e` / `#32CD32`), including live directory tree preview, PL/EN language toggle, and dual-language generation options.
- **[PL]** Ujednolicono interfejs Generatora z ciemnym motywem graficznym zgodnym z `PadSettingsViewNoDevice` (`#1e1e1e` / `#32CD32`), dodając podgląd drzewa katalogów na żywo, przełącznik języka PL/EN oraz opcję jednoczesnej generacji w obu językach.

---


## [2.8.0] - 2026-07-27

### Added / Dodano -- In-Doc Search Engine / Lokalna wyszukiwarka w dokumentacji

- **[EN]** Added a fast, client-side search engine for rendered documentation (`docBody`). Features a "🔎 Find" topbar button and `Ctrl+F` webview shortcut, real-time match highlighting (`<mark>`) preserving DOM syntax highlighting, match counter (`n/N`), arrow/keyboard navigation with auto-scroll to the active highlight, and instant dismissal via `Esc` or `✕`.
- **[PL]** Dodano szybką, lokalną wyszukiwarkę treści wewnątrz wyrenderowanej dokumentacji (`docBody`). Oferuje przycisk „🔎 Find” na górnym pasku, skrót `Ctrl+F` (przechwytywany w webview), dynamiczne podświetlanie trafień (`<mark>`) bez naruszania kolorowania składni (przeszukiwanie węzłów tekstowych DOM), licznik wyników (`n/N`), nawigację klawiaturą z auto-scrollem do aktywnego elementu oraz szybkie zamykanie klawiszem `Esc` lub przyciskiem `✕`.

### Changed / Zmieniono -- Status Bar Branding & MacroPAD Alignment / Aktualizacja paska stanu i spójność z MacroPAD

- **[EN]** Updated status bar item label from "SunGO Creator" to "Project Creator" and added a rocket icon, aligning visual cues with Key #2 on SunGo MacroPAD I and II.
- **[PL]** Zmieniono etykietę na belce stanu z „SunGO Creator” na „Project Creator” oraz dodano ikonę rakiety, zapewniając pełną spójność wizualną z klawiszem nr 2 na urządzeniach SunGo MacroPAD I i II.

### Optimized / Zoptymalizowano -- Performance & Webview Rendering / Optymalizacja wydajności i renderowania

- **[EN]** Refactored search algorithm and webview script execution for zero-latency DOM traversal and overall memory footprint reduction.
- **[PL]** Przeprowadzono optymalizację kodu i algorytmu przeszukiwania drzewa DOM wewnątrz webview, co zapewnia natychmiastowe działanie bez ponownego odpytywania źródła oraz mniejsze zużycie zasobów.

---


## [2.7.9] - 2026-07-24

### Fixed / Poprawiono -- Encoder Zero-Value Handling / Obsługa zerowych raportów enkodera

- **[EN]** Fixed an issue where idle or zero-value HID reports (`value === 0`) from the encoder were erroneously processed as counter-clockwise rotation, preventing accidental trigger of CCW actions (e.g. zoom out).
- **[PL]** Naprawiono błąd, w którym jałowe raporty HID o wartości zerowej (`value === 0`) z enkodera były błędnie interpretowane jako obrót w lewo, co zapobiega przypadkowemu wyzwalaniu akcji CCW (np. pomniejszaniu).

### Added / Dodano -- Function Navigation via Encoder / Nawigacja po funkcjach za pomocą enkodera

- **[EN]** Added next/previous function navigation actions (`next_function` / `prev_function`) assignable to encoder turns, allowing rapid jumping between function definitions within the active file.
- **[PL]** Dodano obsługę nawigacji po funkcjach (następna / poprzednia funkcja) dla pokrętła enkodera, umożliwiającą szybkie przeskakiwanie pomiędzy definicjami funkcji w aktywnym pliku.

---

## [2.7.8] - 2026-07-23

### Fixed / Poprawiono -- Linux HID Handling / Obsługa HID Linux

- **[EN]** Fixed an issue on Linux where scrolling the wheel (Encoder 0) falsely triggered the second encoder's button by implementing strict HID report filtering for shared `hidraw` paths.
- **[PL]** Naprawiono błąd w systemie Linux, w którym użycie rolki (Encoder 0) błędnie aktywowało przycisk drugiego enkodera, poprzez wdrożenie rygorystycznego filtrowania raportów HID dla współdzielonych ścieżek `hidraw`.

### Added / Dodano

- **[EN]** Added detection for shared endpoints and explicit dropping of standard mouse and keyboard reports (IDs 1, 2, 3), ensuring only valid `0x04` encoder payloads are processed.
- **[PL]** Dodano wykrywanie współdzielonych punktów końcowych oraz jawne odrzucanie standardowych raportów myszy i klawiatury (ID 1, 2, 3), co gwarantuje przetwarzanie wyłącznie prawidłowych pakietów enkodera z prefiksem `0x04`.

---
## [2.7.4] - [2.7.7] - 2026-07-23

### ⚠️ Test Build (Pre-release)
### ⚠️ Wersje Testowe (Pre-release)

- **[EN]** Unofficial experimental release available on GitHub. This build is intended specifically for verifying the correct reading of the `Report ID` and `Payload` structure in **HID RAW** mode.

**Known Issues:**
* Incorrect behavior of encoders on Linux operating systems.

------------

- **[PL]** Nieoficjalne wydanie eksperymentalne udostępnione na GitHubie. Wersja ta jest przeznaczona wyłącznie do weryfikacji poprawności odczytu `Report ID` oraz struktury `Payload` w trybie **HID RAW**.

**Znane problemy:**
* Nieprawidłowe zachowanie enkoderów w systemach z rodziny Linux.

---

## [2.7.3] - 2026-07-19

### Fixed / Naprawiono -- Encoder Input Architecture (ENC1 / SW0 / SW1)

- **[EN]** Redesigned the input path for ENC1 rotation and SW0/SW1 push events, replacing the previous simulated F13–F24 keypress approach with a dedicated raw HID input channel (Report ID 4, on an isolated vendor-defined Usage Page). The previous approach relied on the host OS correctly mapping extended function keys (F13–F24) to keyboard events before VS Code's `keybindings` contribution could intercept them — a mapping that Windows generally handles out of the box but that Linux (X11 and Wayland) frequently does not, depending on distribution, desktop environment, and kernel version. This made encoder actions unreliable or entirely non-functional depending on the user's platform.

  With this release, the firmware 5.9.3 pushes raw rotation/press events directly over a second, read-only HID interface, and the extension consumes them and resolves the assigned action locally, without any dependency on OS-level key capture. This removes the platform dependency entirely and applies uniformly across Windows, Linux, and macOS.

  During Windows validation, two related defects surfaced and were corrected:
  1. The extension's hardware-connect routine initialized the HID connection twice in sequence; the encoder event listener was attached to the first (short-lived) handle, which was then closed and replaced before any physical input occurred — silently discarding all encoder/switch events. The listener is now bound at the point the handle is created, guaranteeing it always tracks the live connection.
  2. On Windows, `node-hid` prefixes incoming report buffers with the Report ID byte, shifting all subsequent field offsets by one relative to what the firmware sends; this caused every event to be misread as an unrecognized source. Offset detection is now automatic and platform-independent.

  Encoder assignment in Settings (action-per-direction for ENC1, action-per-press for SW0/SW1) is unchanged from the user's perspective — only the underlying transport was replaced.

  **Status:** verified end-to-end on Windows. Linux validation is in progress; macOS validation is pending.

- **[PL]** Przeprojektowano ścieżkę obsługi zdarzeń obrotu ENC1 oraz naciśnięć SW0/SW1, zastępując dotychczasowe podejście oparte na symulowanych klawiszach F13–F24 dedykowanym kanałem surowych raportów HID (Report ID 4, na wydzielonym, niestandardowym Usage Page). Poprzednie rozwiązanie wymagało, aby system operacyjny poprawnie zmapował rozszerzone klawisze funkcyjne (F13–F24) na zdarzenia klawiatury, zanim mechanizm `keybindings` wtyczki VS Code mógł je przechwycić — mapowanie, które Windows zwykle obsługuje bez dodatkowej konfiguracji, ale które na Linuksie (X11 i Wayland) często zawodzi, w zależności od dystrybucji, środowiska graficznego i wersji jądra. Powodowało to niestabilne działanie enkodera lub jego całkowity brak działania w zależności od platformy użytkownika.

  Od tej wersji firmware 5.9.3 wysyła surowe zdarzenia obrotu/naciśnięcia bezpośrednio przez drugi, przeznaczony tylko do odczytu interfejs HID, a wtyczka odbiera je i lokalnie rozstrzyga przypisaną akcję, bez żadnej zależności od przechwytywania klawiszy na poziomie systemu. Eliminuje to zależność platformową całkowicie i działa jednolicie na Windows, Linux i macOS.

  Podczas testów na Windows ujawniono i naprawiono dwa powiązane błędy:
  1. Procedura wykrywania sprzętu w wtyczce inicjalizowała połączenie HID dwukrotnie pod rząd; nasłuchiwacz zdarzeń enkodera był podpinany do pierwszego, krótkotrwałego uchwytu, który następnie był zamykany i zastępowany, zanim doszło do jakiejkolwiek fizycznej interakcji — co powodowało ciche odrzucanie wszystkich zdarzeń enkodera/przycisków. Nasłuchiwacz jest teraz podpinany w momencie tworzenia uchwytu, co gwarantuje, że zawsze śledzi aktywne połączenie.
  2. Na Windows biblioteka `node-hid` poprzedza przychodzące bufory raportów bajtem Report ID, przesuwając wszystkie kolejne pola o jeden bajt względem tego, co wysyła firmware; powodowało to błędne odczytanie każdego zdarzenia jako nierozpoznanego źródła. Wykrywanie przesunięcia jest teraz automatyczne i niezależne od platformy.

  Przypisywanie akcji w Ustawieniach (akcja per kierunek dla ENC1, akcja per naciśnięcie dla SW0/SW1) pozostaje bez zmian z perspektywy użytkownika — zmienił się wyłącznie mechanizm transportu.

  **Status:** zweryfikowano end-to-end na Windows. Weryfikacja na Linux w toku; weryfikacja na macOS oczekująca.

---
## [2.7.2] 

- Testing wersion -- 
---

## [2.7.1] - 2026-07-18

### Optimized / Zoptymalizowano -- Project Notes / Notatki projektu

- **[EN]** Fully integrated the Project Notes layout, interactive markdown checkboxes, and execution error boundaries with the native NLS localization architecture  for seamless multilingual support.
- **[PL]** W pełni zintegrowano szablon struktury notatek, interaktywne pola wyboru (checkboxy) oraz obsługę błędów wykonawczych z natywną architekturą lokalizacji NLS , zapewniając płynne wsparcie wielojęzyczne.

---

## [2.7.0] - 2026-07-16

### Fixed & Optimized / Poprawiono i Zoptymalizowano  -- Github templates 

- **[EN]** Resolved an issue where the extension output console would freeze after creating a project structure by decoupling log rendering from filesystem cleanup, ensuring complete log compilation and `go mod init` output visibility.
- **[PL]** Naprawiono błąd polegający na zawieszaniu konsoli wyjściowej (Output) po wygenerowaniu struktury projektu poprzez uniezależnienie renderowania logów od operacji czyszczenia dysku, co zapewnia pełną widoczność logów oraz procesu `go mod init`.
- **[EN]** Optimized asynchronous error handling during GitHub template cloning to ensure graceful fallback paths and accurate status synchronization across the SunGo project manager panels.
- **[PL]** Zoptymalizowano asynchroniczną obsługę błędów podczas klonowania szablonów z serwisu GitHub, gwarantując bezpieczne procedury awaryjne (fallback) oraz stabilną synchronizację statusu w panelu menedżera projektów SunGo.

---

## [2.6.9] 

- Testing wersion -- 

---

## [2.6.8] - 2026-07-13

### Changed / Zmieniono

- **[EN]** Code optimization and performance improvements to ensure smoother application response.
- **[PL]** Optymalizacja kodu oraz poprawki wydajnościowe zapewniające płynniejsze działanie aplikacji.

### Fixed / Poprawiono

- **[EN]** Fixed various translation and localization issues across the user interface.
- **[PL]** Poprawiono błędy w tłumaczeniach oraz drobne potknięcia lokalizacyjne w interfejsie użytkownika.

---

## [2.6.7] - 2026-07-07

### Added / Dodano

- **[EN]** Added a contextual link in the Dashboard's Hardware section, shown only when no SunGO MacroPAD is detected, linking directly to the build guide for MacroPAD I and MacroPAD II.
- **[PL]** Dodano kontekstowy link w sekcji Hardware Dashboardu, wyświetlany wyłącznie gdy nie wykryto żadnego SunGO MacroPAD, prowadzący bezpośrednio do instrukcji budowy MacroPAD I i MacroPAD II.

---

## [2.6.6] - 2026-07-06

### Added / Dodano

- **[EN]** The Dashboard's "Installed Tools" panel now displays live SunGO MacroPAD hardware status, showing the detected version (MacroPAD I or II) and firmware, or a clear "None" indicator when no device is connected.
- **[PL]** Panel "Installed Tools" w Dashboardzie wyświetla teraz status podłączonego SunGO MacroPAD w czasie rzeczywistym, pokazując wykrytą wersję (MacroPAD I lub II) wraz z wersją firmware, lub czytelny wskaźnik "Brak" gdy urządzenie nie jest podłączone.
- **[EN]** Reorganized the "Installed Tools" panel into two clearly labeled subsections, Software and Hardware, for improved readability.
- **[PL]** Podzielono panel "Installed Tools" na dwie czytelnie oznaczone podsekcje, Software i Hardware, dla lepszej przejrzystości.

---

## [2.6.5] - 2026-07-06

### Changed & Fixed / Zmieniono i Poprawiono

- **[EN]** Optimized the execution of the `go run` command triggered from the SunGO MacroPAD.
- **[PL]** Zoptymalizowano wywołanie komendy `go run` uruchamianej z poziomu urządzenia SunGO MacroPAD.
- **[EN]** Added new communication commands between the extension and MacroPAD II in preparation for the upcoming firmware 5.9.3 release.
- **[PL]** Dodano nowe komendy w komunikacji pomiędzy wtyczką a urządzeniem MacroPAD II, przygotowane dla nadchodzącego firmware w wersji 5.9.3.
- **[EN]** Optimized the communication protocol to significantly improve data transfer speed and overall responsiveness.
- **[PL]** Zoptymalizowano protokół komunikacyjny, znacznie poprawiając szybkość przesyłania danych i ogólną responsywność działania.

---

## [2.6.4] - 2026-07-03

### Changed & Fixed / Zmieniono i Poprawiono

- **[EN]** General code cleanup and refactoring to improve readability and maintainability.
- **[PL]** Przeprowadzono porządkowanie kodu w celu poprawy jego czytelności i łatwości utrzymania.
- **[EN]** Applied fixes and improvements in communication with MacroPAD v2 to ensure compatibility with the recent firmware update to v5.9.2.
- **[PL]** Wprowadzono poprawki w komunikacji z urządzeniem MacroPAD v2, dostosowujące rozszerzenie do najnowszej aktualizacji firmware w wersji 5.9.2.

---

## [2.6.3] - 2026-06-24

### Fixed / Poprawiono

- **[EN]** Fixed a typo where the non-existent command was called, causing the action to fail silently without execution.
- **[PL]** Naprawiono literówkę polegającą na wywoływaniu nieistniejącej komendy, co skutkowało brakiem reakcji i cichym pominięciem wykonania polecenia.
- **[EN]** Fixed the VS Code startup execution sequence: `checkHardware` now detects the pad while `this.context` is null (skipping `restoreDeviceState`), and once `setContext(context)` is invoked via `extension.ts` or `display()`, `restoreDeviceState()` correctly restores the state sequence ('L' + 'C' + 'X'/'Z').
- **[PL]** Poprawiono kolejność wykonywania ścieżek przy starcie VS Code: `checkHardware` wykrywa pad, gdy `this.context` jest nullem (pomijając `restoreDeviceState`), a po wywołaniu `setContext(context)` z poziomu `extension.ts` lub `display()` następuje poprawne odtworzenie sekwencji stanu (`restoreDeviceState()` -> 'L' + 'C' + 'X'/'Z').
- **[EN]** Applied general code quality improvements, optimizations, and stability fixes within `PadSettingsView2` and `Encoder` commands.
- **[PL]** Wprowadzono ogólne poprawki jakościowe, optymalizacje oraz drobne poprawki w obrębie `PadSettingsView2` oraz komend `Encoder`.

---

## [2.6.2] - 2026-06-23

### Added / Dodano

- **[EN]** Introduced a dedicated webview panel displayed when no SunGO MacroPAD is detected, providing connection guidance and a one-click device re-detection mechanism.
- **[PL]** Dodano dedykowany panel webview, wyświetlany gdy żaden SunGO MacroPAD nie zostanie wykryty, zawierający wskazówki dotyczące połączenia oraz mechanizm ponownego wykrywania urządzenia jednym kliknięciem.
- **[EN]** Added full bilingual NLS localization keys (`pad.nodevice.*`) for the new no-device panel across both English and Polish language packs.
- **[PL]** Dodano pełny zestaw dwujęzycznych kluczy lokalizacyjnych NLS (`pad.nodevice.*`) dla nowego panelu braku urządzenia w pakietach językowych angielskim i polskim.

### Fixed / Poprawiono

- **[EN]** Resolved an issue where opening the MacroPAD settings without any device connected would silently fall through to the V1 configuration panel instead of informing the user.
- **[PL]** Naprawiono błąd, w którym otwarcie ustawień MacroPAD bez podłączonego urządzenia cicho otwierało panel konfiguracji V1 zamiast poinformować użytkownika o braku urządzenia.
- **[EN]** Improved hardware version detection logic in to explicitly match both the USB Product ID and the device serial number (`SR-2026-4050` for V1, `SR-2026-5050` for V2), with a safe V1 fallback for unrecognized hardware variants.
- **[PL]** Ulepszono logikę wykrywania wersji sprzętu, by jawnie dopasowywać zarówno USB Product ID, jak i numer seryjny urządzenia (`SR-2026-4050` dla V1, `SR-2026-5050` dla V2), z bezpiecznym fallbackiem do V1 dla nierozpoznanych wariantów sprzętowych.
- **[EN]** Extended the `openPadSettings` command routing in `extension.ts` to a three-way branch: `NONE` opens the no-device panel, `V2` opens the MacroPAD II settings, and `V1` opens the standard settings view.
- **[PL]** Rozszerzono routing komendy `openPadSettings` w `extension.ts` do trójnikowego rozgałęzienia: `NONE` otwiera panel braku urządzenia, `V2` otwiera ustawienia MacroPAD II, a `V1` otwiera standardowy panel ustawień.
- **[EN]** Corrected a CSS layout defect in the no-device panel where a negative `margin-top` value caused the subtitle element to visually overlap the title.
- **[PL]** Poprawiono błąd układu CSS w panelu braku urządzenia, gdzie ujemna wartość `margin-top` powodowała wizualne nachodzenie elementu podtytułu na tytuł.

---

## [2.6.1] - 2026-06-22

### Fixed / Poprawiono

- **[EN]** Enhanced execution velocity for commands transmitted to MacroPAD II via HID RAW protocols.
- **[PL]** Zwiększono szybkość działania i wykonywania komend wysyłanych do MacroPAD II przez protokół HID RAW.
- **[EN]** Conducted general performance fine-tuning to elevate overall system responsiveness.
- **[PL]** Przeprowadzono ogólne dostrojenie wydajności w celu zwiększenia ogólnej responsywności systemu.
- **[EN]** Addressed general performance bottlenecks to smooth out overall system responsiveness.
- **[PL]** Wyeliminowano ogólne wąskie gardła wydajnościowe, zwiększając płynność i responsywność systemu.

### Optimized / Zoptymalizowano

- **[EN]** Streamlined the internal codebase through comprehensive code cleanup for better maintainability.
- **[PL]** Uporządkowano wewnętrzną strukturę kodu poprzez kompleksowe czyszczenie, poprawiając łatwość jego utrzymania.
- **[EN]** Executed global performance optimizations to minimize runtime overhead and resource consumption.
- **[PL]** Przeprowadzono globalną optymalizację działania aplikacji w celu zminimalizowania narzutu systemowego i zużycia zasobów.

---

## [2.6.0] - 2026-06-16

### Added / Dodano

- **[EN]** Added dropdown lists for intuitive option selection and implemented a reliable configuration persistence mechanism within the Pad Settings panel.
- **[PL]** Dodano rozwijalne listy wyboru w ustawieniach pada oraz zaimplementowano mechanizm trwałego zapisu zmienionych konfiguracji.

### Fixed / Poprawiono

- **[EN]** Fixed command parsing for encoder hardware keys S1 and S2, assigning them as special keys with dynamically modified payload support.
- **[PL]** Naprawiono parsowanie komend dla klawiszy sprzętowych S1 i S2 enkoderów, przypisując je jako klawisze specjalne z obsługą modyfikowanej zawartości.
- **[EN]** Resolved operational issues with the programmable upper encoder (ENC 1) to ensure precise tracking and stability.
- **[PL]** Poprawiono działanie oraz precyzję programowalnego enkodera górnego (ENC 1).
- **[EN]** Corrected hardware command invocation routines and refined shortcut alias assignment logic.
- **[PL]** Poprawiono mechanizm wywoływania komend sprzętowych oraz logikę przypisywania aliasów.

### Optimized / Zoptymalizowano

- **[EN]** Conducted extensive architectural cleanup and refactoring to improve core codebase maintainability and execution velocity.
- **[PL]** Przeprowadzono gruntowne czyszczenie strukturalne oraz refaktoryzację kodu w celu zwiększenia czytelności i szybkości działania aplikacji.
- **[EN]** Enhanced system resource utilization and enforced stricter type safety across hardware communication layers.
- **[PL]** Zoptymalizowano zużycie zasobów systemowych oraz zaostrzono kontrolę typów w warstwach komunikacji niskopoziomowej.

---

## [2.5.7]  -  [2.5.9]

- Testing wersion -- 

---

## [2.5.6] - 2026-06-16

### Fixed / Poprawiono

- **[EN]** Fixed translation errors and corrected typos across various UI language versions.
- **[PL]** Naprawiono błędy w tłumaczeniach oraz poprawiono literówki w różnych wersjach językowych interfejsu użytkownika.
- **[EN]** Resolved minor bugs and overall software stability issues.
- **[PL]** Usunięto drobne błędy oraz poprawiono ogólną stabilność działania oprogramowania.

### Optimized / Zoptymalizowano

- **[EN]** Performance optimizations and general quality-of-life improvements.
- **[PL]** Zoptymalizowano wydajność oraz wprowadzono ogólne poprawki zwiększające komfort użytkowania (QoL).


---

## [2.5.5] - 2026-06-08

### Changed / Zmieniono

- **[EN]** Assigned ENC 0 function to the Mouse Wheel by default.
- **[PL]** Domyślnie przypisano funkcję ENC 0 do kółka myszy (Mouse Wheel).

### Fixed / Poprawiono

- **[EN]** Improved firmware update handling and stability.
- **[PL]** Poprawiono obsługę oraz stabilność procesu aktualizacji oprogramowania układowego (firmware).


### Optimized / Zoptymalizowano

- **[EN]** Enhanced plugin loading speed and reduced initialization time.
- **[PL]** Zoptymalizowano szybkość ładowania wtyczki oraz skrócono czas inicjalizacji.
- **[EN]** Minor memory management improvements and general code refactoring.
- **[PL]** Drobne usprawnienia w zarządzaniu pamięcią oraz ogólna refaktoryzacja kodu.
- **[EN]** Standardized and cleaned up the historical changelog structure for full EN/PL bilingual alignment.
- **[PL]** Ujednolicono i uporządkowano strukturę historycznych wpisów w changelogu w celu pełnego dostosowania do standardu dwujęzycznego EN/PL.


---

## [2.5.3] - 2026-06-01

### Optimized / Zoptymalizowano

- **[EN]** Fixed little bugs in NLS translation keys and refined overall localization accuracy.
- **[PL]** Poprawiono drobne błędy w kluczach tłumaczeń NLS oraz zwiększono dokładność lokalizacyjną interfejsu.
- **[EN]** Architectural cleanup, and significant performance optimizations.
- **[PL]** Czyszczenie strukturalne oraz znaczące optymalizacje wydajnościowe. 

---

## [2.5.2] - 2026-05-28

### Fixed & Optimized / Poprawiono i Zoptymalizowano

- **[EN]** Fixed Raw USB communication issues.
- **[PL]** Poprawiono komunikację Raw USB.
- **[EN]** Improved the firmware installer and updater for MacroPAD II.
- **[PL]** Poprawiono instalator i aktualizator firmware dla MacroPAD II.
- **[EN]** Optimized RAM usage during large data packet buffering.
- **[PL]** Zoptymalizowano zużycie pamięci RAM podczas buforowania dużych pakietów danych.
- **[EN]** Enhanced background thread stability for HID device detection.
- **[PL]** Poprawiono stabilność wątków tła odpowiedzialnych za detekcję urządzeń HID.

---

## [2.5.1] - 2026-05-20

### Added / Dodano

- **[EN]** Added a dedicated configuration file for advanced rotary encoder customization.
- **[PL]** Dodano dedykowany plik konfiguracyjny do zaawansowanej parametryzacji enkoderów obrotowych.

### Fixed & Optimized / Poprawiono i Zoptymalizowano

- **[EN]** Fixed minor bugs in NLS translation keys and refined overall localization accuracy.
- **[PL]** Poprawiono drobne błędy w kluczach tłumaczeń NLS oraz zwiększono dokładność lokalizacyjną interfejsu.
- **[EN]** Comprehensive code refactoring, architectural cleanup, and significant performance optimizations.
- **[PL]** Kompleksowa refaktoryzacja kodu, czyszczenie strukturalne oraz znaczące optymalizacje wydajnościowe.

---

## [2.5.0] - 2026-05-17

### Added / Dodano

- **[EN]** Added new configuration elements in `padSettings2` to dynamically enable/disable rotary encoders and map custom functions to the S1 and S2 hardware keys.
- **[PL]** Dodano nowe elementy konfiguracyjne w `padSettings2` umożliwiające włączanie/wyłączanie enkoderów oraz przypisywanie własnych funkcji dla klawiszy sprzętowych S1 i S2.

### Changed / Zmieniono

- **[EN]** Replaced hardcoded string literals and UI descriptions with centralized NLS (Native Language Support) translation keys.
- **[PL]** Zastąpiono zahardkodowane opisy interfejsu kluczami tłumaczeń systemu NLS (Native Language Support).

### Fixed & Optimized / Poprawiono i Zoptymalizowano

- **[EN]** Deep architectural refactoring, cleanup, and performance optimization of the `padDevice` communication layer.
- **[PL]** Gruntowny refaktoring, czyszczenie oraz optymalizacja wydajnościowa warstwy komunikacyjnej `padDevice`.

---

## [2.4.6] - 2026-05-17

### Optimized / Zoptymalizowano

- **[EN]** Improved the handling of encoder commands (`ENC0` and `ENC1`): command `X` now initializes/enables the encoders, `K1`/`K2` handle Clockwise (CW) and Counter-Clockwise (CCW) rotation codes for both units, and command `S` manages encoder push-button actions.
- **[PL]** Poprawiono obsługę komend enkoderów (`ENC0` i `ENC1`): komenda `X` odpowiada za włączenie enkoderów, `K1`/`K2` obsługują kody obrotu CW i CCW dla enkodera 0 i 1, natomiast komenda `S` obsługuje akcje zintegrowanych przycisków.
- **[EN]** Conducted extensive code refactoring and performance optimization to ensure faster execution and lower latency in hardware-to-software communication.
- **[PL]** Przeprowadzono gruntowny refaktoring oraz optymalizację wydajności kodu, co przekłada się na szybsze działanie i mniejsze opóźnienia w komunikacji na linii urządzenie-oprogramowanie.

---

## [2.4.5] - 2026-05-15

### Added / Dodano

- **[EN]** Added full support for configuring two independent rotary encoders (left and right knobs) with dual-direction detection (CW - Clockwise / CCW - Counter-Clockwise).
- **[PL]** Dodano pełne wsparcie dla konfiguracji dwóch niezależnych enkoderów obrotowych (lewe i prawe pokrętło) z wykrywaniem obu kierunków obrotu (CW - zgodnie z ruchem wskazówek zegara / CCW - przeciwnie do ruchu wskazówek zegara).
- **[EN]** Integrated a dedicated UI section for encoder mapping with NLS translation support, enabling tactical controls like scrolling, cursor movement, volume adjustment, and brightness switching.
- **[PL]** Zintegrowano dedykowaną sekcję UI do mapowania enkoderów z pełną obsługą tłumaczeń NLS, umożliwiając przypisywanie takich akcji jak przewijanie, ruch kursora, regulacja głośności czy zmiana jasności.

### Changed / Zmieniono

- **[EN]** Implemented `saveEncoderAction` and `applyEncoderConfig` message handlers to store custom actions in global state and transmit the configuration directly to the MacroPAD II hardware.
- **[PL]** Zaimplementowano obsługę komunikatów `saveEncoderAction` oraz `applyEncoderConfig` w celu zapisywania niestandardowych akcji w stanie globalnym i przesyłania konfiguracji bezpośrednio do urządzenia MacroPAD II.

---

## [2.4.3] - 2026-05-13

### Added / Dodano

- **[EN]** Added a dedicated "Firmware Update" panel within the SunGO MacroPAD II configuration settings, allowing users to check for OTA updates and enter bootloader mode (RPI-RP2) directly from the UI.
- **[PL]** Dodano dedykowany panel "Firmware Update" w ustawieniach konfiguracji SunGO MacroPAD II, umożliwiający sprawdzanie dostępności aktualizacji OTA oraz przejście w tryb bootloadera (RPI-RP2) bezpośrednio z poziomu interfejsu.
- **[EN]** Introduced a seamless "One-Click Update" system that automatically downloads the latest .uf2 file from GitHub and flashes it onto the RP2040 when a new version is available.
- **[PL]** Wprowadzono system aktualizacji "jednym kliknięciem", który automatycznie pobiera najnowszy plik .uf2 z GitHub i wgrywa go na RP2040, gdy dostępna jest nowa wersja.
- **[EN]** Added a visual progress bar in the PadSettings panel to monitor the update status, followed by an automatic restart of MacroPAD II with the new firmware active.
- **[PL]** W panelu PadSettings dodano pasek postępu monitorujący proces aktualizacji, po którego zakończeniu pad automatycznie uruchamia się ponownie z nowym oprogramowaniem.
- **[EN]** Enabled UI configuration via the Bootloader button to manually enter programming mode if a firmware downgrade is necessary.
- **[PL]** Umożliwiono konfigurację UI poprzez przycisk Bootloader do ręcznego wejścia w tryb programowania, jeśli zajdzie potrzeba powrotu do starszej wersji firmware.
- **[EN]** Added Emergency Mode recovery support by holding keys 9+10+12 while connecting the USB cable to force bootloader mode (RPI-RP2).
- **[PL]** Dodano obsługę trybu awaryjnego (Emergency Mode) poprzez przytrzymanie klawiszy 9+10+12 podczas podłączania kabla USB, aby wymusić tryb bootloadera (RPI-RP2).

### Changed / Zmieniono

- **[EN]** Seamlessly integrated the firmware update panel into the Version 2 settings window, streamlining the hardware update process.
- **[PL]** Panel aktualizacji firmware został bezpośrednio zintegrowany z oknem ustawień wersji 2, co znacznie upraszcza proces aktualizacji sprzętu.

---

## [2.4.2] - 2026-05-09

### Fixed / Poprawiono

- **[EN]** Replaced the unreliable HID command approach with a direct read of `bcdDevice` from the USB descriptor to fetch firmware version instantly upon connection without timeouts or queue blocking.
- **[PL]** Zastąpiono zawodny mechanizm komendy HID bezpośrednim odczytem pola `bcdDevice` z deskryptora USB, co pozwala na natychmiastowy odczyt wersji firmware po podłączeniu bez timeoutów i blokowania kolejki.
- **[EN]** Removed blocking `readTimeout` and async `once('data')` listener from the firmware version request, eliminating the pad freeze when opening the settings panel.
- **[PL]** Usunięto blokujący `readTimeout` i asynchroniczny listener `once('data')` z zapytania o wersję firmware, eliminując zawieszanie pada przy otwieraniu panelu ustawień.

### Changed / Zmieniono

- **[EN]** Updated requirements to ensure compatibility with Firmware v5.6.0 available on GitHub.
- **[PL]** Zaktualizowano wymagania w celu zapewnienia kompatybilności z Firmware v5.6.0 dostępnym w repozytorium GitHub.

---

## [2.4.0] - 2026-05-04

### Added / Dodano

- **[EN]** Added support for extra physical keys A, B, and C on the SunGo Macro PAD II, allowing users to assign frequently used SunGO Tools for instant hardware-triggered access.
- **[PL]** Dodano obsługę dodatkowych klawiszy fizycznych A, B i C w SunGo Macro PAD II, umożliwiając użytkownikom przypisywanie często używanych narzędzi SunGO Tools do przycisków w celu błyskawicznego dostępu sprzętowego.
- **[EN]** Introduced a new, dedicated configuration interface for visual management of Macro PAD II key assignments and behavior.
- **[PL]** Wprowadzono nowy, dedykowany interfejs konfiguracyjny do wizualnego zarządzania przypisaniami i zachowaniem klawiszy Macro PAD II.

### Changed / Zmieniono

- **[EN]** Enabled full support for the new A/B/C key reports, requiring Firmware v5.4 available on GitHub.
- **[PL]** Wdrożono pełną obsługę nowych raportów dla klawiszy A/B/C, wymagając Firmware v5.4 dostępnego w repozytorium GitHub.

---

## [2.3.9] - 2026-05-03

### Fixed / Poprawiono

- **[EN]** Fixed color picker synchronization for keys 10, 11, and 12, ensuring full RGB support across the entire 12-key layout.
- **[PL]** Naprawiono synchronizację selektorów kolorów dla klawiszy 10, 11 i 12, zapewniając pełne wsparcie RGB dla całego układu 12 klawiszy.
- **[EN]** Resolved device recognition issues on Linux by updating `udev` rules and USB descriptors for the new hardware ID (cafe:5050).
- **[PL]** Rozwiązano problemy z rozpoznawaniem urządzenia w systemie Linux poprzez aktualizację reguł `udev` oraz deskryptorów USB dla nowego ID sprzętowego (cafe:5050).

### Optimized / Zoptymalizowano

- **[EN]** Implemented a new, high-contrast "ERROR !!" screen on the LCD, featuring a full-screen red background and large-scale typography for immediate status feedback.
- **[PL]** Wdrożono nową, kontrastową planszę „ERROR !!” na LCD z pełnoekranowym czerwonym tłem i dużą typografią, zapewniającą natychmiastową informację o błędzie.
- **[EN]** Improved the state machine in `display.c` to ensure a smooth transition and automatic return to the Gopher idle screen after clearing status messages.
- **[PL]** Udoskonalono maszynę stanów w `display.c`, zapewniając płynne przejście i automatyczny powrót do ekranu bezczynności z Gopherem po wyczyszczeniu komunikatów statusu.

---

## [2.3.8] - 2026-05-03

### Added / Dodano

- **[EN]** Officially introduced the SunGO PAD v2 prototype, featuring an expanded 12-key layout, rotary encoders, and an LCD Display.
- **[PL]** Oficjalnie wprowadzono prototyp SunGO PAD v2, wyposażony w rozszerzony układ 12 klawiszy, enkodery obrotowe i wyświetlacz LCD.
- **[EN]** Deployment of dedicated testing firmware for the v2 revision to support early development and testing.
- **[PL]** Wdrożono dedykowane oprogramowanie testowe dla rewizji v2 w celu wsparcia wczesnego rozwoju i testów.
- **[EN]** Enhanced the UI with dedicated indicators for the new macro keys (10, 11, 12) in the expanded layout.
- **[PL]** Wzbogacono UI o dedykowane wskaźniki dla nowych klawiszy makr (10, 11, 12) w rozszerzonym układzie.

### Changed / Zmieniono

- **[EN]** Designed the configuration panel to dynamically switch between 9-key (v1) and 12-key (v2) layouts based on detected hardware.
- **[PL]** Panel konfiguracyjny dynamicznie przełącza się między układem 9-klawiszowym (v1) a 12-klawiszowym (v2) na podstawie wykrytego sprzętu.

---

## [2.3.7] - 2026-04-30

### Added / Dodano

- **[EN]** Implemented a robust version recognition system for SunGo MacroPAD series that automatically distinguishes between v1 (fw.4.0) and the new MacroPAD II by analyzing PIDs and Serial Numbers.
- **[PL]** Wprowadzono inteligentny system rozpoznawania wersji SunGo MacroPAD, który automatycznie rozróżnia model v1 (fw.4.0) od nowego MacroPAD II na podstawie analizy identyfikatorów PID oraz numerów seryjnych.

### Changed / Zmieniono

- **[EN]** Updated the localization engine to provide version-specific welcome messages upon device connection.
- **[PL]** Zaktualizowano silnik lokalizacji, aby wyświetlać komunikaty powitalne dopasowane do konkretnej wersji urządzenia po jego podłączeniu.

### Optimized / Zoptymalizowano

- **[EN]** Optimized the HID polling logic and improved conditional hardware checks to prevent false-positive detection, cleaning up the core communication class.
- **[PL]** Zoptymalizowano logikę odpytywania HID oraz poprawiono warunkowe sprawdzanie sprzętu, eliminując błędne wykrycia i oczyszczając główną klasę komunikacyjną.
- **[EN]** Improved the automated shortcut creation process for Windows and Linux, ensuring smoother integration with the system's PATH environment.
- **[PL]** Udoskonalono proces automatycznego tworzenia skrótów dla systemów Windows i Linux, zapewniając lepszą integrację ze zmiennymi środowiskowymi PATH.

---

## [2.3.6] - 2026-04-26

### Changed / Zmieniono

- **[EN]** Integrated a new SVG-based SunGo logo with a smooth hover animation where the sun rotates interactively.
- **[PL]** Zintegrowano nowe logo SunGo oparte na formacie SVG z płynną animacją po najechaniu kursorem, w której słońce obraca się interaktywnie.
- **[EN]** Added a centralized navigation hub within the logo view, providing one-click access to WikiDOC, the Lothar TeaM forum, and the official GitHub repository.
- **[PL]** Dodano centrum nawigacji w widoku logo, zapewniające dostęp jednym kliknięciem do WikiDOC, forum Lothar TeaM oraz oficjalnego repozytorium GitHub.

### Optimized / Zoptymalizowano

- **[EN]** Optimized the sidebar interface with a centered, minimalist link structure for better readability and a professional look.
- **[PL]** Zoptymalizowano interfejs paska bocznego poprzez wyśrodkowaną, minimalistyczną strukturę linków, zapewniając lepszą czytelność i profesjonalny wygląd.

---

## [2.3.5] - 2026-04-25

### Optimized / Zoptymalizowano

- **[EN]** Enabled Gopher to detect Code Review errors in real-time and present them directly in a speech bubble for immediate visibility.
- **[PL]** Gopher wykrywa teraz błędy z Code Review w czasie rzeczywistym i prezentuje je bezpośrednio w dymku, zapewniając ich natychmiastową widoczność.
- **[EN]** Configured the assistant to inform users via a speech bubble about the overall cleanliness and health of their code based on static analysis.
- **[PL]** Asystent informuje teraz w dymku o ogólnej czystości i kondycji kodu na podstawie analizy statycznej.

---

## [2.3.0] - 2026-04-25

### Changed / Zmieniono

- **[EN]** Updated the Code Review panel to provide actionable hints and common solutions for issues detected by static analysis tools.
- **[PL]** Panel Code Review wyświetla teraz praktyczne wskazówki i typowe rozwiązania dla problemów wykrytych przez narzędzia analizy statycznej.
- **[EN]** Integrated the Gopher assistant with `staticcheck` to dynamically react to detected errors and warnings with contextual support.
- **[PL]** Asystent Gopher został zintegrowany z `staticcheck`, dynamicznie reagując na błędy i ostrzeżenia oraz oferując kontekstowe wsparcie.
- **[EN]** Integrated analysis results with SunGo Pad hardware, representing statuses with intuitive color coding for physical feedback.
- **[PL]** Zintegrowano wyniki analizy z urządzeniem SunGo Pad, reprezentując statusy za pomocą intuicyjnych kolorów na urządzeniu.
- **[EN]** Removed `go vet` from the SunGo Tools panel to eliminate redundancy and improve overall performance.
- **[PL]** Usunięto `go vet` z panelu SunGo Tools, aby wyeliminować powtarzające się wyniki i poprawić wydajność.
- **[EN]** Updated the Code Review interface to support new status indicators and improved readability of tool suggestions.
- **[PL]** Odświeżono interfejs Code Review, wprowadzając nowe wskaźniki statusu oraz poprawiając czytelność sugestii narzędziowych.

---

## [2.1.0] - 2026-04-21

### Added / Dodano

- **[EN]** Added a comprehensive Code Review Panel accessible from the SunGo Tools panel, supporting parallel execution of `go vet`, `staticcheck`, and `golangci-lint`.
- **[PL]** Dodano kompleksowy panel statycznej analizy kodu dostępny z panelu SunGo Tools, obsługujący równoległe uruchamianie `go vet`, `staticcheck` oraz `golangci-lint`.
- **[EN]** Implemented visual indicators for real-time tool installation status (green dot for available, gray for missing).
- **[PL]** Wdrożono wizualne wskaźniki statusu instalacji narzędzi w czasie rzeczywistym (zielona kropka dla dostępnych, szara dla braku).
- **[EN]** Created an interactive results list with severity icons, allowing users to click an issue to jump directly to the target file and line.
- **[PL]** Utworzono interaktywną listę wyników z ikonami ważności, umożliwiającą kliknięcie problemu w celu bezpośredniego przejścia do pliku i linii.
- **[EN]** Added filtering by severity and search functionality by file or message content.
- **[PL]** Dodano filtrowanie problemów według ważności oraz wyszukiwanie po pliku lub treści wiadomości.
- **[EN]** Integrated Gopher reactions to analysis results, triggering confetti 🎉 when clear or a sad state 😢 when errors are found.
- **[PL]** Zintegrowano reakcje Gophera na wyniki analizy, uruchamiając confetti 🎉 przy braku błędów lub smutny stan 😢 po wykryciu problemów.
- **[EN]** Full NLS translation support for all labels, buttons, and messages.
- **[PL]** Pełna obsługa tłumaczeń NLS dla wszystkich etykiet, przycisków i komunikatów.

---

## [2.0.0] - 2026-04-21

### Added / Dodano

- **[EN]** Added remote Git template integration to create new projects instantly via high-speed cloning.
- **[PL]** Dodano integrację ze zdalnymi szablonami Git, pozwalającą na błyskawiczne tworzenie nowych projektów poprzez szybkie klonowanie.
- **[EN]** Native support for the curated `sungo_templates` repository, providing pre-configured and optimized Go environments.
- **[PL]** Natywne wsparcie dla wyselekcjonowanego repozytorium `sungo_templates`, dostarczającego zestaw wstępnie skonfigurowanych i zoptymalizowanych środowisk Go.
- **[EN]** Added support for custom template URLs using any public or private Git repository as a project base.
- **[PL]** Dodano obsługę niestandardowych adresów URL szablonów, umożliwiając użycie dowolnego publicznego lub prywatnego repozytorium Git jako bazy projektu.

### Optimized / Zoptymalizowano

- **[EN]** Streamlined the project creation workflow by automatically initializing templates immediately after downloading.
- **[PL]** Usprawniono proces tworzenia projektu poprzez automatyczną inicjalizację szablonów bezpośrednio po pobraniu.

---

## [1.9.1] - 2026-04-19

### Added / Dodano

- **[EN]** Added a Favorite Projects pinning system with a dedicated **★ FAVORITES** section appearing at the top of the sidebar.
- **[PL]** Dodano system przypinania ulubionych projektów z dedykowaną sekcją **★ ULUBIONE** pojawiającą się na samej górze paska bocznego.
- **[EN]** Added inline pin/unpin star icons visible on hover for swift project management without right-clicking.
- **[PL]** Dodano ikony przypinania/odpinania (gwiazdki) widoczne po najechaniu myszą, pozwalające na szybkie zarządzanie projektami bez prawego kliknięcia.
- **[EN]** Added context menu options for pinning and unpinning projects from favorites.
- **[PL]** Dodano opcje menu kontekstowego do przypinania i odpinania projektów z ulubionych.
- **[EN]** Integrated favorite projects into the Dashboard as golden star chips inside the Active Projects card.
- **[PL]** Zintegrowano ulubione projekty z Dashboardem w postaci złotych chipów z gwiazdką na karcie Active Projects.
- **[EN]** Added a rich, browser-style Go Doc Viewer documentation panel accessible from the SunGo Tools panel.
- **[PL]** Dodano bogaty panel dokumentacji Go Doc Viewer w stylu przeglądarki, dostępny z panelu SunGo Tools.
- **[EN]** Implemented an automated Import Browser that displays clickable package imports split into Standard Library and Third-party sections.
- **[PL]** Zaimplementowano automatyczną przeglądarkę importów wyświetlającą klikalne pakiety podzielone na bibliotekę standardową oraz zewnętrzne pakiety.
- **[EN]** Added syntax highlighting for documentation outputs and full package search capabilities.
- **[PL]** Dodano kolorowanie składni dla wyświetlanej dokumentacji oraz pełną funkcjonalność wyszukiwania pakietów.
- **[EN]** Integrated a shortcut button to jump directly to the active package details on `pkg.go.dev`.
- **[PL]** Zintegrowano przycisk skrótu pozwalający na bezpośrednie otwieranie szczegółów pakietu na stronie `pkg.go.dev`.
- **[EN]** Full NLS translation support for all newly introduced labels, components, and messages.
- **[PL]** Pełna obsługa tłumaczeń NLS dla wszystkich nowo wprowadzonych etykiet, komponentów i komunikatów.

### Changed / Zmieniono

- **[EN]** Configured pinned projects to appear exclusively in the favorites section, automatically hiding them from the general project list.
- **[PL]** Skonfigurowano przypięte projekty tak, aby pojawiały się wyłącznie w sekcji ulubionych, automatycznie ukrywając je na ogólnej liście projektów.
- **[EN]** Formatted favorite items to survive VS Code restarts by utilizing global extension state storage.
- **[PL]** Sformatowano ulubione pozycje tak, aby przetrwały restarty VS Code dzięki zapisowi w globalnym stanie rozszerzenia.

---

## [1.8.3] - 2026-04-18

### Added / Dodano

- **[EN]** Added a live animated Gopher Assistant Panel inside the sidebar that reacts in real time to project pipeline actions.
- **[PL]** Dodano animowany panel Asystenta Gopher wewnątrz paska bocznego, który reaguje w czasie rzeczywistym na akcje w potoku projektu.
- **[EN]** Implemented 8 distinct reactive states for Gopher including idle, building, running, testing, go vet, go fmt, error, and build completion.
- **[PL]** Zaimplementowano 8 różnych stanów reaktywnych dla Gophera, w tym bezczynność (idle), budowanie, uruchamianie, testowanie, go vet, go fmt, błąd oraz zakończenie budowania.
- **[EN]** Added localized Gopher Wisdom speech bubbles that rotate useful Go programming tips on click.
- **[PL]** Dodano zlokalizowane chmurki "Mądrości Gophera", które po kliknięciu rotują przydatne wskazówki dotyczące programowania w Go.
- **[EN]** Incorporated a surprise Easter egg animation triggered by triple-clicking the Gopher within 2 seconds.
- **[PL]** Wdrożono niespodziankę w postaci animacji wyzwalanej potrójnym kliknięciem Gophera w ciągu 2 sekund.
- **[EN]** Full NLS translation support for all labels, badges, and status messages within the assistant panel.
- **[PL]** Pełna obsługa tłumaczeń NLS dla wszystkich etykiet, odznak i komunikatów statusu w panelu asystenta.

---

## [1.6.2] - 2026-04-17

### Fixed / Poprawiono

- **[EN]** Fixed a bug in commit message parsing where spaces caused execution failures on Windows, resolved by switching to direct argument passing.
- **[PL]** Naprawiono błąd w parsowaniu opisów commita, w którym spacje powodowały błędy wykonania w systemie Windows, rozwiązując go przez przejście na bezpośrednie przekazywanie argumentów.
- **[EN]** Standardized Git command execution to guarantee cross-platform stability and identical behavior across Windows, Linux, and macOS.
- **[PL]** Zunifikowano sposób wywoływania komend Git, zapewniając identyczne działanie i stabilność wieloplatformową w systemach Windows, Linux i macOS.

### Changed / Zmieniono

- **[EN]** Renamed the Git repository module to "Publish Any Files to Any REPO" to better reflect its universal deployment purpose.
- **[PL]** Zmieniono nazwę modułu repozytoriów Git na „Publish Any Files to Any REPO”, aby lepiej oddać jego uniwersalne przeznaczenie.

---

## [1.6.1] - 2026-04-17

### Added / Dodano

- **[EN]** Added a dedicated Git Repository Module supporting dual repository management without replacing native VS Code Git features.
- **[PL]** Dodano dedykowany moduł repozytoriów Git obsługujący jednoczesne zarządzanie wieloma repozytoriami bez zastępowania natywnych funkcji Git w VS Code.
- **[EN]** Implemented selective deployment capabilities allowing users to push chosen files to external repositories via a picker.
- **[PL]** Zaimplementowano funkcję selektywnego wysyłania, umożliwiającą użytkownikom przesyłanie wybranych plików do zewnętrznych repozytoriów za pomocą pickera.
- **[EN]** Streamlined binary distribution workflows to keep source code in a private repository while pushing compiled assets to a public repository.
- **[PL]** Usprawniono proces dystrybucji plików binarnych, pozwalając na utrzymywanie kodu źródłowego w prywatnym repozytorium przy jednoczesnej publikacji gotowych zasobów w repozytorium publicznym.

---

## [1.5.5] - 2026-04-15

### Added / Dodano

- **[EN]** Added a custom "My Snippets" editor section at the end of the sidebar supporting user-defined patterns.
- **[PL]** Dodano sekcję edytora własnych wzorców „My Snippets” na końcu paska bocznego, obsługującą szablony zdefiniowane przez użytkownika.
- **[EN]** Introduced an integrated UI with an overlay form to add custom snippets with custom title, description, tags, and Go code.
- **[PL]** Wprowadzono zintegrowany interfejs z formularzem nakładki do dodawania własnych snippetów z tytułem, opisem, tagami oraz kodem Go.
- **[EN]** Implemented background-click dismissals and persistent global storage mechanics for custom snippets.
- **[PL]** Wdrożono zamykanie nakładki poprzez kliknięcie w tło oraz mechanizm trwałego zapisu własnych snippetów w `globalStorage`.

### Fixed / Poprawiono

- **[EN]** Refactored the Snippet Manager library to fix translations, standardize English titles, harmonize source code strings, and unify comments to a clean format.
- **[PL]** Przebudowano bibliotekę Snippet Managera w celu poprawy tłumaczeń, ujednolicenia angielskich tytułów, harmonizacji stringów w kodzie oraz unifikacji komentarzy do czytelnego formatu.

---

## [1.5.0] - 2026-04-14

### Added / Dodano

- **[EN]** Added a Snippet Manager offering categorized code patterns for core Go concepts with one-click editor insertion.
- **[PL]** Dodano Menedżer Snippetów oferujący uporządkowane wzorce kodu dla kluczowych koncepcji języka Go z funkcją wstawiania jednym kliknięciem.
- **[EN]** Added a Go Generate Runner interface for scanning and executing `//go:generate` directives with real-time output feedback.
- **[PL]** Dodano interfejs Go Generate Runner do skanowania i uruchamiania dyrektyw `//go:generate` z podglądem danych wyjściowych na żywo.

### Fixed / Poprawiono

- **[EN]** Resolved Webview focus issues within the Snippet Manager and corrected message translations across both features.
- **[PL]** Naprawiono błędy z fokusem w Webview wewnątrz Menedżera Snippetów oraz poprawiono tłumaczenia komunikatów w obu funkcjach.
- **[EN]** Addressed stability issues and optimized performance based on test version feedback.
- **[PL]** Naprawiono błędy stabilności i zoptymalizowano działanie narzędzi na podstawie informacji zwrotnych z wersji testowej.

---

## [1.4.0] - 2026-04-12

### Changed / Zmieniono

- **[EN]** Released an experimental snapshot test version containing initial implementations of the Snippet Manager and Go Generate Runner modules.
- **[PL]** Wydano eksperymentalną wersję testową zawierającą wstępne implementacje modułów Menedżera Snippetów oraz Go Generate Runner.

---

## [1.2.2] - 2026-04-03

### Fixed / Poprawiono

- **[EN]** Corrected several user interface translation keys and notification strings to ensure proper clarity in both English and Polish.
- **[PL]** Poprawiono błędy w tłumaczeniach komunikatów interfejsu oraz powiadomień, zapewniające większą spójność i jasność w języku polskim i angielskim.

---

## [1.1.1] - 2026-03-22

### Changed / Zmieniono

- **[EN]** Optimized file header generator functions and conducted comprehensive code refactoring for core classes.
- **[PL]** Zoptymalizowano funkcje generatora nagłówków oraz przeprowadzono kompleksowy refaktoring kodu głównych klas.
- **[EN]** Added dedicated short-form NLS translation keys for all items within the SunGo Tools View panel to respect active language configurations.
- **[PL]** Dodano dedykowane krótkie klucze tłumaczeń NLS dla wszystkich pozycji w panelu SunGo Tools View, aby poprawnie respektować aktywną konfigurację językową.

---

## [1.1.0] - 2026-03-22

### Added / Dodano

- **[EN]** Added the SunGo Tools View panel in the Explorer sidebar providing direct, quick access to all analytical utilities without switching views.
- **[PL]** Dodano nowy panel SunGo Tools View w pasku eksploratora, zapewniający bezpośredni, szybki dostęp do wszystkich narzędzi analitycznych bez przełączania widoków.

### Changed / Zmieniono

- **[EN]** Reorganized global settings into 4 dedicated, expandable configuration sections: Build, File Header, Code Metrics, and Security.
- **[PL]** Przegrupowano ustawienia globalne rozszerzenia na 4 dedykowane, rozwijane sekcje konfiguracyjne: Build, File Header, Code Metrics oraz Security.
- **[EN]** Updated the active project tree icon to use a green, theme-compliant folder indicator instead of the static Go logo.
- **[PL]** Zaktualizowano ikonę aktywnego projektu w drzewie, wprowadzając zielony wskaźnik folderu zgodny z motywami zamiast statycznego logo Go.
- **[EN]** Unified dashboard and header management icons to use standard VS Code Codicons matching the general editor design guidelines.
- **[PL]** Ujednolicono ikony Dashboardu oraz zarządzania nagłówkami, wprowadzając standardowe ikony Codicons zgodne z wytycznymi projektowymi edytora.

---

## [1.0.0] - 2026-03-22

### Added / Dodano

- **[EN]** Released the first stable milestone milestone of SunGo Project Manager, establishing complete coverage for the entire Go development lifecycle.
- **[PL]** Wydano pierwszą stabilną wersję (milestone) SunGo Project Manager, zapewniając pełne pokrycie całego cyklu życia projektów Go.
- **[EN]** Added a Project Notes system that automatically initializes and opens a structured `.vscode/sungo_notes.md` file upon activation.
- **[PL]** Dodano system notatek projektowych (Project Notes), który automatycznie inicjalizuje i otwiera ustrukturyzowany plik `.vscode/sungo_notes.md`.
- **[EN]** Added a Code Metrics & Refactoring Hints utility that performs recursive static analysis to compute LOC data and present contextual metrics.
- **[PL]** Dodano narzędzie Code Metrics & Refactoring Hints, które przeprowadza rekurencyjną analizę statyczną kodu, wyliczając linie LOC i prezentując metryki kontekstowe.

---

## [0.9.0] - 2026-03-21

### Added / Dodano

- **[EN]** Added a File Header Generator module supporting 5 distinct formatting layouts alongside customizable user-defined template tokens.
- **[PL]** Dodano moduł generatora nagłówków plików (File Header Generator) obsługujący 5 różnych układów formatowania wraz z niestanodwymi tokenami szablonu.
- **[EN]** Implemented a Live Preview panel updating automatically during style adjustments with direct editor insertion capabilities.
- **[PL]** Zaimplementowano panel podglądu na żywo (Live Preview) aktualizujący się automatycznie podczas zmian stylu wraz z funkcją bezpośredniego wstawiania nagłówka.
- **[EN]** Added an automated header injection option triggered instantly upon the creation of new Go files when configured.
- **[PL]** Dodano opcję automatycznego wstrzykiwania nagłówków uruchamianą natychmiast przy tworzeniu nowych plików Go, jeśli funkcja jest włączona.

---

## [0.0.5] - 2026-01-27

### Added / Dodano

- **[EN]** Added a Go compiler presence validator executing upon extension startup to protect new installations from environment configuration errors.
- **[PL]** Dodano weryfikator obecności kompilatora Go uruchamiany podczas startu rozszerzenia, chroniący nowe instalacje przed błędami konfiguracji środowiska.
- **[EN]** Implemented secure system command execution patterns natively supporting whitespaces within workspace project paths.
- **[PL]** Zaimplementowano bezpieczne wzorce wykonywania komend systemowych, natywnie obsługujące znaki spacji w ścieżkach projektów obszaru roboczego.
- **[EN]** Added a status bar shortcut allowing users to trigger standard code formatting routines via the `go fmt` utility.
- **[PL]** Dodano skrót na pasku statusu umożliwiający użytkownikom wywoływanie standardowych procedur formatowania kodu przy użyciu narzędzia `go fmt`.

---

## [0.0.4] - 2026-01-27

### Added / Dodano

- **[EN]** Official initial public launch of the SunGo Project Manager extension on the Visual Studio Code Marketplace.
- **[PL]** Oficjalna pierwsza publiczna premiera rozszerzenia SunGo Project Manager na platformie Visual Studio Code Marketplace.
- **[EN]** Implemented the core localization localization engine with comprehensive translation maps for both English and Polish language packs.
- **[PL]** Zaimplementowano główny silnik lokalizacyjny z pełnymi mapami tłumaczeń dla angielskiego i polskiego pakietu językowego.
- **[EN]** Added baseline workspace structure generators supporting automated module initialization and clean removal profiles.
- **[PL]** Dodano podstawowe generatory struktur obszaru roboczego obsługujące automatyczną inicjalizację modułów oraz profile czystego usuwania.