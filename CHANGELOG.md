# Changelog – SunGo Project Manager

[EN] All notable changes to the "SunGo Project Manager" extension are documented in this file.  
[PL] Wszystkie istotne zmiany w rozszerzeniu "SunGo Project Manager" są dokumentowane w tym pliku.

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