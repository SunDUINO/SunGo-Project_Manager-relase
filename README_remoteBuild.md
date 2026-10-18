[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Remote Build over SSH – Setup & Usage Guide

SunGo can build your project on another computer over SSH and copy the finished binary back into your project — without leaving VS Code. The direction follows the computer VS Code runs on:

| VS Code runs on | Build host | Binary lands in |
|-----------------|------------|-----------------|
| **Windows** | **Linux** | `bin/linux/<project>` |
| **Linux** (or macOS) | **Windows** | `bin/windows/<project>.exe` |

> 💡 This is the way to go for CGO / GUI projects (Ebitengine, Fyne, raylib, webview…) that cannot be cross-compiled. Pure-Go projects can usually be cross-compiled locally with SunGo's normal build (`sungo.build.targetOS`).

---

## ☑️ Step 1 – Turn it on

Open the settings (Ctrl+,), section **SunGo – Remote Build (SSH)**, and tick **Enabled**. Only then does the tool appear in SunGo Tools as **Remote Build (SSH → Linux)** or **Remote Build (SSH → Windows)**, and its commands in the command palette. **Target OS** (`auto` / `linux` / `windows`) can force the direction — `auto` follows the table above.

The tool opens a small menu: **Build on Linux/Windows**, **Build on another host…** (with more than one host), **Test connection** and **Settings…**.

---

## 📋 Step 2 – Prepare the build host (once)

**Common:** SunGo uses the system `ssh` with `-o BatchMode=yes`, so it never asks for or stores passwords — the key login must work **without a password prompt**:

```bash
ssh user@192.168.0.10 echo ok
```

Accept the host key once in that terminal.

### 🐧 Linux host

* Public key in `~/.ssh/authorized_keys` on the host.
* Go (e.g. in `/usr/local/go`), `gcc`, `pkg-config` and the `-dev` packages your project needs (X11/GL for Ebitengine, GTK/WebKit for webview…).

### 🪟 Windows host

* **OpenSSH Server**: *Settings → System → Optional features → Add a feature → OpenSSH Server*, then start the **OpenSSH SSH Server** (`sshd`) service and set it to *Automatic*. Allow port 22 in the firewall if needed.
* **Where the key goes:** for a normal account `C:\Users\<user>\.ssh\authorized_keys`; for an account in the **Administrators** group `C:\ProgramData\ssh\administrators_authorized_keys` (this file must be accessible only to Administrators and SYSTEM). This is the most common cause of `Permission denied`.
* Go for Windows (default `C:\Program Files\Go\bin`). `tar.exe` and PowerShell are part of Windows 10/11. For CGO projects also a C compiler (e.g. MSYS2 / MinGW-w64 `gcc`) on the host's `PATH`.
* SunGo runs PowerShell scripts as `-EncodedCommand`, so it does not matter whether the sshd default shell is `cmd.exe` or PowerShell.

---

## ⚙️ Step 3 – Settings (Ctrl+,)

When no host is set yet, the first build opens the settings already filtered to `@ext:SunRiver-LotharTeaM.sungo-project-manager remoteBuild`. **Settings…** in the menu does the same.

> 🔒 **Privacy:** the connection settings have scope `machine` — they are stored **only in your VS Code user settings on this machine**. They are never written to the project's `.vscode/` folder (so they do not end up in your repository) and the extension itself ships with an empty host.

| Setting | Meaning |
|---------|---------|
| **Enabled** | Turns the whole tool on/off. |
| **Target OS** | `auto` (Windows → Linux host, Linux → Windows host), `linux` or `windows`. |
| **Host** | IP address or name of the build host (e.g. `192.168.0.10`). |
| **User** | SSH user name (key-based login). |
| **Port** | SSH port, default 22. |
| **Remote Dir** | Build folder on the host, default `~/build/${project}` (`${project}` = project folder name, `~` = home folder on the host — also on Windows). |
| **Go Bin** | Folder with the `go` binary. Empty = `/usr/local/go/bin` (Linux) or `C:\Program Files\Go\bin` (Windows). Needed because non-interactive ssh does not read the login profile. |
| **Go Toolchain** | `GOTOOLCHAIN` on the host. `auto` lets Go fetch the version required by `go.mod`. |
| **Webkit Shim** | *Linux host only, on by default.* For `webview_go`, which asks pkg-config for `webkit2gtk-4.0` — no longer shipped by Debian 13 / Ubuntu 24.04+. When the host has `4.1` but not `4.0`, SunGo creates small `.pc` files in `~/.cache/sungo/pkgconfig` pointing to `4.1`; on distros that still have `4.0` it changes nothing. |
| **Run Vet** | Run `go vet ./...` first (report only, never stops the build). |
| **Pack Tar Gz** | *Linux host only.* Also download `<project>_linux_<arch>.tar.gz`, which keeps the executable bit. |
| **Linux Output** | *Linux host only.* `binary` (just the binary), `appimage` (AppImage with icon and `.desktop`; needs `appimagetool` on the host) or `bundle` (tar.gz with program, icon, `.desktop` and `install.sh` that adds it to the menu). A Linux binary cannot carry an icon like an `.exe`; the icon comes from **Package › Icon Path** or `media/icon.png`. |
| **Package** | What to build (`auto` = `./src` if the project has a `src` folder, otherwise `.`). |
| **Exclude** | Top-level entries not sent to the host (default `bin`, `media`, `.git`, `.vscode`, `.sungo`, `node_modules`, `*.md`). |

The normal build settings also apply: `sungo.build.optimizeBinary` adds `-ldflags "-s -w"`, and on a Windows host `sungo.build.hideConsoleWindow` adds `-H=windowsgui`.

**Test connection** checks the key login and `go version` on the host.

**More than one build host?** Add the extra ones to `sungo.remoteBuild.hosts` in your user `settings.json` (fields `host`, `user`, `port`, `remoteDir`, `goBin`, `goToolchain`, `webkitShim`, optional `name`). SunGo then asks which host to use and remembers the choice per workspace; **Build on another host…** always asks.

---

## 🚀 Step 4 – Build

Run **Build on Linux/Windows**. In the **SunGo: Remote Build** Output panel you will see:

1. **Sending sources** – local `tar czf -` streamed into `tar xzf -` on the host. Files you deleted locally are also removed on the host (SunGo remembers what it sent in `.sungo_entries`). The host's Go build cache stays, so the next builds are fast.
2. **`go vet ./...` and `go build -v`** – live output. Remote paths (`src/main.go:12:3`, `C:\…\src\main.go:12:3`) are rewritten to your local files, so every error is clickable and also shows up in the **Problems** panel. `-v` lists the package being compiled.
3. **Downloading the binary** – into `bin/linux/<project>_v<version>` or `bin/windows/<project>_v<version>.exe` (version from `src/main.go`, as in the regular build; without it just `<project>`) (the folder is created when needed). The size is checked against the file on the host.

> ⏳ **Progress:** the notification shows the current step and has a **Cancel** button; a spinner in the status bar (`Remote: <project> — …`) keeps showing the step after you close the notification — click it to open the output. At the end it shows ✓ or ✗ for a few seconds.

> ℹ️ **Executable bit (Linux binary on Windows):** NTFS does not store the Unix `+x` flag. After copying the bare file to Linux run `chmod +x <project>` — or enable **Pack Tar Gz** and use the `.tar.gz`, which keeps it.

---

## 📱 Step 5 – Android APK (Linux host)

Projects with an Android Gradle project in `android/` get a separate **Remote Build (SSH → Android)** button in SunGo Tools, next to **Remote Build (SSH → Linux)** — one click starts the APK build (also the command **SunGo: Remote Build — Android APK (SSH → Linux)**).

1. SunGo sends the sources like the normal remote build (including `android/`).
2. On the host it runs the project's build script with `bash` — by default the first of `build_android.sh`, `android/build.sh`, `build.sh`. No `chmod +x` needed; Windows line endings in the host copy are fixed first. `ANDROID_HOME` defaults to **Android: Sdk** (`~/Android/Sdk`), Go and `platform-tools` are added to `PATH`.
3. The newest `.apk` built in this run (a copy the script put in `bin/`, otherwise Gradle's `outputs/apk`) is downloaded to **`bin/android/`** — e.g. `bin/android/SunGopher_AI-android_v01.11.00.apk`.
4. **Install (adb)** installs it on a phone connected to this computer and starts the app.

The Gradle cache and wrapper (`android/.gradle`, `android/build`, `android/app/build`, `gradlew`, `gradle/`) stay on the host between builds. The progress shows the script's `>> …` steps and the Gradle tasks; Go / Kotlin / Java errors are clickable.

| Setting | Meaning |
|---------|---------|
| **Android: Command** | `auto` (script detection) or your own script / command, e.g. `cd android && ./gradlew assembleRelease`. |
| **Android: Sdk** | Android SDK folder on the host, used when the host does not set `ANDROID_HOME`. |
| **Android: Adb** | Path to `adb` on this computer (empty = `adb` from `PATH`). |
| **Android: Install After Build** | Install and start the app automatically after a successful build. |

The phone needs **USB debugging** turned on. Requirements on the host: JDK 17+, Android SDK (`platforms`, `build-tools`, `platform-tools`), Go.

---

## 🩺 Troubleshooting

| Message | Cause / fix |
|---------|-------------|
| `Remote Build is turned off` | Tick **Remote Build › Enabled** in the settings. |
| `Permission denied (publickey…)` | Key login does not work — see Step 2. Windows host + admin account: key in `C:\ProgramData\ssh\administrators_authorized_keys`. |
| `Connection refused` / timeout | Windows host: is the `sshd` service running and port 22 allowed in the firewall? |
| `Host key verification failed` | Run `ssh user@host` once in a terminal and accept the host key. |
| `'go' not found on the host` | Set **Go Bin** to the folder containing `go`. |
| `Package webkit2gtk-4.0 was not found` | Linux host: **Webkit Shim** must be on (it is by default). If it is on and the error stays, the host has no WebKitGTK dev package at all: `sudo apt install libwebkit2gtk-4.1-dev`. |

---
---

# [PL] SunGo Zdalny build przez SSH – Instrukcja konfiguracji i użytkowania

SunGo potrafi zbudować projekt na innym komputerze przez SSH i skopiować gotową binarkę z powrotem do projektu — bez wychodzenia z VS Code. Kierunek zależy od komputera, na którym działa VS Code:

| VS Code działa na | Host budujący | Binarka trafia do |
|-------------------|---------------|-------------------|
| **Windows** | **Linux** | `bin/linux/<projekt>` |
| **Linux** (lub macOS) | **Windows** | `bin/windows/<projekt>.exe` |

> 💡 To najlepsza droga dla projektów z CGO / GUI (Ebitengine, Fyne, raylib, webview…), których nie da się skompilować skrośnie. Projekty w czystym Go zwykle da się skompilować skrośnie lokalnie zwykłym buildem SunGo (`sungo.build.targetOS`).

---

## ☑️ Krok 1 – Włączenie

Otwórz ustawienia (Ctrl+,), sekcję **SunGo – Remote Build (SSH)**, i zaznacz **Enabled**. Dopiero wtedy narzędzie pojawia się w SunGo Tools jako **Zdalny build (SSH → Linux)** albo **Zdalny build (SSH → Windows)**, a jego komendy w palecie komend. **Target OS** (`auto` / `linux` / `windows`) pozwala wymusić kierunek — `auto` działa według tabeli powyżej.

Narzędzie otwiera małe menu: **Zbuduj na Linux/Windows**, **Zbuduj na innym hoście…** (przy więcej niż jednym hoście), **Sprawdź połączenie** i **Ustawienia…**.

---

## 📋 Krok 2 – Przygotowanie hosta budującego (jednorazowo)

**Wspólne:** SunGo używa systemowego `ssh` z `-o BatchMode=yes`, więc nigdy nie pyta o hasła ani ich nie zapisuje — logowanie kluczem musi działać **bez pytania o hasło**:

```bash
ssh user@192.168.0.10 echo ok
```

Raz zaakceptuj klucz hosta w tym terminalu.

### 🐧 Host Linux

* Klucz publiczny w `~/.ssh/authorized_keys` na hoście.
* Go (np. w `/usr/local/go`), `gcc`, `pkg-config` i pakiety `-dev`, których potrzebuje projekt (X11/GL dla Ebitengine, GTK/WebKit dla webview…).

### 🪟 Host Windows

* **Serwer OpenSSH**: *Ustawienia → System → Funkcje opcjonalne → Dodaj funkcję → Serwer OpenSSH*, potem uruchom usługę **OpenSSH SSH Server** (`sshd`) i ustaw ją na *Automatycznie*. W razie potrzeby odblokuj port 22 w zaporze.
* **Gdzie trafia klucz:** dla zwykłego konta `C:\Users\<użytkownik>\.ssh\authorized_keys`; dla konta z grupy **Administratorzy** `C:\ProgramData\ssh\administrators_authorized_keys` (plik musi być dostępny tylko dla Administratorów i SYSTEM). To najczęstsza przyczyna `Permission denied`.
* Go dla Windows (domyślnie `C:\Program Files\Go\bin`). `tar.exe` i PowerShell są częścią Windows 10/11. Dla projektów z CGO także kompilator C (np. `gcc` z MSYS2 / MinGW-w64) w `PATH` hosta.
* SunGo uruchamia skrypty PowerShell jako `-EncodedCommand`, więc nie ma znaczenia, czy domyślną powłoką sshd jest `cmd.exe`, czy PowerShell.

---

## ⚙️ Krok 3 – Ustawienia (Ctrl+,)

Gdy host nie jest jeszcze ustawiony, pierwszy build sam otwiera ustawienia z filtrem `@ext:SunRiver-LotharTeaM.sungo-project-manager remoteBuild`. To samo robią **Ustawienia…** w menu.

> 🔒 **Prywatność:** ustawienia połączenia mają scope `machine` — są zapisywane **wyłącznie w ustawieniach użytkownika VS Code na tym komputerze**. Nigdy nie trafiają do folderu `.vscode/` projektu (więc nie wylądują w repozytorium), a samo rozszerzenie zawiera pusty host.

| Ustawienie | Znaczenie |
|------------|-----------|
| **Enabled** | Włącza/wyłącza całe narzędzie. |
| **Target OS** | `auto` (Windows → host Linux, Linux → host Windows), `linux` albo `windows`. |
| **Host** | Adres IP lub nazwa hosta budującego (np. `192.168.0.10`). |
| **User** | Nazwa użytkownika SSH (logowanie kluczem). |
| **Port** | Port SSH, domyślnie 22. |
| **Remote Dir** | Folder budowania na hoście, domyślnie `~/build/${project}` (`${project}` = nazwa folderu projektu, `~` = katalog domowy na hoście — także na Windows). |
| **Go Bin** | Folder z programem `go`. Puste = `/usr/local/go/bin` (Linux) albo `C:\Program Files\Go\bin` (Windows). Potrzebne, bo nieinteraktywne ssh nie czyta profilu logowania. |
| **Go Toolchain** | `GOTOOLCHAIN` na hoście. `auto` pozwala Go pobrać wersję wymaganą przez `go.mod`. |
| **Webkit Shim** | *Tylko host Linux, domyślnie włączone.* Dla `webview_go`, który pyta pkg-config o `webkit2gtk-4.0` — Debian 13 / Ubuntu 24.04+ już go nie mają. Gdy host ma `4.1`, a nie ma `4.0`, SunGo tworzy małe pliki `.pc` w `~/.cache/sungo/pkgconfig` wskazujące na `4.1`; na dystrybucjach, które mają `4.0`, nic nie zmienia. |
| **Run Vet** | Najpierw `go vet ./...` (tylko raport, nigdy nie przerywa buildu). |
| **Pack Tar Gz** | *Tylko host Linux.* Pobieraj też `<projekt>_linux_<arch>.tar.gz`, który zachowuje bit wykonywalności. |
| **Linux Output** | *Tylko host Linux.* `binary` (sama binarka), `appimage` (AppImage z ikoną i `.desktop`; wymaga `appimagetool` na hoście) albo `bundle` (tar.gz z programem, ikoną, `.desktop` i `install.sh`, który dodaje go do menu). Binarka linuksowa nie może mieć ikony jak `.exe`; ikona pochodzi z **Package › Icon Path** albo `media/icon.png`. |
| **Package** | Co budować (`auto` = `./src`, jeśli projekt ma folder `src`, w przeciwnym razie `.`). |
| **Exclude** | Wpisy najwyższego poziomu, które nie są wysyłane (domyślnie `bin`, `media`, `.git`, `.vscode`, `.sungo`, `node_modules`, `*.md`). |

Działają też ustawienia zwykłego buildu: `sungo.build.optimizeBinary` dodaje `-ldflags "-s -w"`, a na hoście Windows `sungo.build.hideConsoleWindow` dodaje `-H=windowsgui`.

**Sprawdź połączenie** testuje logowanie kluczem i `go version` na hoście.

**Więcej hostów budujących?** Dopisz kolejne do `sungo.remoteBuild.hosts` w `settings.json` użytkownika (pola `host`, `user`, `port`, `remoteDir`, `goBin`, `goToolchain`, `webkitShim`, opcjonalnie `name`). SunGo zapyta wtedy, którego hosta użyć, i zapamięta wybór per workspace; **Zbuduj na innym hoście…** pyta zawsze.

---

## 🚀 Krok 4 – Build

Uruchom **Zbuduj na Linux/Windows**. W panelu Output **SunGo: Remote Build** zobaczysz:

1. **Wysyłanie źródeł** – lokalny `tar czf -` przesyłany strumieniem do `tar xzf -` na hoście. Pliki usunięte lokalnie znikają też na hoście (SunGo pamięta, co wysłał, w `.sungo_entries`). Cache buildów Go na hoście zostaje, więc kolejne buildy są szybkie.
2. **`go vet ./...` i `go build -v`** – wynik na żywo. Zdalne ścieżki (`src/main.go:12:3`, `C:\…\src\main.go:12:3`) są zamieniane na lokalne pliki, więc każdy błąd jest klikalny i pojawia się też w panelu **Problems**. `-v` pokazuje aktualnie kompilowany pakiet.
3. **Pobieranie binarki** – do `bin/linux/<projekt>_v<wersja>` albo `bin/windows/<projekt>_v<wersja>.exe` (wersja z `src/main.go`, jak przy zwykłym buildzie; bez niej po prostu `<projekt>`) (folder jest tworzony w razie potrzeby). Rozmiar jest porównywany z plikiem na hoście.

> ⏳ **Postęp:** powiadomienie pokazuje bieżący etap i ma przycisk **Anuluj**; spinner na pasku stanu (`Remote: <projekt> — …`) pokazuje etap także po zamknięciu powiadomienia — kliknięcie otwiera wynik. Na koniec przez kilka sekund widać ✓ lub ✗.

> ℹ️ **Bit wykonywalności (binarka linuksowa na Windows):** NTFS nie przechowuje uniksowej flagi `+x`. Po skopiowaniu samego pliku na Linuksa wykonaj `chmod +x <projekt>` — albo włącz **Pack Tar Gz** i użyj `.tar.gz`, który ją zachowuje.

---

## 📱 Krok 5 – APK Androida (host Linux)

Projekty z projektem Gradle w `android/` mają w SunGo Tools osobny przycisk **Zdalny build (SSH → Android)**, obok **Zdalny build (SSH → Linux)** — jedno kliknięcie uruchamia build APK (także komenda **SunGo: Zdalny build — APK Androida (SSH → Linux)**).

1. SunGo wysyła źródła jak przy zwykłym zdalnym buildzie (razem z `android/`).
2. Na hoście uruchamia skrypt projektu przez `bash` — domyślnie pierwszy z `build_android.sh`, `android/build.sh`, `build.sh`. Bez `chmod +x`; windowsowe końce linii w kopii na hoście są najpierw poprawiane. `ANDROID_HOME` domyślnie = **Android: Sdk** (`~/Android/Sdk`), Go i `platform-tools` są dodawane do `PATH`.
3. Najnowszy `.apk` zbudowany w tym przebiegu (kopia, którą skrypt położył w `bin/`, a jeśli jej nie ma — wyjście Gradle `outputs/apk`) jest pobierany do **`bin/android/`** — np. `bin/android/SunGopher_AI-android_v01.11.00.apk`.
4. **Zainstaluj (adb)** instaluje go na telefonie podłączonym do tego komputera i uruchamia aplikację.

Cache i wrapper Gradle (`android/.gradle`, `android/build`, `android/app/build`, `gradlew`, `gradle/`) zostają na hoście między buildami. Postęp pokazuje etapy `>> …` ze skryptu i taski Gradle; błędy Go / Kotlin / Java są klikalne.

| Ustawienie | Znaczenie |
|------------|-----------|
| **Android: Command** | `auto` (wykrywanie skryptu) albo własny skrypt / polecenie, np. `cd android && ./gradlew assembleRelease`. |
| **Android: Sdk** | Folder Android SDK na hoście, używany, gdy host nie ustawia `ANDROID_HOME`. |
| **Android: Adb** | Ścieżka do `adb` na tym komputerze (puste = `adb` z `PATH`). |
| **Android: Install After Build** | Po udanym buildzie automatycznie zainstaluj i uruchom aplikację. |

Telefon musi mieć włączone **debugowanie USB**. Wymagania na hoście: JDK 17+, Android SDK (`platforms`, `build-tools`, `platform-tools`), Go.

---

## 🩺 Rozwiązywanie problemów

| Komunikat | Przyczyna / rozwiązanie |
|-----------|-------------------------|
| `Zdalny build jest wyłączony` | Zaznacz **Remote Build › Enabled** w ustawieniach. |
| `Permission denied (publickey…)` | Logowanie kluczem nie działa — patrz Krok 2. Host Windows + konto administratora: klucz w `C:\ProgramData\ssh\administrators_authorized_keys`. |
| `Connection refused` / timeout | Host Windows: czy usługa `sshd` działa i port 22 jest odblokowany w zaporze? |
| `Host key verification failed` | Uruchom raz `ssh user@host` w terminalu i zaakceptuj klucz hosta. |
| `'go' not found on the host` | Ustaw **Go Bin** na folder z programem `go`. |
| `Package webkit2gtk-4.0 was not found` | Host Linux: **Webkit Shim** musi być włączony (domyślnie jest). Jeśli jest, a błąd zostaje, na hoście brakuje pakietu deweloperskiego WebKitGTK: `sudo apt install libwebkit2gtk-4.1-dev`. |
