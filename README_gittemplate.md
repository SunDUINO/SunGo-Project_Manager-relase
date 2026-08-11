[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Project from GitHub Template – Setup & Usage Guide

SunGo includes a built-in project scaffolder: pick a curated template (or point it at any Git repository of your own) and get a fresh, ready-to-code SunGo project — module renamed, imports remapped, no leftover Git history.  
Access it via the **📦 Project from GitHub Template** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Pick a source

**Curated templates** — SunGo fetches a live list from the [`SunDUINO/sungo-templates`](https://github.com/SunDUINO/sungo-templates) repository and shows each one as a card with its name, description, and tags. Pick one and you're ready to go.

**Your own repository** — Have a project of your own you use as a starting point instead? Paste any Git URL into the custom field. Works the same way as a curated template — same renaming, same cleanup.

---

## ✏️ Step 2 – Name your project

Enter a project name — letters, numbers, dashes, and underscores only. This becomes both the folder name and your new module's name in `go.mod`.

> ⚠️ If a folder with that name already exists in your workspace root, SunGo won't overwrite it — pick a different name.

---

## ▶️ Step 3 – Create

SunGo shallow-clones the source repository into a temporary folder (so it's fast, and no full history gets dragged along), then:

1. Copies the template's files into a proper SunGo project structure.
2. Renames every `${projectName}` placeholder and remaps Go import paths from the template's original module name to yours — including correctly adjusting paths whether the template used a `src/` subfolder or a flat layout.
3. Runs `go mod init` (or writes a fresh `go.mod` directly) so the new project's module matches its name from the start.
4. Writes a working `launch.json` so you can start debugging immediately.
5. Deletes the temporary clone and opens your new project.

The log at the bottom of the panel streams every step live, so you can see exactly what happened if something doesn't look right afterward.

---

## ⚠️ Common Issues

**"A project with this name already exists"** – Pick a different project name, or remove/rename the existing folder first if it was created by mistake.

**"Template directory not found in repository"** – The curated template's expected subfolder wasn't found in the source repo — this usually means the templates repository itself changed structure; try refreshing the template list.

**Imports still reference the template's original module after creation** – This can happen with unusual import patterns the automatic remapping doesn't recognize (e.g. import aliases, or non-standard folder layouts). Search-and-replace the old module name manually in that case.

**Custom URL doesn't work but the same URL clones fine from the terminal** – Make sure the URL is a plain `https://` clone URL (not an SSH URL, unless you've set up SSH Git credentials system-wide) and that the repository is public, or that your system Git is already authenticated for private access.

---
---

# [PL] SunGo Project from GitHub Template – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany generator projektów: wybierz kuratorowany szablon (albo wskaż dowolne własne repozytorium Git) i dostań świeży, gotowy do kodowania projekt SunGo — z przemianowanym modułem, przemapowanymi importami, bez pozostałości historii Git.  
Dostęp przez wpis **📦 Project from GitHub Template** w panelu SunGo Tools.

---

## 📋 Krok 1 – Wybierz źródło

**Kuratorowane szablony** — SunGo pobiera aktualną listę z repozytorium [`SunDUINO/sungo-templates`](https://github.com/SunDUINO/sungo-templates) i pokazuje każdy jako kartę z nazwą, opisem i tagami. Wybierz jeden i jesteś gotowy.

**Własne repozytorium** — Masz własny projekt, którego używasz jako punkt startowy? Wklej dowolny URL Git w pole niestandardowe. Działa tak samo jak kuratorowany szablon — to samo przemianowanie, to samo czyszczenie.

---

## ✏️ Krok 2 – Nazwij projekt

Wpisz nazwę projektu — tylko litery, cyfry, myślniki i podkreślenia. To staje się zarówno nazwą folderu, jak i nazwą nowego modułu w `go.mod`.

> ⚠️ Jeśli folder o tej nazwie już istnieje w korzeniu workspace, SunGo go nie nadpisze — wybierz inną nazwę.

---

## ▶️ Krok 3 – Utwórz

SunGo klonuje płytko (shallow) repozytorium źródłowe do folderu tymczasowego (szybko, bez ciągnięcia pełnej historii), a następnie:

1. Kopiuje pliki szablonu do właściwej struktury projektu SunGo.
2. Przemianowuje każdy placeholder `${projectName}` i przemapowuje ścieżki importów Go z oryginalnej nazwy modułu szablonu na Twoją — łącznie z poprawnym dopasowaniem ścieżek niezależnie od tego, czy szablon używał podfolderu `src/`, czy płaskiego układu.
3. Uruchamia `go mod init` (albo od razu zapisuje świeży `go.mod`), żeby moduł nowego projektu od razu pasował do jego nazwy.
4. Zapisuje działający `launch.json`, żeby móc od razu zacząć debugować.
5. Usuwa tymczasowy klon i otwiera nowy projekt.

Log na dole panelu pokazuje każdy krok na żywo, więc widzisz dokładnie co się stało, jeśli coś potem nie wygląda dobrze.

---

## ⚠️ Częste problemy

**"A project with this name already exists"** – Wybierz inną nazwę projektu, albo usuń/przemianuj istniejący folder najpierw, jeśli powstał przez pomyłkę.

**"Template directory not found in repository"** – Oczekiwany podfolder kuratorowanego szablonu nie został znaleziony w repozytorium źródłowym — zwykle oznacza to, że repozytorium szablonów samo zmieniło strukturę; spróbuj odświeżyć listę szablonów.

**Importy nadal odwołują się do oryginalnego modułu szablonu po utworzeniu** – Może się zdarzyć przy nietypowych wzorcach importów, których automatyczne przemapowanie nie rozpoznaje (np. aliasy importów albo niestandardowe układy folderów). W takim przypadku podmień starą nazwę modułu ręcznie przez znajdź-i-zamień.

**Niestandardowy URL nie działa, choć ten sam URL klonuje się poprawnie z terminala** – Upewnij się, że URL to zwykły adres `https://` do klonowania (nie SSH, chyba że masz systemowo skonfigurowane dane logowania SSH Git) i że repozytorium jest publiczne, albo że Twój systemowy Git jest już uwierzytelniony do dostępu prywatnego.
