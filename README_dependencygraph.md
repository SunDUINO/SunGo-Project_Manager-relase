[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Dependency Graph – Setup & Usage Guide

SunGo includes a built-in, interactive dependency graph powered by `go mod graph` and `go list -json`, showing your external module dependencies and internal package structure side by side.  
Access it via the **🕸️ Dependency Graph** entry in the SunGo Tools panel.

---

## 📋 What you're looking at

The panel opens two graphs side by side — no setup required, both load automatically.

### 🌐 External Dependencies (left)

Built from `go mod graph`. Your project's main module starts in **gold**, its direct dependencies in **green**, and anything deeper in **grey**. To keep the initial view readable, only the first two levels are shown — the rest of the graph exists in memory and reveals itself as you explore.

### 📦 Internal Packages (right)

Built from `go list -json ./...`, showing how your **own** packages import each other (external packages are filtered out — this graph is only about your code). 

> 💡 If your entire project is a single flat package (all `.go` files in one folder, no subpackages — common for smaller tools and games), a package-level graph would just be one lonely node. SunGo detects this and automatically switches to a **file-level view** instead, showing which of your `.go` files reference functions/types declared in another file of the same package. The hint text above the graph tells you which mode you're in.

---

## 🖱️ Interacting with the graphs

| Action | External graph | Internal graph |
|--------|-----------------|-----------------|
| Click a node | Expands its own dependencies | Reveals its folder in the Explorer (or opens the file, in file-level mode) |
| Double-click a node | Opens the package on pkg.go.dev | — |
| Drag a node | Repositions it (physics simulation continues around it) | Same |
| Scroll wheel | Zoom in / out | Same |
| Click + drag background | Pan the graph | Same |

The **"↻ Refresh"** button on each side re-runs the underlying `go` command — useful after adding a new dependency or package.

---

## 🔬 Reading the internal file-level view

When SunGo falls back to showing files instead of packages, connections are found through a lightweight heuristic: for every top-level function, type, variable, or constant declared in file A, SunGo checks whether file B's source text mentions that name. If it does, an arrow is drawn from B to A.

> ⚠️ This is a textual heuristic, not a full compiler-grade analysis — it can occasionally produce a false connection (e.g. a name that also appears in a comment) or miss one hidden behind unusual formatting. Treat it as a helpful map of your code, not a guaranteed-exact call graph.

---

## ⚠️ Common Issues

**"No go.mod found"** – SunGo looks for `go.mod` at your workspace root, then in a `src/` subfolder. If your module lives somewhere else entirely, the graph can't be built.

**External graph looks empty or tiny** – Your project may genuinely have few or no external dependencies yet (a pure standard-library project). That's not a bug — check the Internal panel instead.

**Clicking an external node does nothing** – If a package has no further dependencies of its own (a "leaf" in the graph), there's nothing left to expand — that's expected, not an error.

**Internal graph unexpectedly shows a file-level view** – This happens automatically whenever `go list` reports exactly one package for the whole project. If you expected a multi-package view, check that your subfolders actually contain their own `package` declarations (a folder without a distinct `package` name doesn't count as a separate package to Go).

---
---

# [PL] SunGo Graf Zależności – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany, interaktywny graf zależności oparty na `go mod graph` i `go list -json`, pokazujący zewnętrzne zależności modułów oraz wewnętrzną strukturę pakietów obok siebie.  
Dostęp przez wpis **🕸️ Dependency Graph** w panelu SunGo Tools.

---

## 📋 Co widzisz na ekranie

Panel otwiera dwa grafy obok siebie — bez żadnej konfiguracji, oba ładują się automatycznie.

### 🌐 Zależności zewnętrzne (lewa strona)

Zbudowany z `go mod graph`. Główny moduł Twojego projektu startuje na **złoto**, jego bezpośrednie zależności na **zielono**, a wszystko głębiej na **szaro**. Żeby wstępny widok pozostał czytelny, pokazywane są tylko pierwsze dwa poziomy — reszta grafu istnieje w pamięci i odsłania się w miarę eksploracji.

### 📦 Pakiety wewnętrzne (prawa strona)

Zbudowany z `go list -json ./...`, pokazujący jak **Twoje własne** pakiety importują się nawzajem (zależności zewnętrzne są odfiltrowane — ten graf dotyczy tylko Twojego kodu).

> 💡 Jeśli cały projekt to jeden płaski pakiet (wszystkie pliki `.go` w jednym folderze, bez podpakietów — częste w mniejszych narzędziach i grach), graf na poziomie pakietów pokazałby tylko jeden samotny węzeł. SunGo wykrywa to automatycznie i przełącza się zamiast tego na **widok na poziomie plików**, pokazując które z Twoich plików `.go` odwołują się do funkcji/typów zadeklarowanych w innym pliku tego samego pakietu. Tekst podpowiedzi nad grafem mówi, w którym trybie jesteś.

---

## 🖱️ Obsługa grafów

| Akcja | Graf zewnętrzny | Graf wewnętrzny |
|-------|-------------------|-------------------|
| Kliknięcie węzła | Rozwija jego własne zależności | Odsłania folder w Eksploratorze (albo otwiera plik, w trybie plikowym) |
| Podwójne kliknięcie węzła | Otwiera pakiet na pkg.go.dev | — |
| Przeciągnięcie węzła | Przesuwa go (symulacja fizyki trwa dalej wokół niego) | Tak samo |
| Kółko myszy | Zoom in / out | Tak samo |
| Klik + przeciągnięcie tła | Przesuwanie grafu | Tak samo |

Przycisk **"↻ Refresh"** po każdej stronie ponownie uruchamia bazową komendę `go` — przydatne po dodaniu nowej zależności lub pakietu.

---

## 🔬 Odczytywanie widoku plikowego (wewnętrzny)

Kiedy SunGo przełącza się na pokazywanie plików zamiast pakietów, połączenia wykrywane są lekką heurystyką: dla każdej funkcji, typu, zmiennej lub stałej zadeklarowanej top-level w pliku A, SunGo sprawdza, czy tekst źródłowy pliku B wspomina tę nazwę. Jeśli tak — rysowana jest strzałka od B do A.

> ⚠️ To heurystyka tekstowa, nie pełna analiza na poziomie kompilatora — może czasem pokazać fałszywe połączenie (np. nazwa pojawiająca się też w komentarzu) albo pominąć jakieś ukryte za nietypowym formatowaniem. Traktuj to jako pomocną mapę kodu, a nie gwarantowanie dokładny graf wywołań.

---

## ⚠️ Częste problemy

**"No go.mod found"** – SunGo szuka `go.mod` w korzeniu workspace, a potem w podfolderze `src/`. Jeśli Twój moduł leży zupełnie gdzie indziej, graf nie może zostać zbudowany.

**Graf zewnętrzny wygląda pusto lub jest bardzo mały** – Twój projekt może faktycznie mieć niewiele lub żadnych zależności zewnętrznych (czysty projekt na standardowej bibliotece). To nie błąd — sprawdź zamiast tego panel wewnętrzny.

**Kliknięcie węzła zewnętrznego nic nie robi** – Jeśli pakiet nie ma już żadnych własnych zależności (jest "liściem" w grafie), nie ma czego rozwijać — to oczekiwane, nie błąd.

**Graf wewnętrzny nieoczekiwanie pokazuje widok plikowy** – Dzieje się to automatycznie, gdy `go list` zgłasza dokładnie jeden pakiet dla całego projektu. Jeśli spodziewałeś się widoku wielopakietowego, sprawdź czy Twoje podfoldery faktycznie mają własne deklaracje `package` (folder bez odrębnej nazwy `package` nie liczy się dla Go jako osobny pakiet).
