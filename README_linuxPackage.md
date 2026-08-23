[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Linux Packaging – Setup & Usage Guide

SunGo can turn your compiled Go binary into real, installable Linux packages — `.deb`, `.rpm`, and AppImage — directly from the editor.  
Access it via the **📦 Package for Linux** entry in the SunGo Tools panel.

> ⚠️ This tool only appears when you're building **natively on a Linux host**. If you're cross-compiling a Linux target from Windows, you'll get the raw binary as usual, but not packaging — the packaging tools themselves need to run on Linux.

---

## 📋 Step 1 – Build your project

Run a normal build first (`go build` via SunGo, as always). Packaging always works from your **last successful build** — there's nothing to package until one exists.

---

## 🧰 Step 2 – Required tools

Packaging needs one small external tool per format. SunGo never installs anything system-wide or silently downloads binaries on your behalf — if a tool is missing, you'll see exactly what to run.

| Format | Tool | How to install |
|--------|------|-----------------|
| `.deb` / `.rpm` | [`nfpm`](https://nfpm.goreleaser.com) | `go install github.com/goreleaser/nfpm/v2/cmd/nfpm@latest` — uses the Go toolchain you already have installed to build SunGo projects. |
| AppImage | [`appimagetool`](https://github.com/AppImage/appimagetool) | Download the AppImage build from the [releases page](https://github.com/AppImage/appimagetool/releases), then `chmod +x appimagetool-*.AppImage` and place it somewhere on your `PATH` (e.g. `/usr/local/bin`). |

If you pick a format whose tool isn't found, SunGo shows a dialog with the exact command (and a **Run in Terminal** button for `nfpm`) or a direct link to the releases page (for `appimagetool`). That format is skipped for the current run — everything else you selected still builds normally.

> 💡 You can check tool status anytime in the **Dashboard → Installed Tools → 🐧 Linux Packaging** section (Linux only).

---

## 🔬 Step 3 – Pick your formats

Open **Package for Linux** and check any combination of `.deb`, `.rpm`, and AppImage. Press Enter to build the selected formats, or Esc to cancel.

* **`.deb` / `.rpm`** — built via `nfpm`. Package metadata (name, version, maintainer, description) is generated automatically:
  * **Name** — from the `module` line in `go.mod`.
  * **Version** — the same version SunGo already uses when naming your binary.
  * **Maintainer / Homepage / Description** — from your `package.json`'s `author`, `homepage`, and `description` fields, if present.
* **AppImage** — built via `appimagetool`. SunGo assembles the `AppDir` structure for you (binary, `AppRun` launcher, `.desktop` entry, and an icon).

### 🖼️ AppImage icon

SunGo picks the AppImage's icon automatically, checking these locations in order — no configuration needed for most projects:

1. **`sungo.package.iconPath`** setting, if you've set one (path relative to the project root, or absolute).
2. **A conventional file in your project** — the first one found wins: `icon.png`, `media/icon.png`, `assets/icon.png`, or `.sungo/icon.png`.
3. **SunGo's own icon** — used only as a last-resort fallback, so packaging never fails over a missing icon.

In practice, this means: if your project already has (or you add) a `media/icon.png`, your AppImage gets your own icon automatically, with nothing to set up. Only reach for `sungo.package.iconPath` if you want an icon that doesn't live in one of those conventional spots.

---

## 📦 Where packages go

Every built package lands in the same **`bin/`** folder your regular builds already use — no separate output directory to hunt for. A `.deb`, an `.rpm`, and an `.AppImage` from the same run all sit right next to your compiled binary.

---

## ⚙️ Setting a default selection

**SunGo – Linux Packaging › Default Formats** (`sungo.package.linuxDefaultFormats`) lets you pre-check your usual formats, so the picker opens ready to go — press Enter without touching a single checkbox if you always package the same way.

```json
"sungo.package.linuxDefaultFormats": ["deb", "rpm"]
```

---

## ⚠️ Common Issues

**"Some formats failed" after building** – Open the notification for details; each format fails independently, so a problem with `.rpm` won't stop `.deb` or AppImage from building successfully.

**Tool not found even though I just installed it** – Make sure the install location is actually on your shell's `PATH`, and that you opened a *new* VS Code terminal (or reloaded the window) after installing — an already-open terminal won't pick up a `PATH` change made outside it.

**AppImage build fails with a FUSE-related error** – Some minimal/containerized Linux environments don't have FUSE available, which `appimagetool` itself may need at runtime. Check your distro's docs for enabling FUSE, or run inside a desktop environment where it's typically already present.

**Package for Linux doesn't appear in the Tools panel** – This tool is intentionally hidden outside native Linux builds. If you're on Linux and still don't see it, make sure you're not cross-compiling (check your `sungo.build.targetOS` setting).

---
---

# [PL] SunGo Linux Packaging – Instrukcja instalacji i użytkowania

SunGo potrafi zamienić Twoją skompilowaną binarkę Go w prawdziwe, instalowalne paczki Linuksowe — `.deb`, `.rpm` i AppImage — bezpośrednio z poziomu edytora.  
Dostęp przez wpis **📦 Package for Linux** w panelu SunGo Tools.

> ⚠️ To narzędzie pojawia się wyłącznie przy buildzie **natywnym na hoście Linux**. Jeśli cross-kompilujesz target Linux z poziomu Windows, dostaniesz surową binarkę jak zwykle, ale bez pakowania — same narzędzia pakujące muszą uruchomić się na Linuksie.

---

## 📋 Krok 1 – Zbuduj projekt

Najpierw uruchom zwykły build (`go build` przez SunGo, jak zawsze). Pakowanie zawsze działa na Twoim **ostatnim udanym buildzie** — nie ma czego pakować, dopóki taki nie istnieje.

---

## 🧰 Krok 2 – Wymagane narzędzia

Pakowanie wymaga jednego, małego zewnętrznego narzędzia na format. SunGo nigdy nic nie instaluje systemowo ani nie pobiera binarnych plików po cichu w Twoim imieniu — jeśli narzędzia brakuje, zobaczysz dokładnie co uruchomić.

| Format | Narzędzie | Jak zainstalować |
|--------|-----------|-------------------|
| `.deb` / `.rpm` | [`nfpm`](https://nfpm.goreleaser.com) | `go install github.com/goreleaser/nfpm/v2/cmd/nfpm@latest` — wykorzystuje ten sam toolchain Go, który już masz do budowania projektów SunGo. |
| AppImage | [`appimagetool`](https://github.com/AppImage/appimagetool) | Pobierz plik AppImage ze [strony releases](https://github.com/AppImage/appimagetool/releases), następnie `chmod +x appimagetool-*.AppImage` i umieść go gdzieś na swojej ścieżce `PATH` (np. `/usr/local/bin`). |

Jeśli zaznaczysz format, którego narzędzia nie znaleziono, SunGo pokaże dialog z dokładną komendą (i przyciskiem **Run in Terminal** dla `nfpm`) albo bezpośrednim linkiem do strony releases (dla `appimagetool`). Ten format jest pomijany w bieżącym przebiegu — reszta zaznaczonych formatów buduje się normalnie.

> 💡 Status narzędzi możesz sprawdzić w dowolnej chwili w **Dashboard → Installed Tools → 🐧 Linux Packaging** (tylko na Linuksie).

---

## 🔬 Krok 3 – Wybierz formaty

Otwórz **Package for Linux** i zaznacz dowolną kombinację `.deb`, `.rpm` i AppImage. Enter buduje zaznaczone formaty, Esc anuluje.

* **`.deb` / `.rpm`** — budowane przez `nfpm`. Metadane paczki (nazwa, wersja, maintainer, opis) generowane są automatycznie:
  * **Nazwa** — z linii `module` w `go.mod`.
  * **Wersja** — ta sama wersja, której SunGo już używa przy nazywaniu binarki.
  * **Maintainer / Homepage / Opis** — z pól `author`, `homepage` i `description` w Twoim `package.json`, jeśli są obecne.
* **AppImage** — budowany przez `appimagetool`. SunGo samodzielnie składa strukturę `AppDir` (binarka, launcher `AppRun`, wpis `.desktop` oraz ikona).

### 🖼️ Ikona AppImage

SunGo dobiera ikonę AppImage automatycznie, sprawdzając kolejno te lokalizacje — bez żadnej konfiguracji dla większości projektów:

1. **Ustawienie `sungo.package.iconPath`**, jeśli je ustawiłeś (ścieżka względna do folderu projektu albo absolutna).
2. **Konwencjonalny plik w Twoim projekcie** — wygrywa pierwszy znaleziony: `icon.png`, `media/icon.png`, `assets/icon.png` albo `.sungo/icon.png`.
3. **Ikona samego SunGo** — używana tylko jako ostateczność, żeby pakowanie nigdy nie zawiodło z powodu brakującej ikony.

W praktyce oznacza to: jeśli Twój projekt ma już (albo dodasz) `media/icon.png`, Twój AppImage automatycznie dostanie Twoją ikonę, bez żadnej konfiguracji. Po `sungo.package.iconPath` sięgaj tylko, gdy chcesz użyć ikony spoza tych konwencjonalnych lokalizacji.

---

## 📦 Gdzie lądują paczki

Każda zbudowana paczka trafia do tego samego folderu **`bin/`**, którego używają Wasze zwykłe buildy — bez osobnego katalogu wyjściowego do szukania. `.deb`, `.rpm` i `.AppImage` z tego samego przebiegu siedzą tuż obok skompilowanej binarki.

---

## ⚙️ Ustawianie domyślnego wyboru

**SunGo – Linux Packaging › Default Formats** (`sungo.package.linuxDefaultFormats`) pozwala z góry zaznaczyć zwykle używane formaty, dzięki czemu picker otwiera się gotowy do użycia — wystarczy Enter bez dotykania żadnego checkboxa, jeśli zawsze pakujesz w ten sam sposób.

```json
"sungo.package.linuxDefaultFormats": ["deb", "rpm"]
```

---

## ⚠️ Częste problemy

**"Some formats failed" po zbudowaniu** – Otwórz powiadomienie po szczegóły; każdy format zawodzi niezależnie, więc problem z `.rpm` nie zatrzyma udanego zbudowania `.deb` czy AppImage.

**Narzędzie niewykryte mimo że właśnie je zainstalowałem** – Upewnij się, że lokalizacja instalacji faktycznie jest na `PATH` Twojego shella, i że otworzyłeś *nowy* terminal VS Code (albo przeładowałeś okno) po instalacji — już otwarty terminal nie złapie zmiany `PATH` zrobionej poza nim.

**Build AppImage kończy się błędem związanym z FUSE** – Niektóre minimalne/skonteneryzowane środowiska Linux nie mają dostępnego FUSE, którego `appimagetool` może potrzebować w runtime. Sprawdź dokumentację swojej dystrybucji jak włączyć FUSE, albo uruchom w środowisku desktopowym, gdzie zwykle jest już obecne.

**Package for Linux nie pojawia się w panelu Tools** – To narzędzie jest celowo ukryte poza natywnymi buildami Linux. Jeśli jesteś na Linuksie i nadal go nie widzisz, upewnij się, że nie cross-kompilujesz (sprawdź ustawienie `sungo.build.targetOS`).
