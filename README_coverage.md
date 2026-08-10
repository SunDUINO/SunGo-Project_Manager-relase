[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Test Coverage Viewer – Setup & Usage Guide

SunGo includes a built-in test coverage panel powered by `go test -coverprofile`, with live in-editor highlighting and a per-file summary.  
Access it via the **🧪 Test Coverage** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Write (or generate) your tests

Coverage is calculated from your existing `_test.go` files. A minimal test looks like this:

```go
package main

import "testing"

func TestCreateStars(t *testing.T) {
    stars := createStars()
    if len(stars) == 0 {
        t.Fatal("expected at least one star")
    }
}
```

Don't have any tests yet? Open the source file you want covered and click **"📝 Generate Example Tests"** in the panel — SunGo will pick a couple of functions from that file and append ready-to-fill stubs (with `TODO` markers) into `<filename>_test.go` — a test file for `drawFigures.go` goes into `drawFigures_test.go`, and so on, matching Go's own convention.

> 💡 For a fast way to raise your coverage percentage, check the "Edge cases (raise coverage)" snippet in the Snippet Manager — testing nil / empty / error-path inputs usually covers the branches plain "happy path" tests miss.

---

## ▶️ Step 2 – Run coverage

Click **"▶ Run Coverage"** in the panel. SunGo runs `go test -coverprofile` in the background and reports the result once it finishes.

> ⚠️ If your project's `go.mod` lives in a subfolder (e.g. `src/`) rather than the workspace root, SunGo detects that automatically — no configuration needed.

---

## 🔬 Step 3 – Reading the results

### Total Coverage

A single percentage at the top: total statements covered out of total statements in the project. Color-coded — green (≥80%), yellow (50–79%), red (<50%) — so you can judge project health at a glance.

### Per-File Table

Every file with its own coverage percentage, sorted worst-first so the files needing the most attention are always at the top. Click a row to jump straight to that file.

### In-Editor Highlighting

While coverage data is loaded, every open editor showing a file from the report gets its lines tinted:

| Color | Meaning |
|-------|---------|
| 🟢 Green | Line was executed by at least one test |
| 🔴 Red | Line was never executed |

Toggle this on/off with the **"Highlight in editor"** checkbox in the panel header — handy if the tint gets in the way while you're actively editing.

---

## ⚠️ Common Issues

**Coverage shows 0% for everything** – Almost always means there are no `_test.go` files anywhere in the project yet. `go test -coverprofile` still runs successfully (compiles and reports "no test files"), it just has nothing to measure. Use "📝 Generate Example Tests" to get started.

**"Coverage profile was generated but is empty"** – Same root cause as above, worded differently: your packages compiled fine, but none of them contain any tests.

**Some functions never turn green even with tests passing** – Coverage tracks *executed lines*, not *correct behavior*. A test that calls a function but never exercises its error branch will leave that branch red — that's expected, and a good signal for where to add another test case.

**A file shown in the table isn't the one I expected** – SunGo matches Go's internal module paths back to files on disk by scanning your project tree; in rare cases with duplicate filenames across packages it can pick the wrong match. Click through to confirm, and let us know if you hit this.

---
---

# [PL] SunGo Test Coverage Viewer – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel pokrycia testami oparty na `go test -coverprofile`, z podświetleniem na żywo w edytorze oraz podsumowaniem per plik.  
Dostęp przez wpis **🧪 Test Coverage** w panelu SunGo Tools.

---

## 📋 Krok 1 – Napisz (albo wygeneruj) testy

Pokrycie liczone jest na podstawie Twoich istniejących plików `_test.go`. Minimalny test wygląda tak:

```go
package main

import "testing"

func TestCreateStars(t *testing.T) {
    stars := createStars()
    if len(stars) == 0 {
        t.Fatal("expected at least one star")
    }
}
```

Nie masz jeszcze żadnych testów? Otwórz plik źródłowy, który chcesz pokryć, i kliknij **"📝 Generate Example Tests"** w panelu — SunGo wybierze kilka funkcji z tego pliku i dopisze gotowe do uzupełnienia szkielety (ze znacznikami `TODO`) do pliku `<nazwa_pliku>_test.go` — test dla `drawFigures.go` trafia do `drawFigures_test.go` itd., zgodnie z konwencją samego Go.

> 💡 Szybki sposób na podniesienie procentu pokrycia: sprawdź snippet "Edge cases (raise coverage)" w Snippet Managerze — testowanie wejść nil / pustych / ścieżki błędu zwykle pokrywa gałęzie, które pomijają zwykłe testy "happy path".

---

## ▶️ Krok 2 – Uruchom pokrycie

Kliknij **"▶ Run Coverage"** w panelu. SunGo uruchamia w tle `go test -coverprofile` i pokazuje wynik po zakończeniu.

> ⚠️ Jeśli `go.mod` Twojego projektu leży w podfolderze (np. `src/`), a nie w korzeniu workspace, SunGo wykrywa to automatycznie — nic nie trzeba konfigurować.

---

## 🔬 Krok 3 – Odczytywanie wyników

### Całkowite pokrycie

Pojedynczy procent na górze: łączna liczba pokrytych instrukcji z całkowitej liczby instrukcji w projekcie. Kolorowane — zielony (≥80%), żółty (50–79%), czerwony (<50%) — żeby ocenić stan projektu jednym rzutem oka.

### Tabela per plik

Każdy plik z własnym procentem pokrycia, posortowane od najgorszych, żeby pliki wymagające najwięcej uwagi zawsze były na górze. Kliknięcie wiersza przenosi bezpośrednio do tego pliku.

### Podświetlenie w edytorze

Kiedy dane o pokryciu są załadowane, każdy otwarty edytor pokazujący plik z raportu dostaje podświetlone linie:

| Kolor | Znaczenie |
|-------|-----------|
| 🟢 Zielony | Linia została wykonana przez co najmniej jeden test |
| 🔴 Czerwony | Linia nigdy nie została wykonana |

Włącz/wyłącz to checkboxem **"Highlight in editor"** w nagłówku panelu — przydatne, gdy podświetlenie przeszkadza podczas aktywnej edycji.

---

## ⚠️ Częste problemy

**Pokrycie pokazuje 0% dla wszystkiego** – Niemal zawsze oznacza, że w projekcie nie ma jeszcze żadnych plików `_test.go`. `go test -coverprofile` mimo to kończy się sukcesem (kompiluje i zgłasza "no test files"), po prostu nie ma nic do zmierzenia. Użyj "📝 Generate Example Tests", żeby zacząć.

**"Coverage profile was generated but is empty"** – Ta sama przyczyna co wyżej, tylko inaczej sformułowana: pakiety skompilowały się poprawnie, ale żaden nie zawiera testów.

**Niektóre funkcje nigdy nie stają się zielone mimo przechodzących testów** – Pokrycie śledzi *wykonane linie*, nie *poprawność zachowania*. Test, który woła funkcję, ale nigdy nie wywołuje jej gałęzi błędu, zostawi tę gałąź czerwoną — to oczekiwane i dobra wskazówka, gdzie dodać kolejny przypadek testowy.

**Plik w tabeli nie jest tym, którego się spodziewałem** – SunGo dopasowuje wewnętrzne ścieżki modułów Go z powrotem do plików na dysku przez przeszukanie drzewa projektu; w rzadkich przypadkach z identycznymi nazwami plików w różnych pakietach może trafić na złe dopasowanie. Kliknij, żeby potwierdzić, i daj nam znać jeśli na to trafisz.
