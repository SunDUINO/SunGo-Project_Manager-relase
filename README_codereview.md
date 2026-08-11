[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Code Review – Setup & Usage Guide

SunGo includes a built-in static analysis panel that runs `go vet`, `staticcheck`, and `golangci-lint` against your project and shows the combined findings in one place.  
Access it via the **🔍 Code Review** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Install the analysis tools (optional but recommended)

`go vet` ships with Go itself, so it always works. `staticcheck` and `golangci-lint` are separate tools SunGo can use if they're installed:

```bash
go install honnef.co/go/tools/cmd/staticcheck@latest
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
```

SunGo detects which tools are available on your PATH and only offers the ones it can actually run — you don't need all three, but the more you have, the more thorough the review.

---

## ▶️ Step 2 – Select tools and run

Pick which of the available tools you want to run for this pass, then start the analysis. SunGo streams each tool's output as it runs, so you can see progress rather than waiting for a single combined result at the end.

---

## 🔬 Step 3 – Reading the results

Findings are grouped by tool and by file, each with the offending line and the tool's own message — click through to jump straight to the flagged code.

> 💡 `go vet` catches genuine correctness bugs (suspicious `Printf` formats, unreachable code, mistaken struct copies). `staticcheck` and `golangci-lint` add style, performance, and best-practice checks on top — treat vet's findings as higher priority.

---

## ⚠️ Common Issues

**A tool is missing from the list** – It's not installed, or not on your PATH. Install it with the commands above and restart VS Code so the extension picks up the updated PATH.

**"staticcheck"/"golangci-lint" behaves differently than expected** – Both respect their own config files (`staticcheck.conf`, `.golangci.yml`) if present in your project root — check there first if a check you expected to fire didn't, or vice versa.

**Review takes a long time on a large project** – `golangci-lint` in particular can be slow on first run while it builds its analysis cache; subsequent runs are typically much faster.

---
---

# [PL] SunGo Code Review – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel analizy statycznej, który uruchamia `go vet`, `staticcheck` i `golangci-lint` na Twoim projekcie i pokazuje połączone wyniki w jednym miejscu.  
Dostęp przez wpis **🔍 Code Review** w panelu SunGo Tools.

---

## 📋 Krok 1 – Zainstaluj narzędzia analizy (opcjonalne, ale zalecane)

`go vet` jest częścią samego Go, więc zawsze działa. `staticcheck` i `golangci-lint` to osobne narzędzia, których SunGo może użyć, jeśli są zainstalowane:

```bash
go install honnef.co/go/tools/cmd/staticcheck@latest
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
```

SunGo wykrywa, które narzędzia są dostępne w Twoim PATH i oferuje tylko te, które faktycznie może uruchomić — nie musisz mieć wszystkich trzech, ale im więcej masz, tym dokładniejszy przegląd.

---

## ▶️ Krok 2 – Wybierz narzędzia i uruchom

Wybierz, które z dostępnych narzędzi chcesz uruchomić w tym przebiegu, a następnie rozpocznij analizę. SunGo pokazuje na żywo output każdego narzędzia w miarę uruchamiania, więc widzisz postęp zamiast czekać na jeden połączony wynik na końcu.

---

## 🔬 Krok 3 – Odczytywanie wyników

Wyniki są grupowane po narzędziu i pliku, każdy z linią, której dotyczy problem, i własnym komunikatem narzędzia — kliknięcie przenosi bezpośrednio do oznaczonego kodu.

> 💡 `go vet` wychwytuje realne błędy poprawności (podejrzane formaty `Printf`, nieosiągalny kod, przypadkowe kopiowanie struktur). `staticcheck` i `golangci-lint` dodają do tego sprawdzenia stylu, wydajności i dobrych praktyk — traktuj wyniki vet jako priorytetowe.

---

## ⚠️ Częste problemy

**Narzędzie brakuje na liście** – Nie jest zainstalowane albo nie jest w PATH. Zainstaluj komendami powyżej i zrestartuj VS Code, żeby rozszerzenie zobaczyło zaktualizowany PATH.

**"staticcheck"/"golangci-lint" zachowuje się inaczej niż oczekiwano** – Oba respektują własne pliki konfiguracyjne (`staticcheck.conf`, `.golangci.yml`), jeśli są obecne w korzeniu projektu — sprawdź tam najpierw, jeśli jakaś reguła, której się spodziewałeś, nie zadziałała (albo odwrotnie).

**Przegląd trwa długo na dużym projekcie** – Zwłaszcza `golangci-lint` może być wolny przy pierwszym uruchomieniu, gdy buduje swój cache analizy; kolejne uruchomienia są zwykle dużo szybsze.
