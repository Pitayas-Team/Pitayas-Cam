# Pitaya Cam – aparat telefonu jako kamera internetowa komputera

> Plik przekazania projektu między narzędziami AI (Claude Code ⇄ Antigravity ⇄ inne).
> Przeczytaj go w całości, zanim cokolwiek zmienisz. **Nie ma tu żadnych sekretów** – hasła i klucze są poza repozytorium i nie wolno ich kopiować do kodu, logów ani rozmów.
> Stan na: 2026-10-29. Jeśli zmieniasz architekturę albo sposób wdrażania, zaktualizuj ten plik.

## 1. Czym to jest
**Pitaya Cam** zamienia aparat telefonu w kamerę internetową komputera. Obraz z telefonu trafia do wirtualnej kamery systemowej, którą widzą aplikacje do rozmów i nagrywania.

## 2. Zasady od właściciela
- Obsługa Androida i iPhone'a ma pozostać równoległa (osobne pliki `android.js` i `iphone.js`).
- Zależności systemowe (kamera wirtualna) instaluje instalator — nie uruchamiaj go bez wiedzy właściciela (wymaga uprawnień).

## 3. Gdzie co leży i jak uruchamiać
`npm install`, `npm start`; instalator: `npm run installer`; paczki: `npm run dist`. Wydania robi Pitayas Admin.

## 4. Struktura
```
main.js            okno, serwer, tray, połączenie z telefonem
android.js         Android (adb)
iphone.js, iphone-client.html   iPhone (strona w przeglądarce telefonu)
virtualcam.js      kamera wirtualna
installer-main.js, installer.html, installer.sh, setup-core.sh   instalator
```

## 5. Testowanie
Bez telefonu i kamery wirtualnej nie sprawdzisz przepływu obrazu — napisz o tym wprost. Możesz sprawdzić składnię i serwer.

## 6. Zasady wspólne
- **Język:** interfejs, komentarze, opisy zmian i odpowiedzi po polsku. Marka „Pitayas”; kolory: róż pitai `#ff4fa6`, ciemne tło `#121116`.
- **Wygląd:** matowy, spokojny, czytelny — **nie „AI slop”**: bez świecących gradientów w tytułach, poświat pod przyciskami i udawanego szkła w CSS. Prawdziwe szkło tylko natywne (iOS 26) na elementach, które się nie ruszają.
- **Pitaya Core:** folder `core/` w aplikacji to **kopia** z projektu `Pitayas-Core`. Nie edytuj jej w aplikacji — zmieniaj w `Pitayas-Core` i uruchom `~/Pitayas-Projects/ADMIN/sync-core.sh`. Każda aplikacja rejestruje się w `~/.config/Pitayas/apps/<id>.json` i wystawia kanał sterowania (kontrakt Core 0.2, dla przyszłego Pitaya Hub).
- **Lista zmian:** po **każdej** zmianie w aplikacji dopisz wpis: `node ~/Pitayas-Projects/ADMIN/changelog.js add <id> <feature|fix|change> "opis po polsku"`. `<id>` = nazwa folderu bez „Pitayas-”, małymi literami (np. `screen`, `mobile`, `accounts`, `admin`, `website`). Wpisy trafiają do opisu wydania na GitHubie.
- **Git:** commity jako właściciel (`Pitayas <inbox@rakunek.com>`), krótki opis po polsku, **bez** `Co-Authored-By` i wzmianek o narzędziach AI. Push tylko na bieżącą gałąź, bez force-push bez zgody.
- **Budowanie i wydania:** nie buduj, nie pakuj i nie publikuj wersji bez wyraźnej prośby właściciela. Wydania robi **Pitayas Admin** (`ADMIN/cli.js`, GitHub Releases organizacji Pitayas-Team). Po budowie nie uruchamiaj aplikacji właściciela.
- **Sekrety:** hasła, tokeny, klucze i pliki `.env` nigdy do kodu, logów, commitów ani rozmów.
- **Uczciwość:** nie masz telefonu, iPhone'a ani Windowsa — wyraźnie napisz, czego nie dało się sprawdzić, zamiast twierdzić, że działa.
- **Praca na serwerze:** projekty leżą w `~/Pitayas-Projects` na serwerze rakunek.com (kopia na komputerze właściciela to zapas). Nie startuj zbędnych procesów w tle ani dodatkowych sesji/agentów.
