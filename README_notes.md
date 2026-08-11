[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Project Notes – Setup & Usage Guide

SunGo includes a per-project notes file — a plain Markdown scratchpad that lives alongside your code, for things you don't want to forget but don't want cluttering up your actual source files either.  
Access it via the **📝 Project Notes** entry in the SunGo Tools panel.

---

## 📋 What it is

The first time you open Project Notes for a given project, SunGo creates `.vscode/<project-name>_notes.md` with a simple starter template, and opens it as a normal Markdown editor tab — write in it exactly like any other Markdown file.

Every time you open Project Notes again (from the Tools panel, or from a MacroPAD key if you've assigned it), SunGo brings that same file back into focus rather than opening a new tab — even if it's currently in a background tab or a different editor group.

> 💡 Because it's a real file on disk, it works with everything you'd expect from a Markdown file: your usual formatting shortcuts, the Markdown preview pane, and version control if you choose to track it.

---

## 🖱️ Typical uses

- A running TODO list for the current work session
- Quick reminders about project-specific quirks ("remember: config path differs on Windows")
- Scratch notes while debugging, before they're worth turning into a real comment or issue

---

## ⚠️ Common Issues

**I don't want this file in version control** – Add `.vscode/<project-name>_notes.md` (or a wildcard like `.vscode/*_notes.md`) to your `.gitignore`. If the file was already committed before you added the rule, you'll also need to untrack it once: `git rm --cached .vscode/<project-name>_notes.md`.

**Notes disappeared after renaming the project folder** – The filename is derived from your project folder's name at the time the notes file was created. Renaming the folder afterward doesn't move or rename the notes file — it's still sitting in `.vscode/` under the old name.

**Clicking Project Notes opens a second copy instead of returning to the existing one** – This was a known issue in earlier versions and has since been fixed; make sure you're on the latest version of the extension.

---
---

# [PL] SunGo Project Notes – Instrukcja instalacji i użytkowania

SunGo zawiera plik notatek per projekt — zwykły notatnik Markdown, który leży obok Twojego kodu, na rzeczy, o których nie chcesz zapomnieć, ale też nie chcesz nimi zaśmiecać właściwych plików źródłowych.  
Dostęp przez wpis **📝 Project Notes** w panelu SunGo Tools.

---

## 📋 Czym to jest

Za pierwszym otwarciem Project Notes dla danego projektu, SunGo tworzy `.vscode/<nazwa-projektu>_notes.md` z prostym szablonem startowym i otwiera go jako zwykłą zakładkę edytora Markdown — piszesz w nim dokładnie tak jak w każdym innym pliku Markdown.

Za każdym kolejnym otwarciem Project Notes (z panelu Tools albo z klawisza MacroPAD, jeśli go przypisałeś), SunGo przywraca fokus na ten sam plik zamiast otwierać nową zakładkę — nawet jeśli jest aktualnie w tle albo w innej grupie edytorów.

> 💡 Ponieważ to prawdziwy plik na dysku, działa ze wszystkim, czego oczekujesz od pliku Markdown: zwykłe skróty formatowania, podgląd Markdown i kontrola wersji, jeśli zdecydujesz się go śledzić.

---

## 🖱️ Typowe zastosowania

- Bieżąca lista TODO na obecną sesję pracy
- Szybkie przypomnienia o specyfice projektu ("pamiętaj: ścieżka configu inna na Windows")
- Notatki robocze podczas debugowania, zanim będą warte prawdziwego komentarza albo issue

---

## ⚠️ Częste problemy

**Nie chcę tego pliku w kontroli wersji** – Dodaj `.vscode/<nazwa-projektu>_notes.md` (albo wildcard typu `.vscode/*_notes.md`) do `.gitignore`. Jeśli plik był już wcześniej scommitowany zanim dodałeś regułę, musisz go też raz wypisać ze śledzenia: `git rm --cached .vscode/<nazwa-projektu>_notes.md`.

**Notatki zniknęły po zmianie nazwy folderu projektu** – Nazwa pliku pochodzi z nazwy folderu projektu w momencie utworzenia pliku notatek. Zmiana nazwy folderu później nie przenosi ani nie zmienia nazwy pliku notatek — dalej leży w `.vscode/` pod starą nazwą.

**Kliknięcie Project Notes otwiera drugą kopię zamiast wrócić do istniejącej** – To był znany problem we wcześniejszych wersjach, od tamtej pory naprawiony; upewnij się, że masz najnowszą wersję rozszerzenia.
