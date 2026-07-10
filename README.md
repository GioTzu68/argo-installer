# ARGO — install page (ESP Web Tools)

Pagina statica per installare il firmware ARGO sull'ESP32-S3 direttamente dal browser
(come install.wled.ge). Nessun server: gira tutto lato client via **Web Serial**.

## Contenuto
- `index.html` — pagina con `<esp-web-install-button>` (esp-web-tools da CDN).
- `manifest.json` — descrive il firmware (chip ESP32-S3, versione, path del binario).
- `firmware/argo-s3-vX.Y.Z.bin` — binario **merged** (bootloader+partizioni+app), config `dist` senza credenziali.
- `build.sh` — rigenera il binario dalla build `esp32s3_dist`.

## Pubblicazione (GitHub Pages)
1. Metti questa cartella in una **repo pubblica** (GitHub Pages gratis richiede repo pubblica).
2. Abilita Pages (branch `main`, root). Servita su `https://<utente>.github.io/<repo>/`.
3. HTTPS è automatico (necessario per Web Serial).

## Requisiti utente
- **Chrome / Edge / Opera desktop** (Windows/macOS/Linux). No Firefox/Safari, no mobile.
- ESP32-S3 collegato via USB.

## Aggiornare il firmware pubblicato
1. `bash installer/build.sh` (rigenera il merged bin dalla build dist).
2. Aggiorna `version` e il `path` in `manifest.json`.
3. Commit + push nella repo pubblica.

> Il binario `dist` ha WiFi/MQTT vuoti: al primo avvio parte il portale SoftAP `ARGO-setup`
> per il setup WiFi. Nessuna credenziale personale è inclusa nel binario.
