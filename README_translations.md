[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Translations (i18n) – User Guide

The **Translations** tool (SunGo Tools → **Translations**, or the command **SunGo: Translations (i18n)**) takes care of everything around app texts: it finds missing and unused translations, texts typed straight into the code, creates translation files and translates missing texts – from memory, your glossary or AI.

It recognises three kinds of projects by itself:

| Project | Translation files | In the code |
|---------|-------------------|-------------|
| **Go app** (Fyne, Ebitengine, console…) | `src/lang/nls_pl.json`, `nls_en.json`… | `lang.T("btn_save")` |
| **Webview app** (HTML/JS frontend) | `<frontend>/lang/nls_pl.json`… (next to `index.html`) | JS `t('btn_save')`, HTML `data-t="btn_save"` |
| **VS Code extension** | `package.nls.json` (EN) + `package.nls.pl.json` | `localize('key', 'fallback')` |

> 💡 Older projects with `nls_*.json` directly in the frontend folder (e.g. SunRelease Wizard, SunPLOT) work as they are – nothing is moved.

---

## 🚀 Step 1 – Translation files for a project

* **New project:** in the **Project Creator** tick **🌐 Create translation files** and choose the languages (PL and EN; more languages can be added with the `sungo.i18n.extraLanguages` setting, e.g. `["de", "ja"]`). The project starts with `src/lang/` ready.
* **Existing project without translations:** open the **Translations** panel and click **✨ Generate translations**. A preview shows the new files (base texts: buttons, questions, states, messages, menu) and the obvious texts that will be connected automatically (e.g. a button with exactly "Anuluj" → `btn_cancel`). Nothing is saved until you click **✓ Apply**.

After generating, the button disappears – the project has translations now and the panel shows its other tabs.

---

## 🗂️ Step 2 – The panel

**Project** – the project open in VS Code; with **Whole workspace** ticked you get an overview of all projects in the SunGo folder (the **Workspace** tab) and their translations also feed the translation memory.

### ✅ Key check
* **Missing in a language** – the key is in one file but not in another.
* **Used in code, missing in files** – the code asks for a key that no file has.
* **Untranslated** – empty, or the same text as in Polish. If it should stay the same (e.g. "OK", a product name), click **Identical on purpose**.
* **{n} mismatch** – `{0}`, `{1}` differ between languages.
* **Unused** – the key is not used anywhere (keys built in the code from pieces may show up here by mistake).
* **Fallback differs** (extension only) – the text written in `localize()` differs from the file.

Clicking a place opens the file at the right line.

### ✂️ Hardcoded strings
Texts typed straight into the code (labels, messages, button texts, `placeholder`/`title` in HTML…). Logs, comments, paths, ids and CSS are skipped. Each text has a proposed key – **Extract…** shows a preview (old line → new line, new entries in the translation files); you can change the key before **✓ Apply**. Only that one place is changed.

> 💡 A line that should be left alone: add a comment `sungo-i18n-ignore` on that line.

### ✏️ Translation editor
Polish on the left, the translation on the right. Filters: **to do**, **to review**, **all**, and search.
* **🌐 Translate missing** – fills the gaps in this order: **memory** (the same Polish text already translated in this project, in SunGo or – with Whole workspace – in your other projects), **glossary**, then **AI**.
* AI results are marked **to review**. They are written to the file after **💾 Save changes**, but keep the mark until you click **✓ Accept**.
* A translation that loses `{0}`, an emoji, `**bold**` or an HTML tag is **rejected** and not saved – correct it by hand or translate again.
* **+ Language** adds another language file (texts copied from Polish, to be translated).

### 📚 Glossary
Fixed terms (e.g. "Wydanie" → "Release") and names that must never be translated (e.g. SunGo, your program names). Saved in the project in `.vscode/sungo-glossary.json`; the AI always gets it.

---

## 🤖 Step 3 – AI (optional)

1. Settings (Ctrl+,) → **SunGo – Translations (i18n)** → **Provider**: `gemini` (default), `openai`, `ollama` (local, no key) or `none` (memory and glossary only).
2. **🔑 API key** in the editor (or the command **SunGo: Set AI API key for translations**). The key is kept in VS Code's secure storage, never in the settings files.
3. Right after the key you get a short list of the newest models to choose from. **📋 Model** opens the list again any time (for Ollama: the models installed on your computer).

---

## 🧩 Step 4 – Using translations in your code

### 🐹 Go app (`src/lang`)

```go
import "MyApp/src/lang"   // "<module from go.mod>/src/lang"

fmt.Println(lang.T("btn_save"))              // "Zapisz" / "Save"
msg := lang.T("msg_open_failed", path)       // {0} is replaced by path
```

* At start the language of the system is used; if there is no file for it – English.
* `lang.SetLang("en")` – change the language while the program runs (returns `false` if there is no such file).
* `lang.Lang()` – current language, `lang.Langs()` – available languages, e.g. `[en pl]`.
* The texts are built into the program – you ship one file, no `nls_*.json` next to it.

**Language switch (Fyne example):**

```go
a := app.NewWithID("pl.lothar.myapp")
if saved := a.Preferences().String("lang"); saved != "" {
    lang.SetLang(saved)                       // language remembered from the last run
}
w := a.NewWindow(lang.T("menu_file"))
saveBtn := widget.NewButton(lang.T("btn_save"), func() {})

refresh := func() {                           // set all texts again after a change
    w.SetTitle(lang.T("menu_file"))
    saveBtn.SetText(lang.T("btn_save"))
}
langSel := widget.NewSelect(lang.Langs(), func(l string) {
    lang.SetLang(l)
    a.Preferences().SetString("lang", l)
    refresh()
})
langSel.SetSelected(lang.Lang())
```

> 💡 Widgets do not change their text by themselves – keep one function that sets all texts again and call it after `SetLang`.

### 🌐 Webview app (HTML + JS)

In `index.html`, **before** your own scripts (Generate translations adds this line for you):

```html
<script src="i18n.js"></script>
<script src="app.js"></script>
```

In HTML – the text inside the element stays as a fallback:

```html
<button data-t="btn_save">Zapisz</button>
<input data-tp="ph_search" placeholder="Szukaj…">     <!-- placeholder -->
<span data-tt="tip_refresh" title="Odśwież">⟳</span>  <!-- tooltip (title) -->
```

In JS:

```js
status.textContent = t('state_saved');
alert(t('msg_open_failed', fileName));        // {0} → fileName
```

**Language switch:**

```html
<button class="lang" data-lang="pl">PL</button>
<button class="lang" data-lang="en">EN</button>
```

```js
document.querySelectorAll('.lang').forEach(b =>
  b.addEventListener('click', () => setLang(b.dataset.lang)));

// your own views drawn from JS – draw them again after a change
document.addEventListener('langchange', () => renderList());
```

* At start: the language chosen last time (remembered in the browser storage), otherwise the browser language, otherwise English. `t()` works already in your startup code.
* `setLang('en')` loads `lang/nls_en.json` and refreshes every element with `data-t` / `data-tp` / `data-tt`.
* HTML added later from JS (e.g. `innerHTML`) – call `applyNls(element)` or use `t()` directly in the template.
* `nlsLang()` – current language, `nlsLangs()` – available languages.
* The `lang/` folder must be served together with `index.html` (in apps with an embedded frontend it is, as long as it lies inside the frontend folder).

> 💡 Projects using `data-i18n` attributes (like SunPLOT) keep their own convention – the panel detects it and extracts texts the same way.

### 🧩 VS Code extension

```ts
vscode.window.showInformationMessage(localize('build.done', 'Gotowe: {0}', name));
```

* `package.nls.json` is English (default), `package.nls.pl.json` Polish.
* In `package.json` use `"%key%"`, e.g. `"title": "%cmd.showI18n%"`.
* **Extract…** inserts `localize()` and the import of `localize` by itself.

---

## ➕ Adding a new text by hand

Add the same key to **every** `nls_*.json` file (in Polish and in English), then use it in the code. If you forget a language, **Key check** shows it, and **Translate missing** fills it in.

---

## 🩺 Troubleshooting

* **The key shows up instead of the text** – the key is missing in the files (Key check → *Used in code, missing in files*), or the webview cannot load `lang/nls_*.json` (the files are not served next to `index.html`).
* **Translate missing does nothing / error 401/403** – check the API key (**🔑 API key**) and the provider in the settings.
* **"rejected: {n}" / "rejected: emoji"** – the AI lost a placeholder or an emoji; correct the text by hand.
* **The Generate translations button is missing** – the project already has translation files (they may be deeper, e.g. in `src/web/static`); the panel header shows their folder.

---

# [PL] SunGo Tłumaczenia (i18n) – Instrukcja

Narzędzie **Tłumaczenia** (SunGo Tools → **Tłumaczenia** albo polecenie **SunGo: Tłumaczenia (i18n)**) dba o wszystko, co dotyczy tekstów aplikacji: znajduje brakujące i nieużywane tłumaczenia, teksty wpisane wprost w kod, tworzy pliki tłumaczeń i tłumaczy brakujące teksty – z pamięci, Twojego słownika albo przez AI.

Samo rozpoznaje trzy rodzaje projektów:

| Projekt | Pliki tłumaczeń | W kodzie |
|---------|-----------------|----------|
| **Aplikacja Go** (Fyne, Ebitengine, konsola…) | `src/lang/nls_pl.json`, `nls_en.json`… | `lang.T("btn_save")` |
| **Aplikacja webview** (frontend HTML/JS) | `<frontend>/lang/nls_pl.json`… (obok `index.html`) | JS `t('btn_save')`, HTML `data-t="btn_save"` |
| **Rozszerzenie VS Code** | `package.nls.json` (EN) + `package.nls.pl.json` | `localize('klucz', 'fallback')` |

> 💡 Starsze projekty z `nls_*.json` bezpośrednio w folderze frontendu (np. SunRelease Wizard, SunPLOT) działają tak jak są – nic nie jest przenoszone.

---

## 🚀 Krok 1 – Pliki tłumaczeń w projekcie

* **Nowy projekt:** w **Kreatorze projektu** zaznacz **🌐 Utwórz pliki tłumaczeń** i wybierz języki (PL i EN; kolejne języki dołączysz ustawieniem `sungo.i18n.extraLanguages`, np. `["de", "ja"]`). Projekt startuje z gotowym `src/lang/`.
* **Istniejący projekt bez tłumaczeń:** otwórz panel **Tłumaczenia** i kliknij **✨ Wygeneruj tłumaczenia**. Podgląd pokazuje nowe pliki (teksty bazowe: przyciski, pytania, stany, komunikaty, menu) i oczywiste teksty, które zostaną podpięte automatycznie (np. przycisk z dokładnie „Anuluj” → `btn_cancel`). Nic nie jest zapisywane, dopóki nie klikniesz **✓ Zastosuj**.

Po wygenerowaniu przycisk znika – projekt ma już tłumaczenia, a panel pokazuje pozostałe zakładki.

---

## 🗂️ Krok 2 – Panel

**Projekt** – projekt otwarty w VS Code; z zaznaczonym **Cały workspace** dostajesz przegląd wszystkich projektów z folderu SunGo (zakładka **Workspace**), a ich tłumaczenia zasilają też pamięć tłumaczeń.

### ✅ Kontrola kluczy
* **Brak w języku** – klucz jest w jednym pliku, a w innym nie.
* **Użyte w kodzie, brak w plikach** – kod prosi o klucz, którego nie ma w żadnym pliku.
* **Nieprzetłumaczone** – puste albo ten sam tekst co po polsku. Jeśli ma tak zostać (np. „OK”, nazwa produktu), kliknij **Identyczne celowo**.
* **Niezgodne {n}** – `{0}`, `{1}` różnią się między językami.
* **Nieużywane** – klucz nie jest nigdzie użyty (klucze sklejane w kodzie z kawałków mogą tu trafić niesłusznie).
* **Fallback inny niż w pliku** (tylko rozszerzenie) – tekst wpisany w `localize()` różni się od pliku.

Kliknięcie miejsca otwiera plik na właściwej linii.

### ✂️ Teksty na sztywno
Teksty wpisane wprost w kod (etykiety, komunikaty, napisy na przyciskach, `placeholder`/`title` w HTML…). Logi, komentarze, ścieżki, identyfikatory i CSS są pomijane. Każdy tekst ma proponowany klucz – **Wyciągnij…** pokazuje podgląd (stara linia → nowa linia, nowe wpisy w plikach tłumaczeń); klucz możesz zmienić przed **✓ Zastosuj**. Zmieniane jest tylko to jedno miejsce.

> 💡 Linia, której narzędzie ma nie ruszać: dopisz w niej komentarz `sungo-i18n-ignore`.

### ✏️ Edytor tłumaczeń
Po lewej polski, po prawej tłumaczenie. Filtry: **do zrobienia**, **do sprawdzenia**, **wszystkie** oraz wyszukiwanie.
* **🌐 Przetłumacz brakujące** – uzupełnia braki w tej kolejności: **pamięć** (ten sam polski tekst przetłumaczony już w tym projekcie, w SunGo albo – z opcją Cały workspace – w innych Twoich projektach), **słownik**, na końcu **AI**.
* Wyniki AI są oznaczone **do sprawdzenia**. Trafiają do pliku po **💾 Zapisz zmiany**, ale zachowują oznaczenie, dopóki nie klikniesz **✓ Akceptuj**.
* Tłumaczenie, które zgubiło `{0}`, emoji, `**pogrubienie**` albo tag HTML, jest **odrzucane** i nie zostanie zapisane – popraw je ręcznie albo przetłumacz jeszcze raz.
* **+ Język** dodaje plik kolejnego języka (teksty skopiowane z polskiego, do przetłumaczenia).

### 📚 Słownik
Stałe terminy (np. „Wydanie” → „Release”) i nazwy, których nie wolno tłumaczyć (np. SunGo, nazwy Twoich programów). Zapisywany w projekcie w `.vscode/sungo-glossary.json`; AI zawsze go dostaje.

---

## 🤖 Krok 3 – AI (opcjonalnie)

1. Ustawienia (Ctrl+,) → **SunGo – Translations (i18n)** → **Provider**: `gemini` (domyślnie), `openai`, `ollama` (lokalnie, bez klucza) albo `none` (tylko pamięć i słownik).
2. **🔑 Klucz API** w edytorze (albo polecenie **SunGo: Ustaw klucz API AI do tłumaczeń**). Klucz jest w bezpiecznym magazynie VS Code, nigdy w plikach ustawień.
3. Zaraz po wpisaniu klucza dostajesz krótką listę najnowszych modeli do wyboru. **📋 Model** otwiera ją w każdej chwili (dla Ollamy: modele zainstalowane na Twoim komputerze).

---

## 🧩 Krok 4 – Tłumaczenia w Twoim kodzie

### 🐹 Aplikacja Go (`src/lang`)

```go
import "MojaApka/src/lang"   // "<moduł z go.mod>/src/lang"

fmt.Println(lang.T("btn_save"))              // "Zapisz" / "Save"
msg := lang.T("msg_open_failed", path)       // {0} zostanie zastąpione wartością path
```

* Na starcie używany jest język systemu; gdy nie ma dla niego pliku – angielski.
* `lang.SetLang("en")` – zmiana języka w trakcie działania programu (zwraca `false`, gdy nie ma takiego pliku).
* `lang.Lang()` – bieżący język, `lang.Langs()` – dostępne języki, np. `[en pl]`.
* Teksty są wkompilowane w program – wydajesz jeden plik, bez `nls_*.json` obok.

**Przełącznik języka (przykład Fyne):**

```go
a := app.NewWithID("pl.lothar.mojaapka")
if saved := a.Preferences().String("lang"); saved != "" {
    lang.SetLang(saved)                       // język zapamiętany z poprzedniego uruchomienia
}
w := a.NewWindow(lang.T("menu_file"))
saveBtn := widget.NewButton(lang.T("btn_save"), func() {})

refresh := func() {                           // ponowne ustawienie wszystkich tekstów po zmianie
    w.SetTitle(lang.T("menu_file"))
    saveBtn.SetText(lang.T("btn_save"))
}
langSel := widget.NewSelect(lang.Langs(), func(l string) {
    lang.SetLang(l)
    a.Preferences().SetString("lang", l)
    refresh()
})
langSel.SetSelected(lang.Lang())
```

> 💡 Widżety same nie zmieniają tekstu – trzymaj jedną funkcję, która ustawia wszystkie teksty od nowa, i wywołuj ją po `SetLang`.

### 🌐 Aplikacja webview (HTML + JS)

W `index.html`, **przed** własnymi skryptami (Wygeneruj tłumaczenia dopisuje tę linię sam):

```html
<script src="i18n.js"></script>
<script src="app.js"></script>
```

W HTML – tekst w środku elementu zostaje jako zapas:

```html
<button data-t="btn_save">Zapisz</button>
<input data-tp="ph_search" placeholder="Szukaj…">     <!-- placeholder -->
<span data-tt="tip_refresh" title="Odśwież">⟳</span>  <!-- podpowiedź (title) -->
```

W JS:

```js
status.textContent = t('state_saved');
alert(t('msg_open_failed', fileName));        // {0} → fileName
```

**Przełącznik języka:**

```html
<button class="lang" data-lang="pl">PL</button>
<button class="lang" data-lang="en">EN</button>
```

```js
document.querySelectorAll('.lang').forEach(b =>
  b.addEventListener('click', () => setLang(b.dataset.lang)));

// własne widoki rysowane z JS – narysuj je od nowa po zmianie
document.addEventListener('langchange', () => renderList());
```

* Na starcie: język wybrany ostatnio (zapamiętany w pamięci przeglądarki), inaczej język przeglądarki, inaczej angielski. `t()` działa już w Twoim kodzie startowym.
* `setLang('en')` wczytuje `lang/nls_en.json` i odświeża wszystkie elementy z `data-t` / `data-tp` / `data-tt`.
* HTML dodany później z JS (np. `innerHTML`) – wywołaj `applyNls(element)` albo użyj `t()` bezpośrednio w szablonie.
* `nlsLang()` – bieżący język, `nlsLangs()` – dostępne języki.
* Folder `lang/` musi być serwowany razem z `index.html` (w aplikacjach z wkompilowanym frontendem jest, jeśli leży w folderze frontendu).

> 💡 Projekty z atrybutami `data-i18n` (jak SunPLOT) zachowują swoją konwencję – panel ją rozpoznaje i wyciąga teksty tak samo.

### 🧩 Rozszerzenie VS Code

```ts
vscode.window.showInformationMessage(localize('build.done', 'Gotowe: {0}', name));
```

* `package.nls.json` to angielski (domyślny), `package.nls.pl.json` polski.
* W `package.json` używaj `"%klucz%"`, np. `"title": "%cmd.showI18n%"`.
* **Wyciągnij…** sam wstawia `localize()` i import `localize`.

---

## ➕ Ręczne dodanie nowego tekstu

Dopisz ten sam klucz do **każdego** pliku `nls_*.json` (po polsku i po angielsku), potem użyj go w kodzie. Jeśli zapomnisz o jakimś języku, pokaże to **Kontrola kluczy**, a **Przetłumacz brakujące** go uzupełni.

---

## 🩺 Rozwiązywanie problemów

* **Zamiast tekstu widać klucz** – brakuje klucza w plikach (Kontrola kluczy → *Użyte w kodzie, brak w plikach*) albo webview nie może wczytać `lang/nls_*.json` (pliki nie są serwowane obok `index.html`).
* **Przetłumacz brakujące nic nie robi / błąd 401/403** – sprawdź klucz API (**🔑 Klucz API**) i dostawcę w ustawieniach.
* **„odrzucone: {n}” / „odrzucone: emoji”** – AI zgubiło placeholder albo emoji; popraw tekst ręcznie.
* **Nie ma przycisku Wygeneruj tłumaczenia** – projekt ma już pliki tłumaczeń (mogą leżeć głębiej, np. w `src/web/static`); folder pokazuje nagłówek panelu.
