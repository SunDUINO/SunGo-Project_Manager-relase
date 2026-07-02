# Changelog – SunGO PAD Firmware

[EN] All notable changes to the SunGO PAD firmware are documented in this file.  
[PL] Wszystkie istotne zmiany w oprogramowaniu układowym SunGO PAD są dokumentowane w tym pliku.

---

## [5.9.2] - 2026-07-02

### Changed / Zmieniono

- **[EN]** Reorganized and standardized `report_ID` structures to ensure cleaner packet parsing and better data routing predictability.
- **[PL]** Uporządkowano i ustandaryzowano struktury `report_ID`, aby zapewnić czystsze parsowanie pakietów i lepszą przewidywalność trasowania danych.
- **[EN]** Refined the information screens for tool keys A, B, and C, improving the visual layout and readability of displayed parameters.
- **[PL]** Usprawniono ekrany informacyjne dla klawiszy narzędziowych A, B i C, poprawiając układ wizualny oraz czytelność wyświetlanych parametrów.

### Optimized / Zoptymalizowano

- **[EN]** Enhanced HID RAW communication routines, significantly improving data transfer speeds and reducing overall input latency.
- **[PL]** Zwiększono szybkość procedur komunikacji HID RAW, co znacznie poprawiło prędkość transferu danych i zredukowało ogólne opóźnienia wejścia.
- **[EN]** Conducted comprehensive code refactoring and cleanup to streamline internal logic, remove redundancies, and improve project maintainability.
- **[PL]** Przeprowadzono kompleksowy refaktoring i porządkowanie kodu, aby usprawnić wewnętrzną logikę, usunąć nadmiarowości i ułatwić dalsze utrzymanie projektu.

---

## [5.9.1] - 2026-06-17

### Added / Dodano

- **[EN]** Implemented a dedicated, graphical error handling screen (`display_show_error`) featuring a geometric warning triangle and status text.
- **[PL]** Wdrożono dedykowany, graficzny ekran obsługi błędów (`display_show_error`) zawierający geometryczny trójkąt ostrzegawczy oraz tekst statusu.

### Changed / Zmieniono

- **[EN]** Redesigned the error notification layout to integrate seamlessly with the default dark theme (`C_DARK`), enhancing visual consistency across critical system alerts.
- **[PL]** Przeprojektowano układ powiadomień o błędach, aby bezszwowo integrował się z domyślnym ciemnym motywem (`C_DARK`), podnosząc spójność wizualną krytycznych alertów systemowych.

### Optimized / Zoptymalizowano

- **[EN]** Optimized geometric rendering routines by utilizing line-by-line drawing algorithms (`lcd_hline_f`), eliminating screen flickering and reducing SPI bus overhead during heavy render states.
- **[PL]** Zoptymalizowano procedury renderowania geometrii poprzez użycie algorytmów rysowania linia po linii (`lcd_hline_f`), co wyeliminowało migotanie ekranu i zmniejszyło narzut na magistrali SPI podczas obciążających stanów renderowania.
- **[EN]** Refined display state machine logic to ensure atomic transitions and block redundant frame buffer clear operations during override states.
- **[PL]** Usprawniono logikę maszyny stanów wyświetlacza, zapewniając atomowe przejścia i blokując nadmiarowe operacje czyszczenia bufora ramki w stanach nadpisania (override).

---

## [5.9.0] - 2026-06-08

### Added / Dodano

- **[EN]** Configured the ENC 0 encoder to operate as a Mouse Wheel by default.
- **[PL]** Skonfigurowano pokrętło ENC 0 do domyślnej pracy jako kółko myszy (Mouse Wheel).

### Changed / Zmieniono

- **[EN]** Thorough code refactoring – cleaned up the structure and improved software architecture readability.
- **[PL]** Gruntowna refaktoryzacja kodu – oczyszczono strukturę i poprawiono czytelność architektury oprogramowania.

### Fixed / Poprawiono

- **[EN]** Improved HID RAW communication stability, eliminating transmission errors and enhancing low-level data packet exchange.
- **[PL]** Poprawiono stabilność komunikacji HID RAW – wyeliminowano błędy transmisji i usprawniono niskopoziomową wymianę pakietów danych.

### Optimized / Zoptymalizowano

- **[EN]** Optimized system performance to reduce resource consumption, ensuring more stable firmware execution.
- **[PL]** Zoptymalizowano wydajność systemu – zmniejszono zużycie zasobów, co przekłada się na stabilniejsze działanie oprogramowania układowego.
- **[EN]** Refined LCD graphics rendering, optimizing visual asset delivery and increasing screen animation smoothness.
- **[PL]** Zoptymalizowano renderowanie grafiki LCD – ulepszono wyświetlanie elementów wizualnych oraz zwiększono płynność animacji na ekranie.

---

## [5.8.8] - 2026-05-28

### Changed / Zmieniono

- **[EN]** Conducted a thorough code refactoring to clean up structure and enhance overall software architecture readability.
- **[PL]** Przeprowadzono gruntowną refaktoryzację kodu – oczyszczono strukturę i poprawiono czytelność architektury oprogramowania.

### Fixed / Poprawiono

- **[EN]** Enhanced HID RAW communication stability, eliminating transmission drops and polishing low-level packet data exchange.
- **[PL]** Poprawiono stabilność komunikacji HID RAW – wyeliminowano błędy transmisji i usprawniono niskopoziomową wymianę pakietów danych.

### Optimized / Zoptymalizowano

- **[EN]** Optimized system performance to reduce active resource overhead, contributing to a more reliable firmware runtime.
- **[PL]** Zoptymalizowano wydajność systemową – zmniejszono zużycie zasobów, co przełożyło się na stabilniejsze działanie firmware.
- **[EN]** Upgraded LCD graphics rendering engine, speeding up visual asset output and boosting animation smoothness.
- **[PL]** Zoptymalizowano renderowanie grafiki LCD – usprawniono wyświetlanie elementów wizualnych oraz zwiększono płynność animacji na ekranie.

---

## [5.8.4] - 2026-05-20

### Added / Dodano

- **[EN]** Implemented Report ID 4 specifically dedicated to handling encoder inputs and S1/S2 push buttons.
- **[PL]** Wprowadzono identyfikator raportu (Report ID 4) dedykowany dla obsługi enkoderów oraz przycisków S1/S2.
- **[EN]** Added a new 'Z' command allowing the extension to programmatically disable encoders (replacing the old 'X' toggle).
- **[PL]** Dodano nową komendę „Z”, która umożliwia całkowite wyłączenie enkoderów z poziomu wtyczki (zastępując dawny przełącznik „X”).

### Optimized / Zoptymalizowano

- **[EN]** Refined encoder visualization routines on the LCD screen for smoother interactive rendering.
- **[PL]** Zoptymalizowano płynność działania wizualizacji pracy enkoderów na ekranie LCD.
- **[EN]** Integrated optimization tweaks for the TinyUSB HID module (`Tud_HID`).
- **[PL]** Wprowadzono poprawki optymalizacyjne dla modułu TinyUSB HID (`Tud_HID`).
- **[EN]** Switched to direct HID RAW read/write operations to drastically improve interface responsiveness and data throughput.
- **[PL]** Przejściem na bezpośredni odczyt/zapis RAW uzyskano znacznie szybszą i płynniejszą transmisję danych.

---

## [5.8.2] - 2026-05-17

### Added / Dodano

- **[EN]** Integrated backend support for hardware encoder instructions: 'X' enables encoders (disabled by default), 'K1' maps encoder ENC0, and 'K2' handles encoder ENC1.
- **[PL]** Dodano pełną obsługę komend dla enkoderów: „X” włącza enkodery (domyślnie wyłączone), „K1” obsługuje enkoder ENC0, a „K2” odpowiada za enkoder ENC1.
- **[EN]** Added real-time hardware visualization graphs for encoder rotation states directly on the LCD screen.
- **[PL]** Dodano wizualizację działania i obrotów enkoderów bezpośrednio na ekranie LCD.
- **[EN]** Introduced 'S1' and 'S2' commands to handle physical push button actions built into the encoders.
- **[PL]** Dodano komendy „S1” i „S2” obsługujące fizyczne wciśnięcia wbudowanych przycisków enkoderów.

---

## [5.7.0] - 2026-05-13

### Added / Dodano

- **[EN]** Designed an exclusive "UPDATE FIRMWARE" graphic layout, triggered immediately when the bootloader is booted via PadSettings.
- **[PL]** Dodano dedykowaną planszę graficzną dla trybu „UPDATE FIRMWARE”, wyświetlaną po uruchomieniu bootloadera z poziomu sekcji PadSettings.

### Changed / Zmieniono

- **[EN]** Performed general code refactoring across core modules to clean up sub-system relations.
- **[PL]** Przeprowadzono ogólną refaktoryzację kodu w modułach głównych w celu uporządkowania zależności.

### Fixed / Poprawiono

- **[EN]** Adjusted micro-timings across peripheral control routines to prepare underlying systems for stable encoder signal processing.
- **[PL]** Drobne poprawki w timingach i czasach procesora w celu przygotowania stabilnej obsługi sygnałów z enkoderów.

---

## [5.6.5] - 2026-05-10

### Optimized / Zoptymalizowano

- **[EN]** Optimized general code layout, tuning TinyUSB processing loops and HID RAW communication layer for superior stability and execution speeds.
- **[PL]** Zoptymalizowano kod źródłowy – poprawki w pętli obsługi TinyUSB oraz w warstwie protokołu transmisyjnego HID RAW przyniosły wyższą stabilność i szybkość.

---

## [5.6.0] — 2026-05-09

### Added / Dodano

- **[EN]** Implemented an emergency hardware bootloader trigger: holding down keys 9+10+12 while plugging in USB forces the board into bootloader mode (mounted as "RPI-RP2") instead of loading the main firmware app.
- **[PL]** Dodano wsparcie dla awaryjnego trybu bootloadera – przytrzymanie klawiszy 9+10+12 podczas podłączania kabla USB wymusza wejście w tryb bootloadera (widoczny w systemie jako dysk „RPI-RP2”) zamiast startu aplikacji.
- **[EN]** Added the 'U' runtime command to allow remote bootloader software execution straight from the VS Code extension, laying foundations for seamless OTA firmware upgrades.
- **[PL]** Dodano instrukcję „U” umożliwiającą programowe przejście w tryb bootloadera bezpośrednio z wtyczki VS Code, co stanowi przygotowanie pod zdalne aktualizacje sprzętu (OTA).
- **[EN]** Extracted firmware version tracking macros (`FW_VER_MAJOR`, `FW_VER_MINOR`, `FW_VER_PATCH`) into `usb_descriptors.h`, forming a single source of truth for the USB bcdDevice descriptor and the LCD display info string.
- **[PL]** Przeniesiono wersjonowanie oprogramowania do pliku `usb_descriptors.h` za pomocą makr – jedno wspólne miejsce definicji wersji dla deskryptora USB (bcdDevice) oraz ciągu znaków na ekranie LCD.
- **[EN]** Upgraded the MacroPAD boot splash screen to actively print out the currently active firmware build version.
- **[PL]** Odświeżono logo startowe MacroPADA – na ekranie LCD wyświetla się teraz również aktualnie uruchomiona wersja oprogramowania.
- **[EN]** Integrated new onboard informational splash layouts reflecting Windows mode / Linux mode selection.
- **[PL]** Dodano nowe plansze informacyjne wizualizujące aktualny tryb pracy urządzenia: Windows mode lub Linux mode.

---

## [5.5.0] - 2026-05-09

### Added / Dodano

- **[EN]** Added an emergency hardware bootloader bypass rule mapped to the 9+10+12 key combo during initial USB initialization.
- **[PL]** Dodano obsługę awaryjnego trybu bootloadera poprzez kombinację klawiszy 9+10+12 w trakcie podłączania urządzenia do zasilania USB.
- **[EN]** Added the 'V' querying instruction which echoes back the exact operating firmware build version, critical for debug validation and update verification steps.
- **[PL]** Dodano instrukcję „V”, która zwraca aktualną wersję oprogramowania sprzętowego, co ułatwia debugowanie oraz weryfikację poprawności wgrania nowej paczki.
- **[EN]** Added the 'U' command hook to allow software-triggered bootloader jumps directly from the extension interface, laying down early architecture for Over-The-Air (OTA) flashing.
- **[PL]** Dodano instrukcję „U”, która umożliwia zdalne wywołanie trybu bootloadera z poziomu rozszerzenia – przygotowanie pod nową wersję wtyczki obsługującą bezprzewodowe wgrywanie firmware.

---

## [5.4.0] - 2026-03-05

### Added / Dodano

- **[EN]** Added comprehensive framework maps for extra hardware keys A, B, and C (mapped natively to high-register function keys F21–F23) including custom independent RGB illumination controls.
- **[PL]** Dodano pełną obsługę dodatkowych klawiszy fizycznych A, B, C (zmapowanych jako F21-F23) wraz z dedykowanym przypisywaniem kolorów diod LED.
- **[EN]** Added the 'D' command layout allowing external text strings to dynamically overwrite content blocks on the TFT LCD (e.g., displaying real-time dial states or active modifier actions).
- **[PL]** Dodano komendę „D” pozwalającą na dynamiczne nadpisywanie tekstu na ekranie LCD z poziomu systemu (np. do pokazywania aktualnej funkcji enkoderów).
- **[EN]** Added the 'N' command layer to programmatically override key names rendered over the LCD grids (e.g., swapping labels to "A", "B", "C" for additional key groups).
- **[PL]** Dodano komendę „N” służącą do nadpisywania nazw klawiszy prezentowanych na wyświetlaczu LCD (np. pokazywanie etykiet „A”, „B”, „C” dla nowych przycisków).
- **[EN]** Implemented a safety threshold clamp preventing total user-space backlight blackout accidents by hardcoding a low ceiling block (forcing brightness 0 to clip to 1).
- **[PL]** Wprowadzono sprzętowe zabezpieczenie przed całkowitym wyłączeniem podświetlenia panelu (wartość jasności 0 jest automatycznie podbijana do bezpiecznego poziomu 1).
- **[EN]** Added a post-boot animation status banner identifying the connected operating system on the LCD.
- **[PL]** Wprowadzono wyświetlanie baneru informacyjnego z aktualnie wykrytym systemem operacyjnym (OS) zaraz po zakończeniu animacji startowej.

### Fixed / Poprawiono

- **[EN]** Fixed internally complex packet routing rules pushing inward HID commands from the plugin extension down to their accurate hardware blocks (routing keys to keys, dials to dials, and screen vectors to the display driver).
- **[PL]** Poprawiono routing komend HID przesyłanych z wtyczki do odpowiednich podzespołów (komendy klawiszy trafiają do modułu klawiszy, enkoderów do enkoderów, a ekranu do sterownika LCD).
- **[EN]** Tweaked boot graphics animations to preserve a subtle glowing accent layer inside the center core while stabilizing general frame presentation smoothness.
- **[PL]** Poprawiono animację startową, sprawiając by pozostawiała delikatne tło pośrodku ekranu i cechowała się wyższą płynnością klatek.
- **[EN]** Fixed extra hardware macro targets A, B, C to consistently react to color state overrides and external plugin interrupts.
- **[PL]** Poprawiono obsługę dodatkowych klawiszy A, B, C, aby prawidłowo reagowały na nadpisywanie kolorów (override) oraz komendy przychodzące z rozszerzenia.
- **[EN]** Patched Linux macro emission bindings for keys A, B, C to accurately pass down virtual F21–F23 key codes instead of generic numbers 1–3, removing desktop keyboard layout intercept issues.
- **[PL]** Poprawiono obsługę klawiszy A, B, C pod systemami Linux – wysyłają one teraz kody F21-F23 zamiast standardowych cyfr 1-3, eliminując konflikty skrótów.

### Optimized / Zoptymalizowano

- **[EN]** Optimized math execution behind the backlight luminance scaling engine by rolling a safe mathematical division by 255 rather than bitwise shifts, resulting in true-to-scale brightness steps.
- **[PL]** Zoptymalizowano funkcję nakładania jasności diod – zastąpiono przesunięcie bitowe precyzyjnym dzieleniem przez 255, co gwarantuje bezpieczne skróty i idealną liniowość.

---

## [5.0.0] - 2026-03-02

### Added / Dodano

- **[EN]** Massive hardware expansion over the standard v4.0 SunGo MacroPAD platform: integrated 3 extra auxiliary macro keys (labeled A, B, C) matched with 3 independent RGB status LEDs.
- **[PL]** Potężna rozbudowa architektury firmware v4.0 SunGo MacroPAD – zaimplementowano obsługę 3 dodatkowych klawiszy pomocniczych ABC oraz 3 niezależnych diod LED.
- **[EN]** Built full display subsystem controllers supporting native graphics pipeline acceleration on a new 1.5" TFT LCD module.
- **[PL]** Dodano pełną niskopoziomową obsługę i sterowniki ekranu graficznego TFT LCD o przekątnej 1.5".
- **[EN]** Engineered core signal interruption processing logic for modern rotary hardware encoders.
- **[PL]** Dodano obsługę oraz obsługę przerw dla nowoczesnych enkoderów obrotowych.
- **[EN]** Redesigned case mounting form factor definitions in software to comfortably host all new user inputs and status displays.
- **[PL]** Przeprojektowano strukturę oprogramowania w celu dopasowania parametrów do nowej, fizycznej obudowy urządzenia zawierającej ekran i pokrętła.
