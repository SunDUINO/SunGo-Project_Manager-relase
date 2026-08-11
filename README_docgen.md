[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Documentation Generator – Setup & Usage Guide

SunGo includes a built-in documentation generator that builds a `README.md` (and optionally separate `ARCHITECTURE`, `API`, and `CONTRIBUTING` files) directly from your project's actual structure — `go list -json`, `go.mod`, and your Header Generator settings. Fully local, no AI, no external services involved.  
Access it via the **📄 Doc Generator** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Let SunGo scan your project

The panel scans automatically as soon as it opens — module name, Go version, every package with its own godoc comment, and (if enabled) a rendered directory tree. Click **"Rescan"** any time after editing your code to refresh this data before generating.

---

## ⚙️ Step 2 – Choose language and content

Pick **Polish**, **English**, or generate both at once. Then choose:

**Separate files** (each becomes its own document instead of an inline section in the README):
- `ARCHITECTURE.<LANG>.md`
- `API.<LANG>.md`
- `CONTRIBUTING.<LANG>.md`

**Content options:**
- Badges (Go version, license)
- System requirements
- Build & run instructions
- Directory tree
- Package table

> 💡 Project name and short description default to your project's own name and any module-level godoc comment — edit them directly in the panel before generating if you want something different.

---

## ▶️ Step 3 – Generate

Click generate. SunGo writes the files directly into your project (README.md at the root, the optional separate files into a `Docs/` folder) and shows you which files were created.

---

## ⚠️ Common Issues

**Package table is empty** – Make sure your project actually has a `go.mod` and compiles; the package list comes from `go list -json`, which needs a working module to run against.

**Generated README overwrites my existing one** – Review the output before committing if you already have a hand-written `README.md` with content you want to keep; the generator replaces the file rather than merging with it.

**Directory tree looks cluttered** – The tree renders your whole project structure; if it includes folders you'd rather exclude (build artifacts, vendored code), those typically shouldn't be committed to your repo in the first place — consider whether they belong in `.gitignore`.

**Architecture/API content ends up inline in the README instead of a separate file** – That's expected when the corresponding "separate file" checkbox isn't checked — the content still gets included, just inline rather than split out.

---
---

# [PL] SunGo Documentation Generator – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany generator dokumentacji, który buduje `README.md` (oraz opcjonalnie osobne pliki `ARCHITECTURE`, `API` i `CONTRIBUTING`) bezpośrednio z rzeczywistej struktury projektu — `go list -json`, `go.mod` oraz ustawień Header Generatora. W pełni lokalnie, bez AI, bez zewnętrznych usług.  
Dostęp przez wpis **📄 Doc Generator** w panelu SunGo Tools.

---

## 📋 Krok 1 – Pozwól SunGo zeskanować projekt

Panel skanuje automatycznie zaraz po otwarciu — nazwa modułu, wersja Go, każdy pakiet z własnym komentarzem godoc oraz (jeśli włączone) wyrenderowane drzewo katalogów. Kliknij **"Rescan"** w dowolnym momencie po edycji kodu, żeby odświeżyć te dane przed generowaniem.

---

## ⚙️ Krok 2 – Wybierz język i zawartość

Wybierz **polski**, **angielski**, albo wygeneruj oba naraz. Następnie wybierz:

**Osobne pliki** (każdy staje się własnym dokumentem zamiast sekcji wewnątrz README):
- `ARCHITECTURE.<LANG>.md`
- `API.<LANG>.md`
- `CONTRIBUTING.<LANG>.md`

**Opcje zawartości:**
- Odznaki (wersja Go, licencja)
- Wymagania systemowe
- Instrukcje budowania i uruchamiania
- Drzewo katalogów
- Tabela pakietów

> 💡 Nazwa projektu i krótki opis domyślnie pochodzą z nazwy projektu i komentarza godoc na poziomie modułu — edytuj je bezpośrednio w panelu przed generowaniem, jeśli chcesz czegoś innego.

---

## ▶️ Krok 3 – Wygeneruj

Kliknij generuj. SunGo zapisuje pliki bezpośrednio w projekcie (README.md w korzeniu, opcjonalne osobne pliki do folderu `Docs/`) i pokazuje, które pliki zostały utworzone.

---

## ⚠️ Częste problemy

**Tabela pakietów jest pusta** – Upewnij się, że projekt faktycznie ma `go.mod` i się kompiluje; lista pakietów pochodzi z `go list -json`, który potrzebuje działającego modułu, żeby się uruchomić.

**Wygenerowany README nadpisuje mój istniejący** – Przejrzyj wynik przed commitem, jeśli masz już ręcznie napisany `README.md` z treścią, którą chcesz zachować; generator zastępuje plik zamiast go scalać.

**Drzewo katalogów wygląda na zaśmiecone** – Drzewo renderuje całą strukturę projektu; jeśli zawiera foldery, które wolałbyś wykluczyć (artefakty budowania, kod z vendor), zazwyczaj i tak nie powinny trafiać do repo — rozważ dodanie ich do `.gitignore`.

**Treść Architecture/API ląduje w README zamiast w osobnym pliku** – Tak się dzieje, gdy odpowiedni checkbox "osobny plik" nie jest zaznaczony — treść i tak jest dołączana, tylko wewnątrz README zamiast w osobnym pliku.
