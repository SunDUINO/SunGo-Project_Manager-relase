[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Fuzz Testing – Setup & Usage Guide

SunGo includes a built-in panel for Go's native fuzzer (`go test -fuzz`): pick a fuzz function, choose how long to run it, and get a single, time-bounded run — no background processes, no automation running after you close the panel.  
Access it via the **🐛 Fuzz Testing** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Write (or generate) a fuzz test

A fuzz test looks like this — a seed corpus (`f.Add(...)`) plus a function that gets called repeatedly with generated inputs:

```go
package main

import "testing"

func FuzzParseCommand(f *testing.F) {
    f.Add("move 5 10")
    f.Add("")

    f.Fuzz(func(t *testing.T, input string) {
        _, err := ParseCommand(input)
        if err != nil {
            return // an error is a fine, expected outcome for bad input
        }
        // TODO: assert whatever should always hold true for successfully parsed input
    })
}
```

Don't have one yet? Open the source file you want to fuzz and click **"📝 Generate Example Fuzz Test"** — SunGo picks a function from that file and appends a skeleton to `<filename>_test.go`, the same convention as the Coverage Viewer's generated tests.

> ⚠️ The generated skeleton can't know your function's actual parameter types (that needs full type analysis, not just a name scan), so it leaves the seed value and parameter list marked `TODO` — fill those in to match the function you're targeting before running it.

---

## ▶️ Step 2 – Pick a function and run

The panel lists every `FuzzXxx` function found in your project. Pick one, set a duration in seconds (default 30, capped between 5 and 600), and click **"▶ Run"**.

> 💡 This is a deliberately manual, one-shot action — nothing keeps running once the duration is up or the panel is closed. If you want a longer, unattended fuzzing session, run `go test -fuzz` directly from a terminal instead; that's the right tool for that job.

---

## 🔬 Step 3 – Reading the result

**No crash found** — you get an execution count and executions/sec, so you know the fuzzer actually did meaningful work in the time given, not just a "nothing happened" result.

**Crash found** — you get three things:
| What | Why it matters |
|------|------------------|
| **Failing input path** | Click to open the exact file Go saved — a permanent, minimal reproduction of the crash |
| **Re-run command** | A ready-to-copy `go test -run=...` targeting just that one failing case, for fast iteration in a terminal |
| **Failure detail** | The assertion or panic message extracted from the test output |

> 💡 The failing input file lives under `testdata/fuzz/FuzzXxx/` and is a real file Go itself manages — it becomes part of your test corpus automatically. Committing it to version control means that exact case gets checked on every future `go test` run, even without fuzzing.

---

## ⚠️ Common Issues

**"No fuzz functions found"** – Write one manually or use "Generate Example Fuzz Test" to get started.

**A fuzz run "succeeds" but I expected it to find a bug** – Fuzzing is probabilistic; a short duration may simply not have explored the input space that triggers your bug. Try a longer duration, or add a more targeted seed value with `f.Add(...)` closer to what you suspect breaks it.

**Go compiler not found in PATH** – Same requirement as the rest of SunGo's Go tooling: `go` must be reachable from your terminal's PATH. Restart VS Code after installing/updating Go.

**Run seems to hang near the end** – Go needs a little time after `fuzztime` elapses to shut down cleanly and write out results; the panel's timeout accounts for this automatically, so let it finish rather than assuming it's stuck.

---
---

# [PL] SunGo Fuzz Testing – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel dla natywnego fuzzera Go (`go test -fuzz`): wybierz funkcję fuzz, ustaw czas trwania i dostań jeden, ograniczony czasowo przebieg — żadnych procesów w tle, żadnej automatyki działającej po zamknięciu panelu.  
Dostęp przez wpis **🐛 Fuzz Testing** w panelu SunGo Tools.

---

## 📋 Krok 1 – Napisz (albo wygeneruj) test fuzz

Test fuzz wygląda tak — korpus danych startowych (`f.Add(...)`) plus funkcja wołana wielokrotnie z generowanymi wejściami:

```go
package main

import "testing"

func FuzzParseCommand(f *testing.F) {
    f.Add("move 5 10")
    f.Add("")

    f.Fuzz(func(t *testing.T, input string) {
        _, err := ParseCommand(input)
        if err != nil {
            return // błąd to w porządku, oczekiwany wynik dla złego wejścia
        }
        // TODO: sprawdź asercją to, co zawsze powinno być prawdą dla poprawnie sparsowanego wejścia
    })
}
```

Nie masz jeszcze żadnego? Otwórz plik źródłowy, który chcesz fuzzować, i kliknij **"📝 Generate Example Fuzz Test"** — SunGo wybiera funkcję z tego pliku i dopisuje szkielet do `<nazwa_pliku>_test.go`, ta sama konwencja co wygenerowane testy w Coverage Viewer.

> ⚠️ Wygenerowany szkielet nie może znać rzeczywistych typów parametrów Twojej funkcji (to wymagałoby pełnej analizy typów, nie tylko skanu nazw), więc zostawia wartość seed i listę parametrów oznaczone `TODO` — uzupełnij je zgodnie z funkcją, którą testujesz, zanim uruchomisz.

---

## ▶️ Krok 2 – Wybierz funkcję i uruchom

Panel wylistowuje każdą znalezioną w projekcie funkcję `FuzzXxx`. Wybierz jedną, ustaw czas trwania w sekundach (domyślnie 30, ograniczone od 5 do 600), i kliknij **"▶ Run"**.

> 💡 To celowo ręczna, jednorazowa akcja — nic nie działa dalej po upłynięciu czasu albo zamknięciu panelu. Jeśli chcesz dłuższą, bezobsługową sesję fuzzingu, uruchom `go test -fuzz` bezpośrednio z terminala — to właściwe narzędzie do tego zadania.

---

## 🔬 Krok 3 – Odczytywanie wyniku

**Nie znaleziono awarii** — dostajesz liczbę wykonań i wykonania/sek, więc wiesz, że fuzzer faktycznie wykonał sensowną pracę w danym czasie, a nie po prostu "nic się nie stało".

**Znaleziono awarię** — dostajesz trzy rzeczy:
| Co | Dlaczego to ważne |
|----|---------------------|
| **Ścieżka do awaryjnego wejścia** | Kliknięcie otwiera dokładny plik zapisany przez Go — trwałą, minimalną reprodukcję awarii |
| **Komenda do ponownego uruchomienia** | Gotowa do skopiowania `go test -run=...` celująca tylko w ten jeden przypadek, do szybkiej iteracji w terminalu |
| **Szczegół błędu** | Wiadomość asercji albo panika wyciągnięta z outputu testu |

> 💡 Plik z awaryjnym wejściem leży w `testdata/fuzz/FuzzXxx/` i jest prawdziwym plikiem zarządzanym przez sam Go — automatycznie staje się częścią korpusu testowego. Scommitowanie go do kontroli wersji oznacza, że dokładnie ten przypadek jest sprawdzany przy każdym kolejnym `go test`, nawet bez fuzzingu.

---

## ⚠️ Częste problemy

**"No fuzz functions found"** – Napisz jedną ręcznie albo użyj "Generate Example Fuzz Test", żeby zacząć.

**Przebieg "kończy się sukcesem", a spodziewałem się znalezienia buga** – Fuzzing jest probabilistyczny; krótki czas trwania mógł po prostu nie zbadać przestrzeni wejść, która wywołuje Twój bug. Spróbuj dłuższego czasu, albo dodaj bardziej celowaną wartość seed przez `f.Add(...)`, bliższą temu, co Twoim zdaniem to psuje.

**Go compiler not found in PATH** – Ten sam wymóg co reszta narzędzi Go w SunGo: `go` musi być dostępne z PATH terminala. Zrestartuj VS Code po instalacji/aktualizacji Go.

**Przebieg wygląda jakby zawiesił się pod koniec** – Go potrzebuje chwili po upłynięciu `fuzztime`, żeby czysto się zamknąć i zapisać wyniki; timeout panelu uwzględnia to automatycznie, więc daj mu dokończyć zamiast zakładać, że coś utknęło.
