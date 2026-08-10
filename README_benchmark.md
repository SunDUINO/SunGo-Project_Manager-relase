[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Benchmark Runner – Setup & Usage Guide

SunGo includes a built-in benchmark runner powered by `go test -bench`, with persistent run history, run-to-run comparison, and a performance trend chart.  
Access it via the **⚡ Benchmarks** entry in the SunGo Tools panel.


<img width="783" height="1041" alt="Zrzut ekranu 2026-08-10 141642" src="https://github.com/user-attachments/assets/20bb3ea7-5c91-4121-9f46-3c318dd6d9a1" />


---

## 📋 Step 1 – Write (or generate) your benchmarks

Benchmarks live in a `_test.go` file, just like regular tests. A minimal benchmark looks like this:

```go
package main

import "testing"

func BenchmarkCreateStars(b *testing.B) {
    for i := 0; i < b.N; i++ {
        createStars()
    }
}
```

Don't have any benchmarks yet? Open the source file you want to benchmark and click **"📝 Generate Example Benchmarks"** in the panel — SunGo will pick a couple of functions from that file and append ready-to-fill stubs (with `TODO` markers) into `bench_test.go`, so you always land in the same, predictable file no matter which source file you had open.

> 💡 If you're excluding setup work from the measurement (building test data, opening files, etc.), call `b.ResetTimer()` right after the setup is done — see the "Sub-benchmarks" snippet in the Snippet Manager for a full example.

---

## ▶️ Step 2 – Run your benchmarks

Click **"▶ Run Benchmarks"** in the panel. SunGo runs `go test -bench=. -benchmem -run=^$ ./...` in the background and streams the result once it finishes.

> ⚠️ Benchmarks can take a while, especially with many iterations or large data sets. The button stays disabled while a run is in progress — wait for the result before starting another one.

Every successful run is automatically saved to a persistent history file (`.vscode/.sungo_benchmarks.json`) — nothing to configure, it just accumulates over time (capped at the last 50 runs).

---

## 🔬 Step 3 – Reading the results

### Compare Runs

Pick any two past runs from the **Run A** / **Run B** dropdowns and click **Compare**. The comparison table shows, for every benchmark that exists in either run:

| Symbol | Meaning |
|--------|---------|
| ▼ (green) | Faster in Run B — good |
| ▲ (red) | Slower in Run B — investigate |
| + new | Benchmark exists only in Run B |
| – removed | Benchmark existed in Run A but not in Run B |

### Trend

Pick a specific benchmark from the dropdown to see its `ns/op` plotted across every run in your history — useful for spotting a slow performance regression that crept in over several commits, not just the last one.

### Run History

A simple table of every past run: timestamp, how many benchmarks it contained, and the average `ns/op` across all of them — a quick way to see if a run looks unusually slow before diving into the comparison.

---

## ⚠️ Common Issues

**"No benchmarks found"** – Your project has no functions matching `func BenchmarkXxx(b *testing.B)`. Write one manually or use "📝 Generate Example Benchmarks".

**"Go compiler not found in PATH"** – Same requirement as the rest of SunGo's Go tooling: `go` must be reachable from your terminal's PATH. Restart VS Code after installing/updating Go.

**Benchmark names collide across files** – Go benchmark names must be unique within a package. If "Generate Example Benchmarks" reports a function as already covered but you don't see it in `bench_test.go`, check whether another `_test.go` file in the same package already defines it.

**A benchmark that used to run now times out** – Very expensive benchmarks (or ones with an accidental infinite loop) can exceed the runner's timeout. Reduce the benchmark's workload or check the function for a logic error.

---
---

# [PL] SunGo Benchmark Runner – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany moduł do uruchamiania benchmarków oparty na `go test -bench`, z trwałą historią przebiegów, porównaniem przebiegów oraz wykresem trendu wydajności.  
Dostęp przez wpis **⚡ Benchmarks** w panelu SunGo Tools.

---

## 📋 Krok 1 – Napisz (albo wygeneruj) benchmarki

Benchmarki żyją w pliku `_test.go`, tak jak zwykłe testy. Minimalny benchmark wygląda tak:

```go
package main

import "testing"

func BenchmarkCreateStars(b *testing.B) {
    for i := 0; i < b.N; i++ {
        createStars()
    }
}
```

Nie masz jeszcze żadnych benchmarków? Otwórz plik źródłowy, który chcesz zbenchmarkować, i kliknij **"📝 Generate Example Benchmarks"** w panelu — SunGo wybierze kilka funkcji z tego pliku i dopisze gotowe do uzupełnienia szkielety (ze znacznikami `TODO`) do pliku `bench_test.go` — zawsze trafiasz do tego samego, przewidywalnego pliku, niezależnie który plik źródłowy miałeś otwarty.

> 💡 Jeśli chcesz wykluczyć przygotowanie danych z pomiaru (budowanie danych testowych, otwieranie plików itd.), wywołaj `b.ResetTimer()` zaraz po zakończeniu przygotowania — pełny przykład znajdziesz w snippecie "Sub-benchmarks" w Snippet Managerze.

---

## ▶️ Krok 2 – Uruchom benchmarki

Kliknij **"▶ Run Benchmarks"** w panelu. SunGo uruchamia w tle `go test -bench=. -benchmem -run=^$ ./...` i pokazuje wynik po zakończeniu.

> ⚠️ Benchmarki mogą trwać dłuższą chwilę, zwłaszcza przy dużej liczbie iteracji lub dużych zbiorach danych. Przycisk pozostaje zablokowany podczas trwania przebiegu — poczekaj na wynik przed uruchomieniem kolejnego.

Każdy udany przebieg jest automatycznie zapisywany do trwałego pliku historii (`.vscode/.sungo_benchmarks.json`) — nic nie trzeba konfigurować, historia po prostu narasta w czasie (limit 50 ostatnich przebiegów).

---

## 🔬 Krok 3 – Odczytywanie wyników

### Porównaj przebiegi

Wybierz dwa dowolne wcześniejsze przebiegi z list **Run A** / **Run B** i kliknij **Compare**. Tabela porównania pokazuje, dla każdego benchmarku obecnego w którymkolwiek z przebiegów:

| Symbol | Znaczenie |
|--------|-----------|
| ▼ (zielony) | Szybciej w Run B — dobrze |
| ▲ (czerwony) | Wolniej w Run B — warto sprawdzić |
| + new | Benchmark istnieje tylko w Run B |
| – removed | Benchmark istniał w Run A, ale nie w Run B |

### Trend

Wybierz konkretny benchmark z listy, żeby zobaczyć jego `ns/op` na wykresie dla całej historii — przydatne do wychwycenia powolnej regresji wydajności, która narastała przez kilka commitów, a nie tylko ostatniego.

### Historia przebiegów

Prosta tabela wszystkich wcześniejszych przebiegów: czas, liczba zawartych benchmarków oraz średni `ns/op` ze wszystkich — szybki sposób, żeby ocenić, czy przebieg wygląda nietypowo wolno, zanim zagłębisz się w porównanie.

---

## ⚠️ Częste problemy

**"No benchmarks found"** – Twój projekt nie ma funkcji pasujących do `func BenchmarkXxx(b *testing.B)`. Napisz jedną ręcznie albo użyj "📝 Generate Example Benchmarks".

**"Go compiler not found in PATH"** – Ten sam wymóg co reszta narzędzi Go w SunGo: `go` musi być dostępne z PATH terminala. Zrestartuj VS Code po instalacji/aktualizacji Go.

**Nazwy benchmarków kolidują między plikami** – Nazwy benchmarków w Go muszą być unikalne w obrębie pakietu. Jeśli "Generate Example Benchmarks" zgłasza funkcję jako już pokrytą, ale nie widzisz jej w `bench_test.go`, sprawdź czy inny plik `_test.go` w tym samym pakiecie już jej nie definiuje.

**Benchmark, który wcześniej działał, teraz przekracza limit czasu** – Bardzo kosztowne benchmarki (albo z przypadkową nieskończoną pętlą) mogą przekroczyć limit czasu uruchamiania. Zmniejsz obciążenie benchmarku albo sprawdź funkcję pod kątem błędu logicznego.
