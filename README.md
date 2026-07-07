# Crampa! 🚵‍♂️

Database personale delle salite in bici: tempi, record e statistiche, organizzate per provincia.

Progetto **MEM Software**.

## Cos'è

Crampa! è una PWA (Progressive Web App) a file singolo, senza backend, per tenere traccia delle salite in bici che fai (o vuoi fare): lunghezza, dislivello, pendenza media, categoria di difficoltà (5ª cat. → H.C.) calcolata automaticamente, record personali con storico dei tempi precedenti.

## Funzionalità

- **Lista salite per provincia**, con ricerca, filtri (fatte / da fare / tutte) e ordinamento (nome, difficoltà, lunghezza)
- **Statistiche** per provincia: quante fatte, % di completamento, salita più dura conquistata (con versante di partenza)
- **Categoria di difficoltà automatica**, calcolata con la stessa formula usata nel foglio Excel originale: `pendenza² × distanza / 10 + pendenza × 4`
- **Scheda salita** con tutti i dati, mini-profilo altimetrico stilizzato, modifica completa dei dati (anche a posteriori, per correggere o integrare)
- **Record personale**: data e tempo di percorrenza editabili, con storico dei tentativi precedenti e delta rispetto all'ultimo record
- **Link mappa** opzionale per ogni salita
- **Backup**: esportazione/importazione JSON, copia rapida negli appunti, ripristino ai dati originali

## Dati e sincronizzazione

Tutti i dati sono salvati in **localStorage**, nel browser del dispositivo su cui usi l'app. Questo significa:

- Nessun account, nessun server, nessuna connessione richiesta per l'uso quotidiano.
- **I dati NON si sincronizzano automaticamente tra dispositivi diversi.** Se installi Crampa! su più telefoni/computer, ognuno avrà il proprio database indipendente.
- Per portare i dati da un dispositivo all'altro: usa **Esporta JSON** su un dispositivo e **Importa JSON** sull'altro (oppure "Copia negli appunti" per un backup veloce).

## Pubblicazione su GitHub Pages

1. Crea un repository (es. `crampa`) sotto l'organizzazione/account MEM Software.
2. Carica questi file nella root del repository:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`
3. Vai su **Settings → Pages**, seleziona il branch `main` e la cartella `/ (root)`.
4. L'app sarà disponibile su `https://<utente>.github.io/crampa/`.

## Installazione su iPhone

Apri il link in Safari → tocca **Condividi** → **Aggiungi alla schermata Home**. L'app si aprirà a schermo intero, senza barra di Safari, e supporta correttamente notch/Dynamic Island e status bar.

## File del progetto

| File | Descrizione |
|---|---|
| `index.html` | App completa (HTML + CSS + JS), include i dati di partenza delle salite |
| `manifest.json` | Manifest PWA (nome, icone, colori, modalità standalone) |
| `sw.js` | Service worker per il funzionamento offline (cache dell'app shell) |
| `icon-192.png` / `icon-512.png` | Icone dell'app |

## Note tecniche

- I dati iniziali (~177 salite) sono stati importati da un foglio Excel personale (`Le_Mie_Salite.xlsx`), usato solo come base una tantum: non è più necessario né referenziato dall'app.
- Nessuna dipendenza esterna a runtime, a parte i Google Font (Barlow Condensed, Inter) caricati via CDN.
