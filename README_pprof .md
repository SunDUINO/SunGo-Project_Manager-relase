[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Profiler – Setup & Usage Guide

SunGo includes a built-in profiling panel powered by `go tool pprof`.  
Access it via the `$(pulse)` icon next to your active project in the Tree View.

---

## 📋 Step 1 – Instrument your code

Add profiling code to your `main.go`. You can copy the snippets directly from the SunGo Profiler panel.

### CPU Profile
```go
import (
    "os"
    "runtime/pprof"
)

func main() {
    // CPU profiling – place at the very beginning of main()
    f, _ := os.Create("cpu.prof")
    pprof.StartCPUProfile(f)
    defer pprof.StopCPUProfile()

    // ... rest of your code
}
```

### Memory Profile
```go
import (
    "os"
    "runtime/pprof"
)

func main() {
    // Memory profiling – defer runs at the end of main()
    fm, _ := os.Create("mem.prof")
    defer fm.Close()
    defer pprof.WriteHeapProfile(fm)

    // ... rest of your code
}
```

> 💡 You can use both CPU and Memory profiling at the same time — just add both blocks to `main()`.

---

## ▶️ Step 2 – Run your program

Build and run your project normally. The `.prof` files are created in the **project root directory** while the program runs.

```bash
go run ./src/main.go
# or
./bin/MyApp.exe
```

> ⚠️ For CPU profiling the program must run long enough to collect meaningful samples (at least a few seconds). For a game — play it for a while, then close it.

---

## 🔬 Step 3 – Open the Profiler panel

1. Click the **`$(pulse)`** icon next to your active project in the SunGo Tree View
2. SunGo automatically detects `cpu.prof` / `mem.prof` in the project root
3. The panel shows:
   - **Top 20 functions** table with visual percentage bars (flat time / memory)
   - **Flame Graph** SVG (requires Graphviz – see below)

You can also load any `.prof` file manually via the **📂 Load** button.

---

## 🔥 Flame Graph – Graphviz Installation

The Flame Graph requires **Graphviz** (`dot` command). Without it, only the Top 20 table is shown.

### 🪟 Windows

**Option A – winget (recommended):**
```powershell
winget install graphviz
```

**Option B – Chocolatey:**
```powershell
choco install graphviz
```

After installation, **add Graphviz to PATH** if it wasn't done automatically:

1. Open **System Properties** → **Advanced** → **Environment Variables**
2. Under **System Variables** find `Path` → click **Edit**
3. Add: `C:\Program Files\Graphviz\bin`
4. Click OK and **restart VS Code completely**

If Graphviz was installed but `dot` is still not found, add the PATH permanently via PowerShell **(run as Administrator)**:

```powershell
[System.Environment]::SetEnvironmentVariable(
    "PATH",
    [System.Environment]::GetEnvironmentVariable("PATH", "Machine") + ";C:\Program Files\Graphviz\bin",
    "Machine"
)
```

Verify in PowerShell:
```powershell
dot -V
# dot - graphviz version X.X.X
```

> ⚠️ Always restart VS Code after installing Graphviz – the extension reads PATH at startup.

---

### 🐧 Linux

```bash
# Ubuntu / Debian
sudo apt install graphviz

# Arch Linux
sudo pacman -S graphviz

# Fedora
sudo dnf install graphviz
```

Verify:
```bash
dot -V
```

No PATH changes needed on Linux – package managers add `dot` to `/usr/bin` automatically.

---

### 🍎 macOS

```bash
brew install graphviz
```

Verify:
```bash
dot -V
```

---

## 🖱️ Using the Flame Graph

| Action | Result |
|--------|--------|
| Scroll wheel | Zoom in / out |
| Click + drag | Pan the graph |
| 🌐 Open in Browser | Full resolution view in system browser |

> 💡 The flame graph is limited to nodes accounting for >1% of total time/memory (`-nodefraction=0.01`). This keeps the graph readable by hiding tiny helper functions.

---

## 📊 Reading the Top 20 Table

| Column | Description |
|--------|-------------|
| **Function** | Short function name (hover for full path) |
| **Flat** | Time/memory spent directly in this function |
| **Flat %** | Percentage of total — used for the visual bar |
| **Cum** | Cumulative time/memory including called functions |
| **Cum %** | Cumulative percentage |

> 💡 **Flat** tells you where time is actually spent. **Cum** tells you which call chains are most expensive.

---

## ⚠️ Common Issues

**"unrecognized profile format"** – Memory profile requires a compiled binary. SunGo automatically looks for the latest binary in `bin/`. Make sure you have built the project at least once before profiling memory.

**"Profile may be empty"** – Binary was compiled with `-s -w` (optimization strips symbols). Disable optimization in SunGo settings (`sungo.build.optimizeBinary = false`) and rebuild before profiling.

**Flame Graph not showing** – Graphviz not installed or not in PATH. See installation steps above. Always restart VS Code after installing.

**Very short programs** – CPU profiling needs at least 1–2 seconds of execution to collect samples. Hello World won't produce useful data.

---

---

# [PL] SunGo Profiler – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel profilowania oparty na `go tool pprof`.  
Dostęp przez ikonę `$(pulse)` przy aktywnym projekcie w drzewie projektów.

---

## 📋 Krok 1 – Instrumentacja kodu

Dodaj kod profilowania do `main.go`. Snippety możesz skopiować bezpośrednio z panelu SunGo Profiler.

### Profil CPU
```go
import (
    "os"
    "runtime/pprof"
)

func main() {
    // Profilowanie CPU – umieść na samym początku main()
    f, _ := os.Create("cpu.prof")
    pprof.StartCPUProfile(f)
    defer pprof.StopCPUProfile()

    // ... reszta kodu
}
```

### Profil pamięci (Memory)
```go
import (
    "os"
    "runtime/pprof"
)

func main() {
    // Profilowanie pamięci – defer wykonuje się na końcu main()
    fm, _ := os.Create("mem.prof")
    defer fm.Close()
    defer pprof.WriteHeapProfile(fm)

    // ... reszta kodu
}
```

> 💡 Możesz używać obu profili jednocześnie – dodaj oba bloki do `main()`.


```go
import (
    "os"
    "runtime/pprof"
)

func main() {

    // Profilowanie CPU – umieść na samym początku main()
    f, _ := os.Create("cpu.prof")
    pprof.StartCPUProfile(f)
    defer pprof.StopCPUProfile()

    // Profilowanie pamięci – defer wykonuje się na końcu main()
    fm, _ := os.Create("mem.prof")
    defer fm.Close()
    defer pprof.WriteHeapProfile(fm)

    // ... reszta kodu
}
```

---

## ▶️ Krok 2 – Uruchom program

Zbuduj i uruchom projekt normalnie. Pliki `.prof` powstają w **katalogu głównym projektu** podczas działania programu.

```bash
go run ./src/main.go
# lub
./bin/MyApp.exe
```

> ⚠️ Dla profilowania CPU program musi działać wystarczająco długo (co najmniej kilka sekund). Dla gry – zagraj chwilę, potem zamknij.

---

## 🔬 Krok 3 – Otwórz panel Profilera

1. Kliknij ikonę **`$(pulse)`** przy aktywnym projekcie w drzewie SunGo
2. SunGo automatycznie wykrywa `cpu.prof` / `mem.prof` w katalogu projektu
3. Panel pokazuje:
   - Tabelę **Top 20 funkcji** z wizualnymi paskami procentowymi
   - **Flame Graph** SVG (wymaga Graphviz – patrz poniżej)

Możesz też wczytać dowolny plik `.prof` ręcznie przez przycisk **📂 Load**.

---

## 🔥 Flame Graph – Instalacja Graphviz

Flame Graph wymaga **Graphviz** (komenda `dot`). Bez niego dostępna jest tylko tabela Top 20.

### 🪟 Windows

**Opcja A – winget (zalecane):**
```powershell
winget install graphviz
```

**Opcja B – Chocolatey:**
```powershell
choco install graphviz
```

Po instalacji **dodaj Graphviz do PATH** jeśli nie zostało zrobione automatycznie:

1. Otwórz **Właściwości systemu** → **Zaawansowane** → **Zmienne środowiskowe**
2. W sekcji **Zmienne systemowe** znajdź `Path` → kliknij **Edytuj**
3. Dodaj: `C:\Program Files\Graphviz\bin`
4. Kliknij OK i **zrestartuj VS Code całkowicie**

Jeśli Graphviz jest zainstalowany ale `dot` nadal nie jest widoczny, dodaj PATH trwale przez PowerShell **(uruchom jako Administrator)**:

```powershell
[System.Environment]::SetEnvironmentVariable(
    "PATH",
    [System.Environment]::GetEnvironmentVariable("PATH", "Machine") + ";C:\Program Files\Graphviz\bin",
    "Machine"
)
```

Weryfikacja w PowerShell:
```powershell
dot -V
# dot - graphviz version X.X.X
```

> ⚠️ Zawsze restartuj VS Code po instalacji Graphviz – rozszerzenie odczytuje PATH przy starcie.

---

### 🐧 Linux

```bash
# Ubuntu / Debian
sudo apt install graphviz

# Arch Linux
sudo pacman -S graphviz

# Fedora
sudo dnf install graphviz
```

Weryfikacja:
```bash
dot -V
```

Na Linuxie nie trzeba ręcznie dodawać do PATH – menedżer pakietów instaluje `dot` w `/usr/bin` automatycznie.

---

### 🍎 macOS

```bash
brew install graphviz
```

Weryfikacja:
```bash
dot -V
```

---

## 🖱️ Obsługa Flame Graph

| Akcja | Efekt |
|-------|-------|
| Kółko myszy | Zoom in / out |
| Klik + przeciągnij | Przesuwanie grafu |
| 🌐 Otwórz w przeglądarce | Pełna rozdzielczość w przeglądarce systemowej |

> 💡 Graf ograniczony jest do węzłów odpowiadających za >1% czasu/pamięci (`-nodefraction=0.01`). Dzięki temu pomijane są drobne funkcje pomocnicze i graf pozostaje czytelny.

---

## 📊 Odczytywanie tabeli Top 20

| Kolumna | Opis |
|---------|------|
| **Function** | Skrócona nazwa funkcji (najedź aby zobaczyć pełną ścieżkę) |
| **Flat** | Czas/pamięć spędzone bezpośrednio w tej funkcji |
| **Flat %** | Procent sumy – podstawa paska wizualnego |
| **Cum** | Czas/pamięć łącznie z wywoływanymi funkcjami |
| **Cum %** | Procent kumulatywny |

> 💡 **Flat** mówi gdzie faktycznie spędzany jest czas. **Cum** mówi które łańcuchy wywołań są najkosztowniejsze.

---

## ⚠️ Częste problemy

**"unrecognized profile format"** – Profil pamięci wymaga skompilowanej binarki. SunGo automatycznie szuka najnowszej binarki w `bin/`. Upewnij się że projekt był zbudowany co najmniej raz przed profilowaniem pamięci.

**"Profile may be empty"** – Binarka skompilowana z `-s -w` (optymalizacja usuwa symbole). Wyłącz optymalizację w ustawieniach SunGo (`sungo.build.optimizeBinary = false`) i zbuduj ponownie przed profilowaniem.

**Flame Graph się nie pojawia** – Graphviz nie zainstalowany lub nie w PATH. Sprawdź kroki instalacji powyżej. Zawsze restartuj VS Code po instalacji.

**Bardzo krótkie programy** – Profilowanie CPU potrzebuje co najmniej 1–2 sekund wykonania aby zebrać próbki. Hello World nie da użytecznych danych.
