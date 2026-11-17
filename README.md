# Blocca Tavolo – estensione per Owlbear Rodeo

Blocca zoom e vista sul monitor del tavolo, con il quadretto calibrato a 1 pollice
(o alla misura che preferite), così le miniature fisiche restano sempre in scala.

## Come funziona

- Si attiva **solo sul dispositivo** in cui spuntate “Questo dispositivo è il monitor del tavolo”
  (l’impostazione resta salvata in quel browser). Il portatile del master resta libero.
- Controlla la vista a intervalli: se un tocco, un pizzico o la rotellina l’hanno cambiata,
  la riporta indietro. A riposo controlla ogni 0,4 secondi; appena rileva un gesto passa a
  0,08 secondi per 2 secondi, così la correzione è quasi immediata.
- Modalità:
  - **Solo zoom**: la scala resta fissa, la mappa si può spostare (compatibile con Sync View del master).
  - **Zoom e vista**: blocca anche gli spostamenti. Cambiando scena si riaggancia dove si apre.
- **Telecomando del master** (visibile solo al GM): “Sblocca il tavolo” e “Blocca il tavolo qui”,
  per cambiare mappa senza toccare il monitor.

## Installazione (gratuita, con GitHub Pages)

1. Create un account su github.com e un nuovo repository **pubblico** (es. `blocco-tavolo`).
2. Caricate nel repository tutti i file di questa cartella
   (`manifest.json`, `index.html`, `background.html`, `popover.js`, `background.js`, `icon.svg`).
3. Nel repository: **Settings → Pages → Build and deployment → Deploy from a branch**,
   scegliete `main` e la cartella `/ (root)`, poi salvate. Dopo un minuto il sito è online.
4. Il link dell’estensione sarà:
   `https://VOSTRO-UTENTE.github.io/blocco-tavolo/manifest.json`
5. In Owlbear Rodeo: profilo → **Extensions** → **+ (Add Custom Extension)** → incollate il link.
6. Nella stanza, abilitate l’estensione dal gestore estensioni.

## Prima calibrazione (sul monitor del tavolo)

1. Aprite la stanza nella finestra del tavolo e cliccate l’icona del lucchetto in alto a sinistra.
2. Spuntate “Questo dispositivo è il monitor del tavolo”.
3. Inserite la diagonale (es. 27). La risoluzione viene rilevata da sola.
4. Premete “Applica la scala ora”, poi misurate 10 quadretti col righello
   e inserite i millimetri reali in “Verifica col righello” → **Correggi**.
   Ripetete finché 10 quadretti misurano 254 mm.
5. Scegliete la modalità di blocco. Fatto.

La misura col righello è quella che conta: corregge anche la scala di Windows
e lo zoom del browser.

## Note

- Funziona con mouse, touch capacitivo e cornici IR: non blocca i gesti,
  annulla il risultato. Durante un pizzico la mappa può “tremare” per un attimo
  prima di tornare a posto.
- Funziona con qualsiasi tipo di griglia della scena, perché legge i DPI della griglia.
- Se il master usa Sync View con la modalità “Zoom e vista”, il tavolo torna indietro:
  usate prima “Sblocca il tavolo”, oppure la modalità “Solo zoom”.

## Sorgenti

Il codice leggibile è in `src/`. Per ricompilare:
`npx esbuild src/background.js src/popover.js --bundle --format=iife --minify --outdir=.`
