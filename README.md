# Voedingslogboek — iPhone PWA

Een Nederlandstalig voedings- en klachtenlogboek. Geen account, analytics of serverdatabase: registraties worden in de lokale browseropslag (`localStorage`) bewaard. De hosting levert alleen de statische appbestanden. Dit prototype is geen medisch hulpmiddel of diagnose.

## Inbegrepen

- Maaltijd/drank, datum en tijd, hoeveelheid, bereidingswijze en opmerkingen.
- Klachten met ernst 0–10, beginmoment, optionele duur en een koppeling naar een eerdere maaltijd (ook van een eerdere dag).
- Ziektefase, stress en medicatie één keer in het dagoverzicht; voedingsmomenten houden alleen maaltijdgegevens.
- Daggeschiedenis met klachten en gegeten maaltijden op dezelfde dag.
- Bij een klacht wordt de meest recente eerdere maaltijd voorgesteld; je kunt elke eerder geregistreerde maaltijd kiezen.
- Inzichten tellen alleen maaltijden die je zelf aan een klacht koppelde, naast hoe vaak je die maaltijd registreerde. Dit zijn mogelijke patronen, geen bewijs van oorzaak.
- CSV-export en volledige JSON-back-up/import.
- Donker thema, offline shell-cache via service worker; manifest, iOS-metagegevens en app-iconen.
- Mobiele bediening, datumvalidatie, begrensde invoer en bevestiging bij wissen/herstellen.

## Testen op een computer

Open deze map met een lokale webserver; rechtstreeks `index.html` openen werkt voor de basis, maar service workers/offline PWA vereisen HTTPS of localhost. Bijvoorbeeld met Python: `python -m http.server 8000` en open `http://localhost:8000`.

## Publiceren met GitHub Pages

1. Maak op GitHub een nieuwe repository aan. Upload de bestanden uit deze map (niet de `outputs`-map zelf) naar de hoofdmap van de repository.
2. Ga naar **Settings → Pages**. Kies **Deploy from a branch**, branch `main` en map `/ (root)`; sla op.
3. Wacht op de getoonde publicatiestatus en open de Pages-URL op je iPhone in Safari.
4. Tik **Deel → Zet op beginscherm → Voeg toe**. Start de app via het nieuwe icoon. Laad de URL eerst online zodat offlinebestanden in cache staan.

GitHub host alleen de appcode. Publiceer nooit JSON- of CSV-exports. Op een publieke repository is de appcode zichtbaar, niet de registraties die op je iPhone blijven.

## Andere hosting

Upload dezelfde bestanden naar een statische HTTPS-host (bijvoorbeeld Netlify, Cloudflare Pages of eigen webhosting). Als de app in een submap staat, behoud dan de gehele mapstructuur. HTTPS is nodig voor service workers en PWA-installatie. Test de uiteindelijke URL in Safari.

## Back-ups en privacy

Maak regelmatig een JSON-back-up via **Privacy** en bewaar deze versleuteld of op een andere veilige plek. Import vervangt de huidige gegevens; exporteer eerst als je die wilt behouden. Wissen van Safari-websitegegevens, verwijderen van de web-app, toestelverlies of opslaglimieten kunnen lokale gegevens onherstelbaar verwijderen. Er is geen synchronisatie tussen apparaten. CSV is bedoeld om te openen of te bespreken, JSON om terug te zetten. Exports bevatten gevoelige gezondheidsinformatie.

Inzichten tonen tellingen en geregistreerde maaltijdkoppelingen; ze bepalen geen oorzaak. Gebruik het logboek als gesprekssteun met je zorgverlener.
