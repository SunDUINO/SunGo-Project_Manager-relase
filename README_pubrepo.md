[EN] English description is available below.  
[PL] Opis w języku polskim znajduje się poniżej.

---

# [EN] SunGo Publish Any File to Any Repo – Setup & Usage Guide

SunGo includes a built-in tool for publishing any file (or set of files) from your project straight to a Git repository — without leaving VS Code or touching your terminal.  
Access it via the **🚀 Publish Any File to Any Repo** entry in the SunGo Tools panel.

---

## 📋 Step 1 – Set the destination repository

Enter the repository URL and branch, or pick one from **Saved Repositories** if you've published there before — SunGo remembers your last 10 destinations automatically. Typing a different URL always works too; it doesn't have to be on the saved list.

> 💡 Use **"💾 Save to list"** to add the currently typed URL without publishing yet, and **"🗑 Remove from list"** to clean up an entry you no longer need.

---

## 📂 Step 2 – Select files and write a commit message

Choose which files from your project to publish, and write a commit message describing the change. Only the files you select are sent — nothing else in your project is touched or exposed.

---

## ▶️ Step 3 – Publish

Click the publish button. SunGo clones (or syncs, if it's published there before) the destination repository into an isolated, temporary working folder — separate from your own project's Git history entirely — copies your selected files in, commits, and pushes.

> 💡 Each destination repository gets its own isolated working folder internally, and that folder is automatically cleaned up after every publish — switching between different destinations never causes a conflict.

---

## ⚠️ Common Issues

**"Repository URL is required" / "No files selected"** – Both a destination and at least one file are required before publishing; fill in the missing field and try again.

**Push fails with an authentication error** – This tool uses your system's own Git credentials (the same ones your terminal's `git push` would use). Make sure you're authenticated for the destination repo — an SSH key, a stored credential, or a credential helper configured for HTTPS.

**"Nothing new to commit"** – The files you selected are already identical to what's in the destination repository; nothing was published because there was nothing to change.

**I want to stop tracking a saved repository from showing sensitive history** – Removing it from the saved list only affects SunGo's own memory of the URL — it doesn't touch the destination repository itself or any commits already pushed there.

---
---

# [PL] SunGo Publish Any File to Any Repo – Instrukcja instalacji i użytkowania

SunGo zawiera wbudowane narzędzie do publikowania dowolnego pliku (lub zestawu plików) z Twojego projektu bezpośrednio do repozytorium Git — bez opuszczania VS Code i bez terminala.  
Dostęp przez wpis **🚀 Publish Any File to Any Repo** w panelu SunGo Tools.

---

## 📋 Krok 1 – Ustaw repozytorium docelowe

Wpisz adres URL repozytorium i branch, albo wybierz z **Saved Repositories**, jeśli już tam kiedyś publikowałeś — SunGo automatycznie pamięta ostatnie 10 adresów docelowych. Wpisanie innego adresu też zawsze działa; nie musi być na zapisanej liście.

> 💡 Użyj **"💾 Save to list"**, żeby dodać obecnie wpisany adres bez publikowania jeszcze, i **"🗑 Remove from list"**, żeby posprzątać wpis, którego już nie potrzebujesz.

---

## 📂 Krok 2 – Wybierz pliki i napisz commit message

Wybierz, które pliki z projektu opublikować, i napisz wiadomość commita opisującą zmianę. Wysyłane są tylko wybrane pliki — nic więcej z Twojego projektu nie jest ruszane ani udostępniane.

---

## ▶️ Krok 3 – Opublikuj

Kliknij przycisk publikacji. SunGo klonuje (albo synchronizuje, jeśli już tam wcześniej publikowałeś) repozytorium docelowe do odizolowanego, tymczasowego folderu roboczego — całkowicie osobnego od historii Git Twojego własnego projektu — kopiuje tam wybrane pliki, commituje i pushuje.

> 💡 Każde repozytorium docelowe ma wewnętrznie własny, odizolowany folder roboczy, który jest automatycznie czyszczony po każdej publikacji — przełączanie się między różnymi adresami docelowymi nigdy nie powoduje konfliktu.

---

## ⚠️ Częste problemy

**"Repository URL is required" / "No files selected"** – Zarówno adres docelowy, jak i co najmniej jeden plik są wymagane przed publikacją; uzupełnij brakujące pole i spróbuj ponownie.

**Push kończy się błędem uwierzytelniania** – To narzędzie używa Twoich własnych, systemowych danych uwierzytelniających Git (tych samych, których użyłby `git push` w terminalu). Upewnij się, że jesteś uwierzytelniony dla repozytorium docelowego — klucz SSH, zapisane dane logowania albo credential helper skonfigurowany dla HTTPS.

**"Nothing new to commit"** – Wybrane pliki są już identyczne z tym, co jest w repozytorium docelowym; nic nie zostało opublikowane, bo nie było czego zmieniać.

**Chcę przestać śledzić zapisane repozytorium, żeby nie pokazywało wrażliwej historii** – Usunięcie go z zapisanej listy dotyczy tylko pamięci SunGo o tym adresie — nie rusza samego repozytorium docelowego ani żadnych commitów już tam wypchniętych.
