## v5.6.0 — 2026-05-09

* Dodano wsparcie dla awaryjnego trybu bootloadera — wciśnięcie klawiszy 9+10+12 podczas podłączania do USB spowoduje wejście w tryb bootloadera (widoczny   jako „RPI-RP2" w systemie) zamiast normalnego uruchomienia firmware.
* Dodano instrukcję U — umożliwia wejście w tryb bootloadera z poziomu wtyczki VS Code, przygotowanie pod OTA (zdalną aktualizację firmware).
* Wersja firmware przeniesiona do usb_descriptors.h (makra FW_VER_MAJOR, FW_VER_MINOR, FW_VER_PATCH)
  — jedno miejsce definicji dla deskryptora USB (bcdDevice) i stringa wyświetlanego na LCD.
* Poprawione logo startowe MacroPADA — na LCD wyświetla się również aktualna wersja firmware.
* Nowe plansze informacyjne ustawień  Windows mode/Linux mode 

## v.5.5.0   2026-05-09
 * dodano wsparcie dla awaryjnego trybu bootloadera - wcisniecie klawiszy 9+10+12
   podczas podłączania do USB spowoduje wejście w tryb bootloadera (widoczny jako "RPI-RP2" w systemie) 
 * dodano instrukcję 'V' , która zwraca aktualną wersję firmware (przydatne do debugowania i weryfikacji aktualizacji)
 * dodano instrukcję 'U' , która umożliwia wejście w rtyb bootloadera z poziomu wtyczki - przygotowanie pod nową wersję 
   wtyczki - (umożliwia zdalną aktualizację firmware)
 
## v.5.4.0   2026-03-05 
 * dodano obsługę dodatkowych klawiszy A,B,C (F21-F23) i przypisanie im kolorów
 * poprawiono routing komend HID z wtyczki do odpowiednich modułów (klawisze → klawisze, enkodery → enkodery, display → display)
 * dodano komendę 'D' do nadpisywania tekstu na LCD (np. do pokazywania aktualnej funkcji enkoderów)
 * dodano komendę 'N' do nadpisywania nazw klawiszy na LCD (np. pokazywanie "A", "B", "C" dla dodatkowych klawiszy)
 * dodano zabezpieczenie przed totalnym wyłączeniem podświetlenia (jasność 0 → 1)
 * zoptymalizowano funkcję nakładania jasności, żeby była bezpieczna i dawała idealną precyzję (dzielenie przez 255 zamiast przesunięcia bitowego)
 * dodano pokaz baneru z aktualnym OS na LCD po animacji startowej
 * poprawiono animację startową, żeby zostawiała delikatne tło w środku i była bardziej płynna
 * poprawiono obsługę klawiszy A, B, C, żeby reagowały na override koloru i komendy z wtyczki
 * poprawiono obsługę klawiszy A, B, C, w systemie Linux, żeby wysyłały F21-F23 zamiast 1-3, żeby uniknąć konfliktów z innymi funkcjami systemowymi
