[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Code Metrics – Setup & Usage Guide

SunGo includes a built-in code metrics panel that scans your project's `.go` files and flags functions and files that are getting hard to maintain — no external linter required, everything runs locally.  
Access it via the **📊 Code Metrics** entry in the SunGo Tools panel.

---

## 📋 What it measures

For every function: lines of code, number of parameters, nesting depth, and whether it has a godoc comment (checked only for exported — capitalized — functions, since unexported ones don't need one). For every file: total lines and function count.

---

## ⚠️ Refactoring Hints

Any function or file that crosses a threshold gets a hint, color-coded by severity:

| Icon | Severity | Meaning |
|------|----------|---------|
| 🔴 | Error | Well over the limit — worth prioritizing |
| 🟡 | Warning | Over the limit |
| 🔵 | Info | Missing godoc on an exported function |

Click any hint to jump straight to that line in the editor. When a function is flagged for length, SunGo also suggests other sizeable functions in the same file that might be worth extracting into.

### Adjusting the thresholds

The default limits (50 lines per function, 300 per file, 5 parameters, nesting depth 3) can be tuned in your VS Code settings:

```json
"sungo.metrics.maxFuncLines": 50,
"sungo.metrics.maxFileLines": 300,
"sungo.metrics.maxParams": 5,
"sungo.metrics.maxNesting": 3
```

---

## 🔬 Reading the tables

**Functions** — every function in your project, sorted largest-first, with a visual bar for LOC alongside parameter count, nesting depth, and godoc status. **Files** — the same idea at file level. Click any row to jump to that code.

---

## ⚠️ Common Issues

**"No functions found in src/"** – SunGo scans your workspace for `.go` files, skipping `vendor/`, `bin/`, `.git/`, and test files (`_test.go`). If your source lives somewhere unusual, it may not be picked up.

**A function I know is long isn't flagged** – Check your threshold settings above; if you've raised `maxFuncLines`, shorter "long" functions won't trigger a hint anymore.

**Godoc hint fires for a function I don't intend to export** – Go treats any capitalized function name as exported/public, regardless of intent. If it's meant to stay internal, lowercase the name; otherwise, add the godoc comment.

---
---

# [PL] SunGo Code Metrics – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel metryk kodu, który skanuje pliki `.go` Twojego projektu i oznacza funkcje oraz pliki, które robią się trudne w utrzymaniu — bez zewnętrznego lintera, wszystko działa lokalnie.  
Dostęp przez wpis **📊 Code Metrics** w panelu SunGo Tools.

---

## 📋 Co jest mierzone

Dla każdej funkcji: liczba linii kodu, liczba parametrów, głębokość zagnieżdżenia oraz czy ma komentarz godoc (sprawdzane tylko dla eksportowanych — zaczynających się wielką literą — funkcji, bo nieeksportowane go nie potrzebują). Dla każdego pliku: łączna liczba linii i liczba funkcji.

---

## ⚠️ Sugestie refaktoryzacji

Każda funkcja lub plik przekraczający próg dostaje sugestię, kolorowaną wg wagi:

| Ikona | Waga | Znaczenie |
|-------|------|-----------|
| 🔴 | Error | Znacznie powyżej limitu — warto potraktować priorytetowo |
| 🟡 | Warning | Powyżej limitu |
| 🔵 | Info | Brak godoc na eksportowanej funkcji |

Kliknięcie sugestii przenosi bezpośrednio do tej linii w edytorze. Kiedy funkcja jest oznaczona za długość, SunGo sugeruje też inne większe funkcje w tym samym pliku, które mogłyby być warte wydzielenia.

### Dostosowanie progów

Domyślne limity (50 linii na funkcję, 300 na plik, 5 parametrów, głębokość zagnieżdżenia 3) można dostroić w ustawieniach VS Code:

```json
"sungo.metrics.maxFuncLines": 50,
"sungo.metrics.maxFileLines": 300,
"sungo.metrics.maxParams": 5,
"sungo.metrics.maxNesting": 3
```

---

## 🔬 Odczytywanie tabel

**Functions** — każda funkcja w projekcie, posortowana od największych, z wizualnym paskiem LOC obok liczby parametrów, głębokości zagnieżdżenia i statusu godoc. **Files** — ta sama idea na poziomie pliku. Kliknięcie wiersza przenosi do tego kodu.

---

## ⚠️ Częste problemy

**"No functions found in src/"** – SunGo skanuje workspace w poszukiwaniu plików `.go`, pomijając `vendor/`, `bin/`, `.git/` i pliki testowe (`_test.go`). Jeśli Twoje źródła leżą w nietypowym miejscu, mogą nie zostać wykryte.

**Funkcja, o której wiem że jest długa, nie jest oznaczona** – Sprawdź ustawienia progów powyżej; jeśli podniosłeś `maxFuncLines`, krótsze "długie" funkcje przestaną wywoływać sugestię.

**Sugestia godoc pojawia się dla funkcji, której nie zamierzam eksportować** – Go traktuje każdą nazwę funkcji zaczynającą się wielką literą jako eksportowaną/publiczną, niezależnie od intencji. Jeśli ma zostać wewnętrzna, zmień nazwę na małą literę; w przeciwnym razie dodaj komentarz godoc.
