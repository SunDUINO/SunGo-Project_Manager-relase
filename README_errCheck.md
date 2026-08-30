[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Unchecked Error Scanner – Setup & Usage Guide

SunGo includes a built-in scanner that finds `err` values which are silently dropped — a class of bug the Go compiler doesn't catch on its own.  
Access it via the **🚨 Unchecked Error Scanner** entry in the SunGo Tools panel.

No external tools required — this is a self-contained analyzer, same philosophy as Code Metrics.

---

## 📋 Step 1 – Open the panel

Just click **Unchecked Error Scanner** in SunGo Tools; it scans every `.go` file in your project (excluding `vendor/` and `_test.go` files) — no build step needed.

---

## 🔬 Step 2 – Reading the results

The scanner looks for two distinct patterns:

### 🔴 Unchecked err

Every assignment to a variable literally named `err` is tracked forward through its enclosing function. If it gets **overwritten by a later assignment** before ever being checked, or the function **returns without ever using it**, it's flagged. This is the sneaky case the Go compiler misses: as long as `err` is used *somewhere* in the function, the compiler is satisfied — even if one particular call's result was silently thrown away in between.

### 🟡 Discarded call

A bare statement call — `something()` with no assignment at all — to a function or method **defined in your own project** whose last return value is `error`. The return value (including the error) is completely discarded. Calls into external packages or the standard library are never flagged this way — SunGo only knows the exact signature of code it can see in your project, and won't guess about anything else.

Click any finding to jump straight to the offending line.

---

## ⚠️ Common Issues

**A call to `fmt.Println` / `file.Close()` / a stdlib function isn't flagged even though it returns an error** – This is intentional, not a bug. "Discarded call" detection only covers functions and methods **defined in your own project**, to avoid guessing at external signatures and producing false positives.

**`if err := doSomething(); err != nil { ... }` gets flagged even though it's checked** – This idiom (assignment and check on the same line) is explicitly recognized and should never be flagged. If you see this happening, please check whether the line was reformatted onto multiple lines — only single-line assignments and single-line function signatures are analyzed in this version.

**I intentionally want to ignore an error** – Use the standard Go idiom `_ = err` right after the assignment; the scanner treats this as an explicit, intentional use and won't flag it.

**A function that returns `error` isn't recognized as "local"** – Its signature must be written on a single line ending in `{` (standard `gofmt` style). Multi-line function signatures aren't indexed in this version.

---
---

# [PL] SunGo Skaner Niesprawdzonych Błędów – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany skaner, który znajduje wartości `err` po cichu porzucane — klasę błędu, której kompilator Go sam z siebie nie wyłapie.  
Dostęp przez wpis **🚨 Unchecked Error Scanner** w panelu SunGo Tools.

Nie wymaga żadnych zewnętrznych narzędzi — to samodzielny analizator, ta sama filozofia co Code Metrics.

---

## 📋 Krok 1 – Otwórz panel

Wystarczy kliknąć **Unchecked Error Scanner** w SunGo Tools; skanuje każdy plik `.go` w projekcie (pomijając `vendor/` i pliki `_test.go`) — bez potrzeby budowania.

---

## 🔬 Krok 2 – Odczytywanie wyników

Skaner szuka dwóch odrębnych wzorców:

### 🔴 Unchecked err (niesprawdzony err)

Każde przypisanie do zmiennej dosłownie nazwanej `err` jest śledzone w przód przez obejmującą ją funkcję. Jeśli zostanie **nadpisane kolejnym przypisaniem** zanim zostanie sprawdzone, albo funkcja **zakończy się bez jego użycia** — zostaje to zgłoszone. To ten podstępny przypadek, którego kompilator Go nie wyłapuje: dopóki `err` jest użyty *gdziekolwiek* w funkcji, kompilator jest zadowolony — nawet jeśli wynik jednego konkretnego wywołania został po cichu odrzucony po drodze.

### 🟡 Discarded call (odrzucone wywołanie)

Samodzielne wywołanie-instrukcja — `something()` bez żadnego przypisania — funkcji lub metody **zdefiniowanej w Twoim projekcie**, której ostatnia wartość zwracana to `error`. Wynik (w tym błąd) jest całkowicie odrzucany. Wywołania do pakietów zewnętrznych lub biblioteki standardowej nigdy nie są w ten sposób zgłaszane — SunGo zna dokładną sygnaturę tylko kodu, który widzi w Twoim projekcie, i nie zgaduje niczego więcej.

Kliknięcie dowolnego wyniku przenosi bezpośrednio do właściwej linii.

---

## ⚠️ Częste problemy

**Wywołanie `fmt.Println` / `file.Close()` / funkcji stdlib nie jest zgłaszane, mimo że zwraca błąd** – To celowe, nie błąd. Wykrywanie "Discarded call" obejmuje wyłącznie funkcje i metody **zdefiniowane w Twoim projekcie**, żeby uniknąć zgadywania sygnatur zewnętrznych i fałszywych alarmów.

**`if err := zrobCos(); err != nil { ... }` jest zgłaszane, mimo że jest sprawdzane** – Ten idiom (przypisanie i sprawdzenie w tej samej linii) jest jawnie rozpoznawany i nigdy nie powinien być zgłaszany. Jeśli to widzisz, sprawdź czy linia nie została sformatowana na kilka linii — w tej wersji analizowane są tylko przypisania i sygnatury funkcji zapisane w jednej linii.

**Świadomie chcę zignorować błąd** – Użyj standardowego idiomu Go `_ = err` zaraz po przypisaniu; skaner traktuje to jako jawne, świadome użycie i nie zgłosi go.

**Funkcja zwracająca `error` nie jest rozpoznawana jako "lokalna"** – Jej sygnatura musi być zapisana w jednej linii kończącej się na `{` (standardowy styl `gofmt`). Sygnatury funkcji rozbite na kilka linii nie są indeksowane w tej wersji.
