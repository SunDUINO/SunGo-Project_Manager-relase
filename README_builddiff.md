[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Build Diff & Timeline – Setup & Usage Guide

SunGo includes a built-in build comparison panel: every time you build your project, a snapshot of your binary is recorded, so you can compare any two builds side by side and see exactly what changed.  
Access it via the **📊 Build Diff** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Build your project a few times

Each build you run through SunGo is captured as a snapshot (size, and per-symbol breakdown) and added to a persistent history — nothing to configure, it just accumulates as you work.

> 💡 The comparison only gets useful once you have at least two snapshots. Build once, make some changes, build again, then open the panel.

---

## 🔬 Step 2 – Compare two builds

Pick any two past snapshots and compare them. You'll see:

| Signal | Meaning |
|--------|---------|
| ▲ grew | This part of the binary got bigger between the two builds |
| ▼ shrunk | This part got smaller |
| + added | Present in the newer build only |
| – removed | Present in the older build only, gone in the newer one |

This is the fastest way to answer "why did my binary suddenly get bigger?" after adding a dependency or refactoring — instead of guessing, you see exactly which symbols changed.

---

## 🕐 Timeline

A running history of every build snapshot — size and timestamp — so you can spot a trend (steady growth, a sudden jump) even before doing a specific two-build comparison.

---

## ⚠️ Common Issues

**Only one entry in the history** – You need at least two builds for a comparison to have something to compare against. Keep building as you work.

**A dependency shows as "added" that I didn't add on purpose** – Transitive dependencies count too — a small direct dependency can quietly pull in a much larger one. Check `go mod graph` or the Dependency Graph tool to see the full chain.

**History grows large over a long project lifetime** – Snapshots are capped automatically so the history file doesn't grow without bound; older entries roll off as new ones are added.

---
---

# [PL] SunGo Build Diff & Timeline – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowany panel porównywania buildów: za każdym razem, gdy budujesz projekt, zapisywana jest migawka Twojej binarki, dzięki czemu możesz porównać dowolne dwa buildy obok siebie i zobaczyć dokładnie, co się zmieniło.  
Dostęp przez wpis **📊 Build Diff** w panelu SunGo Tools.

---

## 📋 Krok 1 – Zbuduj projekt kilka razy

Każdy build uruchomiony przez SunGo jest przechwytywany jako migawka (rozmiar oraz podział na symbole) i dodawany do trwałej historii — nic nie trzeba konfigurować, po prostu narasta w miarę pracy.

> 💡 Porównanie staje się użyteczne dopiero przy co najmniej dwóch migawkach. Zbuduj raz, wprowadź jakieś zmiany, zbuduj ponownie, a potem otwórz panel.

---

## 🔬 Krok 2 – Porównaj dwa buildy

Wybierz dwie dowolne wcześniejsze migawki i porównaj je. Zobaczysz:

| Sygnał | Znaczenie |
|--------|-----------|
| ▲ grew | Ta część binarki urosła między dwoma buildami |
| ▼ shrunk | Ta część zmalała |
| + added | Obecne tylko w nowszym buildzie |
| – removed | Obecne tylko w starszym buildzie, zniknęło w nowszym |

To najszybszy sposób, żeby odpowiedzieć na pytanie "dlaczego moja binarka nagle urosła?" po dodaniu zależności albo refaktoryzacji — zamiast zgadywać, widzisz dokładnie które symbole się zmieniły.

---

## 🕐 Historia (Timeline)

Bieżąca historia każdej migawki builda — rozmiar i czas — dzięki czemu widać trend (stopniowy wzrost, nagły skok) jeszcze przed konkretnym porównaniem dwóch buildów.

---

## ⚠️ Częste problemy

**Tylko jeden wpis w historii** – Potrzebujesz co najmniej dwóch buildów, żeby porównanie miało z czym porównywać. Buduj dalej w miarę pracy.

**Zależność pokazuje się jako "added", której nie dodałem świadomie** – Zależności tranzytywne też się liczą — mała, bezpośrednia zależność może po cichu ciągnąć za sobą dużo większą. Sprawdź `go mod graph` albo narzędzie Dependency Graph, żeby zobaczyć pełny łańcuch.

**Historia rośnie duża przy długim życiu projektu** – Migawki są automatycznie limitowane, żeby plik historii nie rósł bez ograniczeń; starsze wpisy są usuwane w miarę dodawania nowych.
