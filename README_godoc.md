[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Go Doc Viewer – Setup & Usage Guide

SunGo includes a built-in documentation browser powered by `go doc`, with search, navigation history, and automatic import detection from your active file — no need to leave VS Code to look up a standard library or third-party package.  
Access it via the **📖 Go Doc Viewer** entry in the SunGo Tools panel.

---

## 📋 Imports from your current file

As soon as you open the panel (or switch to a different `.go` file while it's open), SunGo lists every package your active file imports — click any one of them for its documentation instantly, no typing required.

---

## 🔍 Looking up any package

Type a package path into the search box — anything from the standard library (`fmt`, `net/http`) to a full module path for a third-party dependency — and press **Enter** or click **"🔍 Doc"**.

> 💡 To search *within* an already-open doc page for a specific function or symbol, click **"🔎 Find"** (or `Ctrl+F` while focused on the panel) rather than re-running a full lookup.

---

## 🖱️ Navigating

Use the **back / forward** buttons to move through your lookup history, just like a browser — handy when you followed a chain of related types and want to retrace your steps.

Each documentation entry also gives you:

| Action | What it does |
|--------|---------------|
| **🌐 Open in Browser** | Opens the same package on pkg.go.dev in your system browser |
| **📋 Copy** | Copies a symbol's name to your clipboard |

---

## ⚠️ Common Issues

**"Package not found"** – The package needs to be resolvable by `go doc` from your project's module context — a typo in the path, or a dependency that isn't actually in your `go.mod`, will both produce this.

**Imports list is empty** – Make sure a `.go` file is the active editor tab; the imports list is tied to whichever Go file currently has focus.

**Documentation looks outdated compared to pkg.go.dev** – `go doc` reads from the exact version of the package currently resolved in your `go.mod`/`go.sum`, which may be older than the latest release shown on pkg.go.dev. Use "Open in Browser" to see the very latest published docs.

---
---

# [PL] SunGo Go Doc Viewer – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowaną przeglądarkę dokumentacji opartą na `go doc`, z wyszukiwarką, historią nawigacji i automatycznym wykrywaniem importów z aktywnego pliku — nie trzeba opuszczać VS Code, żeby sprawdzić bibliotekę standardową albo zależność zewnętrzną.  
Dostęp przez wpis **📖 Go Doc Viewer** w panelu SunGo Tools.

---

## 📋 Importy z aktualnego pliku

Zaraz po otwarciu panelu (albo przełączeniu na inny plik `.go` gdy jest otwarty), SunGo wylistuje każdy pakiet importowany przez Twój aktywny plik — kliknij dowolny z nich, żeby od razu dostać jego dokumentację, bez wpisywania niczego.

---

## 🔍 Wyszukiwanie dowolnego pakietu

Wpisz ścieżkę pakietu w pole wyszukiwania — cokolwiek z biblioteki standardowej (`fmt`, `net/http`) po pełną ścieżkę modułu dla zależności zewnętrznej — i naciśnij **Enter** albo kliknij **"🔍 Doc"**.

> 💡 Żeby szukać *wewnątrz* już otwartej strony dokumentacji konkretnej funkcji lub symbolu, kliknij **"🔎 Find"** (albo `Ctrl+F` z fokusem na panelu) zamiast ponownie uruchamiać pełne wyszukiwanie.

---

## 🖱️ Nawigacja

Użyj przycisków **wstecz / dalej**, żeby poruszać się po historii wyszukiwań, tak jak w przeglądarce — przydatne, kiedy przeszedłeś przez łańcuch powiązanych typów i chcesz się cofnąć.

Każdy wpis dokumentacji daje też:

| Akcja | Co robi |
|-------|---------|
| **🌐 Open in Browser** | Otwiera ten sam pakiet na pkg.go.dev w przeglądarce systemowej |
| **📋 Copy** | Kopiuje nazwę symbolu do schowka |

---

## ⚠️ Częste problemy

**"Package not found"** – Pakiet musi być rozwiązywalny przez `go doc` w kontekście modułu Twojego projektu — literówka w ścieżce albo zależność, której faktycznie nie ma w `go.mod`, obie dadzą ten sam efekt.

**Lista importów jest pusta** – Upewnij się, że aktywną zakładką edytora jest plik `.go`; lista importów jest powiązana z tym, który plik Go ma aktualnie fokus.

**Dokumentacja wygląda na nieaktualną w porównaniu do pkg.go.dev** – `go doc` czyta z dokładnej wersji pakietu aktualnie rozwiązanej w `go.mod`/`go.sum`, która może być starsza niż najnowsze wydanie pokazane na pkg.go.dev. Użyj "Open in Browser", żeby zobaczyć najnowszą opublikowaną dokumentację.
