# Denim – instrukcja budowania

Potrzebujesz na komputerze:
- Node.js (nodejs.org, wersja LTS)
- Android: Android Studio (developer.android.com/studio)
- iPhone: Mac z Xcode

## Android (plik .apk)

1. Rozpakuj folder, otwórz w nim terminal.
2. Zainstaluj paczki:
       npm install
3. Dodaj Androida:
       npx cap add android
4. Wygeneruj ikonę Denim:
       npx capacitor-assets generate --android
5. Zsynchronizuj:
       npx cap sync android
6. Zbuduj plik apk (wymaga Android Studio, bo ma Javę i SDK):
       npx cap open android
   W Android Studio: Build -> Build Bundle(s) / APK(s) -> Build APK(s).
   Gotowy plik: android/app/build/outputs/apk/debug/app-debug.apk
7. Wyślij plik na telefon (kabel, Dysk Google, AirDrop itp.), otwórz go
   i zainstaluj. Telefon zapyta o zgodę na instalację z nieznanych źródeł.

## iPhone (tylko Mac)

1. npm install
2. npx cap add ios
3. npx capacitor-assets generate --ios
4. npx cap sync ios
5. npx cap open ios
6. W Xcode: wybierz projekt App -> Signing & Capabilities -> Team (zaloguj
   swoje Apple ID), podłącz iPhone'a kablem, wybierz go u góry i kliknij Run.
   Na darmowym koncie apka działa 7 dni, potem trzeba wgrać ją ponownie.
   Na iPhonie włącz: Ustawienia -> Prywatność i bezpieczeństwo -> Tryb dewelopera.

## Zmiany w apce

Cały kod apki jest w www/index.html. Po zmianie uruchom:
    npx cap sync
i zbuduj ponownie.

## iPhone BEZ Maca (plik .ipa zbudowany w chmurze)

1. Załóż darmowe konto na github.com i utwórz nowe repozytorium (np. "denim").
2. Wrzuć do niego całą zawartość tego folderu (Add file -> Upload files),
   razem z folderem .github. Gałąź musi nazywać się "main".
3. Wejdź w zakładkę Actions -> "Build iOS IPA" -> Run workflow.
   Po kilku minutach na dole strony pojawi się plik "Denim-ipa". Pobierz go
   i rozpakuj, w środku jest Denim.ipa.
4. Na komputerze (Windows lub Mac) zainstaluj Sideloadly (sideloadly.io)
   albo AltStore (altstore.io).
5. Podłącz iPhone'a kablem, w Sideloadly wybierz Denim.ipa, wpisz swoje
   Apple ID i kliknij Start.
6. Na iPhonie: Ustawienia -> Ogólne -> VPN i zarządzanie urządzeniem ->
   zaufaj swojemu Apple ID. Potem włącz Tryb dewelopera
   (Ustawienia -> Prywatność i bezpieczeństwo).

Na darmowym Apple ID apka działa 7 dni. AltStore potrafi odświeżać ją
automatycznie, gdy komputer jest w tej samej sieci Wi-Fi.
