# [BUILD] SunGo MacroPAD v2 — 

![MacroPAD v2](../../image/MacroPADv2.png)

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
## Pimoroni PGA2040

<img width="674" height="664" alt="i-pimoroni-pga2040-8mb-zgodny-z-raspberry-pi-pico" src="https://github.com/user-attachments/assets/bd0e7812-0487-43de-95e1-b3b2495c350a" />

### Pinout:

<img width="764" height="496" alt="pga2040_1024x1024" src="https://github.com/user-attachments/assets/42eca50e-2e6d-4408-af02-bb190fc5321f" />

--- 

## Gniazdo USB C 

<img width="437" height="245" alt="2rbsA" src="https://github.com/user-attachments/assets/65e7cd1b-3dba-467c-b122-c32c0802ff01" />
przydatne dla płytek pimoroni pga.

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

## Enkodery:
| Enkoder | Pin | Pin GPIO |
| :--- | :--- | :--- |
| **ENC0** | A | GPIO22 |
|          | B | GPIO24 |
| **ENC1** | A | GPIO23 |
|          | B | GPIO25 |
---

## 🌈 Podłączenie diod WS2812B (RGB)

Diody połączone są szeregowo w układzie typu **"snake" (wąż)**. Oznacza to, że sygnał biegnie zygzakiem pod przełącznikami, co ułatwia prowadzenie przewodów i optymalizuje ścieżkę sygnałową.

### Schemat połączenia diod:
```text
LED0 (SW1) ──► LED1 (SW2) ──► LED2 (SW3)    | ──►LED9 (SW10) ──► LED10 (SW11) ──► LED11 (SW12)
                                 │          |
LED5 (SW4) ◄── LED4 (SW5) ◄── LED3 (SW6)    |
  │                                         |
LED6 (SW7) ──► LED7 (SW8) ──► LED8 (SW9) ──►|  
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

## UWAGA:  SunGo MacroPAD II wymaga najnowszej wersji wtyczki SunGO Project Manager
-- od wersji v2.3.7 SunGO Project Manager - Wprowadziłem rozpoznawanie hardware
-- firmware 5.0 dla SunGO MacroPAD II  nie działa z wcześniejszymi wersjami wtyczki.

<img width="464" height="78" alt="Zrzut ekranu 2026-04-30 213136" src="https://github.com/user-attachments/assets/9cfe653e-23e7-4937-9ab5-f7b107e89c4a" />


Rozpoznawanie hardware we wtyczce jest związane z rozbudową panelu konfiguracji MacroPAD,a  w zwiazku z nowymi funkcjami
Nowy panel Konfiguracji będzie dostępny we wtyczce niebawem. Na chwilę obecną w testowym firmware MacroPAD zachował fukcjonalność 
wersji 1 z dodatkową wizualizacją na LCD 

<img width="718" height="375" alt="Zrzut ekranu 2026-04-28 214445" src="https://github.com/user-attachments/assets/be5b7a7a-3c1b-4587-a19a-3aef516b25b9" />

<img width="800" height="600" alt="101af0ae5a8ebf573c19cf5da10ae5aa" src="https://github.com/user-attachments/assets/60a1e979-1cd1-4137-9082-caa80c459c55" />


---
## UWAGA !!

- Linux wymaga dodania regół udev dla nowego urządzenia:
- Zaktualizuj plik reguł jesli miałeś PAD v1  lub utwórz (/etc/udev/rules.d/99-sungo.rules), dodając nowe ID:
  
```
# Reguła dla SunGo MacroPAD I
SUBSYSTEM=="hidraw", ATTRS{idVendor}=="cafe", ATTRS{idProduct}=="4050", MODE="0666"
# Reguła dla SunGo MacroPAD II  - DODAJ TO: 
SUBSYSTEM=="hidraw", ATTRS{idVendor}=="cafe", ATTRS{idProduct}=="5050", MODE="0666"
```
Po zapisaniu pliku przeładuj reguły komendą:

```
sudo udevadm control --reload-rules && sudo udevadm trigger
```
## Krok po kroku:

https://github.com/SunDUINO/SunGo-Project_Manager-relase/blob/main/README.md#-linux-setup--sungo-pad-udev-rules

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
