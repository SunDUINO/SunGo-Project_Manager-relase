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
