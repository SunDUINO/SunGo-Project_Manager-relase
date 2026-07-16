# 🚀 SunGo Project Manager

### 🌐 Language / Język
* **[EN]** English description is available below.
* **[PL]** Opis w języku polskim znajduje się poniżej.

---

### 📝 Release Notes & Documentation

> 💡 **[EN]** Minor updates, hotfixes, and comprehensive technical adjustments are documented exclusively in the `changelog.md` file.
> 💡 **[PL]** Drobne zmiany, poprawki (hotfixy) oraz szczegółowe modyfikacje techniczne są rejestrowane wyłącznie w pliku `changelog.md`.

---

### 📚 Resources / Zasoby

* 📖 **[Wiki & Documentation]** [SunGO Macro PAD II - Wiki Docs](https://github.com/SunDUINO/SunGo-Project_Manager-relase/wiki)

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
* [EN: What's New (v2.7.0) - Git Template Browser Optimization](#-whats-new-v270--git-template-browser-optimization)
* [EN: What's New (v2.6.2) – Smart Device Detection & No-Device Panel](#whats-new-v262--smart-device-detection--no-device-panel)
* [EN: What's New (v2.6.0) – Peripheral Customization & Core Persistence](#whats-new-v260-–-peripheral-customization--core-persistence)
* [EN: What's New (v2.5.0) – Advanced Hardware Control & Localization Engine](#whats-new-v250-–-advanced-hardware-control--localization-engine)
* [EN: What's New (v2.4.5) – Rotary Encoders Configuration](#whats-new-v245-–-rotary-encoders-configuration)
* [EN: What's New (v2.4.3) – Automated Firmware Updates & OTA](#whats-new-v243--automated-firmware-updates--ota)
* [EN: What's New (v2.4.0) – SunGO PAD II Customization](#-whats-new-v240--sungo-pad-ii-customization--key-mapping)
* [EN: What's New (v2.3.8) – SunGO PAD v2 & Adaptive UI](#-whats-new-v238--sungo-pad-v2--adaptive-ui)
* [EN: What's New (v2.3.0) – Enhanced Code Insights](#whats-new-v230--enhanced-code-insights)
* [EN: What's New (v2.1.0) – Code Review Panel](#whats-new-v210-–-code-review-panel)
* [EN: What's New (v2.0.0) – Github Templates](#whats-new-v200-–-github-templates)
* [EN: What's New (v1.9.1) – Favorites & Go Doc Viewer](#whats-new-v191--favorite-projects--go-doc-viewer)
* [EN: What's New (v1.8.3) – Gopher Assistant](#whats-new-v183--gopher-assistant)
* [EN: Key Features](#key-features)
* [EN: SunGo Project Manager](#en-sungo-project-manager)




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
// SunGO MacroPAD v1
SUBSYSTEM=="hidraw", ATTRS{idVendor}=="cafe", ATTRS{idProduct}=="4050", MODE="0666"
// SunGO MacroPAD v2 
SUBSYSTEM=="hidraw", ATTRS{idVendor}=="cafe", ATTRS{idProduct}=="5050", MODE="0666"
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

### 🚀 What's New (v2.7.0) – Git Template Browser Optimization

* **Guaranteed Output Logs:** Resolved a critical bug where the extension output console would freeze right after creating the project structure. Log rendering is now fully decoupled from filesystem cleanup operations, ensuring successful compilation of tracking data and clear feedback for `go mod init`.
* **Enhanced Import Reliability:** Improved asynchronous error handling during GitHub template cloning to provide graceful fallbacks and precise status synchronization across the SunGo project manager panels.

---

# What's New (v2.6.2) – Smart Device Detection & No-Device Panel

The `v2.6.2` update hardens the hardware detection pipeline for the **SunGO MacroPAD** family and eliminates a long-standing UX issue where opening the settings panel without a connected device would silently open the V1 configuration view.

* **No-Device Panel:** When no SunGO MacroPAD is detected at startup, the extension now opens a dedicated informational panel instead of silently falling back to the V1 settings view. The panel provides step-by-step connection guidance and a one-click re-detection button — no need to restart VS Code.
* **Dual-Signal Version Detection:** Hardware identification now cross-checks both the USB **Product ID** and the device **serial number** (`SR-2026-4050` → V1, `SR-2026-5050` → V2), preventing misidentification on systems where the HID descriptor is reported differently across operating systems.
* **Three-Way Settings Routing:** The `openPadSettings` command now branches across three distinct paths — `NONE` (no device), `V1` (MacroPAD I), and `V2` (MacroPAD II) — replacing the previous two-way fallback that treated a missing device as a V1 unit.
* **Full Bilingual NLS Coverage:** All new UI strings in the no-device panel are localized through the native NLS key system across both English and Polish language packs (`pad.nodevice`).

### 🔌 No-Device Panel — Feature Overview

| Feature | Description |
| :--- | :--- |
| **Connection hints** | Three actionable steps guiding the user to verify cable, LED state, and USB reconnection |
| **Re-detect button** | Disposes the current panel and re-invokes `openPadSettings` without restarting the editor |
| **Linux notice** | Displays an additional udev permission reminder on Linux systems |
| **README shortcut** | Direct link to the setup documentation from within the panel |

### 🔍 Improved Hardware Identification 

Previously, version detection relied solely on the USB Product ID with a single serial number fallback string. The updated logic applies explicit matching for both hardware signals:

| Signal | V1 | V2 |
| :--- | :--- | :--- |
| **USB Product ID** | `0x4050` | `0x5050` |
| **Serial Number** | `SR-2026-4050` | `SR-2026-5050` |
| **Fallback** | V1 (safe default for unrecognised variants) | — |

---


# What's New (v2.6.0) – Peripheral Customization & Core Persistence

The `v2.6.0` update focuses on improving peripheral customization, expanding UI interaction options, and elevating the stability of the hardware interface for **MacroPAD II**.

* **Dynamic Selectors:** Replaced fixed layout options with interactive dropdown menus in the configuration view, streamlining how actions, commands, and profiles are assigned.
* **State & Preference Persistence:** Implemented an automated background mechanism to save device configurations, ensuring your customized profiles and hardware maps are retained across extension and editor restarts.
* **Advanced Button Parsing (S1 & S2):** Resolved critical interaction processing bugs for the encoder push-switches. The S1 and S2 hardware inputs are now fully operational as specialized triggers that accept modified arguments and complex variables.
* **Upper Encoder (ENC 1) Precision:** Fixed operational tracking regressions affecting the top programmable control knob. Directional monitoring has been fully restored, preventing missed steps and ensuring clean mechanical feedback.
* **Execution Bridge & Routing:** Patched internal message handling routines to ensure all mapped operations and defined shortcuts trigger instantly with zero communication lag.

### 🎛️ Refactored Configuration & Hardware Mapping
The hardware interaction layer has been updated to provide smoother event processing and predictable profile behavior during active workspace switches.

| Feature / Hardware Element | Configuration Type | Core Trigger Method / Action | Description |
| :--- | :--- | :--- | :--- |
| **Interface Selector** | Interactive Dropdown Menu | `renderDynamicDropdownUI` | Replaces legacy static text fields with smart contextual layout selectors. |
| **S1 / S2 Push Switches** | Macro Bindable Trigger | `parseEncoderSwitchEvent` | Enhanced click registration supporting multi-argument commands without dropouts. |
| **Upper Encoder (ENC 1)** | Hardware Interrupt Tracking | `monitorUpperEncoderRotary` | Re-calibrated rotary step counter ensuring immediate CW/CCW resolution tracking. |
| **Configuration Cache** | Automised Background Engine | `flushSettingsToGlobalState` | Seamless background write synchronization that secures mappings against app crashes. |

### 🚀 Architectural Optimization (`padDevice`)
* **Codebase Modernization:** Conducted deep structural refactoring and cleanup to eliminate redundant processes, optimizing runtime velocity and UI responsiveness.
* **Type Safety & Footprint Reduction:** Implemented stricter type checking rules in low-level routines, visibly lowering hardware resource consumption during live device communication.

--- 

# What's New (v2.5.0) – Advanced Hardware Control & Localization Engine

The latest update for **SunGo Project Manager** introduces granular peripheral hardware control for the **SunGO MacroPAD II**, a structural localization refactor across the entire codebase, and performance optimizations.

* **Granular Encoder Control:** Added structural elements within `padSettings2` to dynamically enable or disable the dual rotary encoders, eliminating unintended macro triggers when the knobs are not in use.
* **Tactical Key Remapping (S1/S2):** Full macro assignment support for the auxiliary hardware keys **S1** and **S2**, unlocking additional tactical layout workflows.
* **NLS Localization Migration:** Removed all remaining hardcoded strings and UI descriptions, completely replacing them with native **NLS (Native Language Support) translation keys** for seamless multi-language compliance.
* **Refactoring & Core Clean-up:** The `padDevice` communication layer has been heavily optimized and cleaned up to lower memory footprint and improve HID RAW frame processing reliability.

### 🎛️ Expanded Configuration Structure (`padSettings2`)
The hardware configuration schema has been enhanced to accommodate peripheral status flags and custom button bindings. Settings are automatically synchronized with the device using updated configuration packets.

| Feature / Hardware Element | Configuration Type | Core Trigger Method / Action | Description |
| :--- | :--- | :--- | :--- |
| **Rotary Encoders (Left/Right)** | Boolean Switch (`true`/`false`) | `toggleEncoderHardware` | Complete activation or suppression of hardware interrupt signals from the knobs. |
| **S1 Function Key** | Macro Bindable Selector | `assignS1KeyAction` | Custom VS Code command or system macro executed on single tap. |
| **S2 Function Key** | Macro Bindable Selector | `assignS2KeyAction` | Custom VS Code command or system macro executed on single tap. |
| **Localization Core** | NLS Subsystem Engine | `vscode.l10n` Integration | Centralized UI text loading according to the global VS Code environment language. |

### 🚀 Performance & Memory Optimization (`padDevice`)
The underlying communication layer `padDevice` underwent a deep architectural review:
* **Buffer Pooling:** Reimplemented the HID packet distribution to reuse active byte arrays, significantly reducing GC (Garbage Collection) overhead during high-frequency encoder rotation.
* **Dead Code Elimination:** Removed legacy descriptors and unused packet definitions, resulting in a cleaner, maintainable, and lighter subsystem footprint.

---

# What's New (v2.4.5) – Rotary Encoders Configuration

The latest release brings full integration for the twin rotary encoders on the **SunGO MacroPAD II**, allowing you to bind tactical commands to physical hardware rotations.

> ⚠️ **Firmware Compatibility Note:** This feature is prepared for full integration with the upcoming **firmware v5.8.0**, which will be available shortly. Ensure your device is updated as soon as it drops to unlock complete dual-direction knob capabilities.

* **Dual-Knob Independent Mapping:** Separate configuration for the **left knob** and **right knob**.
* **Direction Awareness:** Bind completely different VS Code or system actions depending on whether you rotate **CW** (Clockwise) or **CCW** (Counter-Clockwise).
* **Hardware Sync:** Settings are safely synchronized with the pad's global state and pushed to the device via dedicated HID configuration packets.

| Feature / Funkcja | Description / Opis | Action Triggers / Wyzwalacze |
| :--- | :--- | :--- |
| **Left / Right Knobs** | Independent encoder configuration | `saveEncoderAction` & `applyEncoderConfig` |
| **CW / CCW Control** | Dual-direction macro triggers | Cursor Up/Down, Scroll, Vol, Brightness |
| **State Persistence** | Config saved globally within VS Code | Instant hardware sync on apply |

---




# What's New (v2.4.3) – Automated Firmware Updates & OTA

The latest update for **SunGo Project Manager** introduces a complete firmware management suite for the **SunGO MacroPAD II**, making hardware maintenance as simple as a single click.

* **Automated OTA Updates:** No more manual flashing. If a new version is detected on GitHub, simply click **UPDATE**. The extension downloads the `.uf2` file and flashes it directly to the RP2040.
* **One-Click Bootloader:** Enter programming mode (RPI-RP2) instantly via the UI without touching the physical button.
* **Visual Progress:** Monitor the update status with a real-time progress bar in the **PadSettings** panel. The device restarts automatically once the new firmware is active.
* **Safety Features:**
    * **Manual Downgrade:** Use the UI Bootloader button to manually flash older versions if needed.
    * **Emergency Recovery:** Hold keys **9+10+12** while connecting USB to force bootloader mode.

| Feature | Description | Requirement |
| :--- | :--- | :--- |
| **OTA Update** | Automatic GitHub download & flash | MacroPAD II |
| **Progress Bar** | Real-time visual feedback in settings | v2.4.3 Extension |
| **Auto-Restart** | Instant reboot after successful flash | Firmware 5.6.0+ |



---

## 🔁 What's New (v2.4.0) – SunGO PAD II Customization

<img width="1232" height="853" alt="Zrzut ekranu 2026-05-04 214559" src="https://github.com/user-attachments/assets/5c83a1d6-2f4a-4bc9-afc4-0e4fd369dbd9" />


#### ⌨️ Extra Function Keys: A, B, and C
The latest update unlocks the full potential of the **SunGO Macro PAD II**. You can now assign your most frequently used tools from the **SunGO Tools** section to the physical keys **A, B, and C**.

**Key Features:**
* **Custom Mapping:** Choose which tool (e.g., Binary Analyzer, Go Doc Viewer, Code Metrics) is triggered by each function key.
* **New PAD II Settings Panel:** A dedicated, visual configuration interface for managing your Macro PAD II layout.
* **Instant Workflow:** Launch complex analysis tools with a single physical press, without searching through VS Code menus.

> 💡 **Master's Tip:** To use these new features, your SunGO Macro PAD II requires **Firmware v5.4**. You can find the latest binary and source code in the hardware section of our repository.
> 🔗 [Get Firmware v5.4 on GitHub](https://github.com/SunDUINO/SunGo-Project_Manager-relase/tree/main/hardware/SunGO_PAD_v2)

| Feature | Description | Requirement |
| :--- | :--- | :--- |
| **Mapping A/B/C** | Assign tools like `Profiler`, `Dependencies`, or `Notes` | SunGo PAD II |
| **Visual Config** | New UI panel for tactile feedback management | v2.4.0 Extension |
| **Firmware Sync** | Full support for new HID reports | Firmware 5.4+ |

* `SunGo: Macro PAD II Settings` — Open the visual mapping panel.
* `SunGo Tools: Quick Assign Tool` — Quickly bind a tool to keys A, B, or C.

---

## ⭐ What's New (v2.3.8) – SunGO PAD v2 & Adaptive UI

### 🛠️ Hardware Revision 2.0 (Work in Progress)
A new version of the physical SunGO PAD is currently under development. This revision expands the interface with additional macro keys and rotary encoders for even better workflow control.

<p align="center">
<img width="1128" height="846" alt="IMG_20260430_192849293" src="https://github.com/user-attachments/assets/75457240-cfa3-43d2-94dc-38a3ce401bb9" />
</p>

* **Status:** Hardware is in the preparation/prototype phase.
* **Testing Firmware:** Experimental firmware for the new revision is available on GitHub Hardware section.
    * 🔗 [SunGO PAD v2 – Testing Firmware](https://github.com/SunDUINO/SunGo-Project_Manager-relase/tree/main/hardware/SunGO_PAD_v2)
  

### 🎛️ Intelligent Hardware Detection
The configuration panel now automatically detects the connected hardware version and adjusts the UI layout accordingly.

* **SunGO PAD v1:** Classic 3x3 layout.
* **SunGO PAD v2:** Expanded layout with support for keys 10, 11, 12 and visual indicators.

<p align="center">
  <img width="1225" height="710" alt="Zrzut ekranu 2026-05-01 220530" src="https://github.com/user-attachments/assets/76abd990-8456-43c4-98de-e6ddd96b6fd9" />
  <img width="1130" height="702" alt="Zrzut ekranu 2026-05-01 220343" src="https://github.com/user-attachments/assets/38dd32ec-7dc5-4504-8c9f-b858105b84f1" />
  <br>
  <em>Adaptive UI: Standard 9-key configuration (left) vs. New 12-key configuration (right).</em>
</p>

---

## ⭐ What's New (v2.3.0) – Enhanced Code Insights

### 🔍 Enhanced Code Review & Integration

Version 2.3.0 focuses on deeper integration and smarter feedback. The Code Review panel is now more than just a list of issues – it's an interactive learning tool connected to your Gopher Assistant.

**Key Updates:**
- 💡 **Smart Suggestions** – Added built-in hints and solutions for common issues detected by analysis tools.
- 🤖 **Gopher Assistant Integration** – Your Gopher now reacts dynamically to `staticcheck` results, offering contextual help for specific errors.
- 📋 **SunGo Pad Sync** – Full integration with SunGo Pad; analysis statuses are now visually represented with intuitive color coding.
- 🧹 **Streamlined Panel** – Removed `go vet` to reduce redundancy and focus on more advanced analysis tools (`staticcheck`, `golangci-lint`).

> 💡 **Tip:** Click on a `staticcheck` error to see how the Gopher Assistant can help you refactor your code!
>

---


## ⭐ What's New (v2.1.0) – Code Review Panel

### 🔍 Code Review Panel

A brand new static code analysis panel accessible directly from the **SunGo Tools** sidebar. Analyze your Go code without external APIs – everything runs locally on your machine.

**Supported Tools:**
| Tool | Description |
|------|-------------|
| **go vet** | Go's built-in static analyzer |
| **staticcheck** | Advanced analysis with 100+ checks |
| **golangci-lint** | Fast linter aggregator |

**Features:**
- ✅ **Real-time status** – Green dots for available tools, gray for not installed
- 🎯 **Interactive results** – Click any issue to jump to file and line
- 🔍 **Filtering & search** – Filter by severity (errors/warnings) or search by content
- 🎉 **Gopher reactions** – Confetti when code is clean, sad Gopher when issues found
- 🌐 **Bilingual** – Full Polish and English support

> ⚠️ **Note:** If a tool is not installed, its checkbox will be grayed out. Install manually:
> 
> **Windows (PowerShell):**
> ```powershell
> # staticcheck
> go install honnef.co/go/tools/cmd/staticcheck@latest
> 
> # golangci-lint
> Invoke-WebRequest -Uri "https://github.com/golangci/golangci-lint/releases/download/v1.64.5/golangci-lint-1.64.5-windows-amd64.zip" -OutFile "golangci-lint.zip"
> Expand-Archive -Path "golangci-lint.zip" -DestinationPath "$env:GOPATH\bin"
> Remove-Item "golangci-lint.zip"
> ```
> 
> **Linux (Terminal):**
> ```bash
> # staticcheck
> go install honnef.co/go/tools/cmd/staticcheck@latest
> 
> # golangci-lint
> curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b $(go env GOPATH)/bin
> ```
> Or download directly from: [staticcheck](https://staticcheck.io/), [golangci-lint](https://golangci-lint.run/)


> 💡 Run analysis from the SunGo Tools panel or use the `SunGo: Code Review` command.


---

## ⭐ What's New (v2.0.0) – Github Templates 

### 📦 Project Templates from Git (GitHub Templates)
Instantly bootstrap your new Go projects using remote Git repositories. This feature is integrated into the Project Creator and the SunGo Tools sidebar.

**How it works:**

**Select Source:** Click the "📦 From GitHub Template" button in the Project Creator or select "Project from GitHub" from the SunGo Tools menu.

**Project Name:** Enter your project name in the creator's side panel.

**Choose a Template: * SunGo Templates:** The extension fetches a curated list via GitHub API and displays it as tiles (e.g., Console CLI, Raylib 3D Scene, Gin REST API, Fyne Desktop App).

**From URL:** Use the From URL tab to provide a custom source. Supports user/repo shorthand, full HTTPS, and SSH links.

**Automation:** Upon clicking Create Project, the extension:

- Performs a git clone --depth=1 for maximum speed.
- Automatically removes the .git/ folder, providing a clean slate for your own version control.
- Deploys the template structure directly into your workspace.

---

## ⭐ What's New (v1.9.1) – Favorite Projects & Go Doc Viewer

### ⭐ Favorite Projects

Pin your most-used projects to the top of the SunGo sidebar for instant access — no more scrolling through long project lists.

**How to use:**

- **Hover** over any project in the tree → click the ⭐ icon to pin it
- **Hover** over a favorite → click the unpin icon to remove it
- Or **right-click** any project → **Pin to Favorites** / **Unpin from Favorites**

Pinned projects appear in a dedicated **★ FAVORITES** section at the top of the sidebar and as golden chips in the Home Dashboard. They are automatically hidden from the main project list to avoid duplicates.

Favorites are stored permanently in the extension's global state and survive VS Code restarts.

---

### 📖 Go Doc Viewer

A full-featured Go documentation browser built directly into VS Code — accessible from the **SunGo Tools** panel (click `$(book)` Go Doc Viewer).

| Feature | Description |
|---|---|
| **Import Browser** | Automatically reads `import` statements from your active `.go` file and lists them as clickable links |
| **Standard / Third-party** | Imports are split into two groups for quick scanning |
| **Package Search** | Type `fmt`, `net/http`, or `sync.WaitGroup` — press Enter to load docs instantly |
| **Navigation** | ← → buttons for browsing history, just like a web browser |
| **Syntax Highlighting** | `func` in blue · `type` in gold · `const` in amber · `var` in pink |
| **pkg.go.dev** | 🌐 button opens the current package on `pkg.go.dev` |

> 💡 **Tip:** Click **↺ Refresh** in the topbar after switching to a different `.go` file to update the import list.

---

## 🐹 What's New (v1.8.3) – Gopher Assistant

The SunGo Manager sidebar now has a live companion. Click the **☀️ SunGo icon** in the VS Code Activity Bar to open the panel — the Gopher Assistant sits right below the project list.

![Gopher Assistant](https://forum.lothar-team.pl//ext/dmzx/imageupload/img-files/48/f7258b8/6081905/d96b0debfe79558beff978af0298a0be.png)

> 💡 **Tip:** You can drag the Gopher panel to the **right-side Secondary Sidebar** (where Copilot sits) for a permanent companion view. VS Code remembers the position between sessions.

### How it works

The Gopher reacts automatically — no setup needed. It watches your Go diagnostics and responds to every SunGo action:

| State | When it appears |
|---|---|
| 📖 **Idle** – glasses on, reading a book | Default state, no active operation |
| ⚙️ **Building** – wrench out, gear spinning | During `go build` |
| 🚀 **Running** – laptop open, progress bar | During `go run` |
| 🧪 **Testing** – focused, progress bar | During `go test` |
| 🔍 **Go Vet** – glasses + spinning gear | During static analysis |
| 📝 **Go Fmt** – calm, book open | During code formatting |
| ❌ **Error** – tears, red X marks | Compilation error detected |
| 🎉 **OK** – happy eyes, stars, confetti | Build succeeded! |

### Interacting with the Gopher

- **Click** the speech bubble or the **🐹 Gopher Wisdom** button → new Go tip in your language (EN/PL)
- **Triple-click** the Gopher within 2 seconds ... suprised 

### Moving the Gopher to the right side

1. Open the SunGo panel (`☀️` icon in the Activity Bar)
2. Right-click the **Gopher Assistant** section header
3. Select **Move View** → **Secondary Side Bar**

The Gopher will sit on the right permanently from that point on.

---

## 🚀 What's New (v1.6.1)

### 🧰 Dual Repository Support
- I have added a Git repository management module. It does not replace the built-in VS Code Git features; instead, it allows you to push specific files—selected via a picker—to any external repository.
- This is especially useful when you maintain a private repository for your source code but want to publish specific assets (such as binaries) to a separate public repository.

### Universal Compatibility: Works independently of your current workspace. Use it to bridge any project with your external release or backup repositories.

### Select files to publish:

* Click to select a file
* Ctrl + Click for multiple selection
* Shift + Click for range selection

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
* [PL: Co nowego (v2.7.0) - Optymalizacja kreatora szablonów Git](#-co-nowego-v270--optymalizacja-kreatora-szablonów-git)
* [PL: Co nowego (v2.6.2) – Inteligentne wykrywanie i panel braku urządzenia](#co-nowego-v262--inteligentne-wykrywanie-i-panel-braku-urządzenia)
* [PL: Co nowego (v2.6.0) – Personalizacja peryferiów i trwałość konfiguracji](#co-nowego-v260-–-personalizacja-peryferiów-i-trwałość-konfiguracji)
* [PL: Co nowego (v2.5.0) – Zaawansowane sterowanie sprzętem i silnik lokalizacji](#co-nowego-v250-–-zaawansowane-sterowanie-sprzętem-i-silnik-lokalizacji)
* [PL: Co nowego (v2.4.3) – Automatyczne aktualizacje firmware i OTA](#co-nowego-v243--automatyczne-aktualizacje-firmware-i-ota)
* [PL: Co nowego (v2.4.0) – Personalizacja SunGO PAD II](#-co-nowego-v240--personalizacja-sungo-pad-ii-i-mapowanie-klawiszy)
* [PL: Co nowego (v2.3.8) – SunGO PAD v2 i Adaptacyjne UI](#-co-nowego-v238--sungo-pad-v2-i-adaptacyjne-ui)
* [PL: Co nowego (v2.3.0) – Udoskonalone analizy kodu](#co-nowego-v230--udoskonalone-analizy-kodu)
* [PL: Co nowego (v2.1.0) – Panel Code Review](#co-nowego-v210-–-panel-code-review)
* [PL: Co nowego (v2.0.0) – Github Templates](#co-nowego-v200-–-github-templates)
* [PL: Co nowego (v1.9.1) – Ulubione projekty i Go Doc Viewer](#co-nowego-v191--ulubione-projekty-i-przeglądarka-go-doc)
* [PL: Co nowego (v1.8.3) – Asystent Gopher](#co-nowego-v183--asystent-gopher)
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


### 🚀 Co nowego (v2.7.0) – Optymalizacja kreatora szablonów Git

* **Gwarancja kompletności logów w Output:** Rozwiązano problem zamrażania konsoli wyjściowej na finałowym etapie generowania projektu. Renderowanie logów zostało w pełni uniezależnione od operacji I/O na dysku, dzięki czemu komunikaty o powodzeniu operacji oraz inicjalizacji `go mod` zawsze wyświetlają się do samego końca.
* **Zwiększona niezawodność importu:** Udoskonalono asynchroniczną obsługę błędów podczas klonowania z GitHub, zapewniając bezpieczne procedury wyjścia awaryjnego (fallback) oraz precyzyjne odświeżanie statusu w panelu menedżera projektów SunGo.

---

# Co nowego (v2.6.2) – Inteligentne wykrywanie i panel braku urządzenia

Wersja `v2.6.2` wzmacnia potok wykrywania sprzętu dla całej rodziny **SunGO MacroPAD** i eliminuje długo istniejący problem UX, w którym otwarcie panelu ustawień bez podłączonego urządzenia cicho otwierało widok konfiguracji V1.

* **Panel braku urządzenia:** Gdy przy starcie wtyczki żaden SunGO MacroPAD nie zostanie wykryty, rozszerzenie otwiera teraz dedykowany panel informacyjny zamiast cicho cofać się do ustawień V1. Panel zawiera instrukcję połączenia krok po kroku oraz przycisk ponownego wykrywania urządzenia — bez konieczności restartu VS Code.
* **Wykrywanie wersji dwoma sygnałami:** Identyfikacja sprzętu sprawdza teraz zarówno USB **Product ID**, jak i **numer seryjny** urządzenia (`SR-2026-4050` → V1, `SR-2026-5050` → V2), zapobiegając błędnej identyfikacji na systemach, gdzie deskryptor HID jest raportowany inaczej w zależności od systemu operacyjnego.
* **Trójnikowe przekierowanie ustawień:** Komenda `openPadSettings` rozgałęzia się teraz na trzy odrębne ścieżki — `NONE` (brak urządzenia), `V1` (MacroPAD I) oraz `V2` (MacroPAD II) — zastępując poprzedni dwustanowy fallback, który traktował brakujące urządzenie jak jednostkę V1.
* **Pełna dwujęzyczna lokalizacja NLS:** Wszystkie nowe ciągi UI w panelu braku urządzenia są zlokalizowane przez natywny system kluczy NLS w obu pakietach językowych — angielskim i polskim (`pad.nodevice`).

### 🔌 Panel braku urządzenia — przegląd funkcji

| Funkcja | Opis |
| :--- | :--- |
| **Wskazówki połączenia** | Trzy działania naprawcze prowadzące przez weryfikację kabla, stanu LED i ponowne podłączenie USB |
| **Przycisk ponownego wykrywania** | Zamyka bieżący panel i ponownie wywołuje `openPadSettings` bez restartu edytora |
| **Komunikat dla Linuxa** | Na systemach Linux wyświetla dodatkowe przypomnienie o konfiguracji uprawnień udev |
| **Skrót do README** | Bezpośredni link do dokumentacji konfiguracyjnej z poziomu panelu |

### 🔍 Ulepszona identyfikacja sprzętu (`padDevice`)

Poprzednio wykrywanie wersji opierało się wyłącznie na USB Product ID z jednym ciągiem fallback numeru seryjnego. Zaktualizowana logika stosuje jawne dopasowanie dla obu sygnałów sprzętowych:

| Sygnał | V1 | V2 |
| :--- | :--- | :--- |
| **USB Product ID** | `0x4050` | `0x5050` |
| **Numer seryjny** | `SR-2026-4050` | `SR-2026-5050` |
| **Fallback** | V1 (bezpieczny domyślny dla nieznanych wariantów) | — |

### No Device Connected ...

<img width="861" height="652" alt="Zrzut ekranu 2026-07-05 123337" src="https://github.com/user-attachments/assets/57325c3a-7aed-43de-87ba-4aa98c25dd0c" />

### SunGO MacroPAD I Detect ...

<img width="1248" height="745" alt="Zrzut ekranu 2026-07-05 123246" src="https://github.com/user-attachments/assets/e8217225-cf3b-4876-bfa0-e41a9c65c86a" />

### SunGO MacroPAD II Detect ...

<img width="1393" height="1023" alt="Zrzut ekranu 2026-07-05 123516" src="https://github.com/user-attachments/assets/c71e111a-1611-4c43-9285-a9b2b94f10da" />


---

# Co nowego (v2.6.0) – Personalizacja peryferiów i trwałość konfiguracji

Wydanie `v2.6.0` koncentruje się na rozszerzeniu możliwości personalizacji peryferiów, wprowadzeniu elastycznych opcji interfejsu użytkownika oraz podniesieniu stabilności komunikacji sprzętowej dla **MacroPAD II**.

* **Wygodne Listy Wyboru:** Tradycyjne opcje konfiguracyjne zastąpiono interaktywnymi listami rozwijalnymi, co znacznie upraszcza przypisywanie akcji, makr oraz profili sterowania w panelu ustawień.
* **Trwały Zapis Preferencji:** Wdrożono automatyczny mechanizm zapisu stanów w tle, dzięki czemu zmodyfikowane parametry pracy urządzenia są bezpiecznie zachowywane i nie resetują się po restarcie aplikacji.
* **Zaawansowana Interpretacja Przycisków (S1 i S2):** Usunięto błędy przetwarzania sygnałów ze zintegrowanych przełączników enkoderów. Przyciski S1 i S2 działają teraz stabilnie jako wejścia specjalne, bezproblemowo obsługując modyfikowaną zawartość.
* **Precyzja Górnego Pokrętła (ENC 1):** Wyeliminowano problemy z odczytem ruchu górnego enkodera programowalnego. Pełna dokładność rejestrowania obrotu została przywrócona, co zapobiega gubieniu kroków przy szybkich zmianach pozycji.
* **Wyzwalanie Operacji i Mapowanie:** Poprawiono wewnętrzny mostek komunikacyjny, gwarantując, że przypisane aliasy oraz polecenia są realizowane natychmiastowo i bez przestojów w kolejce rozkazów.

### 🎛️ Zmodernizowana struktura konfiguracji i mapowania
Warstwa obsługi zdarzeń sprzętowych została przebudowana, aby zapewnić płynniejszą reakcję urządzenia oraz przewidywalne zachowanie profili podczas przełączania obszarów roboczych.

| Funkcja / Element sprzętowy | Typ konfiguracji | Metoda wyzwalająca / Akcja | Opis |
| :--- | :--- | :--- | :--- |
| **Selektor Interfejsu** | Interaktywna lista rozwijana | `renderDynamicDropdownUI` | Zastępuje stare pola tekstowe inteligentnymi, kontekstowymi listami wyboru. |
| **Przyciski Enkoderów S1 / S2** | Powiązanie makr i komend | `parseEncoderSwitchEvent` | Poprawiona rejestracja kliknięć, w pełni obsługująca komendy z wieloma argumentami. |
| **Górny Enkoder (ENC 1)** | Przerwanie kontrolera ruchu | `monitorUpperEncoderRotary` | Skalibrowany na nowo licznik kroków, zapewniający precyzyjne śledzenie obrotu CW/CCW. |
| **Pamięć Podręczna Ustawień** | Automatyczny silnik tła | `flushSettingsToGlobalState` | Bezpieczna synchronizacja zmian w tle, chroniąca układ klawiszy przed utratą danych. |

### ⚡ Optymalizacja Strukturalna (`padDevice`)
* **Modernizacja Kodu Źródłowego:** Przeprowadzono gruntowne czyszczenie struktury kodu oraz refaktoryzację, usuwając zbędne procesy i zauważalnie zwiększając płynność działania interfejsu.
* **Rygorystyczna Kontrola Typów:** Zaostrzono reguły sprawdzania danych w procedurach niskopoziomowych, zmniejszając narzut na zasoby systemowe podczas ciągłego odpytywania podłączonego sprzętu.

---

# Co nowego (v2.5.0) – Zaawansowane sterowanie sprzętem i silnik lokalizacji

Najnowsza aktualizacja **SunGo Project Manager** wprowadza szczegółową kontrolę nad peryferiami sprzętowymi **SunGO MacroPAD II**, strukturalny refaktoring lokalizacyjny w całym kodzie źródłowym oraz optymalizacje wydajnościowe.

* **Zarządzanie pracą enkoderów:** Wprowadzono nowe elementy struktury w `padSettings2` umożliwiające dynamiczne włączanie i wyłączanie obydwu enkoderów obrotowych, co zapobiega przypadkowemu wyzwalaniu makr.
* **Mapowanie klawiszy funkcyjnych S1/S2:** Dodano pełne wsparcie dla przypisywania akcji oraz dedykowanych funkcji makr dla dodatkowych klawiszy sprzętowych **S1** i **S2**.
* **Migracja na klucze tłumaczeń NLS:** Wyeliminowano wszystkie zahardkodowane opisy interfejsu użytkownika, zastępując je elastycznym systemem kluczy tłumaczeń **NLS (Native Language Support)**.
* **Refaktoring i czyszczenie kodu `padDevice`:** Warstwa komunikacyjna odpowiedzialna za obsługę kontrolera została zoptymalizowana pod kątem alokacji pamięci oraz niezawodności przetwarzania ramek HID RAW.

### 🎛️ Rozbudowana struktura konfiguracji (`padSettings2`)
Schemat konfiguracyjny kontrolera sprzętowego został rozszerzony o flagi stanu peryferiów i niestandardowe powiązania klawiszy. Wszystkie parametry są automatycznie synchronizowane z urządzeniem za pomocą natywnych pakietów konfiguracyjnych HID.

| Funkcja / Element sprzętowy | Typ konfiguracji | Metoda wyzwalająca / Akcja | Opis |
| :--- | :--- | :--- | :--- |
| **Enkodery (Lewy/Prawy)** | Przełącznik Boolean (`true`/`false`) | `toggleEncoderHardware` | Pełna aktywacja lub programowe tłumienie sygnałów przerwań sprzętowych z pokręteł. |
| **Klawisz funkcyjny S1** | Selektor powiązań makr | `assignS1KeyAction` | Przypisanie dowolnej komendy VS Code lub makra systemowego pod fizyczny przycisk S1. |
| **Klawisz funkcyjny S2** | Selektor powiązań makr | `assignS2KeyAction` | Przypisanie dowolnej komendy VS Code lub makra systemowego pod fizyczny przycisk S2. |
| **Silnik lokalizacji** | Podsystem NLS | Integracja `vscode.l10n` | Scentralizowane ładowanie opisów interfejsu na podstawie języka środowiska VS Code. |

### 🚀 Optymalizacja wydajności warstwy `padDevice`
Niskopoziomowy moduł komunikacyjny `padDevice` przeszedł gruntowny przegląd architektury:
* **Pula buforów (Buffer Pooling):** Przeprojektowano wysyłanie pakietów HID tak, aby wielokrotnie wykorzystywać te same tablice bajtów. Zredukowało to narzut Garbage Collectora (GC) podczas intensywnego obracania enkoderami.
* **Czyszczenie kodu (Dead Code Elimination):** Usunięto przestarzałe deskryptory oraz nieużywane definicje pakietów, dzięki czemu kod jest czystszy, łatwiejszy w utrzymaniu i lżejszy dla systemu.

---

# Co nowego (v2.4.5) – Konfiguracja Enkoderów Obrotowych

Najnowsza wersja wprowadza pełną integrację dla dwóch enkoderów obrotowych w **SunGO MacroPAD II**, umożliwiając przypisywanie zaawansowanych komend i makr do fizycznego obrotu pokręteł.

> ⚠️ **Uwaga dotycząca kompatybilności:** Funkcja ta została przygotowana do pełnej integracji z nadchodzącym **firmware v5.8.0**, które będzie dostępne już niebawem. Upewnij się, że zaktualizujesz swoje urządzenie natychmiast po jego premierze, aby w pełni odblokować dwukierunkową obsługę pokręteł.

* **Niezależne mapowanie:** Osobna konfiguracja dla **lewego** oraz **prawego pokrętła**.
* **Wykrywanie kierunku obrotu:** Możliwość przypisania skrajnie różnych akcji VS Code lub systemowych dla obrotu **CW** (zgodnie z ruchem wskazówek zegara) oraz **CCW** (przeciwnie do ruchu wskazówek zegara).
* **Synchronizacja sprzętowa:** Ustawienia są trwale zapisywane w stanie globalnym rozszerzenia i natychmiastowo przesyłane do pamięci kontrolera za pomocą dedykowanych pakietów konfiguracyjnych HID.

| Funkcja | Opis | Wyzwalacze komunikatów |
| :--- | :--- | :--- |
| **Lewe / Prawe Pokrętło** | Niezależna konfiguracja każdego z enkoderów | `saveEncoderAction` & `applyEncoderConfig` |
| **Kontrola CW / CCW** | Dwukierunkowe wyzwalanie przypisanych makr | Góra/Dół, Przewijanie, Głośność, Jasność |
| **Trwałość Stanu** | Zapis konfiguracji w globalState VS Code | Natychmiastowy hardware sync po zatwierdzeniu |

---

# Co nowego (v2.4.3) – Automatyczne aktualizacje firmware i OTA

Najnowsza wersja **SunGo Project Manager** wprowadza kompletny system zarządzania oprogramowaniem układowym dla **SunGO MacroPAD II**, upraszczając konserwację sprzętu do jednego kliknięcia.

* **Automatyczne aktualizacje OTA:** Zapomnij o ręcznym kopiowaniu plików. Jeśli na GitHubie pojawi się nowa wersja, po prostu kliknij **UPDATE**. Rozszerzenie samo pobierze plik `.uf2` i wgra go do RP2040.
* **Bootloader jednym kliknięciem:** Wejdź w tryb programowania (RPI-RP2) bezpośrednio z poziomu interfejsu, bez konieczności rozkręcania obudowy czy naciskania fizycznych przycisków.
* **Wizualny postęp:** Śledź status aktualizacji na pasku postępu w panelu **PadSettings**. Po zakończeniu, pad automatycznie zrestartuje się z nowym oprogramowaniem.
* **Funkcje ratunkowe:**
    * **Ręczny Downgrade:** Przycisk Bootloader w UI pozwala na ręczne wgranie starszych wersji oprogramowania.
    * **Tryb awaryjny:** Przytrzymaj klawisze **9+10+12** podczas podłączania USB, aby wymusić tryb bootloadera w sytuacjach awaryjnych.

| Funkcja | Opis | Wymagania |
| :--- | :--- | :--- |
| **Aktualizacja OTA** | Automatyczne pobieranie i wgrywanie z GitHub | MacroPAD II |
| **Pasek postępu** | Wizualny feedback w ustawieniach | Wtyczka v2.4.3 |
| **Auto-Restart** | Natychmiastowy restart po wgraniu kodu | Firmware 5.6.0+ |

---

### ⭐ Co nowego (v2.4.0) – Personalizacja SunGO PAD II

#### ⌨️ Dodatkowe klawisze funkcyjne: A, B oraz C
Najnowsza aktualizacja uwalnia pełny potencjał **SunGO Macro PAD II**. Teraz możesz przypisać swoje najczęściej używane narzędzia z sekcji **SunGO Tools** do fizycznych przycisków **A, B oraz C**.

<img width="1232" height="853" alt="Zrzut ekranu 2026-05-04 214559" src="https://github.com/user-attachments/assets/e16be8d1-acda-4a2b-b626-3934568909b2" />


**Nowości:**
* **Własne Mapowanie:** Sam zdecyduj, które narzędzie (np. Binary Analyzer, Go Doc Viewer, Code Metrics) zostanie uruchomione po naciśnięciu konkretnego klawisza.
* **Nowy Panel Ustawień PAD II:** Dedykowany, wizualny interfejs konfiguracyjny do zarządzania układem Twojego Macro PAD-a.
* **Błyskawiczny Workflow:** Uruchamiaj zaawansowane narzędzia analizy jednym kliknięciem fizycznego przycisku, bez przeszukiwania menu w VS Code.

> 💡 **Master's Tip:** Aby skorzystać z nowych funkcji, Twój SunGO Macro PAD II wymaga **Firmware'u w wersji 5.4**. Najnowsze pliki binarne oraz kod źródłowy znajdziesz w sekcji hardware naszego repozytorium.
> 🔗 [Pobierz Firmware v5.4 z GitHub](https://github.com/SunDUINO/SunGo-Project_Manager-relase/tree/main/hardware/SunGO_PAD_v2)

| Funkcja | Opis | Wymagania |
| :--- | :--- | :--- |
| **Mapowanie A/B/C** | Przypisz narzędzia typu `Profiler`, `Dependencies` lub `Notes` | SunGo PAD II |
| **Wizualna Konfiguracja** | Nowy panel UI do zarządzania feedbackiem tactile | Wtyczka v2.4.0 |
| **Synchronizacja Firmware** | Pełna obsługa nowych raportów HID | Firmware 5.4+ |

* `SunGo: Macro PAD II Settings` — Otwórz wizualny panel mapowania.
* `SunGo Tools: Quick Assign Tool` — Szybkie przypisanie narzędzia do klawiszy A, B lub C.

---

## ⭐ Co nowego (v2.3.8) – SunGO PAD v2 i Adaptacyjne UI

### 🛠️ Rewizja Sprzętu 2.0 (W fazie przygotowania)
Nowa wersja fizycznego kontrolera SunGO PAD jest obecnie w fazie opracowywania. Ta rewizja rozszerza interfejs o dodatkowe klawisze makr oraz enkodery obrotowe dla jeszcze lepszej kontroli pracy.

<p align="center">
<img width="1128" height="846" alt="IMG_20260430_192849293" src="https://github.com/user-attachments/assets/75457240-cfa3-43d2-94dc-38a3ce401bb9" />
</p>

* **Status:** Sprzęt jest w fazie przygotowania/prototypowania.
* **Firmware Testowy:** Eksperymentalne oprogramowanie dla nowej rewizji jest dostępne na GitHubie.
    * 🔗 [SunGO PAD v2 – Firmware Testowy](https://github.com/SunDUINO/SunGo-Project_Manager-relase/tree/main/hardware/SunGO_PAD_v2)
 


### 🎛️ Inteligentne Wykrywanie Sprzętu
Panel konfiguracyjny automatycznie wykrywa teraz wersję podłączonego sprzętu i dostosowuje układ interfejsu (UI) do urządzenia.

* **SunGO PAD v1:** Klasyczny układ 3x3.
* **SunGO PAD v2:** Rozszerzony układ z obsługą klawiszy 10, 11, 12 oraz wizualnymi wskaźnikami.

<p align="center">
  <img width="1225" height="710" alt="Zrzut ekranu 2026-05-01 220530" src="https://github.com/user-attachments/assets/76abd990-8456-43c4-98de-e6ddd96b6fd9" />
  <img width="1130" height="702" alt="Zrzut ekranu 2026-05-01 220343" src="https://github.com/user-attachments/assets/38dd32ec-7dc5-4504-8c9f-b858105b84f1" />
  <br>
  <em>Adaptive UI: Standard 9-key configuration (left) vs. New 12-key configuration (right).</em>
</p>

---

## ⭐ Co nowego (v2.3.0) – Udoskonalone analizy kodu

### 🔍 Udoskonalony Panel Code Review i Integracja

Wersja 2.3.0 stawia na głębszą integrację i inteligentne wsparcie. Panel Code Review to teraz coś więcej niż lista błędów – to interaktywne narzędzie edukacyjne połączone z Twoim Asystentem Gopherem.

**Kluczowe nowości:**
- 💡 **Inteligentne Podpowiedzi** – Dodano gotowe sugestie i rozwiązania dla typowych problemów wykrywanych przez narzędzia analityczne.
- 🤖 **Integracja z Gopherem** – Twój asystent Gopher dynamicznie reaguje na błędy z `staticcheck`, oferując kontekstową pomoc.
- 📋 **Synchronizacja z SunGo Pad** – Pełna integracja z SunGo Padem; statusy analizy są teraz prezentowane za pomocą intuicyjnych kolorów.
- 🧹 **Uproszczony Panel** – Usunięto narzędzie `go vet` w celu wyeliminowania powtarzających się wyników i skupienia się na zaawansowanych analyzerach (`staticcheck`, `golangci-lint`).

 
> 💡 **Wskazówka:** Kliknij błąd `staticcheck`, aby zobaczyć, jak Asystent Gopher pomoże Ci w refaktoryzacji kodu!

---


## ⭐ Co nowego (v2.1.0) – Panel Code Review

### 🔍 Panel Code Review

Całkowicie nowy panel statycznej analizy kodu dostępny bezpośrednio z panelu **SunGo Tools**. Analizuj kod Go bez zewnętrznych API – wszystko działa lokalnie na Twoim komputerze.

**Obsługiwane narzędzia:**
| Narzędzie | Opis |
|-----------|------|
| **go vet** | Wbudowany analizator statyczny Go |
| **staticcheck** | Zaawansowana analiza z ponad 100 sprawdzeniami |
| **golangci-lint** | Szybki agregator linterów |

**Funkcje:**
- ✅ **Status w czasie rzeczywistym** – Zielone kropki dla dostępnych narzędzi, szare dla niezainstalowanych
- 🎯 **Interaktywne wyniki** – Kliknij problem, aby przejść do pliku i linii
- 🔍 **Filtrowanie i wyszukiwanie** – Filtruj według ważności lub szukaj w treści
- 🎉 **Reakcje Gophera** – Confetti gdy kod jest czysty, smutny Gopher gdy są błędy
- 🌐 **Dwujęzyczny** – Pełna obsługa polskiego i angielskiego

> ⚠️ **Uwaga:** Jeśli narzędzie nie jest zainstalowane, jego checkbox będzie wyszarzony. Zainstaluj je ręcznie:
> 
> **Windows (PowerShell):**
> ```powershell
> # staticcheck
> go install honnef.co/go/tools/cmd/staticcheck@latest
> 
> # golangci-lint
> Invoke-WebRequest -Uri "https://github.com/golangci/golangci-lint/releases/download/v1.64.5/golangci-lint-1.64.5-windows-amd64.zip" -OutFile "golangci-lint.zip"
> Expand-Archive -Path "golangci-lint.zip" -DestinationPath "$env:GOPATH\bin"
> Remove-Item "golangci-lint.zip"
> ```
> 
> **Linux (Terminal):**
> ```bash
> # staticcheck
> go install honnef.co/go/tools/cmd/staticcheck@latest
> 
> # golangci-lint
> curl -sSfL https://raw.githubusercontent.com/golangci/golangci-lint/master/install.sh | sh -s -- -b $(go env GOPATH)/bin
> ```
> 
> Lub pobierz bezpośrednio ze strony: [staticcheck](https://staticcheck.io/), [golangci-lint](https://golangci-lint.run/)


> 💡 Uruchom analizę z panelu SunGo Tools lub użyj komendy `SunGo: Code Review`.

---
## ⭐ Co nowego (v2.0.0) – Github templates

###  📦 Tworzenie projektów z szablonów Git (GitHub Templates)
Funkcja umożliwia błyskawiczne rozpoczęcie pracy nad nowym projektem w oparciu o gotowe repozytoria Git. Dostępna bezpośrednio z Creatora Projektów oraz narzędzi w panelu SunGo Tools.

**Jak to działa:**

**Wybierz źródło:** W kreatorze projektów kliknij przycisk "📦 From GitHub Template" lub wybierz "Project from GitHub" z menu SunGo Tools po lewej stronie.
**Nazwij projekt:** Wpisz nazwę projektu w panelu bocznym kreatora.
**Wybierz szablon:** SunGo Templates: Rozszerzenie pobiera listę z GitHub API i wyświetla ją w formie czytelnych kafelków (np. Console CLI, Raylib 3D Scene, Gin REST API, Fyne Desktop App).
**From URL:** Możesz podać własny adres w polu Custom URL. Obsługiwane są formaty użytkownik/repo, pełne linki HTTPS oraz SSH.

**Automatyzacja:** Po kliknięciu Create Project, rozszerzenie:

- Wykonuje git clone --depth=1 (szybkie pobranie najnowszej migawki).
- Automatycznie usuwa folder .git/, abyś otrzymał "czysty" projekt (No .git history – clean project).
- Kopiuje pliki bezpośrednio do Twojego workspace, gotowe do pracy.

---
## ⭐ Co nowego (v1.9.1) – Ulubione projekty i Przeglądarka Go Doc

### ⭐ Ulubione projekty

Przypinaj najczęściej używane projekty na górę panelu SunGo dla natychmiastowego dostępu — koniec ze scrollowaniem przez długie listy projektów.

**Jak używać:**

- **Najedź** na projekt w drzewie → kliknij ikonkę ⭐, aby przypiąć
- **Najedź** na ulubiony projekt → kliknij ikonkę odpięcia, aby usunąć z ulubionych
- Lub **kliknij prawym przyciskiem** → **Przypnij do ulubionych** / **Odepnij z ulubionych**

Przypięte projekty pojawiają się w dedykowanej sekcji **★ ULUBIONE** na górze panelu bocznego oraz jako złote chipy w Dashboardzie Home. Automatycznie znikają z głównej listy projektów, aby uniknąć duplikatów.

Ulubione są przechowywane w globalnym stanie rozszerzenia i przeżywają restart VS Code.

---

### 📖 Przeglądarka Go Doc

Pełnoprawna przeglądarka dokumentacji Go wbudowana bezpośrednio w VS Code — dostępna z panelu **SunGo Tools** (kliknij `$(book)` Go Doc Viewer).

| Funkcja | Opis |
|---|---|
| **Przeglądarka importów** | Automatycznie odczytuje instrukcje `import` z aktywnego pliku `.go` i wyświetla je jako klikalne linki |
| **Standard / Zewnętrzne** | Importy podzielone na dwie grupy dla szybkiego przeglądu |
| **Wyszukiwarka pakietów** | Wpisz `fmt`, `net/http` lub `sync.WaitGroup` — naciśnij Enter, aby natychmiast załadować dokumentację |
| **Nawigacja** | Przyciski ← → do przeglądania historii, jak w przeglądarce internetowej |
| **Kolorowanie składni** | `func` niebiesko · `type` złoto · `const` bursztynowo · `var` różowo |
| **pkg.go.dev** | Przycisk 🌐 otwiera aktualny pakiet na `pkg.go.dev` |

> 💡 **Wskazówka:** Kliknij **↺ Odśwież** na górnym pasku po przełączeniu na inny plik `.go`, aby zaktualizować listę importów.


---

## 🐹 Co nowego (v1.8.3) – Asystent Gopher

Panel SunGo Manager ma teraz żywego towarzysza. Kliknij ikonę **☀️ SunGo** na pasku aktywności VS Code, aby otworzyć panel — Asystent Gopher siedzi tuż pod listą projektów.

> 💡 **Wskazówka:** Panel Gophera możesz przeciągnąć na **prawy pasek boczny** (Secondary Sidebar — tam gdzie siedzi Copilot) dla stałego widoku towarzyszącego. VS Code zapamiętuje tę pozycję między sesjami.

### Jak to działa

Gopher reaguje automatycznie — bez żadnej konfiguracji. Obserwuje diagnostykę Go i odpowiada na każdą akcję SunGo:

| Stan | Kiedy się pojawia |
|---|---|
| 📖 **Idle** – okulary, czyta książkę | Stan domyślny, brak aktywnej operacji |
| ⚙️ **Budowanie** – klucz, wirująca zębatka | Podczas `go build` |
| 🚀 **Uruchomiony** – laptop, pasek postępu | Podczas `go run` |
| 🧪 **Testy** – skupiony, pasek postępu | Podczas `go test` |
| 🔍 **Go Vet** – okulary + zębatka | Podczas analizy statycznej |
| 📝 **Go Fmt** – spokojny, otwarta książka | Podczas formatowania kodu |
| ❌ **Błąd** – łzy, czerwone X | Wykryto błąd kompilacji |
| 🎉 **OK** – szczęśliwe oczy, gwiazdki, confetti | Build zakończony sukcesem! |

### Interakcja z Gopherem

- **Kliknij** bańkę dymkową lub przycisk **🐹 Mądrość Gophera** → nowa wskazówka Go w Twoim języku (EN/PL)
- **Kliknij 3 razy** w ciągu 2 sekund ....

### Przeniesienie Gophera na prawą stronę

1. Otwórz panel SunGo (ikona `☀️` na pasku aktywności)
2. Kliknij prawym przyciskiem nagłówek sekcji **Gopher Assistant**
3. Wybierz **Move View** → **Secondary Side Bar**

Od tego momentu Gopher siedzi po prawej stronie na stałe.

---

## 🚀 Co nowego (v1.6.1)

### 🧰 Dual Repository
- Dodałem moduł obsługi repozytoriów Git. Nie zastępuje on wbudowanej w VS Code obsługi systemów kontroli wersji, lecz dodaje możliwość wysyłania wybranych plików (za pomocą pickera) do dowolnego zewnętrznego repozytorium.

- Jest to szczególnie przydatne, gdy pracujesz w prywatnym repozytorium z kodem źródłowym, a chcesz publikować jedynie wybrane pliki (np. pliki binarne) w osobnym, publicznym repozytorium.

- Uniwersalna kompatybilność: Działa niezależnie od aktualnie otwartego projektu. Używaj go do łączenia dowolnego workspace'u z zewnętrznymi repozytoriami wydań lub kopii zapasowych.

### Wybór plików:
* Kliknij, aby wybrać plik
* Ctrl + Klik, aby wybrać wiele plików
* Shift + Klik, aby wybrać zakres plików

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
