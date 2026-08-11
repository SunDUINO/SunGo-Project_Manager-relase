[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Go Generate Runner – Setup & Usage Guide

SunGo includes a built-in `go generate` runner: it scans your project for `//go:generate` directives, lets you run them one at a time or all together, and streams the output live.  
Access it via the **⚡ Go Generate** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Add generate directives to your code

`//go:generate` directives live as comments directly above the code they relate to — nothing SunGo-specific here, this is standard Go tooling:

```go
//go:generate stringer -type=Weekday
type Weekday int
```

Don't have any yet? SunGo simply won't find anything to list — this tool discovers existing directives, it doesn't create them for you.

---

## 🔬 Step 2 – Review what SunGo found

Opening the panel automatically scans your workspace and lists every directive found, along with the file and line it lives on. Click any entry to jump straight to that line in the editor.

---

## ▶️ Step 3 – Run

Run a single directive with its own button, or click **"Run All"** to execute every directive found across the project in sequence. Output streams into the panel in real time as each command runs, so you can catch a failure as it happens rather than waiting for everything to finish.

Use **"Scan"** to re-discover directives after adding or editing one, and **"Clear Output"** to reset the log between runs.

---

## ⚠️ Common Issues

**"command not found" when running a directive** – The tool referenced in the directive (e.g. `stringer`, `mockgen`) needs to be installed and on your PATH separately — `go generate` doesn't install tools for you. Run `go install <tool>@latest` for whatever the directive calls.

**Directive doesn't show up in the list** – Check the exact syntax: it must be `//go:generate` with no space between `//` and `go:generate`, and it must be a standalone comment line (not part of a larger comment block).

**"Run All" stops partway through** – If one directive fails, check its output in the panel before assuming later ones didn't run — depending on the failure, some setups continue to the next directive while others may not.

---
---

# [PL] SunGo Go Generate Runner – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany runner `go generate`: skanuje projekt w poszukiwaniu dyrektyw `//go:generate`, pozwala uruchamiać je pojedynczo albo wszystkie naraz, i pokazuje output na żywo.  
Dostęp przez wpis **⚡ Go Generate** w panelu SunGo Tools.

---

## 📋 Krok 1 – Dodaj dyrektywy generate do kodu

Dyrektywy `//go:generate` żyją jako komentarze bezpośrednio nad kodem, którego dotyczą — nic specyficznego dla SunGo, to standardowe narzędzie Go:

```go
//go:generate stringer -type=Weekday
type Weekday int
```

Nie masz jeszcze żadnych? SunGo po prostu nic nie znajdzie do wylistowania — to narzędzie odkrywa istniejące dyrektywy, nie tworzy ich za Ciebie.

---

## 🔬 Krok 2 – Przejrzyj co SunGo znalazło

Otwarcie panelu automatycznie skanuje workspace i wylistowuje każdą znalezioną dyrektywę wraz z plikiem i linią, w której się znajduje. Kliknij dowolny wpis, żeby przejść bezpośrednio do tej linii w edytorze.

---

## ▶️ Krok 3 – Uruchom

Uruchom pojedynczą dyrektywę własnym przyciskiem, albo kliknij **"Run All"**, żeby wykonać po kolei wszystkie dyrektywy znalezione w projekcie. Output pokazuje się w panelu na żywo w trakcie działania każdej komendy, więc widzisz błąd w momencie jego wystąpienia, zamiast czekać na koniec wszystkiego.

Użyj **"Scan"**, żeby ponownie odkryć dyrektywy po dodaniu lub edycji którejś, i **"Clear Output"**, żeby wyczyścić log między uruchomieniami.

---

## ⚠️ Częste problemy

**"command not found" przy uruchamianiu dyrektywy** – Narzędzie użyte w dyrektywie (np. `stringer`, `mockgen`) musi być zainstalowane i w PATH osobno — `go generate` nie instaluje narzędzi za Ciebie. Uruchom `go install <narzędzie>@latest` dla tego, co woła dyrektywa.

**Dyrektywa nie pojawia się na liście** – Sprawdź dokładną składnię: musi to być `//go:generate` bez spacji między `//` a `go:generate`, i musi to być samodzielna linia komentarza (nie część większego bloku komentarza).

**"Run All" zatrzymuje się w połowie** – Jeśli jedna dyrektywa zawiedzie, sprawdź jej output w panelu zanim założysz, że kolejne się nie uruchomiły — w zależności od rodzaju błędu, niektóre konfiguracje przechodzą do następnej dyrektywy, a inne mogą nie kontynuować.
