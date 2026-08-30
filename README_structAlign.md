[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Struct Field Alignment Optimizer – Setup & Usage Guide

SunGo includes a built-in struct memory layout analyzer that finds wasted padding caused by field order and can reorder fields for you with a single click.  
Access it via the **📦 Struct Field Alignment** entry in the SunGo Tools panel.

No external tools required — this is a self-contained analyzer, same philosophy as Code Metrics.

---

## 📋 Step 1 – Open the panel

Unlike the Binary Analyzer, this tool doesn't need a compiled binary — it works directly on your source code. Just click **Struct Field Alignment** in SunGo Tools; it scans every `.go` file in your project (excluding `vendor/` and `_test.go` files) and lists every struct it found.

---

## 🔬 Step 2 – Reading the results

### Overview

Four quick counters: total structs found, how many can be optimized, total bytes wasted across the project, and how many were skipped (see below).

### Structs to Optimize

Each entry shows the struct's current size vs. its optimal size (e.g. "24 → 16 bytes"), a badge with the exact bytes saved, and two rows of field chips — **Current** order and **Optimal** order — so you can see exactly which fields would move. Click the struct name to jump to its declaration; click **🔧 Fix** to reorder the fields automatically and reformat the file.

### Already Optimal / Skipped

Structs with zero wasted bytes are listed separately for reference. Structs are skipped (and excluded from the byte-waste calculation) when they:
- use generic type parameters (`type Stack[T any] struct {`) — size depends on instantiation, can't be computed statically;
- contain a manual padding field named `_` — usually intentional (e.g. for cgo/hardware layouts), so SunGo leaves it alone;
- contain an inline nested type spanning multiple lines — not safely rewritable;
- have no fields at all.

### Target Architecture

The byte counts depend on pointer/int size, which differs by architecture. SunGo reads your `sungo.build.targetArch` setting automatically (4-byte words on `arm`, 8-byte on `amd64`/`arm64`). Use the **Target: 64-bit / 32-bit** button in the panel header to preview the other architecture without changing your actual build setting.

---

## ⚠️ Common Issues

**"≈ estimated" badge next to a struct** – The struct contains a field whose type comes from another package (not defined in your project) or couldn't be resolved precisely. SunGo estimates it as one machine word rather than guessing a specific size — the byte counts for that struct may be slightly off.

**Struct doesn't show up in the list at all** – Check that its `type Name struct {` line is written on a single line (the standard `gofmt` style). Multi-line signatures aren't scanned in this version.

**"Fix" button is missing** – Only structs with actual wasted bytes (waste > 0) get a Fix button; already-optimal structs don't need one.

**Standalone comments between fields disappeared after Fix** – A known limitation: comment lines that aren't attached to a specific field (sitting alone between two fields) are not preserved by the automatic reorder. Comments on the *same line* as a field are preserved correctly.

---
---

# [PL] SunGo Optymalizator Wyrównania Pól Struktur – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany analizator układu pamięci structów, który znajduje zmarnowany padding wynikający z kolejności pól i potrafi przestawić pola jednym kliknięciem.  
Dostęp przez wpis **📦 Struct Field Alignment** w panelu SunGo Tools.

Nie wymaga żadnych zewnętrznych narzędzi — to samodzielny analizator, ta sama filozofia co Code Metrics.

---

## 📋 Krok 1 – Otwórz panel

W przeciwieństwie do Binary Analyzer, to narzędzie nie potrzebuje skompilowanej binarki — działa bezpośrednio na kodzie źródłowym. Wystarczy kliknąć **Struct Field Alignment** w SunGo Tools; skanuje każdy plik `.go` w projekcie (pomijając `vendor/` i pliki `_test.go`) i wypisuje każdy znaleziony struct.

---

## 🔬 Krok 2 – Odczytywanie wyników

### Przegląd

Cztery szybkie liczniki: łączna liczba znalezionych structów, ile z nich można zoptymalizować, łączna liczba zmarnowanych bajtów w całym projekcie oraz ile zostało pominiętych (patrz niżej).

### Structy do optymalizacji

Każdy wpis pokazuje obecny rozmiar structa vs. rozmiar optymalny (np. "24 → 16 bajtów"), plakietkę z dokładną liczbą zaoszczędzonych bajtów oraz dwa rzędy "chipów" pól — kolejność **Current** i **Optimal** — dzięki czemu widać dokładnie, które pola się przesuną. Kliknięcie nazwy structa przenosi do jego deklaracji; kliknięcie **🔧 Fix** automatycznie przestawia pola i formatuje plik.

### Już optymalne / Pominięte

Structy z zerowym marnotrawstwem bajtów są wypisane osobno dla informacji. Structy są pomijane (i wykluczone z liczenia zmarnowanych bajtów), gdy:
- używają parametrów generycznych (`type Stack[T any] struct {`) — rozmiar zależy od instancjacji, nie da się go policzyć statycznie;
- zawierają ręczne pole paddingowe o nazwie `_` — zwykle celowe (np. dla layoutów cgo/sprzętowych), więc SunGo ich nie rusza;
- zawierają zagnieżdżony typ rozbity na kilka linii — nie da się tego bezpiecznie przepisać;
- w ogóle nie mają pól.

### Docelowa architektura

Liczba bajtów zależy od rozmiaru wskaźnika/int, który różni się w zależności od architektury. SunGo automatycznie odczytuje ustawienie `sungo.build.targetArch` (4-bajtowe słowo na `arm`, 8-bajtowe na `amd64`/`arm64`). Przycisk **Target: 64-bit / 32-bit** w nagłówku panelu pozwala podejrzeć drugą architekturę bez zmiany faktycznego ustawienia builda.

---

## ⚠️ Częste problemy

**Plakietka "≈ estimated" przy strukcie** – Struct zawiera pole, którego typ pochodzi z innego pakietu (nie zdefiniowanego w Twoim projekcie) albo nie dało się go precyzyjnie rozwiązać. SunGo szacuje go jako jedno słowo maszynowe zamiast zgadywać konkretny rozmiar — liczby bajtów dla tego structa mogą być lekko nieprecyzyjne.

**Struct w ogóle nie pojawia się na liście** – Sprawdź, czy linia `type Name struct {` jest zapisana w jednej linii (standardowy styl `gofmt`). Sygnatury rozbite na kilka linii nie są skanowane w tej wersji.

**Brak przycisku "Fix"** – Przycisk Fix pojawia się tylko przy strukturach z realnie zmarnowanymi bajtami (waste > 0); już optymalne structy go nie potrzebują.

**Samodzielne komentarze między polami zniknęły po Fix** – Znane ograniczenie: linie komentarzy nieprzypisane do konkretnego pola (stojące samotnie między dwoma polami) nie są zachowywane przy automatycznym przestawianiu. Komentarze w *tej samej linii* co pole są zachowywane poprawnie.
