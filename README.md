# SunGo Project Manager

[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Project Manager

**SunGo Project Manager** is a streamlined, efficient tool for managing your Go language projects inside Visual Studio Code, designed for simplicity and a clean, professional workflow.

![SunGo Demo](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/06be103/0d1f4b0/5e6c00051b6d3d97748d476b36fb2910.gif)

> 💡 **Master's Tip:** SunGo is 100% functional as a standalone extension. The physical SunGO PAD is an optional (but awesome) hardware companion for electronics enthusiasts.

## 💡 Philosophy & UX

### Project Philosophy
> **"SunGo was created to bring order to the Go development process. I believe that a clean project structure and optimized binaries are the foundation of professional software."**

#### ⚡ JetBrains-like Experience
SunGo aims to bring the "it just works" comfort known from premium IDEs to the lightweight Visual Studio Code:
* **Zero-Config Debugging:** Automatically generates and updates `launch.json`. No more manual path editing to start your debugger.
* **Contextual Intelligence:** All Go-specific actions (Build, Run, Test, Sign) are available exactly where you need them — in the status bar, editor title, and context menus.
* **Automated Housekeeping:** From `go mod tidy` to cleaning the `/bin` folder, SunGo handles the repetitive tasks so you can focus on the logic.
* **Binary Health Monitor:** Instant feedback on your executable size directly in the status bar.

--- 

### 🌟 Why SunGo? (Gopher Rules)
* **Binary Identity:** Every `main.go` gets a unique project header encoded in binary format. Your code, your signature.
* **Performance First:** Automatically applies `-s -w` linker flags to strip debug data—making your binaries up to 40% smaller.
* **Zero-Config Debugging:** Automatically generates `launch.json`. No more manual path editing to start debugging.
* **TDD Ready:** Every project starts with a generated `main_test.go`. Don't just code—verify.


![Marketplace Version](https://img.shields.io/visual-studio-marketplace/v/SunRiver-LotharTeaM.sungo-project-manager?label=version&color=orange)

## 📖 Table of Contents
* [EN: Requirements & Installation](#requirements-installation)
* [EN: SunGO PAD – Visual Status Feedback](#sungo-pad-visual-status-feedback-optional-hardware)
* [EN: Linux Setup – udev rules](#linux-setup-sungo-pad-udev-rules)
* [EN: What's New (v1.5.0)](#whats-new-v110)
* [EN: What's New (v1.0.0)](#whats-new-v100)
* [EN: What's New (v0.9.0)](#whats-new-v090)
* [EN: Key Features](#key-features)
* [PL: SunGo Project Manager](#pl-sungo-project-manager)

---

## 📦 Requirements & Installation

Before installing SunGo Project Manager, make sure the following tools are available on your system. All of them are required for full functionality (building, linting, GUI libraries, and PAD communication).

### 1. Visual Studio Code
The extension runs inside VS Code.  
🔗 [Download VS Code](https://code.visualstudio.com/)

### 2. Go Official VS Code Extension (gopls)
Provides language server support, IntelliSense, and `gopls` integration. Install directly from the VS Code Marketplace.  
🔗 [Go Extension for VS Code](https://marketplace.visualstudio.com/items?itemName=golang.go)

### 3. Go Compiler
The Go toolchain is required for building and running your projects.  
🔗 [Download Go](https://go.dev/dl/)

### 4. GCC Compiler – MSYS2 / MinGW-w64 (Windows) / / Native GCC (Linux)
Required for building native libraries (e.g., **Fyne**, **Raylib**) that depend on **CGO**. 
* **Windows (Automated):** You no longer need to install GCC manually. If SunGo detects it's missing, simply click **"Install GCC (MSYS2)"** in the Dashboard (HOME). The extension will download and configure the environment for you.
* **Linux (Manual):** Install the GCC toolchain using your package manager:
    * *Ubuntu/Debian:* `sudo apt update && sudo apt install build-essential`
    * *Arch Linux:* `sudo pacman -S base-devel`
    * *Fedora:* `sudo dnf groupinstall "Development Tools"`


### 5. PowerShell 7 (Core) (Windows)
SunGo uses PowerShell scripts for certain automation tasks. PowerShell 7 (cross-platform Core edition) is required.  
🔗 [Download PowerShell 7](https://github.com/PowerShell/PowerShell/releases/latest)

### 6. Git
Required for version control integration and dependency management.  
🔗 [Download Git](https://git-scm.com/downloads)

### 7. (Optional) Go GUI Libraries
If your project uses graphical interfaces, install the relevant library:

| Library | Purpose | Install |
|---|---|---|
| **Fyne** | Cross-platform GUI toolkit | `go get fyne.io/fyne/v2` |
| **Raylib-go** | Game / multimedia framework | `go get github.com/gen2brain/raylib-go/raylib` |

> Both Fyne and Raylib require GCC (step 4) to compile via CGO.

### ✅ Quick Checklist

```
[ ] VS Code installed
[ ] Go official extension (gopls) installed
[ ] Go compiler installed and in PATH
[ ] TDM-GCC 64-bit 10.3.0 installed and in PATH
[ ] PowerShell 7 (Core) installed
[ ] Git installed
[ ] (Optional) Fyne / Raylib-go for GUI projects
```

### Installing SunGo Project Manager
Search for **"SunGo Project Manager"** in the VS Code Extensions panel, or install directly from the Marketplace:  
🔗 [SunGo Project Manager on VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=SunRiver-LotharTeaM.sungo-project-manager)

---

## 🎛 SunGO PAD – Visual Status Feedback Optional Hardware 

<p align="center">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/0facbd3/efd9d1f/a959bed88632c98c1ec184462e2b05a6.jpg" width="240" alt="Idle State">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/419a0c0/78fd922/4264b947ca652cadcdb72a558fb1f0d4.jpg" width="240" alt="RUN State - Green">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/d43865b/3a57d46/e45fbf12ef4d64c0e2d30cfce2db251b.jpg" width="240" alt="Error State - Red">
</p>

The physical **SunGO PAD** provides real-time visual feedback via native HID RAW communication. Key backlight colors dynamically reflect the current state of your build pipeline — without ever needing to glance at the terminal.

- ⚪ **Idle** – system ready, waiting for action
- 🟢 **Green** – RUN / Build completed successfully
- 🔴 **Red** – linter or compilation error detected

### 🔀 OS Toggle (Windows / Linux)
Press **keys 1+7+9 simultaneously** (VS Code + Build + Test) to switch the PAD between Windows and Linux mode:

| Combination | Result | Indicator |
|---|---|---|
| 1+7+9 | Switch to Linux | 🔴 3 red flashes |
| 1+7+9 again | Switch to Windows | 🔵 3 blue flashes |

> The selected mode is saved permanently in the PAD flash memory and survives power cycles. Default mode is Windows.

> **Note:** The SunGo extension is fully functional **without** the physical hardware. The PAD is an optional companion device that replaces status bar controls with tactile buttons and vivid LED feedback for a more immersive development experience.

### 🔧 Firmware & Build
Detailed firmware releases, flashing instructions, and build information for the SunGO PAD are documented on the official forum:  
🔗 [SunGO PAD – Official Thread](https://forum.lothar-team.pl/viewtopic.php?t=1092)

---

## 🐧 Linux Setup – SunGO PAD (udev rules)

On Linux, access to HID RAW devices requires a one-time permission configuration. Without it the PAD will be detected but LEDs and commands won't work.

**1. Open a terminal (`Ctrl+Alt+T`) and create the rules file:**
```bash
sudo nano /etc/udev/rules.d/99-sungo-pad.rules
```

**2. Paste the following line:**
```
SUBSYSTEM=="hidraw", ATTRS{idVendor}=="cafe", ATTRS{idProduct}=="4050", MODE="0666"
```

**3. Save (`Ctrl+O`, `Enter`) and exit (`Ctrl+X`)**

**4. Reload rules and reconnect the PAD:**
```bash
sudo udevadm control --reload-rules && sudo udevadm trigger
```

> ✅ This is a one-time setup. The rule persists after system reboots.  
> 💡 After saving the rules, disconnect and reconnect the PAD.  
> 🔁 Remember to press **1+7+9** on the PAD to switch to Linux mode (🔴 3 red flashes = Linux active).

---

## 🚀 What's New (v1.5.5)

### 🛠️ Translation Fixes & Code Cleanup
Major update to the Snippet Manager content:
* **38 UI & Content Fixes:** All snippet titles, Go source code strings (`log.Println`, `errors.New`), and code comments have been translated to English or unified into a professional `// EN / PL` format.

### 📝 Snippet Editor
You can now extend the built-in library with your own code patterns:
* **My Snippets Category:** A new dedicated section at the bottom of the sidebar for your custom collection.
* **Integrated Editor:** Use the **+ Add Snippet** button to open a sleek overlay form (Title, Description, Tags, and Go Code with syntax-friendly styling).
* **Persistent Storage:** Custom snippets are saved to global storage and persist between sessions.
* **Management:** Full support for adding and deleting your own snippets directly from the UI.

---

## 🚀 What's New (v1.5.0)

### 🧰 Snippet Manager
I have added a built-in Snippet Manager that stores frequently used code patterns for quick access. You can easily copy or insert them directly into your active editor with a single click.

Features:

Webview Category Panel: A dedicated sidebar/panel to browse snippets by category, including Goroutines, Error Handling, Context, Mutexes, Channels, HTTP, and Struct Patterns.
One-Click Insertion: Use the "Insert" button to instantly paste any snippet into your current cursor position in the editor.

### 🧰 Go Generate Runners 
The Go Generate Runner is a dedicated tool designed to automate and simplify the execution of code generation tasks within your Go projects. Instead of manually running commands from the terminal, you can manage your entire generation workflow through a visual interface.

Features:

Workspace Scanning: Automatically finds all //go:generate directives across your .go files.
Directives List: Displays identified tasks with their corresponding filename and line number.
Execution Control: Run individual directives or execute all of them at once.
Real-time Output: Monitor the generation process with a live output feed.


---

## 🚀 What's New (v1.1.0)

### 🧰 SunGo Tools View
New panel in the Explorer sidebar with a clickable list of all SunGo tools – accessible from anywhere in VS Code without switching to the project tree:
- Binary Analyzer, Go Vet, Build Diff, Dependencies, Profiler, Code Metrics, Project Notes, Header Generator

### ⚙️ Settings grouped into sections
`Ctrl+,` now shows SunGo settings split into 4 dedicated expandable sections:
**SunGo – Build** · **SunGo – File Header** · **SunGo – Code Metrics** · **SunGo – Security**

### 🎨 UI improvements
- Active project shows green `$(folder-active)` icon (color now works correctly)
- Inline icons in Tree View reduced from 7 to 3 (Analyzer, Vet, Build Diff) – rest available in Tools View
- Dashboard header icons unified – Header Generator, Notes and Metrics use Codicons matching PAD/Settings style

---

## 🚀 What's New (v1.0.0)

### 📝 Project Notes
New `$(notebook)` icon in the Tree View and Dashboard – opens `.vscode/sungo_notes.md` in the editor. Created automatically with a TODO / Ideas / Notes template on first use.

### 📊 Code Metrics & Refactoring Hints
New `$(dashboard)` panel – recursively scans all `.go` files (skips `vendor/`, `bin/`, `.git/`):
- **Overview:** file count, function count, total LOC, Code Health indicator 🟢🟡🔴
- **Refactoring Hints:** functions too long, too many parameters, deep nesting, missing godoc, large files – each hint is clickable and navigates directly to the code
- **Functions table** sorted by size with visual bars – click to jump to definition
- **Files table** – click to open file
- Thresholds configurable in `Ctrl+,`: `sungo.metrics.maxFuncLines`, `maxFileLines`, `maxParams`, `maxNesting`

### 🏁 v1.0.0 Milestone
SunGo now covers the full Go development lifecycle – from project creation to profiling, cross-compilation and code quality analysis.

---

## 🚀 What's New (v0.9.0)

### 📝 File Header Generator
New panel accessible via `SunGo: Header Generator` command (Command Palette or right-click on `.go` file):
- **5 built-in styles:** Fancy Box `╔═╗`, Box `/****/`, Block `/* */`, Line `//`, Minimal – plus Custom and None
- **Live preview** – updates instantly as you change style or author settings
- **Insert button** – inserts the header at line 0 of the active editor
- **Auto-insert** – enable `sungo.header.autoInsert` to add headers to every new `.go` file automatically
- **Project Creator integration** – choose header style when creating a new project; applied to `main.go` on creation
- **Custom template** with clickable tokens: `{project}` `{file}` `{author}` `{team}` `{website}` `{forum}` `{github}` `{version}` `{license}` `{date}` `{year}`
- **GitHub auto-detected** from `go.mod` – no per-project configuration needed
- Global settings in `Ctrl+,`: author, team, website, forum, license, style, auto-insert
- Editor accessible also via the `📝` icon in the Dashboard header (next to the Gopher)

---

## 🚀 What's New (v0.8.0)

### 🔬 SunGo Profiler (pprof)
New panel accessible via the `$(pulse)` icon in the Project Tree View (active project only):
- **Top 20 functions** table with visual percentage bars – CPU time or memory allocation
- **Flame Graph** SVG with zoom (scroll), pan (drag) and **Open in Browser** button
- Auto-detects `cpu.prof` / `mem.prof` in project root
- Welcome screen with ready-to-paste **CPU and Memory snippets** (Copy button)
- Load any `.prof` file via file picker
- Graphviz detection with platform-specific install hint if missing

> 📖 **[Profiler Setup & Usage Guide](https://github.com/SunDUINO/SunGo-Project_Manager-relase/blob/main/README_pprof.md)** – instrumentation snippets, Graphviz installation (Windows/Linux/macOS), PATH setup, flame graph usage and common issues

### 🔧 Terminal Fix
SunGo Terminal no longer shows the yellow warning triangle – added `strictEnv: false` and `env` passthrough to `createTerminal()`.

---

## 🚀 What's New (v0.7.0)

### 🌍 Cross-Compilation Support
SunGo now supports building binaries for any platform directly from Settings (`Ctrl+,`):
- **`sungo.build.targetOS`** – choose target OS: `auto` (current system), `windows`, `linux`, `darwin`
- **`sungo.build.targetArch`** – choose architecture: `amd64`, `arm64`, `arm`
- Cross-compiled binaries land in `bin/cross/` with the platform suffix in the name (e.g. `MyApp_linux_amd64`)
- `CGO_ENABLED=0` is set automatically for cross-builds
- ⚠️ If CGO is detected in your project, SunGo **blocks the build** and shows a platform-specific message with required toolchain info

> 📖 **[CGO Cross-Compilation Setup Guide](https://github.com/SunDUINO/SunGo-Project_Manager-relase/blob/main/README_crosscompile.md)** – toolchains for all platform combinations (Linux→Windows, Linux→macOS, Windows→Linux and more)

### 📊 Build Diff & Timeline
New panel accessible via the `$(git-compare)` icon in the Project Tree View:
- Select any two builds from history and compare them side by side
- Tables: **Grown / Shrunk / Added / Removed** symbols (top 20 each)
- Summary bar: size A, size B, delta, build time A & B
- Scrollable **Build Timeline** showing the last 10 builds with timestamps, size delta and build time
- UI unified with the Binary Analyzer style (dark theme, gold/green accents)

---

## 🚀 What's New (v0.6.0)

* **Dependency Viewer:** A full dedicated panel for browsing and managing your project's Go modules — version info, update detection, and one-click upgrades.
* **Binary Size Alert:** Set a size threshold in settings — SunGo will warn you and flash the PAD purple when your binary grows too large.
* **Go Vet Integration:** Run a deep static analysis of your entire project with one click. The PAD gives you instant physical feedback on the result.
* **PAD Flash API:** New internal flash mechanism for physical alert signals — color pulses that restore automatically without changing your key scheme.

---

### 📦 Dependency Viewer

SunGo now includes a dedicated **Dependency Viewer** panel — accessible via the `$(library)` icon next to your project in the Tree View.

The panel runs `go list -u -m -json all` to fetch full dependency info including available updates:

| Column  | Description |
|---------|-------------|
| **Module** | Full module path (short name + full path below) |
| **Version** | Currently installed version |
| **Update** | 🟢 current &nbsp;·&nbsp; 🔴 `vX.Y.Z` when newer version available |
| **Type** | `direct` / `indirect` / `main module` |
| **Actions** | 📖 open on pkg.go.dev &nbsp;·&nbsp; ⬆️ update this package |

The **Update All** button runs `go get -u ./...` + `go mod tidy` for the entire dependency tree at once.

> 💡 **Tip:** The first load may take a moment — Go contacts the module registry to check for newer versions.

---

### 🔔 Binary Size Alert

Set a maximum binary size threshold in Extension Settings (`ctrl+,`):

```
sungo.build.maxSizeMB = 10
```

After every successful build, SunGo compares the output size against your threshold. If exceeded:
* A warning notification appears in VS Code.
* The SunGO PAD **flashes purple 3 times** as a physical alert — no need to look at the screen.

Set to `0` (default) to disable the alert entirely.

---

### 🐛 Go Vet Integration

`go vet` catches bugs that the compiler allows but are almost certainly wrong — wrong format strings, deferred calls in loops, mutex copies, and more.

**How to run:**
* **Right-click** on `main.go` in the Explorer → `SunGo: Go Vet`
* **Click** the `$(bug)` icon next to your project in the SunGo Tree View

Results appear in the **`SunGo: Go Vet`** Output Channel.

The SunGO PAD provides instant physical feedback:
* 🟢 **3 green flashes** – no issues found
* 🔴 **3 red flashes** – issues detected, check the Output Channel

## 🚀 What's New (v0.5.3) 

The latest version of SunGo introduces advanced diagnostic tools for executable files, giving you full control over the size and structure of your Go applications.

### 📊 Advanced Binary Analyzer
You not only see the file size, but also what it consists of. The analyzer panel provides:
* **Component Analysis:** Check the percentage share of Go Runtime, standard libraries, and external C dependencies.
* **Your Code Breakdown:** A detailed view of every function and variable in your `main` package, sorted by size with byte-accurate measurements and visual bars.
* **Inverted Parser Engine:** The symbol engine recognizes Go code explicitly — any unknown symbol is automatically classified as `External C / Libs`, making it compatible with any library out of the box (Raylib, Fyne, Ebitengine, SDL…).
* **Trend History:** Visualization of size changes on line charts after each build.
* **One-Click Access:** Click the size indicator on the Status Bar to open both the `/bin` folder and the Analyzer panel simultaneously.

![SunGo Binary Analyzer](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/34b2958/1f69c83/b9b5df7eab1691a0611509040627dfea.gif)

### 🛠️ Optimization Control (Linker Flags)
Easy access to binary optimization settings. Now, with a single toggle in settings (`ctrl+,`), you can:
* **Minimize the binary:** by enabling `-s -w` (strip) flags to remove symbol tables and debugging information.
* **Full Diagnostics:** Disable optimization to get full insight into symbols and a precise analysis of the binary file's composition.

## 🛠 Key Features
- **Automated Project Structure** – Create `src/` folder and `main.go` with a single click.
- **Debugger Configuration** – Automatically generates a ready-to-use `launch.json` — no manual path editing required.
- **Binary Headers** – Each new `main.go` gets a unique project name encoded in binary format as a header.
- **Binary Optimization** – Automatic `-s -w` linker flags for smaller, faster executables.
- **Localization** – Full support for Polish and English interfaces.

## 🖥️ Platform Support

| Component                        | Windows | Linux |
|----------------------------------|---------|-------|
| SunGo VS Code Extension          |   ✅    |  ✅  |
| Binary Size Tracking & Analytics |   ✅    |  ✅  |
| SunGO PAD (HID RAW)              |   ✅    |  ✅  |

> The extension works fully on both **Windows** and **Linux**. The physical SunGO PAD communicates via HID RAW and is supported on both platforms as well. The PAD is entirely optional — the extension is 100% functional without it.

## 👤 About the Author

**Andrzej Gromczyński (SunRiver)** – electronics enthusiast, embedded systems programmer, and technical author at **Helion** Publishing. Active community member and forum at [forum.lothar-team.pl](https://forum.lothar-team.pl/).

### 📚 Books (Helion)

🔗 [All titles on Helion.pl](https://helion.pl/autorzy/andrzej-gromczynski)

## ⚖️ License
Proprietary (Freeware) – Free for both private and commercial use in compiled form.  
Copying, modifying, decompiling, or redistributing without the author's written consent is prohibited.  
See the LICENSE file for full terms.

---


---

# [PL] SunGo Project Manager

**SunGo Project Manager** to proste i skuteczne narzędzie do zarządzania projektami w języku Go, stworzone z myślą o wygodzie i porządku w kodzie. 

> 💡 **Master Tips** Wtyczka SunGo działa w 100% samodzielnie. Fizyczny kontroler SunGO PAD to opcjonalny dodatek dla entuzjastów elektroniki i tactile feedbacku.

### Filozofia Projektu
> **"SunGo powstało, aby wprowadzić porządek do procesu tworzenia aplikacji w języku Go. Wierzę, że przejrzysta struktura projektu i zoptymalizowane pliki binarne są fundamentem profesjonalnego oprogramowania."**

#### ⚡ Wygoda w stylu JetBrains
SunGo dąży do przeniesienia komfortu znanego z płatnych środowisk (IDE) do lekkiego edytora VS Code:
* **Debugowanie bez konfiguracji:** Automatycznie generuje i aktualizuje plik `launch.json`. Zapomnij o ręcznym wpisywaniu ścieżek, by uruchomić debugger.
* **Inteligentny kontekst:** Wszystkie akcje specyficzne dla Go (Build, Run, Test, Sign) są tam, gdzie ich potrzebujesz — na pasku statusu, nad edytorem i w menu pod prawym przyciskiem.
* **Automatyczne porządki:** Od `go mod tidy` po czyszczenie folderu `/bin`, SunGo zajmuje się powtarzalnymi zadaniami, pozwalając Ci skupić się na samym kodzie.
- **Analiza Rozmiaru Binarki** – Inteligentny licznik na pasku stanu, który porównuje wagę Twojego pliku `.exe` z poprzednim buildem. Od razu widzisz efekty optymalizacji.

---

### 🌟 Dlaczego SunGo? (Gopher Rules)
* **Binarna Tożsamość:** Każdy plik `main.go` otrzymuje unikalny nagłówek projektu zakodowany binarnie. Twój kod, Twój cyfrowy podpis.
* **Wydajność Przede Wszystkim:** Automatycznie stosuje flagi linkera `-s -w`, usuwając zbędne dane debugowania – Twoje binarki są do 40% mniejsze.
* **Debugowanie bez Konfiguracji:** Automatycznie generuje `launch.json`. Zapomnij o ręcznym ustawianiu ścieżek, by zacząć debugować.
* **Gotowość do Testów (TDD):** Każdy projekt startuje z wygenerowanym plikiem `main_test.go`. Nie tylko pisz kod – od razu go sprawdzaj.

![Wersja Marketplace](https://img.shields.io/visual-studio-marketplace/v/SunRiver-LotharTeaM.sungo-project-manager?label=wersja&color=orange)

## 📖 Spis treści
* [PL: Wymagania i Instalacja](#wymagania-i-instalacja)
* [PL: SunGO PAD – Visual Status Feedback](#sungo-pad-visual-status-feedback-optional-hardware)
* [PL: Linux – Konfiguracja udev](#linux-konfiguracja-sungo-pad-reguły-udev)
* [PL: Co nowego (v1.5.0)](#co-nowego-v110)
* [PL: Co nowego (v1.0.0)](#co-nowego-v100)
* [PL: Co nowego (v0.9.0)](#co-nowego-v090)
* [PL: Kluczowe Funkcje](#kluczowe-funkcje)

---

## 📦 Wymagania i Instalacja

Przed zainstalowaniem wtyczki SunGo Project Manager upewnij się, że poniższe narzędzia są dostępne w Twoim systemie. Wszystkie są wymagane do pełnej funkcjonalności (budowanie, linting, biblioteki GUI, komunikacja z PAD).

### 1. Visual Studio Code
Wtyczka działa wewnątrz VS Code.  
🔗 [Pobierz VS Code](https://code.visualstudio.com/)

### 2. Oficjalna wtyczka Go dla VS Code (gopls)
Zapewnia obsługę serwera językowego, IntelliSense oraz integrację z `gopls`. Zainstaluj bezpośrednio z VS Code Marketplace.  
🔗 [Wtyczka Go dla VS Code](https://marketplace.visualstudio.com/items?itemName=golang.go)

### 3. Kompilator Go
Wymagany do budowania i uruchamiania projektów.  
🔗 [Pobierz Go](https://go.dev/dl/)

### 4. Kompilator GCC – MSYS2  MinGW-w64 (Windows) / Native GCC (Linux)
Wymagany do budowania natywnych bibliotek GUI takich jak **Fyne** i **Raylib**, które korzystają z CGO.  
* **Windows (Automatycznie):** - Nie musisz już instalować GCC ręcznie. Jeśli SunGo wykryje jego brak, po prostu kliknij **"Zainstaluj GCC (MSYS2)"** w Dashboardzie (HOME). Rozszerzenie pobierze i skonfiguruje środowisko za Ciebie.
* **Linux (Ręcznie):** Zainstaluj zestaw narzędzi GCC za pomocą menedżera pakietów:
    * *Ubuntu/Debian:* `sudo apt update && sudo apt install build-essential`
    * *Arch Linux:* `sudo pacman -S base-devel`
    * *Fedora:* `sudo dnf groupinstall "Development Tools"`

### 5. PowerShell 7 (Core) (Windows)
SunGo korzysta ze skryptów PowerShell do automatyzacji zadań. Wymagana jest wersja 7 (edycja Core).  
🔗 [Pobierz PowerShell 7](https://github.com/PowerShell/PowerShell/releases/latest)

### 6. Git
Wymagany do integracji z kontrolą wersji i zarządzania zależnościami.  
🔗 [Pobierz Git](https://git-scm.com/downloads)

### 7. (Opcjonalnie) Biblioteki GUI dla Go
Jeśli Twój projekt korzysta z interfejsów graficznych, zainstaluj odpowiednią bibliotekę:

| Biblioteka | Zastosowanie | Instalacja |
|---|---|---|
| **Fyne** | Wieloplatformowy toolkit GUI | `go get fyne.io/fyne/v2` |
| **Raylib-go** | Framework do gier i multimediów | `go get github.com/gen2brain/raylib-go/raylib` |

> Obie biblioteki wymagają GCC (krok 4) do kompilacji przez CGO.

### ✅ Szybka lista kontrolna

```
[ ] VS Code zainstalowany
[ ] Oficjalna wtyczka Go (gopls) zainstalowana
[ ] Kompilator Go zainstalowany i dostępny w PATH
[ ] TDM-GCC 64-bit 10.3.0 zainstalowany i dostępny w PATH
[ ] PowerShell 7 (Core) zainstalowany
[ ] Git zainstalowany
[ ] (Opcjonalnie) Fyne / Raylib-go dla projektów GUI
```

### Instalacja SunGo Project Manager
Wyszukaj **„SunGo Project Manager"** w panelu Rozszerzeń VS Code lub zainstaluj bezpośrednio z Marketplace:  
🔗 [SunGo Project Manager na VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=SunRiver-LotharTeaM.sungo-project-manager)

---

## 🎛 SunGO PAD – Visual Status Feedback

<p align="center">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/0facbd3/efd9d1f/a959bed88632c98c1ec184462e2b05a6.jpg" width="240" alt="Idle State">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/419a0c0/78fd922/4264b947ca652cadcdb72a558fb1f0d4.jpg" width="240" alt="RUN State - Green">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/d43865b/3a57d46/e45fbf12ef4d64c0e2d30cfce2db251b.jpg" width="240" alt="Error State - Red">
</p>

Fizyczny **SunGO PAD** zapewnia natychmiastowy feedback wizualny w czasie rzeczywistym poprzez HID RAW. Kolory klawiszy odzwierciedlają aktualny stan procesu (RUN, BUILD, LINTER, ERROR) bez konieczności patrzenia w terminal.

- ⚪ **Idle** – system gotowy do pracy
- 🟢 **Green** – RUN / Build zakończony sukcesem
- 🔴 **Red** – błąd lintera lub kompilacji

### 🔀 Przełączanie systemu (Windows / Linux)
Naciśnij jednocześnie **klawisze 1+7+9** (VS Code + Build + Test) aby przełączyć PAD między trybem Windows a Linux:

| Kombinacja | Efekt | Sygnalizacja |
|---|---|---|
| 1+7+9 | Przełącz na Linux | 🔴 3 czerwone mignięcia |
| 1+7+9 ponownie | Przełącz na Windows | 🔵 3 niebieskie mignięcia |

> Wybrany tryb jest zapisywany trwale w pamięci flash PAD-a i pozostaje po odłączeniu zasilania. Domyślny tryb to Windows.

> **Ważne:** Wtyczka SunGo działa w pełni autonomicznie. Posiadanie fizycznego PAD-a nie jest wymagane, ale znacząco podnosi komfort pracy poprzez fizyczne przyciski sterujące i sygnalizację LED.

### 🔧 Firmware & Build
Szczegółowe instrukcje flashowania oraz informacje o budowie SunGO PAD znajdują się na oficjalnym forum:  
🔗 [https://forum.lothar-team.pl/viewtopic.php?t=1092](https://forum.lothar-team.pl/viewtopic.php?t=1092)

---

## 🐧 Linux – Konfiguracja SunGO PAD (reguły udev)

Na Linuxie dostęp do urządzeń HID RAW wymaga jednorazowej konfiguracji uprawnień. Bez niej pad zostanie wykryty, ale LEDy i komendy nie będą działać.

**1. Otwórz terminal (`Ctrl+Alt+T`) i utwórz plik reguł:**
```bash
sudo nano /etc/udev/rules.d/99-sungo-pad.rules
```

**2. Wpisz następującą linię:**
```
SUBSYSTEM=="hidraw", ATTRS{idVendor}=="cafe", ATTRS{idProduct}=="4050", MODE="0666"
```

**3. Zapisz (`Ctrl+O`, `Enter`) i wyjdź (`Ctrl+X`)**

**4. Przeładuj reguły i podłącz pad ponownie:**
```bash
sudo udevadm control --reload-rules && sudo udevadm trigger
```

> ✅ To jednorazowa konfiguracja. Reguła pozostaje aktywna po restarcie systemu.  
> 💡 Po zapisaniu reguł odłącz i podłącz pad ponownie.  
> 🔁 Pamiętaj nacisnąć **1+7+9** na padzie aby przełączyć w tryb Linux (🔴 3 czerwone mignięcia = tryb Linux aktywny).

---

## 🚀 Co nowego (v1.5.5)

### 🛠️ Poprawki tłumaczeń i czyszczenie kodu
Gruntowna aktualizacja zawartości Snippet Managera:
* **38 poprawek UI i treści:** Wszystkie tytuły snippetów, stringi w kodzie Go (`log.Println`, `errors.New`) oraz komentarze w kodzie zostały przetłumaczone na język angielski lub ujednolicone do formatu `// EN / PL`.

### 📝 Edytor snippetów
Możesz teraz rozszerzać wbudowaną bibliotekę o własne wzorce kodu:
* **Kategoria "My Snippets":** Nowa sekcja na końcu listy w sidebarze przeznaczona na Twoje własne snippety.
* **Zintegrowany edytor:** Przycisk **+ Add Snippet** otwiera nakładkę z formularzem (Tytuł, Opis, Tagi oraz kod Go z czytelnym, zielonym fontem monospace).
* **Trwały zapis:** Własne snippety są zapisywane w globalnej pamięci rozszerzenia i pozostają dostępne między sesjami.
* **Zarządzanie:** Pełna obsługa dodawania i usuwania własnych fragmentów kodu bezpośrednio z interfejsu.

---

## 🚀 Co nowego (v1.5.0)

### 🧰 Snippet Manager 

Dodałem wbudowany moduł Snippet Manager, który przechowuje często używane wzorce kodu, zapewniając do nich błyskawiczny dostęp. Możesz je łatwo kopiować lub wstawiać bezpośrednio do aktywnego edytora za pomocą jednego kliknięcia.

Najważniejsze funkcje:

Panel Webview z kategoriami: Dedykowany panel boczny umożliwiający przeglądanie snippetów według kategorii, takich jak: Goroutines, Error Handling, Context, Mutexes, Channels, HTTP oraz Struct Patterns.

Wstawianie jednym kliknięciem: Użyj przycisku „Insert”, aby natychmiast wkleić wybrany fragment kodu w miejscu, w którym znajduje się kursor w edytorze.

### 🧰 Go Generate Runner
To dedykowane narzędzie stworzone do automatyzacji i uproszczenia zadań związanych z generowaniem kodu w projektach Go. Zamiast ręcznie wpisywać komendy w terminalu, możesz zarządzać całym procesem z poziomu wygodnego interfejsu wizualnego.

Funkcje:

Skanowanie projektu: Automatycznie wyszukuje wszystkie dyrektywy //go:generate w plikach .go.
Lista dyrektyw: Wyświetla znalezione zadania wraz z nazwą pliku i numerem linii.
Kontrola uruchamiania: Pozwala na wywołanie pojedynczej instrukcji lub wszystkich naraz.
Podgląd na żywo: Monitoruje proces generowania, wyświetlając wyniki (output) w czasie rzeczywistym.


---

## 🚀 Co nowego (v1.1.0)

### 🧰 SunGo Tools View
Nowy panel w pasku eksploratora z klikalną listą wszystkich narzędzi SunGo – dostępny z każdego miejsca w VS Code bez przełączania się do drzewa projektów:
- Binary Analyzer, Go Vet, Build Diff, Dependencies, Profiler, Code Metrics, Project Notes, Header Generator

### ⚙️ Ustawienia pogrupowane w sekcje
`Ctrl+,` pokazuje teraz ustawienia SunGo podzielone na 4 dedykowane sekcje:
**SunGo – Build** · **SunGo – File Header** · **SunGo – Code Metrics** · **SunGo – Security**

### 🎨 Poprawki UI
- Aktywny projekt pokazuje zieloną ikonę `$(folder-active)` (kolor działa poprawnie)
- Ikony inline w drzewie projektów zredukowane z 7 do 3 (Analyzer, Vet, Build Diff) – reszta w Tools View
- Ikony w nagłówku Dashboardu ujednolicone – Header Generator, Notes i Metrics używają Codicons zgodnych ze stylem PAD/Settings

---

## 🚀 Co nowego (v1.0.0)

### 📝 Notatki projektu
Nowa ikona `$(notebook)` w drzewie projektów i Dashboardzie – otwiera `.vscode/sungo_notes.md` w edytorze. Tworzony automatycznie z szablonem TODO / Ideas / Notes przy pierwszym użyciu.

### 📊 Metryki kodu i sugestie refaktoringu
Nowy panel `$(dashboard)` – rekurencyjnie skanuje wszystkie pliki `.go` (pomija `vendor/`, `bin/`, `.git/`):
- **Overview:** liczba plików, funkcji, total LOC, wskaźnik zdrowia kodu 🟢🟡🔴
- **Sugestie refaktoringu:** za długie funkcje, za dużo parametrów, głębokie zagnieżdżenie, brak godoc, duże pliki – każda sugestia jest klikalna i przenosi do kodu
- **Tabela funkcji** posortowana wg rozmiaru z paskami – klik przenosi do definicji
- **Tabela plików** – klik otwiera plik
- Progi konfigurowalne w `Ctrl+,`: `sungo.metrics.maxFuncLines`, `maxFileLines`, `maxParams`, `maxNesting`

### 🏁 Milestone v1.0.0
SunGo obejmuje teraz pełny cykl życia projektu Go – od tworzenia, przez profilowanie i cross-compilation, aż po analizę jakości kodu.

---

## 🚀 Co nowego (v0.9.0)

### 📝 Generator nagłówków plików
Nowy panel dostępny przez komendę `SunGo: Header Generator` (paleta komend lub prawy klik na `.go`):
- **5 wbudowanych stylów:** Fancy Box `╔═╗`, Box `/****/`, Block `/* */`, Line `//`, Minimal – plus Custom i None
- **Podgląd live** – aktualizuje się natychmiast przy zmianie stylu lub ustawień autora
- **Przycisk Insert** – wstawia nagłówek w linii 0 aktywnego edytora
- **Auto-insert** – włącz `sungo.header.autoInsert` aby dodawać nagłówki do każdego nowego pliku `.go`
- **Integracja z kreatorem projektów** – wybierz styl nagłówka przy tworzeniu projektu; stosowany do `main.go` przy tworzeniu
- **Własny szablon** z klikalnymi tokenami: `{project}` `{file}` `{author}` `{team}` `{website}` `{forum}` `{github}` `{version}` `{license}` `{date}` `{year}`
- **GitHub wykrywany automatycznie** z `go.mod` – brak konfiguracji per projekt
- Ustawienia globalne w `Ctrl+,`: autor, zespół, strona, forum, licencja, styl, auto-insert
- Edytor dostępny również przez ikonę `📝` w nagłówku Dashboardu (obok Gophera)


---

## 🚀 Co nowego (v0.8.0)

### 🔬 SunGo Profiler (pprof)
Nowy panel dostępny przez ikonę `$(pulse)` w drzewie projektów (tylko aktywny projekt):
- Tabela **Top 20 funkcji** z wizualnymi paskami – czas CPU lub alokacje pamięci
- **Flame Graph** SVG z zoomem (kółko myszy), przesuwaniem (drag) i przyciskiem **Otwórz w przeglądarce**
- Automatyczne wykrywanie `cpu.prof` / `mem.prof` w katalogu projektu
- Ekran powitalny z gotowymi snippetami **CPU i Memory** (przycisk Copy)
- Wczytanie dowolnego pliku `.prof` przez file picker
- Wykrywanie Graphviz z wskazówką instalacji per platforma gdy brak

> 📖 **[Przewodnik instalacji i użytkowania Profilera](https://github.com/SunDUINO/SunGo-Project_Manager-relase/blob/main/README_pprof.md)** – snippety instrumentacji, instalacja Graphviz (Windows/Linux/macOS), konfiguracja PATH, obsługa flame graph i częste problemy

### 🔧 Poprawka terminala
Terminal SunGo nie wyświetla już żółtego trójkąta ostrzegawczego – dodano `strictEnv: false` i przekazywanie `env` do `createTerminal()`.

---

## 🚀 Co nowego (v0.7.0)

### 🌍 Cross-Compilation
SunGo obsługuje teraz budowanie binarek na dowolną platformę z poziomu Ustawień (`Ctrl+,`):
- **`sungo.build.targetOS`** – docelowy system: `auto` (bieżący), `windows`, `linux`, `darwin`
- **`sungo.build.targetArch`** – architektura: `amd64`, `arm64`, `arm`
- Binarka trafia do `bin/cross/` z sufiksem platformy (np. `MyApp_linux_amd64`)
- `CGO_ENABLED=0` ustawiane automatycznie przy cross-buildzie
- ⚠️ Gdy wykryto CGO, SunGo **blokuje build** i wyświetla komunikat z informacją jaki toolchain jest wymagany dla danej kombinacji platform

> 📖 **[Przewodnik konfiguracji CGO Cross-Compilation](https://github.com/SunDUINO/SunGo-Project_Manager-relase/blob/main/README_crosscompile.md)** – toolchainy dla wszystkich kombinacji platform (Linux→Windows, Linux→macOS, Windows→Linux i inne)

### 📊 Build Diff & Timeline
Nowy panel dostępny przez ikonę `$(git-compare)` w drzewie projektów:
- Porównaj dowolne dwa buildy obok siebie
- Tabele: **Większe / Mniejsze / Nowe / Usunięte** symbole (top 20)
- Pasek podsumowania: rozmiar A, B, delta, czas builda A i B
- Przewijana **Historia buildów** – ostatnie 10 z datą, deltą rozmiaru i czasem kompilacji

---

## 🚀 Co nowego (v0.6.0)

* **Przeglądarka Zależności:** Nowy dedykowany panel do przeglądania i zarządzania modułami Go — informacje o wersjach, wykrywanie aktualizacji i aktualizacja jednym kliknięciem.
* **Alert Rozmiaru Binarki:** Ustaw próg rozmiaru w ustawieniach — SunGo powiadomi Cię i zamiga PAD na fioletowo gdy binareka urośnie za bardzo.
* **Integracja Go Vet:** Uruchom głęboką analizę statyczną całego projektu jednym kliknięciem. PAD daje natychmiastowy fizyczny feedback na wyniku.
* **Flash API dla PAD-a:** Nowy wewnętrzny mechanizm pulsowania kolorem — sygnały świetlne które przywracają schemat klawiszy automatycznie po zakończeniu sekwencji.

---

### 📦 Przeglądarka Zależności

SunGo posiada teraz dedykowany panel **Przeglądarki Zależności** — dostępny przez ikonę `$(library)` obok projektu w drzewie projektów.

Panel uruchamia `go list -u -m -json all` aby pobrać pełne informacje o zależnościach wraz z dostępnymi aktualizacjami:

| Kolumna | Opis |
|---------|------|
| **Moduł** | Pełna ścieżka modułu (skrócona nazwa + pełna ścieżka poniżej) |
| **Wersja** | Aktualnie zainstalowana wersja |
| **Aktualizacja** | 🟢 aktualna &nbsp;·&nbsp; 🔴 `vX.Y.Z` gdy dostępna nowsza wersja |
| **Typ** | `direct` / `indirect` / `main module` |
| **Akcje** | 📖 otwórz na pkg.go.dev &nbsp;·&nbsp; ⬆️ aktualizuj ten pakiet |

Przycisk **Update All** uruchamia `go get -u ./...` + `go mod tidy` dla całego drzewa zależności naraz.

> 💡 **Wskazówka:** Pierwsze ładowanie może chwilę potrwać — Go odpytuje rejestr modułów w poszukiwaniu nowszych wersji.

---

### 🔔 Alert Rozmiaru Binarki

Ustaw maksymalny próg rozmiaru binarki w Ustawieniach Rozszerzenia (`ctrl+,`):

```
sungo.build.maxSizeMB = 10
```

Po każdym udanym buildzie SunGo porównuje rozmiar pliku wyjściowego z Twoim progiem. Po przekroczeniu:
* W VS Code pojawia się powiadomienie ostrzegawcze.
* SunGO PAD **trzykrotnie miga na fioletowo** jako fizyczny sygnał alarmowy — bez konieczności patrzenia na ekran.

Ustaw `0` (domyślnie) aby całkowicie wyłączyć alert.

---

### 🐛 Integracja Go Vet

`go vet` wykrywa błędy które kompilator przepuszcza, a które prawie zawsze są pomyłką — nieprawidłowe formatowanie stringów, wywołania `defer` w pętlach, kopiowanie mutexów i wiele więcej.

**Jak uruchomić:**
* **Kliknij prawym przyciskiem** na `main.go` w Eksploratorze → `SunGo: Go Vet`
* **Kliknij** ikonę `$(bug)` obok projektu w drzewie SunGo

Wyniki pojawiają się w kanale wyjściowym **`SunGo: Go Vet`**.

SunGO PAD daje natychmiastowy fizyczny feedback:
* 🟢 **3 zielone mignięcia** – brak problemów
* 🔴 **3 czerwone mignięcia** – wykryto problemy, sprawdź kanał Output


## 🚀 Co nowego (v0.5.3)

Najnowsza wersja SunGo wprowadza zaawansowane narzędzia do diagnostyki plików wykonywalnych, pozwalając Ci na pełną kontrolę nad rozmiarem i strukturą Twoich aplikacji w Go.

### 📊 Zaawansowany Binary Analyzer
Widzisz nie tylko rozmiar pliku, ale też z czego się składa. Panel analizatora oferuje:
* **Analiza składu:** Sprawdź procentowy udział Go Runtime, bibliotek standardowych i zewnętrznych zależności C.
* **Rozkład Twojego Kodu:** Szczegółowy widok każdej funkcji i zmiennej w pakiecie `main`, posortowanych według rozmiaru z dokładnymi wartościami w bajtach i wizualnymi paskami.
* **Odwrócony silnik parsera:** Silnik symboli rozpoznaje kod Go wprost — każdy nieznany symbol jest automatycznie klasyfikowany jako `External C / Libs`, co zapewnia kompatybilność z każdą biblioteką bez ręcznych aktualizacji (Raylib, Fyne, Ebitengine, SDL…).
* **Historia trendów:** Wizualizacja zmian rozmiaru na wykresach liniowych po każdym buildzie.
* **Dostęp jednym kliknięciem:** Kliknij wskaźnik rozmiaru na pasku stanu, aby jednocześnie otworzyć folder `/bin` i panel Analyzera.

![SunGo Binary Analyzer](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/34b2958/1f69c83/b9b5df7eab1691a0611509040627dfea.gif)

### 🛠️ Kontrola Optymalizacji (Linker Flags)
Łatwy dostęp do ustawień optymalizacji binarki. Teraz jednym przełącznikiem w ustawieniach (`ctrl+,`) możesz:
* **Zmniejszyć binarkę:** włączając flagi `-s -w` (strip), aby usunąć tabele symboli i informacje debugowania. 
* **Pełna Diagnostyka:** Wyłącz optymalizację  aby uzyskać pełny wgląd w symbole i precyzyjną analizę składu pliku binarnego

## 🛠 Kluczowe Funkcje
- **Struktura na start** – Automatyczne tworzenie folderu `src/` i pliku `main.go`.
- **Konfiguracja Debuggera** – Generowanie `launch.json` bez ręcznego wpisywania ścieżek.
- **Binarne Nagłówki** – Każdy nowy plik `main.go` otrzymuje nazwę projektu zakodowaną binarnie.
- **Lokalizacja** – Obsługuje języki polski i angielski.

## 🖥️ Obsługiwane platformy

| Komponent                            | Windows | Linux |
|--------------------------------------|---------|-------|
| Wtyczka SunGo dla VS Code            |    ✅   |  ✅  |
| Śledzenie i analiza rozmiaru binarki |    ✅   |  ✅  |
| SunGO PAD (HID RAW)                  |    ✅   |  ✅  |

> Wtyczka działa w pełni zarówno na **Windows**, jak i na **Linux**. Fizyczny SunGO PAD komunikuje się przez HID RAW i jest obsługiwany na obu platformach. PAD jest w pełni opcjonalny — wtyczka działa w 100% bez niego.

## 👤 O autorze

**Andrzej Gromczyński (SunRiver)** – pasjonat elektroniki, programista systemów wbudowanych i autor książek technicznych w wydawnictwie **Helion**. Aktywny uczestnik społeczności prowadzi forum [forum.lothar-team.pl](https://forum.lothar-team.pl/).

### 📚 Książki (Helion)

🔗 [Wszystkie tytuły na Helion.pl](https://helion.pl/autorzy/andrzej-gromczynski)

## ⚖️ Licencja
Proprietary (Freeware) – Bezpłatne do użytku prywatnego i komercyjnego w formie skompilowanej.  
Kopiowanie, modyfikowanie, dekompilowanie lub redystrybucja bez pisemnej zgody autora jest zabroniona.  
Pełne warunki licencji znajdują się w pliku LICENSE.