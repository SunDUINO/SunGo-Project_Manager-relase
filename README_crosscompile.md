
[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.


# [EN] SunGo – CGO Cross-Compilation Guide

SunGo supports cross-compilation via `sungo.build.targetOS` and `sungo.build.targetArch` settings.  
For pure Go projects (no CGO) this works out of the box. For projects using CGO libraries (Raylib, Fyne, Qt, SDL2…) a cross-compiler toolchain is required.

> ⚠️ **Note:** SunGo automatically detects CGO usage and blocks cross-compilation with an informative message if no toolchain is available.

---

## 🟦 Pure Go (no CGO)

Libraries like **Ebiten**, `net/http`, `encoding/json` and the Go standard library do **not** require CGO.  
Cross-compilation works with a single setting change — no additional tools needed.

| Target OS | Works out of the box |
|-----------|---------------------|
| Windows   | ✅ |
| Linux     | ✅ |
| macOS     | ✅ |

---

## 🟧 CGO Libraries

| Library | CGO required |
|---------|-------------|
| Raylib (`gen2brain/raylib-go`) | ✅ |
| Fyne (`fyne.io/fyne`) | ✅ |
| Qt (`therecipe/qt`) | ✅ |
| SDL2 (`go-sdl2`) | ✅ |
| OpenGL / GLFW (`go-gl`) | ✅ |
| SQLite (`mattn/go-sqlite3`) | ✅ |
| GTK3 (`gotk3`) | ✅ |
| Ebiten (`hajimehoshi/ebiten`) | ❌ pure Go |

---

## 🐧 Linux → 🪟 Windows

Install the MinGW-w64 cross-compiler:

```bash
# Ubuntu / Debian
sudo apt install mingw-w64

# Arch Linux
sudo pacman -S mingw-w64-gcc

# Fedora
sudo dnf install mingw64-gcc
```

Build with SunGo (settings):
```
sungo.build.targetOS   = windows
sungo.build.targetArch = amd64
```

If you need to build manually:
```bash
CC=x86_64-w64-mingw32-gcc CGO_ENABLED=1 GOOS=windows GOARCH=amd64 \
  go build -o bin/cross/MyApp_windows_amd64.exe ./src/main.go
```

For 32-bit Windows:
```bash
CC=i686-w64-mingw32-gcc CGO_ENABLED=1 GOOS=windows GOARCH=386 \
  go build -o bin/cross/MyApp_windows_386.exe ./src/main.go
```

---

## 🐧 Linux → 🍎 macOS

Cross-compiling to macOS with CGO requires **osxcross** and the **macOS SDK**.  
This is legally restricted — the macOS SDK may only be used on Apple hardware.

### Steps (advanced):

1. Obtain the macOS SDK (from a macOS machine or Xcode):
```bash
# On a macOS machine:
xcodebuild -showsdks
# Copy /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk
```

2. Build osxcross:
```bash
git clone https://github.com/tpoechtrager/osxcross
cd osxcross
# Place MacOSX.sdk.tar.xz in tarballs/
./build.sh
```

3. Build:
```bash
PATH="$PATH:/path/to/osxcross/target/bin" \
CC=o64-clang CGO_ENABLED=1 GOOS=darwin GOARCH=amd64 \
  go build -o bin/cross/MyApp_darwin_amd64 ./src/main.go
```

> ⚠️ This setup is complex. For macOS targets it is strongly recommended to build natively on a macOS machine.

---

## 🪟 Windows → 🐧 Linux

**Option A – WSL2 (recommended):**

1. Install WSL2 with Ubuntu:
```powershell
wsl --install
```

2. Inside WSL2:
```bash
sudo apt install gcc
```

3. Build inside WSL2 using SunGo or manually:
```bash
CGO_ENABLED=1 GOOS=linux GOARCH=amd64 \
  go build -o bin/cross/MyApp_linux_amd64 ./src/main.go
```

**Option B – Linux sysroot (advanced):**  
Requires setting up a Linux sysroot and cross GCC — not recommended for most users.

---

## 🪟 Windows → 🍎 macOS

Cross-compiling to macOS from Windows with CGO is **not supported** without:
- A macOS SDK (legally restricted to Apple hardware)
- osxcross built on a Linux/macOS host

> ✅ **Recommended:** Use a macOS machine or a macOS CI runner (GitHub Actions `macos-latest`) to build macOS binaries natively.

---

## 🍎 macOS → 🪟 Windows

Install MinGW via Homebrew:

```bash
brew install mingw-w64
```

Build:
```bash
CC=x86_64-w64-mingw32-gcc CGO_ENABLED=1 GOOS=windows GOARCH=amd64 \
  go build -o bin/cross/MyApp_windows_amd64.exe ./src/main.go
```

---

## 🍎 macOS → 🐧 Linux

Requires a Linux cross-compiler. Install via Homebrew:

```bash
brew install FiloSottile/musl-cross/musl-cross
```

Build:
```bash
CC=x86_64-linux-musl-gcc CGO_ENABLED=1 GOOS=linux GOARCH=amd64 \
  go build -o bin/cross/MyApp_linux_amd64 ./src/main.go
```

---

## 💡 GitHub Actions – recommended approach for macOS targets

If you need macOS binaries without a Mac, use GitHub Actions:

```yaml
jobs:
  build-macos:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-go@v5
        with:
          go-version: '1.22'
      - run: go build -o bin/MyApp_darwin_amd64 ./src/main.go
```

---

---

# [PL] SunGo – Przewodnik Cross-Compilation z CGO

SunGo obsługuje cross-compilation przez ustawienia `sungo.build.targetOS` i `sungo.build.targetArch`.  
Dla projektów w czystym Go (bez CGO) działa od razu po zmianie ustawienia. Dla projektów z bibliotekami CGO (Raylib, Fyne, Qt, SDL2…) wymagany jest cross-compiler toolchain.

> ⚠️ **Uwaga:** SunGo automatycznie wykrywa użycie CGO i blokuje cross-compilation z informacyjnym komunikatem gdy toolchain nie jest dostępny.

---

## 🟦 Czyste Go (bez CGO)

Biblioteki takie jak **Ebiten**, `net/http`, `encoding/json` i biblioteka standardowa Go **nie wymagają** CGO.  
Cross-compilation działa po zmianie ustawienia – bez żadnych dodatkowych narzędzi.

| Docelowy system | Działa od razu |
|-----------------|---------------|
| Windows         | ✅ |
| Linux           | ✅ |
| macOS           | ✅ |

---

## 🟧 Biblioteki CGO

| Biblioteka | Wymaga CGO |
|------------|-----------|
| Raylib (`gen2brain/raylib-go`) | ✅ |
| Fyne (`fyne.io/fyne`) | ✅ |
| Qt (`therecipe/qt`) | ✅ |
| SDL2 (`go-sdl2`) | ✅ |
| OpenGL / GLFW (`go-gl`) | ✅ |
| SQLite (`mattn/go-sqlite3`) | ✅ |
| GTK3 (`gotk3`) | ✅ |
| Ebiten (`hajimehoshi/ebiten`) | ❌ czyste Go |

---

## 🐧 Linux → 🪟 Windows

Zainstaluj cross-compiler MinGW-w64:

```bash
# Ubuntu / Debian
sudo apt install mingw-w64

# Arch Linux
sudo pacman -S mingw-w64-gcc

# Fedora
sudo dnf install mingw64-gcc
```

Ustawienia w SunGo:
```
sungo.build.targetOS   = windows
sungo.build.targetArch = amd64
```

Ręczne wywołanie:
```bash
CC=x86_64-w64-mingw32-gcc CGO_ENABLED=1 GOOS=windows GOARCH=amd64 \
  go build -o bin/cross/MyApp_windows_amd64.exe ./src/main.go
```

---

## 🐧 Linux → 🍎 macOS

Cross-compilation na macOS z CGO wymaga **osxcross** i **macOS SDK**.  
Użycie SDK jest prawnie ograniczone – może być stosowane wyłącznie na sprzęcie Apple.

### Kroki (zaawansowane):

1. Pobierz macOS SDK (z maszyny macOS lub Xcode):
```bash
# Na maszynie macOS:
xcodebuild -showsdks
# Skopiuj /Library/Developer/CommandLineTools/SDKs/MacOSX.sdk
```

2. Zbuduj osxcross:
```bash
git clone https://github.com/tpoechtrager/osxcross
cd osxcross
# Umieść MacOSX.sdk.tar.xz w tarballs/
./build.sh
```

3. Kompiluj:
```bash
PATH="$PATH:/path/to/osxcross/target/bin" \
CC=o64-clang CGO_ENABLED=1 GOOS=darwin GOARCH=amd64 \
  go build -o bin/cross/MyApp_darwin_amd64 ./src/main.go
```

> ⚠️ Konfiguracja jest skomplikowana. Dla celów macOS zalecane jest budowanie natywnie na maszynie macOS.

---

## 🪟 Windows → 🐧 Linux

**Opcja A – WSL2 (zalecane):**

1. Zainstaluj WSL2 z Ubuntu:
```powershell
wsl --install
```

2. Wewnątrz WSL2:
```bash
sudo apt install gcc
```

3. Kompiluj wewnątrz WSL2:
```bash
CGO_ENABLED=1 GOOS=linux GOARCH=amd64 \
  go build -o bin/cross/MyApp_linux_amd64 ./src/main.go
```

**Opcja B – Linux sysroot (zaawansowane):**  
Wymaga konfiguracji Linux sysroot i cross GCC – niezalecane dla większości użytkowników.

---

## 🪟 Windows → 🍎 macOS

Cross-compilation na macOS z Windows z CGO **nie jest wspierana** bez:
- macOS SDK (prawnie ograniczone do sprzętu Apple)
- osxcross zbudowanego na hoście Linux/macOS

> ✅ **Zalecane:** Użyj maszyny macOS lub runnera CI z macOS (GitHub Actions `macos-latest`) do natywnego budowania binarek macOS.

---

## 🍎 macOS → 🪟 Windows

Zainstaluj MinGW przez Homebrew:

```bash
brew install mingw-w64
```

Kompiluj:
```bash
CC=x86_64-w64-mingw32-gcc CGO_ENABLED=1 GOOS=windows GOARCH=amd64 \
  go build -o bin/cross/MyApp_windows_amd64.exe ./src/main.go
```

---

## 🍎 macOS → 🐧 Linux

Wymaga Linux cross-compilera. Zainstaluj przez Homebrew:

```bash
brew install FiloSottile/musl-cross/musl-cross
```

Kompiluj:
```bash
CC=x86_64-linux-musl-gcc CGO_ENABLED=1 GOOS=linux GOARCH=amd64 \
  go build -o bin/cross/MyApp_linux_amd64 ./src/main.go
```

---

## 💡 GitHub Actions – zalecane dla binarek macOS

Jeśli potrzebujesz binarek macOS bez Maca, użyj GitHub Actions:

```yaml
jobs:
  build-macos:
    runs-on: macos-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-go@v5
        with:
          go-version: '1.22'
      - run: go build -o bin/MyApp_darwin_amd64 ./src/main.go
```
