# Howto: Caja 1.26.4 auf Ubuntu 24.04 kompilieren

Dieses Howto beschreibt, wie du Caja 1.26.4 aus den Quellen auf Ubuntu 24.04.2 kompilieren kannst. Es wird speziell auf die Probleme mit `autopoint` und `gettext` eingegangen, die bei diesem Prozess auftreten können.

## Voraussetzungen
- Stelle sicher, dass du die notwendigen Build-Tools und Abhängigkeiten installiert hast:
  ```bash
  sudo apt-get install build-essential git libexempi-dev libgirepository1.0-dev libnotify-dev libexif-dev gvfs-libs mate-common libmate-desktop-dev gettext autopoint
  ```

## Schritt 1: Caja-Quellcode klonen
- Klone das Caja-Repository und wechsle zur Version 1.26.4:
  ```bash
  git clone --recurse-submodules https://github.com/mate-desktop/caja.git
  cd caja
  git checkout v1.26.4
  ```

## Schritt 2: Build-Dateien generieren
- Führe `autogen.sh` aus:
  ```bash
  ./autogen.sh --prefix=/usr
  ```
- **Hinweis**: Falls du eine Fehlermeldung wie "autopoint not found" bekommst, stelle sicher, dass `autopoint` installiert ist:
  ```bash
  sudo apt-get install autopoint
  ```

## Schritt 3: Konfigurieren und kompilieren
- Konfiguriere und baue Caja:
  ```bash
  ./configure --prefix=/usr
  make
  sudo make install
  ```

## Schritt 4: Fehlerbehebung
- **Problem mit `mate-common`**: Falls du eine Fehlermeldung wie "You need to install mate-common from the MATE Git" siehst, installiere `mate-common` aus den Ubuntu-Repositories:
  ```bash
  sudo apt-get install mate-common
  ```
- **Fehlende Abhängigkeiten**: Falls weitere Abhängigkeiten fehlen, kannst du sie mit folgendem Befehl installieren:
  ```bash
  sudo apt-get build-dep caja
  ```

## Zusätzliche Hinweise
- Nach der Installation von Caja 1.26.4 könnte es notwendig sein, sich abzumelden und wieder anzumelden, damit die neue Version geladen wird.
- Falls du Probleme mit `gettext` und `autopoint` hast, stelle sicher, dass beide Pakete installiert sind:
  ```bash
  sudo apt-get install gettext autopoint
  ```

Mit diesen Schritten solltest du in der Lage sein, Caja 1.26.4 erfolgreich zu kompilieren und zu installieren.