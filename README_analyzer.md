[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Binary Analyzer – Setup & Usage Guide

SunGo includes a built-in binary size analyzer that breaks down your compiled binary by symbol and tracks its size over time.  
Access it via the **📊 Binary Analyzer** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Build your project

The analyzer needs a compiled binary to inspect. Build your project normally (SunGo's build command, or `go build`) before opening the panel — SunGo automatically looks for the most recently built binary in `bin/`.

---

## 🔬 Step 2 – Reading the results

### Top Symbols Table

A breakdown of the largest contributors to your binary's size — which packages and functions take up the most space, sorted largest-first with a visual percentage bar. Useful for spotting an unexpectedly large dependency before it becomes a habit.

### Size History Trend

Every time you run the analyzer, the total binary size is recorded. Over multiple builds, this becomes a chart showing whether your binary is growing, shrinking, or holding steady — handy for catching a dependency that quietly bloated your build.

---

## ⚠️ Common Issues

**"No binary found"** – Build your project at least once first; the analyzer inspects an existing binary, it doesn't compile one itself.

**Binary size looks unexpectedly large** – Check whether debug symbols are included. Building with `-s -w` (stripping symbols) produces a noticeably smaller binary — see the `sungo.build.optimizeBinary` setting mentioned in the Profiler guide.

**History chart is empty or has only one point** – The trend needs multiple builds over time to be useful. Keep building and re-running the analyzer as your project evolves.

---
---

# [PL] SunGo Binary Analyzer – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany analizator rozmiaru binarki, który pokazuje podział na symbole i śledzi rozmiar w czasie.  
Dostęp przez wpis **📊 Binary Analyzer** w panelu SunGo Tools.

---

## 📋 Krok 1 – Zbuduj projekt

Analizator potrzebuje skompilowanej binarki do zbadania. Zbuduj projekt normalnie (komendą budowania SunGo albo `go build`) przed otwarciem panelu — SunGo automatycznie szuka najnowszej zbudowanej binarki w `bin/`.

---

## 🔬 Krok 2 – Odczytywanie wyników

### Tabela największych symboli

Podział największych "konsumentów" rozmiaru binarki — które pakiety i funkcje zajmują najwięcej miejsca, posortowane od największych, z wizualnym paskiem procentowym. Przydatne do wychwycenia nieoczekiwanie dużej zależności, zanim stanie się nawykiem.

### Trend historii rozmiaru

Za każdym razem, gdy uruchamiasz analizator, całkowity rozmiar binarki jest zapisywany. Po kilku buildach zamienia się to w wykres pokazujący, czy binarka rośnie, maleje, czy pozostaje stabilna — przydatne do wychwycenia zależności, która po cichu rozdęła build.

---

## ⚠️ Częste problemy

**"No binary found"** – Zbuduj projekt co najmniej raz najpierw; analizator bada istniejącą binarkę, sam jej nie kompiluje.

**Rozmiar binarki wydaje się nieoczekiwanie duży** – Sprawdź czy zawiera symbole debugowania. Build z `-s -w` (usuwanie symboli) daje zauważalnie mniejszą binarkę — patrz ustawienie `sungo.build.optimizeBinary` wspomniane w instrukcji Profilera.

**Wykres historii jest pusty albo ma tylko jeden punkt** – Trend potrzebuje kilku buildów w czasie, żeby był użyteczny. Buduj dalej i uruchamiaj analizator ponownie w miarę rozwoju projektu.
