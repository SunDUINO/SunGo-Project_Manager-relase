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
* [EN: Requirements & Installation](#-requirements--installation)
* [EN: SunGO PAD – Visual Status Feedback](#-sungo-pad--visual-status-feedback)
* [EN: Linux Setup – udev rules](#-linux-setup--sungo-pad-udev-rules)
* [EN: What's New (v0.4.5)](#-whats-new-v045)
* [EN: Key Features](#-key-features)
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

## 🚀 What's New (v0.5.0)

* **Advanced Binary Dashboard:** A brand new, interactive interface for analyzing your Go executables.
* **Live Visual Analytics:** Integrated charts showing binary size trends and internal composition (Runtime vs. User Code).
* **Improved UI Engine:** New responsive grid layout for better data density and visual clarity.

## 🔍 How to use Binary Analyzer?

To open the advanced dashboard and see your build statistics:
1. **Build your project** – use the "Build" button in the Status Bar or Editor Title menu.
2. **Open SunGo Panel** – click the **SunGo "Sun" icon** in the VS Code Activity Bar (on the far left, usually below the Marketplace icon).
3. **Select Analyzer** – in the Project Tree View, click the **Chart icon** next to your active project name.
4. The **SunGo Binary Analyzer** dashboard will appear with your size trends and file composition.

> 💡 **Tip:** While the status bar shows real-time size changes, this dashboard provides deep insights into what exactly makes up your binary.

## 🚀 What's New (v0.4.5)

* **Binary Size Analyzer:** Monitor your `.exe` size in real-time on the Status Bar.
* **Trend Indicators:** Visual cues (▲/▼) and dynamic colors show if your code is getting optimized.
* **Quick Bin Access:** Open your output folder with a single click on the size display.

![Binary Size Analyzer](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/bf1cb9d/c209eae/88625cbbb9040a48ef679d48d91c039b.png)
![Build Process](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/baa1669/3ac74e5/d55423d1dbcc93da75fc94b89d2ea739.png)

> 💡 **Master's Tip:** Want to see the status bar turn **Green**? Enable the `-s -w` flags in SunGo settings to strip debug information and shrink your binary size by up to 30%!

## 🚀 What's New (v0.4.2)

- **Improved GCC Diagnostics** – Fixed a bug where the MSYS2 installation button wouldn't show up if the system reported a specific "No Finding" string. Now, tool detection is more robust and cross-platform friendly.

<p align="center">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/9548a47/44b233a/503c223d8f92e4e111064e80d85dc955.png" width="600" alt="GCC Install Button">
</p>

### 🚀 What's New in v0.4.1 

- **One-Click Windows GCC Setup:** If a C compiler is missing, SunGo now offers automated MSYS2 (MinGW-w64) installation directly from the Dashboard (HOME). Essential for Go projects using CGO 
- **Smarter Debugging:** Enhanced `launch.json` generator with support for precise debugger paths. Just press **F5** and it works!

## 🚀 What's New (v0.4.0)

- **📐 Dashboard Layout Redesign** – the main panel has been restructured into a two-column grid: Active Projects and Security & System are stacked in the left column, while Installed Tools occupies the full right column for better use of screen space.
- **💡 PAD LED Brightness Persistence** – fixed an issue where the PAD would always boot at full brightness regardless of the saved slider value. Brightness is now restored from `globalState` immediately on panel open and on every PAD reconnect — no need to touch the slider.

##  🚀 What's New (v0.3.12)

- **🐹 Gopher Wisdom (Master's Tips)** - unique support system for Go developers! Now, the Gopher is not just a mascot, but your personal mentor.
- **Interactive Icon:** Click the blinking Gopher in the Dashboard header to summon some knowledge.
- **Dedicated Output Channel:** Wisdom is displayed in a specialized `SunGo Gopher` output channel (located next to the Terminal). This ensures the Gopher ASCII Art and tips remain perfectly aligned and readable on all systems, including Linux.
- **Master's Advice:** The knowledge base contains dozens of professional tips covering variable shadowing, mutex pitfalls, `range` loop optimizations, and safe goroutine management.

## 🚀 What's New (v0.3.10)?
- **Path Case-Sensitivity Fix** – Resolved an issue where the Linux configuration guide could not be opened.
- **UI Refinement** – The Linux setup guide is now neatly integrated into the user color schemes panel for better accessibility and a cleaner look.

## 🚀 What's New (v0.3.9)?
- **Linux udev setup guide** – PAD color settings panel now includes a built-in Linux configuration guide with a direct link to README instructions.

## 🚀 What's New (v0.3.8)?
- **Full Linux PAD Support** – SunGO PAD now works natively on Linux via HID RAW.
  - Automatic HID device detection regardless of `usagePage` reported by the Linux kernel
  - HID report byte layout adjusted for Linux `hidraw` driver (no prepended Report ID)
  - Terminal now uses system bash shell (`$SHELL`) on Linux instead of PowerShell
  - Keys 2–9 send `Ctrl+Shift+F13–F20` on Linux to avoid conflicts with system shortcuts
  - Keybindings registered for both platforms: Windows (`Ctrl+Alt+Shift+2–9`) and Linux (`Ctrl+Shift+F13–F20`)

## 🚀 What's New (v0.3.6)?
- **Linux PAD Support** – The SunGO PAD now works on Linux. Press **1+7+9** simultaneously to toggle between Windows and Linux mode. The setting is saved permanently in the PAD firmware flash memory.
  - 🔵 **3 blue flashes** – switched to Windows mode (Win+R → `sungo.cmd`)
  - 🔴 **3 red flashes** – switched to Linux mode (Alt+F2 → `sungo`)

## 🚀 What's New (v0.3.2)?
- **New Demoscene EASTER EGG** – You have to see this one for yourself.

## 🚀 What's New (v0.3.1)?
- **PAD LED Brightness Control** – Added smooth, real-time backlight intensity adjustment for all keys.

## 🚀 What's New (v0.3.0)?

<img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/fe43817/9644700/638df64e49a97fdc8d2fdd0139067b1c.gif" width="240" alt="Keypad color settings">

- **PAD Color Customization** – New Webview interface to assign custom colors to each of the 9 buttons individually.
- **Configuration Memory** – Persistent storage for button color assignments across VS Code sessions using `globalState`.
- **Firmware v2.3 Sync** – Fixed HID key mapping to eliminate the button function offset bug.
- **Registration Stability** – Resolved "command already exists" errors that occurred during extension reload.
- **Clean Boot** – Replaced legacy color defaults with the new professional SunGo palette.

## 🚀 What's New (v0.2.9)?
- **Extended PAD Color System** – Added new action colors (Blue, White, Yellow, Purple) via HID RAW.
- **Real-Time Action Feedback** – Physical PAD reflects live states: format, build, run, and signing.
- **HID RAW Stability** – Improved device detection and automatic reinitialization after disconnects.
- **Per-Key State Preservation** – Each button independently retains its color state.
- **Intelligent PAD Command Queue** – Throttling and buffering for reliable HID communication.
- **Enhanced Firmware Integration** – Full support for new PAD commands: `B`, `W`, `Y`, `P`, `C`, `R`, `E`, and `O`.

---

## 📂 Version Archive

<details>
<summary>Expand previous changes (v0.2.8 – v0.0.9)</summary>

### 🚀 v0.2.8
- **SunGO PAD Support** – Color integration for RUN, BUILD, and linter error states.
- **Refactoring** – KeyPAD and Security logic separated into dedicated source files.

### 🚀 v0.2.6
- **SunGo Dedicated Pad Support** – Full integration with the custom 9-key mechanical macro pad. Control building, running, and signing processes with physical hardware.
- **Advanced Console Control** – New `Hide Console Window` option via `-H=windowsgui` flag.

### 🚀 v0.2.5
- **Advanced Test Engine** – Brand new module integrating `go test` with a graphical UI.
- **Automated Test Generation** – Generates `main_test.go` for every new project automatically.
- **SunRiver Cow Says (ASCII Art)** – Notification system triggered on successful test runs.

### 🚀 v0.1.5 (Security Suite)
- **Code Signing (Sign)** – Digitally sign your binaries immediately after compilation.
- **File Unlocking (Unlock)** – Remove permission flags that prevent executables from running.
</details>

---

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
* [PL: Wymagania i Instalacja](#-wymagania-i-instalacja)
* [PL: SunGO PAD – Visual Status Feedback](#-sungo-pad--visual-status-feedback-1)
* [PL: Linux – Konfiguracja udev](#-linux--konfiguracja-sungo-pad-reguły-udev)
* [PL: Co nowego (v0.4.5)](#-co-nowego-v045)
* [PL: Kluczowe Funkcje](#-kluczowe-funkcje)

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

## 🚀 Co nowego (v0.5.0)

* **Zaawansowany Dashboard Binarki:** Zupełnie nowy, interaktywny interfejs do analizy Twoich plików wykonywalnych Go.
* **Wizualna Analityka Live:** Zintegrowane wykresy pokazujące trendy zmian rozmiaru oraz skład wewnętrzny binarki (Runtime vs. Kod Użytkownika).
* **Nowoczesny Layout:** Nowy układ siatki (Grid), który zapewnia lepszą przejrzystość danych i stabilność wykresów przy zmianie rozmiaru okna.

## 🔍 Jak korzystać z Analizatora Binarek?

Aby otworzyć zaawansowany panel i sprawdzić statystyki swojego buildu:
1. **Zbuduj projekt** – użyj przycisku "Build" na pasku stanu lub w menu nad edytorem.
2. **Otwórz panel SunGo** – kliknij **ikonę „słoneczka” SunGo** na pasku bocznym VS Code (po lewej stronie, zazwyczaj pod ikoną Marketplace).
3. **Uruchom Analizator** – w widoku drzewa projektów kliknij **ikonę wykresu** obok nazwy swojego projektu.
4. Otworzy się panel **SunGo Binary Analyzer**, prezentujący trendy zmian i skład pliku.

> 💡 **Porada:** Wskaźnik na pasku stanu informuje o zmianach na bieżąco, natomiast ten dashboard pozwala dokładnie zrozumieć, z czego wynika końcowy rozmiar Twojej binarki. 

## 🚀 Co nowego (v0.4.5)

* **Analiza rozmiaru binarki:** Śledzenie wagi pliku wykonywalnego w czasie rzeczywistym na pasku stanu.
* **Wskaźniki trendu:** Wizualne symbole (▲/▼) i dynamiczne kolory informujące o skutkach zmian w kodzie.
* **Szybki dostęp do folderu Bin:** Otwieranie folderu wynikowego jednym kliknięciem w licznik rozmiaru.

![Analiza rozmiaru](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/bf1cb9d/c209eae/88625cbbb9040a48ef679d48d91c039b.png)
![Proces kompilacji](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/baa1669/3ac74e5/d55423d1dbcc93da75fc94b89d2ea739.png)

> 💡 **Master's Tip:** Chcesz zobaczyć zielony kolor na pasku stanu? Włącz flagi `-s -w` w ustawieniach SunGo, aby usunąć informacje debugowania i zmniejszyć rozmiar binarki nawet o 30%!

## 🚀 Co nowego (v0.4.2)?

- **Ulepszona diagnostyka GCC** – Naprawiono błąd, przez który przycisk instalacji MSYS2 nie pojawiał się przy specyficznym komunikacie statusu "No Finding". Teraz wykrywanie narzędzi jest znacznie skuteczniejsze i odporne na różnice w zwracanych ciągach znaków.

<p align="center">
  <img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/9548a47/44b233a/503c223d8f92e4e111064e80d85dc955.png" width="600" alt="Przycisk instalacji GCC">
</p>

### 🚀 Co nowego w v0.4.1

- **Instalacja GCC jednym kliknięciem:** Jeśli brakuje kompilatora C, SunGo oferuje teraz automatyczną instalację środowiska MSYS2 (MinGW-w64) wprost z Dashboardu. Niezbędne dla projektów wykorzystujących CGO.
- **Inteligentniejszy Debugging:** Ulepszony generator `launch.json` ze wsparciem dla precyzyjnych ścieżek debuggera. Po prostu naciśnij **F5** i gotowe!

## 🚀 Co nowego (v0.4.0)?

- **📐 Nowy układ Dashboardu** – główny panel został przeprojektowany na siatkę dwukolumnową: Active Projects i Security & System ułożone są w lewej kolumnie, a Installed Tools zajmuje całą prawą kolumnę, lepiej wykorzystując przestrzeń ekranu.
- **💡 Trwała jasność diod PAD** – naprawiono problem, w którym PAD zawsze startował z pełną jasnością niezależnie od zapisanej wartości suwaka. Jasność jest teraz przywracana z `globalState` natychmiast po otwarciu panelu i przy każdym ponownym podłączeniu PAD-a.

## 🚀 Co nowego (v0.3.12)?
- **🐹 Gopher Wisdom (Mądrości Gophera)** – unikalny system wsparcia dla programistów Go! Teraz Gopher to nie tylko maskotka, ale Twój osobisty mentor.
- **Interaktywna Ikona:** Kliknij mrugającego Gophera w nagłówku Dashboardu, aby przywołać nową poradę.
- **Dedykowany Kanał Output:** Mądrości wyświetlane są w specjalnym kanale wyjściowym `SunGo Gopher` (widocznym obok Terminala). Dzięki temu ASCII Art Gophera i jego rady są zawsze czytelne i poprawnie sformatowane, także w systemach Linux.
- **Rady Mastera:** Baza wiedzy zawiera porady dotyczących m.in. *shadowingu* zmiennych, pułapek w *mutexach*, optymalizacji pętli `range` oraz bezpiecznej pracy z goroutines.

## 🚀 Co nowego (v0.3.10)?
- **Poprawka wielkości liter w ścieżkach** – Rozwiązano problem, przez który instrukcja konfiguracji nie otwierała się na systemach Linux.
- **Ulepszony interfejs** – Instrukcja konfiguracji udev została zintegrowana z panelem schematów użytkownika, co zapewnia lepszy dostęp i czystszy wygląd panelu.

## 🚀 Co nowego (v0.3.9)?
- **Instrukcja konfiguracji udev dla Linuxa** – Panel ustawień kolorów pada zawiera teraz wbudowaną instrukcję konfiguracji Linuxa z bezpośrednim odnośnikiem do README.

## 🚀 Co nowego (v0.3.8)?
- **Pełna obsługa PAD na Linuxie** – SunGO PAD działa teraz natywnie na Linuxie przez HID RAW.
  - Automatyczne wykrywanie urządzenia HID niezależnie od `usagePage` zwracanego przez jądro Linuxa
  - Poprawiony układ bajtów raportu HID dla sterownika `hidraw` (bez prepended Report ID)
  - Terminal używa systemowego shella bash (`$SHELL`) na Linuxie zamiast PowerShell
  - Klawisze 2–9 wysyłają `Ctrl+Shift+F13–F20` na Linuxie, eliminując konflikty z systemowymi skrótami
  - Keybindings zarejestrowane dla obu platform: Windows (`Ctrl+Alt+Shift+2–9`) i Linux (`Ctrl+Shift+F13–F20`)

## 🚀 Co nowego (v0.3.6)?
- **Obsługa PAD na Linuxie** – SunGO PAD działa teraz również na Linuxie. Naciśnij jednocześnie **1+7+9** aby przełączyć między trybem Windows a Linux. Ustawienie jest zapisywane trwale w pamięci flash PAD-a.
  - 🔵 **3 niebieskie mignięcia** – przełączono na tryb Windows (Win+R → `sungo.cmd`)
  - 🔴 **3 czerwone mignięcia** – przełączono na tryb Linux (Alt+F2 → `sungo`)

## 🚀 Co nowego (v0.3.5)?
- **Obsługa MacroPAD na Linuxie** – SunGO MacroPAD działa w pełni teraz również na Linuxie. Naciśnij jednocześnie **1+7+9** aby przełączyć między trybem Windows a Linux. Ustawienie jest zapisywane trwale w pamięci flash PAD-a.
  - 🔵 **3 niebieskie mignięcia** – przełączono na tryb Windows (Win+R → `sungo.cmd`)
  - 🔴 **3 czerwone mignięcia** – przełączono na tryb Linux (Alt+F2 → `sungo`)

## 🚀 Co nowego (v0.3.2)?
- **Nowy Demoscenowy EASTER EGG** – Musicie to zobaczyć!

## 🚀 Co nowego (v0.3.1)?
- **Kontrola jasności diod PAD** – Teraz dostępna jest płynna regulacja jasności podświetlenia klawiszy.

## 🚀 Co nowego (v0.3.0)?

<img src="https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/d4b22ef/07e1369/563af8d8fd7d213180ef2dbfcbb5b0f5.png" width="240" alt="Keypad color settings">

- **Personalizacja kolorów PAD** – Nowy interfejs Webview umożliwiający przypisanie własnych kolorów do każdego z 9 przycisków.
- **Pamięć konfiguracji** – Automatyczne zapisywanie i odtwarzanie kolorów przycisków po restarcie VS Code (`globalState`).
- **Synchronizacja z Firmware v2.3** – Poprawione mapowanie klawiszy HID, eliminujące przesunięcie funkcji przycisków.
- **Stabilność rejestracji** – Rozwiązano problem duplikacji komend przy przeładowywaniu rozszerzenia.
- **Optymalizacja startu** – Usunięcie starych wartości domyślnych kolorów na rzecz nowej palety SunGo.

## 🚀 Co nowego (v0.2.9)?
- **Rozszerzony System Kolorów PAD** – Nowe komendy kolorów (Blue, White, Yellow, Purple) przez HID RAW.
- **Kolory Akcji w czasie rzeczywistym** – Fizyczny PAD odzwierciedla stan (format, build, run, signing).
- **Stabilność HID-RAW** – Ulepszony mechanizm wykrywania urządzenia i ponownej inicjalizacji.
- **Inteligentna kolejka komend** – Throttling i buforowanie komend dla stabilnej transmisji HID.
- **Lepsza integracja z firmware** – Obsługa nowych komend: `B`, `W`, `Y`, `P`, `C`, `R`, `E`, `O`.

---

## 📂 Archiwum wersji

<details>
<summary>Rozwiń poprzednie zmiany (v0.2.8 - v0.0.9)</summary>

### 🚀 v0.2.8
- **SunGO PAD Support** – Integracja kolorów dla RUN, BUILD i błędów lintera.
- **Refaktoryzacja** – Obsługa KeyPADA i Security w osobnych plikach.

### 🚀 v0.2.6
- **SunGo Dedicated Pad Support** – Pełna integracja z 9-przyciskową klawiaturą mechaniczną.
- **Zaawansowana Kontrola Konsoli** – Opcja `Hide Console Window` (`-H=windowsgui`).

### 🚀 v0.2.5
- **SunGo Test Engine** – Nowy moduł integrujący `go test` z GUI.
- **SunRiver Cow says (ASCII Art)** – System powiadomień po zdanym teście.

### 🚀 v0.1.5 (Security Suite)
- **Podpisywanie Cyfrowe (Sign)** – Podpisywanie binarek bezpośrednio po kompilacji.
- **Naprawa uprawnień (Unlock)** – Automatyczne usuwanie blokad systemowych.
</details>

---

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
