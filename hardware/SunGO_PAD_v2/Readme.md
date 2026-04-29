# [BUILD] SunGo MacroPAD v2 — 

Jak zbudować własny pad 3x3 + 3 z RGB 
dwoma encoderami i LCD 240x240 , jest to rozwiniecie poprzedniej wersji v1. 

Poniżej znajduje się kompletny opis dla osób chcących zbudować własny egzemplarz MacroPADa. Firmware jest już w wersji stabilnej i w pełni współpracuje z dedykowaną wtyczką do **VSCode**, więc możecie śmiało przystępować do prac.

---

## 🛒 Lista zakupów

* **Switche:** 12x switch mechaniczny (np. Cherry MX Blue lub dowolny popularny klon).
* **Podświetlenie:** 12x dioda adresowalna **WS2812B** (można wykorzystać pociętą taśmę LED).
* **Encodery:**  2x Encoder dowolny przykręcany do obudowy.
* **Wyświetlacz:**  1,54" TFT 240x240 SPI z kontrolerem ST7789
* **Mikrokontroler:** Płytka z układem **RP2040** (rekomendowane: Pimoroni PGA2040, Waveshare RP2040 Zero lub inne zgodne).
* **Okablowanie:** Cienkie przewody, opcjonalnie kawałek skrętki komputerowej (świetnie nadaje się jako sztywny drut do łączenia matrycy).
* **Obudowa:** Wydruk 3D. W projekcie wykorzystano model: [SunGo MacroPAD na MakerWorld](https://makerworld.com/pl/models/109775#profileId-1092486).

---

## 🔧 Podłączenie przełączników

Przełączniki pracują w układzie **matrycy 3x3** w trybie **Direct** ze wspólną masą (GND).

### Schemat rozmieszczenia:
| | | | | | |
| :---: | :---: | :---: |:---: |:---: |:---: |
| SW1 | SW2 | SW3 | SW10 | SW11 | SW12 |
| SW4 | SW5 | SW6 |      |      | ENC0 |
| SW7 | SW8 | SW9 |      |      | ENC1 |

### Mapowanie pinów GPIO:
| Przełącznik | Pin GPIO | Przełącznik | Pin GPIO | Przełącznik | Pin GPIO |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SW1** | GPIO2 | **SW2** | GPIO3 | **SW3** | GPIO4 |
| **SW4** | GPIO7 | **SW5** | GPIO6 | **SW6** | GPIO5 |
| **SW7** | GPIO8 | **SW8** | GPIO9 | **SW9** | GPIO10|
| **SW10**| GPIO11| **SW11**| GPIO12| **SW12**| GPIO13|

## Przyciski Encoderów:
| Przełącznik | Pin GPIO |
| :--- | :--- |
| **ENC0** | GPIO14 |
| **ENC1** | GPIO15 |


---

## 🌈 Podłączenie diod WS2812B (RGB)

Diody połączone są szeregowo w układzie typu **"snake" (wąż)**. Oznacza to, że sygnał biegnie zygzakiem pod przełącznikami, co ułatwia prowadzenie przewodów i optymalizuje ścieżkę sygnałową.

### Schemat połączenia diod:
```text
LED0 (SW1) ──► LED1 (SW2) ──► LED2 (SW3)
                                 │
LED5 (SW4) ◄── LED4 (SW5) ◄── LED3 (SW6)
  │
LED6 (SW7) ──► LED7 (SW8) ──► LED8 (SW9)
```

### Pin danych (DIN): Podłączony do GPIO16.
### Zasilanie: Diody można zasilić napięciem 3.3V lub 5V.

### Zarządzanie energią: W firmware jasność została ograniczona do 40%. Dzięki temu diody zachowują świetną widoczność, a pobór prądu jest bezpieczny dla standardów USB 2.0 i nowszych.

## UWAGA: Przy montażu zwróć szczególną uwagę na orientację diod. Strzałki na obudowach WS2812B wskazują kierunek przepływu danych (Data Out).
---
## 🌈 Podłączenie LCD SPI?:

- uzywamy SPIO w RP2040

- GPIO18 -- CLK, 
- GPIO19 -- TX,
- GPIO17 -- CS, 
- GPIO20 -- DC, 
- GPIO21 -- RST

---

## 💾 Oprogramowanie i konfiguracja

Firmware dla Macropada V2  bedzie dostepne niebawem ....

Instalacja Firmware
Przygotuj plik firmware w formacie .uf2.

Podłącz płytkę RP2040 do komputera, trzymając wciśnięty przycisk BOOTSEL.

Urządzenie zostanie wykryte jako dysk wymienny.

Przeciągnij i upuść plik .uf2 na ten dysk. Po poprawnym wgraniu, MacroPAD zrestartuje się i będzie gotowy do pracy.

Keycapy
Jeśli korzystasz z drukarki Bambu Lab z systemem AMS (np. model A1), w załączniku znajdziesz dedykowane projekty keycapów, które pozwolą Ci na estetyczne wykończenie projektu.

Projekt SunGo MacroPAD v2  — 2026
