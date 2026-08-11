[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Dependencies – Setup & Usage Guide

SunGo includes a built-in dependencies panel that lists every module your project depends on — direct and indirect — pulled straight from Go's own module system.  
Access it via the **📦 Dependencies** entry in the SunGo Tools panel.

---

## 📋 What you're looking at

The panel reads your project's full module list (`go list -m -json all`) and shows every dependency with its version, split into:

| Type | Meaning |
|------|---------|
| **Direct** | Listed explicitly in your `go.mod`'s `require` block — you import these yourself |
| **Indirect** | Pulled in by one of your direct dependencies, not something you reference directly |

> 💡 For a visual, connected view of *how* these dependencies relate to each other (who requires whom) rather than a flat list, see the **Dependency Graph** tool — the two are complementary.

---

## 🖱️ Using the panel

Click any dependency to open its documentation page on pkg.go.dev — the fastest way to check a package's API, changelog, or license without leaving VS Code.

---

## ⚠️ Common Issues

**A dependency I removed still shows up** – Run `go mod tidy` in your terminal to clean up `go.mod`/`go.sum`, then refresh the panel.

**Version looks unexpected (older than what I specified)** – Go's module resolution picks the *minimum* version that satisfies every dependency's own requirements — check `go mod graph` or the Dependency Graph tool to see which other module is pinning it lower than you expected.

**List is very long** – Normal for projects with several sizable dependencies, since indirect dependencies expand quickly. Use it to audit your dependency footprint occasionally, not necessarily every day.

---
---

# [PL] SunGo Dependencies – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel zależności, który wylistuje każdy moduł, od którego zależy Twój projekt — bezpośrednio i pośrednio — pobrany wprost z systemu modułów Go.  
Dostęp przez wpis **📦 Dependencies** w panelu SunGo Tools.

---

## 📋 Co widzisz na ekranie

Panel odczytuje pełną listę modułów projektu (`go list -m -json all`) i pokazuje każdą zależność z wersją, podzieloną na:

| Typ | Znaczenie |
|-----|-----------|
| **Direct** | Wypisane wprost w bloku `require` Twojego `go.mod` — importujesz je sam |
| **Indirect** | Wciągnięte przez jedną z Twoich bezpośrednich zależności, nie odwołujesz się do nich bezpośrednio |

> 💡 Po wizualny, połączony widok tego *jak* te zależności się ze sobą łączą (kto od kogo wymaga), a nie płaską listę, zobacz narzędzie **Dependency Graph** — te dwa się uzupełniają.

---

## 🖱️ Obsługa panelu

Kliknij dowolną zależność, żeby otworzyć jej stronę dokumentacji na pkg.go.dev — najszybszy sposób sprawdzenia API pakietu, historii zmian czy licencji bez opuszczania VS Code.

---

## ⚠️ Częste problemy

**Zależność, którą usunąłem, dalej się pokazuje** – Uruchom `go mod tidy` w terminalu, żeby posprzątać `go.mod`/`go.sum`, a potem odśwież panel.

**Wersja wygląda nieoczekiwanie (starsza niż to, co podałem)** – System modułów Go wybiera *minimalną* wersję spełniającą wymagania wszystkich zależności — sprawdź `go mod graph` albo narzędzie Dependency Graph, żeby zobaczyć który inny moduł przypina ją niżej niż się spodziewałeś.

**Lista jest bardzo długa** – Normalne dla projektów z kilkoma większymi zależnościami, bo zależności pośrednie szybko się rozrastają. Użyj tego do okazjonalnego audytu zależności, niekoniecznie codziennie.
