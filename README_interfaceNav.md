[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Interface Satisfaction Navigator – Setup & Usage Guide

SunGo includes a built-in CodeLens that answers two questions right where you're reading the code: "which types implement this interface?" and "which interfaces does this type implement?"

Unlike the other SunGo Tools, this one isn't a panel you open — it works automatically, inline, above your Go type declarations.

No external tools required — this is a self-contained analyzer, same philosophy as Code Metrics.

---

## 📋 Step 1 – Just open a Go file

The moment you open any `.go` file in your project, SunGo scans your whole workspace in the background and adds small clickable labels (CodeLenses) directly above every `interface` and named type declaration. There's nothing to configure or turn on.

---

## 🔬 Step 2 – Reading the CodeLenses

### Above an interface declaration

```go
🔎 3 implementations
type Writer interface {
    Write(p []byte) (n int, err error)
}
```

Click it to see a list of every type in your project that satisfies this interface. With a single match, it jumps straight there; with several, you get a quick-pick list.

### Above a struct or named type declaration

```go
🧩 implements 2 interfaces
type File struct { ... }
```

Click it to see which interfaces this type satisfies, with the same jump / quick-pick behavior.

Only types and interfaces that actually have at least one method get a lens — a plain data struct with no methods can't implement anything, so it stays lens-free to avoid clutter.

---

## 🔁 Step 3 – Keeping the index fresh

The index is rebuilt automatically every time you **save** a `.go` file. If you've just done a large rename or refactor across many files without saving each one individually (e.g. a search-and-replace across the whole project), use the **🧩 Interface Navigator (Refresh)** entry in the SunGo Tools panel to force a full re-index.

---

## ⚠️ Common Issues

**"No implementations found" on an interface I know has implementers** – Check that both the interface's method signatures and the implementing type's method signatures are written on a single line ending in `{` (standard `gofmt` style) — multi-line signatures aren't indexed in this version. Also double check the method signatures match *exactly*, including parameter and return types (not just names).

**"(≈ approx.)" next to an implementation count** – The interface embeds another interface that SunGo couldn't resolve locally (e.g. `io.Reader` from the standard library). SunGo still checks the methods it *can* see, but the count may be incomplete since it doesn't know the embedded interface's full method set.

**A lens shows a type that doesn't really implement the interface (or misses one that does)** – SunGo doesn't distinguish value-receiver vs. pointer-receiver method sets — it merges both together per type name. It also matches methods on **any type in the project sharing that method name**, without knowing which receiver they're actually attached to when names collide across types. This is an intentional trade-off to stay dependency-free; if you rely heavily on interface satisfaction checks, still run `go build`/`go vet` as the source of truth.

**Lenses don't update after I close and reopen VS Code** – They should appear again automatically the next time a Go file is opened; if not, use the manual **Interface Navigator (Refresh)** entry in SunGo Tools.

---
```go

//EN
//This code demonstrates how the Interface Navigator tool works. It includes examples of 
//types and their respective implementations. 

//PL
//Ten kod pozwala zobrazować działanie narzędzia Interface Navigator. 
//Zawiera praktyczne przykłady typów oraz odpowiadających im implementacji.

package main

import (
	"fmt"
	"math"
)

// Shape is implemented by anything that can report its area and perimeter.
type Shape interface {
	Area() float64
	Perimeter() float64
}

// Named is implemented by anything that has a name.
type Named interface {
	Name() string
}

// NamedShape embeds both Shape and Named — a type must satisfy all three
// methods (Area, Perimeter, Name) to implement it.
type NamedShape interface {
	Shape
	Named
}

type Circle struct {
	Radius float64
}

func (c Circle) Area() float64      { return math.Pi * c.Radius * c.Radius }
func (c Circle) Perimeter() float64 { return 2 * math.Pi * c.Radius }
func (c Circle) Name() string       { return "circle" }

type Square struct {
	Side float64
}

func (s Square) Area() float64      { return s.Side * s.Side }
func (s Square) Perimeter() float64 { return 4 * s.Side }

type Logger struct {
	Prefix string
}

func (l Logger) Name() string { return l.Prefix }

func main() {
	fmt.Println("Circle area:", Circle{Radius: 2}.Area())
	fmt.Println("Square area:", Square{Side: 3}.Area())
	fmt.Println("Logger name:", Logger{Prefix: "app"}.Name())
}

```
---

# [PL] SunGo Nawigator Zgodności Interfejsów – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany CodeLens, który odpowiada na dwa pytania dokładnie tam, gdzie czytasz kod: "które typy implementują ten interfejs?" i "jakie interfejsy implementuje ten typ?"

W przeciwieństwie do pozostałych narzędzi SunGo Tools, to nie jest panel, który się otwiera — działa automatycznie, w tekście, nad deklaracjami typów Go.

Nie wymaga żadnych zewnętrznych narzędzi — to samodzielny analizator, ta sama filozofia co Code Metrics.

---

## 📋 Krok 1 – Po prostu otwórz plik Go

W momencie otwarcia dowolnego pliku `.go` w projekcie, SunGo skanuje w tle cały workspace i dodaje małe klikalne etykiety (CodeLensy) bezpośrednio nad każdą deklaracją `interface` i nazwanego typu. Nie trzeba niczego konfigurować ani włączać.

---

## 🔬 Krok 2 – Odczytywanie CodeLensów

### Nad deklaracją interfejsu

```go
🔎 3 implementations
type Writer interface {
    Write(p []byte) (n int, err error)
}
```

Kliknięcie pokazuje listę wszystkich typów w projekcie, które spełniają ten interfejs. Przy jednym dopasowaniu następuje bezpośrednie przejście; przy kilku pojawia się lista szybkiego wyboru.

### Nad deklaracją structa lub nazwanego typu

```go
🧩 implements 2 interfaces
type File struct { ... }
```

Kliknięcie pokazuje, które interfejsy ten typ spełnia, z tym samym zachowaniem przejścia / szybkiego wyboru.

Lens pojawia się tylko przy typach i interfejsach, które mają co najmniej jedną metodę — zwykły struct z danymi bez metod nie może niczego implementować, więc pozostaje bez lensa, żeby nie zaśmiecać widoku.

---

## 🔁 Krok 3 – Odświeżanie indeksu

Indeks jest automatycznie przebudowywany za każdym razem, gdy **zapisujesz** plik `.go`. Jeśli właśnie wykonałeś duże przemianowanie lub refaktoring w wielu plikach bez zapisywania każdego z osobna (np. znajdź-i-zamień w całym projekcie), użyj wpisu **🧩 Interface Navigator (Refresh)** w panelu SunGo Tools, żeby wymusić pełne przeindeksowanie.

---

## ⚠️ Częste problemy

**"No implementations found" przy interfejsie, o którym wiem, że ma implementacje** – Sprawdź, czy zarówno sygnatury metod interfejsu, jak i sygnatury metod implementującego typu, są zapisane w jednej linii kończącej się na `{` (standardowy styl `gofmt`) — sygnatury rozbite na kilka linii nie są indeksowane w tej wersji. Sprawdź też, czy sygnatury metod pasują *dokładnie*, łącznie z typami parametrów i wartości zwracanych (nie tylko nazwami).

**"(≈ approx.)" przy liczbie implementacji** – Interfejs osadza inny interfejs, którego SunGo nie potrafił rozwiązać lokalnie (np. `io.Reader` z biblioteki standardowej). SunGo nadal sprawdza metody, które *widzi*, ale liczba może być niepełna, bo nie zna pełnego zestawu metod osadzonego interfejsu.

**Lens pokazuje typ, który tak naprawdę nie implementuje interfejsu (albo pomija taki, który implementuje)** – SunGo nie rozróżnia zestawu metod odbiornika wartościowego od wskaźnikowego — łączy oba dla danej nazwy typu. Dopasowuje też metody na **dowolnym typie w projekcie dzielącym tę nazwę metody**, nie wiedząc, do którego odbiornika faktycznie należą, gdy nazwy się powtarzają między typami. To celowy kompromis, żeby zostać bez zależności zewnętrznych; jeśli mocno polegasz na sprawdzaniu zgodności interfejsów, nadal traktuj `go build`/`go vet` jako źródło prawdy.

**Lensy nie aktualizują się po zamknięciu i ponownym otwarciu VS Code** – Powinny pojawić się ponownie automatycznie przy następnym otwarciu pliku Go; jeśli nie, użyj ręcznego wpisu **Interface Navigator (Refresh)** w SunGo Tools.

