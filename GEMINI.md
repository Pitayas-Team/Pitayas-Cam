# Instrukcje dla Antigravity / Gemini

Cały kontekst projektu **Pitaya Cam** (cel, zasady od właściciela, struktura, uruchamianie i wdrażanie, testowanie, znane ograniczenia) jest w pliku **`AGENTS.md`** w tym samym katalogu – przeczytaj go najpierw i traktuj jako obowiązujący.

Najważniejsze w skrócie:
- Electron: odbiera obraz z telefonu (Android przez adb/`android.js`, iPhone przez stronę `iphone-client.html`/`iphone.js`) i podaje go jako kamerę wirtualną (`virtualcam.js`).
- Po stronie telefonu to moduł `cam` w `Pitayas-Mobile` (port Cam to port strony iPhone + 2).
- Ma własny instalator zależności (`installer-main.js`, `installer.html`, `installer.sh`, `setup-core.sh`).
- Wszystko po polsku; wygląd matowy i spokojny, nie „AI slop”.
- Po każdej zmianie dopisz wpis w liście zmian: `node ~/Pitayas-Projects/ADMIN/changelog.js add <id> <feature|fix|change> "opis"`.
- Commity jako właściciel, **bez** „Co-Authored-By” i wzmianek o AI. Nie buduj ani nie publikuj wersji bez prośby.
- Nigdy nie kopiuj sekretów (hasła, tokeny, `.env`) do kodu, logów ani czatu. Napisz, czego nie mogłeś sprawdzić.
