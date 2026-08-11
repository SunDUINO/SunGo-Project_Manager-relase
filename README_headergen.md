[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Header Generator – Setup & Usage Guide

SunGo includes a built-in file header generator: pick a style, fill in your author details once, and insert a consistent comment header into any `.go` file — with a live preview as you type.  
Access it via the **✏️ Header Generator** entry in the SunGo Tools panel.

---

## 🎨 Step 1 – Pick a style

Six built-in styles are available, from a decorative boxed header down to a single comment line:

| Style | Look |
|-------|------|
| **Fancy** | Full double-line box border, most decorative |
| **Box** | Single-line box border |
| **Block** | Plain `/* ... */` block, no border |
| **Line** | Plain `//` comment lines, no border |
| **Minimal** | One line: project, file, author, date |
| **Custom** | Your own template — see below |
| **None** | Skip the header entirely |

The preview at the bottom of the panel updates live as you switch styles or edit your details.

---

## ✏️ Custom templates

Pick **Custom** to write your own single-line format using tokens — click any token below the text box to insert it at your cursor:

```
{project} {file} {author} {team} {website} {forum} {github} {version} {license} {date} {year}
```

For example: `// {project} v{version} — {author} — {date}`

---

## 👤 Step 2 – Fill in your details (once)

Author, team, website, forum, and license are saved to your VS Code settings, so you only need to enter them once — every future header reuses them automatically.

> 💡 **GitHub** and **Version** are filled in automatically when possible: GitHub from your `go.mod`'s module path, Version by scanning `src/main.go` for a `version`/`ver` variable assignment. No need to type these by hand if they're already in your code.

Check **"Auto-insert header on new .go file"** to have SunGo add the header automatically every time you create a new Go file, without opening this panel each time.

---

## ⬆️ Step 3 – Insert

With the style and preview looking right, click **"⬆ Insert into file"** to add the header to the top of your currently open file. Click **"💾 Save Settings"** first if you've changed any author details you want to keep for next time.

---

## ⚠️ Common Issues

**Version isn't auto-detected** – SunGo looks for a pattern like `version := "1.0.0"` or `ver = "1.0.0"` specifically in `src/main.go`. If your project structure or variable naming is different, just type the version manually — it won't be overwritten.

**Header gets inserted twice** – If you have "Auto-insert on new file" enabled *and* manually click "Insert" on a freshly created file, you'll get two headers. Turn off auto-insert if you prefer doing it manually, or just delete the duplicate.

**Custom template tokens aren't replaced** – Tokens are case-sensitive and must match exactly, including the curly braces — `{Author}` won't work, only `{author}`. Click the token buttons instead of typing them by hand to avoid typos.

---
---

# [PL] SunGo Header Generator – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany generator nagłówków plików: wybierz styl, uzupełnij dane autora raz, a potem wstawiaj spójny nagłówek komentarza do dowolnego pliku `.go` — z podglądem na żywo w trakcie pisania.  
Dostęp przez wpis **✏️ Header Generator** w panelu SunGo Tools.

---

## 🎨 Krok 1 – Wybierz styl

Dostępnych jest sześć wbudowanych stylów, od ozdobnego nagłówka w ramce po pojedynczą linię komentarza:

| Styl | Wygląd |
|------|--------|
| **Fancy** | Pełna ramka z podwójną linią, najbardziej ozdobny |
| **Box** | Ramka z pojedynczą linią |
| **Block** | Zwykły blok `/* ... */`, bez ramki |
| **Line** | Zwykłe linie komentarza `//`, bez ramki |
| **Minimal** | Jedna linia: projekt, plik, autor, data |
| **Custom** | Twój własny szablon — patrz niżej |
| **None** | Pomiń nagłówek całkowicie |

Podgląd na dole panelu aktualizuje się na żywo przy zmianie stylu albo edycji danych.

---

## ✏️ Własne szablony

Wybierz **Custom**, żeby napisać własny, jednoliniowy format za pomocą tokenów — kliknij dowolny token pod polem tekstowym, żeby wstawić go w pozycji kursora:

```
{project} {file} {author} {team} {website} {forum} {github} {version} {license} {date} {year}
```

Na przykład: `// {project} v{version} — {author} — {date}`

---

## 👤 Krok 2 – Uzupełnij dane (raz)

Autor, zespół, strona, forum i licencja są zapisywane w ustawieniach VS Code, więc musisz je wpisać tylko raz — każdy kolejny nagłówek automatycznie ich używa.

> 💡 **GitHub** i **Wersja** są wypełniane automatycznie, gdy to możliwe: GitHub z nazwy modułu w `go.mod`, Wersja przez przeszukanie `src/main.go` pod kątem przypisania zmiennej `version`/`ver`. Nie musisz wpisywać ich ręcznie, jeśli są już w Twoim kodzie.

Zaznacz **"Auto-insert header on new .go file"**, żeby SunGo automatycznie dodawał nagłówek za każdym razem, gdy tworzysz nowy plik Go, bez otwierania tego panelu za każdym razem.

---

## ⬆️ Krok 3 – Wstaw

Kiedy styl i podgląd wyglądają dobrze, kliknij **"⬆ Insert into file"**, żeby dodać nagłówek na górę aktualnie otwartego pliku. Kliknij najpierw **"💾 Save Settings"**, jeśli zmieniłeś jakieś dane autora, które chcesz zachować na przyszłość.

---

## ⚠️ Częste problemy

**Wersja nie jest wykrywana automatycznie** – SunGo szuka wzorca typu `version := "1.0.0"` albo `ver = "1.0.0"` konkretnie w `src/main.go`. Jeśli struktura Twojego projektu albo nazewnictwo zmiennych jest inne, po prostu wpisz wersję ręcznie — nie zostanie nadpisana.

**Nagłówek wstawia się dwa razy** – Jeśli masz włączone "Auto-insert on new file" *i* ręcznie klikniesz "Insert" na świeżo utworzonym pliku, dostaniesz dwa nagłówki. Wyłącz auto-insert, jeśli wolisz robić to ręcznie, albo po prostu usuń duplikat.

**Tokeny w niestandardowym szablonie nie są podmieniane** – Tokeny są wrażliwe na wielkość liter i muszą pasować dokładnie, łącznie z klamrami — `{Author}` nie zadziała, tylko `{author}`. Klikaj przyciski tokenów zamiast wpisywać je ręcznie, żeby uniknąć literówek.
