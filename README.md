# 📚 EPUB Library & Reader

Un lettore EPUB completo e moderno con gestione libreria integrata, supporto per modalità di lettura avanzate e estrazione capitoli. Interamente sviluppato in HTML, CSS e JavaScript vanilla, senza dipendenze esterne (eccetto ePub.js).

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

## 🌟 Caratteristiche Principali

- **🌍 Traduzione Integrata**: Leggi libri in qualsiasi lingua tradotti istantaneamente nella tua lingua madre tramite il browser - niente più attese per le traduzioni ufficiali!
- **📚 Libreria Digitale**: Gestisci la tua collezione di ebook con copertine e metadati
- **📖 Lettura Multi-Modalità**: Pagina singola, doppia pagina e scroll continuo
- **🎨 Personalizzazione Totale**: 15 temi raggruppati per sfondo, dimensione font, interlinea regolabili tramite popup dedicati
- **📦 Sistema di Raccolta Chunks**: Seleziona e raccogli automaticamente testo e immagini mentre leggi (copy-based o manuale)
- **📝 Editor Report Integrato**: Trasforma i chunks raccolti in report professionali con un editor WYSIWYG custom (basato su contenteditable + execCommand) con supporto nativo per tabelle e ridimensionamento immagini
- **🎯 Highlighting & Dictionary**: Evidenzia testo con colori e cerca parole al volo su WordReference
- **📄 Estrazione Capitoli**: Esporta singoli capitoli o intere sezioni gerarchiche in formato HTML, PDF o DOCX standalone
- **🔖 Navigazione Intelligente**: Indice interattivo con gerarchia espandibile + segnalibri personali
- **💾 Persistenza Locale**: Tutti i libri salvati in IndexedDB, preferenze in localStorage
- **📱 Responsive Design**: Interfaccia ottimizzata per desktop e tablet
- **🔒 Privacy Totale**: Zero server, zero tracking, tutto funziona localmente nel browser

---

## ⚡ Funzionalità Basate su Servizi Browser

Questo lettore EPUB sfrutta intensamente le API native del browser per offrire funzionalità avanzate senza necessità di backend server.

### 🌐 Traduzione Dinamica Integrata

**Traduzione tramite Browser nativo**

- Utilizza l'API di traduzione integrata del browser (Google Translate, Microsoft Translator, ecc.)
- **Metodo 1**: Click destro su qualsiasi testo → "Traduci in [lingua]"
- **Metodo 2**: Click sull'icona di traduzione del browser nella barra degli indirizzi
- **Supporto completo**: Traduce l'intero capitolo estratto mantenendo formattazione e immagini
- **Nessun server esterno**: La traduzione avviene direttamente nel browser
- **Privacy garantita**: Nessun dato inviato a servizi terzi oltre al browser

**Come funziona:**

Il capitolo viene estratto come documento HTML standalone con tag lingua corretto. Il browser rileva la lingua e offre automaticamente la traduzione. L'utente seleziona la lingua target e ottiene la traduzione istantanea dell'intera pagina.

### 📦 Sistema di Raccolta Chunks (Text & Images)

Una delle funzionalità più innovative: **raccolta automatica e manuale di frammenti** durante la lettura.

#### 🎯 Cosa sono i "Chunks"?

I chunks sono **porzioni di contenuto** (testo + immagini) che puoi raccogliere mentre leggi per:

- Creare riassunti personalizzati
- Estrarre citazioni importanti
- Collezionare immagini e grafici
- Assemblare report di studio

#### 🔄 Modalità di Raccolta

**1. Raccolta Automatica (Copy-Based)**

Seleziona testo o immagini nel capitolo estratto e premi **Ctrl+C** (⌘+C su Mac). Il contenuto viene automaticamente aggiunto alla collezione e il counter si aggiorna in tempo reale.

**2. Raccolta Manuale (Button-Based)**

Seleziona testo o immagini, poi click sul pulsante **"Add Selection"** (icona `bi-plus-circle`). Una toast notification conferma l'aggiunta con il numero di chunks raccolti. La selezione viene deselezionata automaticamente.

#### 💾 Storage dei Chunks

Ogni chunk è composto da tipo, contenuto HTML (incluse eventuali immagini in base64) e timestamp. Lo storage usa localStorage come priorità con fallback in-memory per contesti isolati (es. blob URLs).

**Key localStorage:** `epub-chunks-collection`

#### 📊 Counter Dinamico

Il counter nella toolbar mostra sempre il numero di chunks raccolti e si aggiorna automaticamente dopo ogni operazione: aumenta all'aggiunta, si azzera al clear, e ripristina il valore salvato al caricamento della pagina.

### 📝 Generazione Report con Editor Custom

Dopo aver raccolto i chunks, puoi trasformarli in un **report editabile professionale**.

#### 🚀 Creazione Report

Il pulsante **"Launch Editor"** apre un menu dropdown con due opzioni: caricare nell'editor tutti gli elementi della collezione oppure l'intero capitolo estratto corrente.

#### ✏️ Editor WYSIWYG Custom

Una nuova finestra si apre con un editor HTML **contenteditable** costruito su misura, con toolbar superiore e plugin nativi per tabelle e immagini:

**Toolbar dell'editor:**

- **B / I / U / S**: Grassetto, corsivo, sottolineato, barrato
- **H1 / H2 / H3 / P**: Formattazione blocco (intestazioni e paragrafo)
- **• L / 1. L**: Lista puntata e lista numerata
- **🖼️**: Inserimento immagine da file (base64 inline)
- **A− / A+**: Dimensione font (8–28px)
- **🖨️ Stampa / PDF**: Stampa o salva come PDF
- **📋 HTML**: Copia l'intero HTML dell'editor negli appunti

**Plugin Tabelle:**

Quando il cursore si trova all'interno di una cella, compare una toolbar contestuale flottante. Cliccando su "⚙️ Modifica" si apre un dialog dedicato con le seguenti operazioni: inserisci riga sopra/sotto, elimina riga, inserisci colonna a sinistra/destra, elimina colonna.

**Plugin Immagini:**

Le immagini nel documento mostrano un overlay di selezione con handles di ridimensionamento ai bordi, permettendo di scalare l'immagine direttamente nel documento senza lasciare l'editor.

#### 📄 Export PDF dal Report

Una volta completato il report, click su **"🖨️ Stampa / PDF"**. Il processo usa il dialog di stampa nativo del browser con CSS `@media print` ottimizzati: la toolbar viene nascosta, il documento si espande a pagina intera con font adatto alla stampa e gestione automatica dei page break.

**Caratteristiche Export:**

- 📏 Formato A4 (210mm × 297mm)
- 🖼️ Alta risoluzione (scale: 2)
- 📄 Multi-pagina automatico
- 🎨 Preserva colori e formattazione
- 🖼️ Immagini incluse (base64)

#### 🗑️ Clear Collection

Pulsante **"Clear Collection"** (icona `bi-trash`):

- Richiede conferma: "Clear all collected chunks?"
- Rimuove tutti i chunks da storage
- Resetta counter a 0
- Toast notification: "Collection cleared"

---

## 🎯 Modalità di Utilizzo

L'applicazione opera in **tre modalità principali**, ciascuna con la propria toolbar personalizzata:

### 1️⃣ Modalità Libreria

### 2️⃣ Modalità Lettura (Finestra Principale)

### 3️⃣ Modalità Capitolo Estratto

---

## 📖 Modalità 1: LIBRERIA

![Library View](https://via.placeholder.com/800x400/667eea/ffffff?text=Library+View)

### Interfaccia

- **Vista a griglia** con copertine dei libri
- **Card responsive** con hover effect
- **Metadati visibili**: Titolo e autore su ogni card
- **Stato vuoto** con messaggio invitante quando nessun libro è presente

### Toolbar della Libreria

| Pulsante        | Icona            | Funzione                                                   |
| --------------- | ---------------- | ---------------------------------------------------------- |
| **Import Book** | `bi-plus-circle` | Apre il file picker per importare file EPUB nella libreria |

### Funzionalità

#### 📥 Importazione Libri

Click su "Import Book" → Seleziona file .epub → Libro salvato in IndexedDB.

- Salvataggio automatico dei metadati (titolo, autore, copertina)
- Estrazione e memorizzazione della cover image
- Feedback visivo durante l'import (loading overlay)

#### 📚 Visualizzazione Collezione

- Griglia responsive (auto-fill minimo 160px)
- Massimo 1200px di larghezza per leggibilità
- Copertine con fallback iconografico se mancanti
- Titolo e autore troncati elegantemente

#### 🗑️ Eliminazione Libri

- Pulsante **Delete** (icona X) appare on-hover sulla card
- Conferma tramite dialog nativo del browser
- Rimozione permanente da IndexedDB
- Aggiornamento automatico della griglia

#### 📖 Apertura Libro

- **Click sulla card** per aprire il libro nel lettore
- Transizione fluida alla modalità lettura
- Caricamento automatico dell'ultima posizione salvata

---

## 📱 Modalità 2: LETTURA (Finestra Principale)

![Reader View](https://via.placeholder.com/800x400/764ba2/ffffff?text=Reader+View)

### Layout

- **Header** con gradient viola e toolbar completa
- **Sidebar** laterale con indice dei contenuti
- **Viewer** centrale per il contenuto dell'EPUB
- **Footer** con informazioni di posizione e capitolo

### 🛠️ Toolbar Completa della Finestra Principale

#### Gruppo 1: Navigazione Sidebar

| Pulsante            | Icona               | Funzione                           | Note                    |
| ------------------- | ------------------- | ---------------------------------- | ----------------------- |
| **Toggle Sidebar**  | `bi-layout-sidebar` | Mostra/nascondi indice TOC         | Attivo/Inattivo         |
| **User Bookmarks**  | `bi-bookmark-star`  | Apre cassetto segnalibri personali | Badge con contatore     |

#### Gruppo 2: Personalizzazione

| Pulsante       | Icona        | Funzione                                              |
| -------------- | ------------ | ----------------------------------------------------- |
| **Typography** | `bi-type`    | Apre popup con controlli font, interlinea, layout pagina |
| **Theme**      | `bi-palette` | Apre popup selettore temi (15 disponibili)            |

#### Gruppo 3: Modalità di Lettura

| Pulsante        | Icona              | Funzione                        | Stati           |
| --------------- | ------------------ | ------------------------------- | --------------- |
| **Scroll Mode** | `bi-arrow-down-up` | Toggle scroll continuo/paginato | Attivo/Inattivo |

#### Gruppo 4: Zoom e Interfaccia

| Pulsante        | Icona    | Funzione                            | Valori                   |
| --------------- | -------- | ----------------------------------- | ------------------------ |
| **Button Zoom** | `%`      | Cicla zoom della toolbar            | 100%, 110%, 120%, 130%   |
| **Interface**   | `bi-eye` | Apre popup impostazioni interfaccia | Colori toolbar, sidebar, nav buttons |

#### Gruppo 5: Salvataggio

| Pulsante       | Icona         | Funzione                                            |
| -------------- | ------------- | --------------------------------------------------- |
| **Save State** | `bi-floppy`   | Salva manualmente posizione e preferenze del libro  |

#### Gruppo 6: Estrazione Capitolo

| Pulsante            | Icona                        | Funzione                 | Dropdown                                    |
| ------------------- | ---------------------------- | ------------------------ | ------------------------------------------- |
| **Extract Chapter** | `bi-file-earmark-arrow-down` | Estrai capitolo corrente | `bi-file-earmark` Solo capitolo / `bi-diagram-3` Capitolo + sottolivelli |

### 📋 Funzionalità Dettagliate

#### 🎨 Temi Disponibili (15 temi)

I temi sono organizzati in 5 gruppi per sfondo e selezionabili tramite swatches visivi nel popup:

**White:** Normal (bianco puro), Soft White (bianco leggermente attenuato)

**Cream / Sepia:** Cream (#fdf6e3), Sepia (#f4ecd8), Parchment (#eee5d3) — tutti con testo marrone scuro, ideali per lettura prolungata

**Light Gray:** Light Gray (#e5e7eb), Cool Gray (#dfe3e8), Warm Gray (#e8e4df)

**Medium Gray:** Mid Gray (#b0b8c1), Slate (#94a3b8)

**Dark Gray:** Dark Gray (#4b5563), Charcoal (#374151)

**Dark / Black:** Dark (#1a1a1a), Midnight (#0f1117), True Black (#000000)

#### 🔤 Popup Typography

Il popup Typography è accessibile tramite il pulsante con icona `bi-type` e raccoglie tutti i controlli tipografici in un unico pannello:

- **Font Size**: `bi-dash` e `bi-plus` con valore corrente visualizzato, reset con `bi-arrow-counterclockwise`
- **Line Height**: `bi-dash` e `bi-plus` con valore corrente, reset con `bi-arrow-counterclockwise`
- **Page View**: `bi-file-earmark` Pagina Singola e `bi-book` Doppia Pagina

#### 🖥️ Popup Interface Settings

Il popup Interface permette di personalizzare l'aspetto dell'interfaccia con color picker e slider dedicati:

- **Toolbar Color**: colore di sfondo della toolbar principale
- **Sidebar Color**: colore di sfondo della sidebar indice
- **Nav Buttons Color**: colore dei pulsanti di navigazione flottanti
- **Nav Opacity**: opacità dei pulsanti di navigazione (0.1–1.0)
- **Bookmark Drawer Color**: colore dello sfondo del cassetto segnalibri

#### 📄 Modalità di Lettura

**Pagina Singola** (default): una pagina alla volta, navigazione con frecce flottanti, ideale per schermi piccoli.

**Pagina Doppia**: due pagine affiancate, simulazione libro aperto, disabilitata in scroll mode, ottimale per schermi larghi (>1024px).

**Scroll Mode**: flusso continuo verticale, ideale per lettura immersiva. In questa modalità i pulsanti freccia flottanti vengono nascosti automaticamente.

#### 🔖 Sidebar Indice (TOC)

- **Struttura gerarchica** espandibile (max 3 livelli)
- **Indicatori visivi**: `▸` per elementi espandibili, `▾` per aperti, `•` per elementi foglia
- **Click su elemento**: naviga alla sezione ed espande/collassa sottoelements
- **Stili differenziati** per livelli (level-1, level-2, level-3)

#### 🔖 Segnalibri Personali (User Bookmarks)

Un cassetto laterale dedicato ai segnalibri creati dall'utente:

- Click su **User Bookmarks** (`bi-bookmark-star`) per aprire il cassetto
- Pulsante **New Bookmark** per aggiungere la posizione corrente
- Badge numerico mostra il totale dei segnalibri salvati
- Ogni segnalibro è eliminabile singolarmente

#### 💾 Salvataggio Automatico vs. Manuale

- **Auto-save**: posizione di lettura salvata automaticamente durante la navigazione
- **Save State** (`bi-floppy`): salvataggio esplicito di tutte le preferenze correnti (font, tema, layout, ecc.) per quel libro specifico

#### 🗺️ Estrazione Capitolo con Dropdown

Il pulsante **Extract Chapter** apre un menu a tendina con due opzioni:

- **Current chapter only**: estrae solo il capitolo corrente
- **Current + all sublevels**: estrae il capitolo corrente insieme a tutti i sottolivelli gerarchici nella struttura TOC

---

## 🎯 Modalità 3: CAPITOLO ESTRATTO

![Extracted Chapter](https://via.placeholder.com/800x400/10b981/ffffff?text=Extracted+Chapter)

### Caratteristiche Specifiche

- **Finestra separata** (`window.open`)
- **Toolbar completa** per gestione capitolo e raccolta chunks
- **Export multipli**: Print/PDF, DOCX, PDF Viewer
- **Preview immediato** del contenuto estratto
- **Sistema di raccolta** testo/immagini integrato
- **Editor Summernote** per report personalizzati

### 🛠️ Toolbar Completa della Finestra Capitolo

#### Gruppo 1: Tipografia e Zoom

| Pulsante        | Icona     | Funzione                                          |
| --------------- | --------- | ------------------------------------------------- |
| **Typography**  | `bi-type` | Apre popup con controlli font size e interlinea   |
| **Button Zoom** | `%`       | Cicla zoom della toolbar (100%, 110%, 120%, 130%) |

#### Gruppo 2: Highlighting & Dictionary

| Pulsante       | Icona            | Funzione                                  | Colori/Note                                         |
| -------------- | ---------------- | ----------------------------------------- | --------------------------------------------------- |
| **Highlight**  | `bi-highlighter` | Evidenzia testo con dropdown colori       | Yellow, Green, Pink + `bi-eraser` Rimuovi           |
| **Dictionary** | `bi-globe`       | Apre WordReference per parola selezionata | Apre in nuova tab                                   |

**Highlight Dropdown Menu:**

- Click su icona highlighter → Apre menu colori
- **3 colori disponibili**: Yellow (default), Green, Pink
- **Opzione Rimuovi** (`bi-eraser`): rimuove evidenziazioni dalla selezione
- Seleziona colore → cambia colore default, poi click su testo selezionato → applica highlight

#### Gruppo 3: Collezione Chunks

| Pulsante             | Icona              | Funzione                       | Note                                                              |
| -------------------- | ------------------ | ------------------------------ | ----------------------------------------------------------------- |
| **Clear Collection** | `bi-trash`         | Svuota collezione chunks       | Richiede conferma                                                 |
| **Add Selection**    | `bi-plus-circle`   | Aggiungi selezione manualmente | Testo + immagini                                                  |
| **Chunk Counter**    | Badge numerico     | Mostra numero chunks raccolti  | Aggiornamento live                                                |
| **Launch Editor**    | `bi-pencil-square` | Apre l'editor con dropdown     | `bi-collection` Dalla collezione / `bi-book` Dal capitolo         |

#### Gruppo 4: Export & Print

| Pulsante             | Icona                  | Funzione                         | Output                         |
| -------------------- | ---------------------- | -------------------------------- | ------------------------------ |
| **Print / Save PDF** | `bi-printer`           | Stampa o salva come PDF (Ctrl+P) | File .pdf via dialog browser   |
| **Save as DOCX**     | `bi-file-earmark-word` | Esporta capitolo in Word         | File .docx download automatico |
| **PDF Viewer**       | `bi-file-pdf`          | Apre Mozilla PDF.js viewer       | Nuova tab                      |

### 📤 Funzionalità Export

#### 🖨️ Print / Save as PDF

Usa il dialog di stampa nativo del browser. Rispetta i CSS `@media print`, preserva formattazione e immagini con paginazione automatica. L'utente sceglie "Salva come PDF" nel dialog per ottenere un file .pdf.

#### 📝 Save as DOCX

Esporta il capitolo estratto direttamente in formato Word (.docx) con download automatico. Preserva la struttura del testo e la formattazione di base.

#### 📊 Word Count

- **Calcolo dinamico** del numero di parole
- Rimozione HTML tags per conteggio accurato
- Display in tempo reale nell'header
- Formato: `[N] words` (es. "1,245 words")

### 🎨 Highlighting System

**Come funziona:**

1. **Seleziona testo** nel capitolo
2. **Click su Highlight button** → Si apre dropdown con i colori
3. **Scegli colore** → Il pulsante cambia aspetto (mostra colore selezionato)
4. **Seleziona altro testo** → Click su Highlight → Applica evidenziazione
5. **Per rimuovere**: seleziona testo evidenziato → scegli l'opzione "Remove" con icona eraser

### 📖 Dictionary Lookup

**Funzionalità:**

- Seleziona una parola nel testo
- Click su **Dictionary button** (icona globo)
- Si apre WordReference in nuova tab
- URL generato automaticamente dalla parola selezionata (prima parola, senza punteggiatura)

### 🔄 Workflow Completo di Studio

**Scenario tipico:**

1. **Apertura Capitolo**: Libreria → Seleziona libro → Click Extract Chapter → Nuova finestra

2. **Lettura e Annotazione**: Leggi testo → Seleziona passaggio importante → Ctrl+C (auto-raccolto). Oppure: Seleziona → Click "Add Selection" (manuale).

3. **Evidenziazione**: Seleziona → Click Highlight → Scegli colore → Applica

4. **Lookup Parole**: Doppio-click parola → Click Dictionary → Consulta definizione

5. **Traduzione (se necessario)**: Click destro → "Traduci in Italiano" → Intero capitolo tradotto

6. **Creazione Report**: Click "Launch Editor" → Scegli sorgente → Si apre Summernote con i contenuti

7. **Editing Report**: Modifica testo → Aggiungi note → Formatta → Inserisci tabelle/link

8. **Export Finale**: Click "Export PDF" → Download report.pdf → Salvato in Downloads/

### 🎨 Sincronizzazione Theme

- I temi nella finestra estratta **sincronizzano** con la finestra principale
- Stessi 5 temi disponibili
- Persistenza indipendente (localStorage separato)

---

## 🔌 API Browser Utilizzate

Questo lettore EPUB è un esempio di **progressive web application** che sfrutta le API native del browser senza necessità di server backend.

### 💾 IndexedDB API

**Utilizzo:** Storage persistente della libreria EPUB

**Schema oggetto libro:** ogni libro è memorizzato con un ID univoco basato su timestamp, titolo e autore estratti dai metadati EPUB, il file completo come ArrayBuffer, la copertina in base64 e la data di aggiunta.

**Operazioni supportate:**

- `openDB()`: Apertura/creazione database con gestione VersionError
- `saveBookToDB(file)`: Salvataggio libro con estrazione metadata
- `getAllBooks()`: Recupero lista libri per griglia libreria
- `deleteBook(id)`: Rimozione permanente libro

**Vantaggi:**

- ✅ Storage illimitato (quote generose, tipicamente 50-100MB+)
- ✅ Persistenza dati tra sessioni
- ✅ Performance elevate per operazioni su blob
- ✅ Supporto transazioni ACID

### 🗄️ LocalStorage API

**Utilizzo:** Preferenze utente e raccolta chunks temporanei

**Keys utilizzate:**

- `epub-${bookTitle}-position`: ultima posizione di lettura (CFI string)
- `epub-fontSize`: dimensione font (50-200)
- `epub-lineHeight`: interlinea (1.0-1.8)
- `epub-theme`: nome tema corrente
- `epub-scrollMode`: booleano modalità scroll
- `epub-chunks-collection`: array JSON dei chunks raccolti

**Fallback Strategy:** se localStorage non è disponibile (es. blob:// URLs o iframe sandboxed), viene usato un oggetto in-memory come storage alternativo.

### 📋 Clipboard API

**Utilizzo:** Cattura automatica selezioni per raccolta chunks

Il listener sull'evento `copy` cattura automaticamente ogni selezione copiata: estrae il contenuto HTML completo (incluse immagini), lo salva nella collection e mostra un feedback visivo con toast.

**Caratteristiche:**

- ⚡ Cattura automatica e non-intrusiva
- 🖼️ Supporto immagini inline (base64)
- 📝 Preserva formattazione HTML
- 🔔 Feedback visivo con toast

### 🎨 Selection API

**Utilizzo:** Gestione selezioni per highlight, dictionary, add manual

Permette di ottenere il testo selezionato, il DOM range corrispondente, e di wrappare la selezione con elementi span per il highlighting. Usata anche per il dictionary lookup e la raccolta manuale.

**Use cases:** highlighting con colori, dictionary lookup, aggiunta manuale a collection, gestione evento copy.

### 🖼️ FileReader API

**Utilizzo:** Conversione file EPUB e immagini

Legge il file EPUB come ArrayBuffer per la memorizzazione in IndexedDB, e converte le copertine da blob URL a base64 per la visualizzazione persistente nelle card della libreria.

### 🌐 Blob & URL APIs

**Utilizzo:** Creazione finestre standalone per capitoli estratti

Il capitolo estratto viene convertito in un Blob HTML, poi in un URL temporaneo (`URL.createObjectURL`), aperto in una nuova finestra con `window.open`. L'URL temporaneo viene revocato automaticamente dopo l'uso.

**Vantaggi:**

- ✅ Finestre completamente standalone
- ✅ Nessun server richiesto
- ✅ Funziona offline
- ✅ Sicuro (same-origin policy)

### 🖨️ Print API

**Utilizzo:** Stampa e salvataggio PDF dal browser

Trigger diretto di `window.print()` che apre il dialog di stampa del browser. L'utente può scegliere "Salva come PDF". Rispetta i CSS `@media print` per una formattazione ottimale del documento stampato.

### 🔤 Canvas API (via html2canvas)

**Utilizzo:** Conversione HTML → Image per export PDF da Summernote

Renderizza il contenuto HTML dell'editor su canvas ad alta risoluzione (scale 2), con supporto CORS per le immagini. Il canvas viene convertito in PNG e inserito nel PDF tramite jsPDF con gestione multi-pagina automatica.

### 🌍 Translation API (Browser Native)

**Utilizzo:** Traduzione integrata del browser

**Metodi di attivazione:**

**1. Context Menu (Click destro)**: il browser mostra l'opzione "Traduci in [lingua]" nel menu contestuale.

**2. Translation Bar (Automatica)**: il browser rileva la lingua straniera tramite il tag `<html lang="...">` e mostra automaticamente la barra di traduzione.

**3. Extension Button**: icona traduzione nella barra degli indirizzi, click per selezionare la lingua target.

**Caratteristiche:**

- 🌐 Supporto 100+ lingue
- ⚡ Traduzione quasi istantanea
- 🎨 Preserva layout e formattazione
- 🖼️ Non traduce immagini (corretto)
- 🔄 Reversibile (torna all'originale)

**Privacy:**

- ⚠️ Google Translate: Invia contenuto a Google servers
- ⚠️ Microsoft Translator: Invia contenuto a Microsoft servers
- ℹ️ Alcune versioni di Chrome supportano traduzione offline

### 📊 Riepilogo API Utilizzate

| API              | Utilizzo Principale     | Fallback      | Offline               |
| ---------------- | ----------------------- | ------------- | --------------------- |
| **IndexedDB**    | Libreria EPUB           | ❌ Nessuno     | ✅ Sì                  |
| **LocalStorage** | Preferenze + Chunks     | Memory Object | ✅ Sì                  |
| **Clipboard**    | Auto-capture copy       | ❌ Nessuno     | ✅ Sì                  |
| **Selection**    | Highlight + Dictionary  | ❌ Nessuno     | ✅ Sì                  |
| **FileReader**   | Import EPUB             | ❌ Nessuno     | ✅ Sì                  |
| **Blob/URL**     | Finestre estratte       | ❌ Nessuno     | ✅ Sì                  |
| **Print**        | Save as PDF             | ❌ Nessuno     | ✅ Sì                  |
| **Canvas**       | HTML→Image (PDF export) | ❌ Nessuno     | ⚠️ Dipende da CDN     |
| **Translation**  | Traduzione testo        | ❌ Nessuno     | ⚠️ Dipende da browser |

**Legenda Offline:**

- ✅ Sì: Funziona completamente offline
- ⚠️ Dipende: Richiede risorse esterne (CDN, server traduzione)
- ❌ No: Richiede connessione obbligatoria

---

## 🔧 Dettagli Tecnici

### 📚 Librerie Utilizzate

Le seguenti librerie esterne sono caricate via CDN:

- **ePub.js** (cdn.jsdelivr.net): rendering del formato EPUB nel browser
- **JSZip** (cdn.jsdelivr.net): decompressione file EPUB
- **Bootstrap Icons** (cdn.jsdelivr.net): iconografia dell'interfaccia
- **jsPDF** (cdnjs.cloudflare.com): generazione PDF dall'editor report
- **html2canvas** (cdnjs.cloudflare.com): conversione HTML in immagine per PDF

L'editor report è implementato **senza librerie esterne**, usando direttamente le API `contenteditable` e `document.execCommand` del browser, con plugin custom per la gestione di tabelle e ridimensionamento immagini.

### 💾 Storage Architecture

**IndexedDB (Libreria):** database `EpubLibraryDB` con store `books`. Ogni record contiene ID univoco, titolo, autore, copertina in base64, ArrayBuffer del file e data di aggiunta.

**LocalStorage (Preferenze):** chiavi per posizione di lettura per libro, dimensione font, interlinea, tema, modalità scroll, e collezione chunks.

### 🎯 Algoritmi Chiave

**Navigazione per Href:** risolve l'href relativo rispetto al manifest EPUB, ottiene il CFI corrispondente, porta la rendition a quella posizione e aggiorna la posizione corrente.

**Estrazione Capitolo:** ottiene la posizione corrente, trova il corrispondente item nel TOC, estrae l'intervallo di sezioni (con opzione di includere sottolivelli), concatena i contenuti HTML e apre il risultato in una nuova finestra con toolbar completa.

**Ricreazione Rendition:** salva la posizione corrente, distrugge la rendition esistente, la ricrea con le nuove opzioni (spread, flow), ripristina la posizione salvata e ri-applica il tema.

### 🎨 Sistema Temi

15 temi predefiniti organizzati in 5 gruppi per sfondo: White (Normal, Soft White), Cream/Sepia (Cream, Sepia, Parchment), Light Gray (Light Gray, Cool Gray, Warm Gray), Medium Gray (Mid Gray, Slate), Dark/Black (Dark Gray, Charcoal, Dark, Midnight, True Black). I temi vengono applicati tramite il sistema `rendition.themes` di ePub.js e selezionati tramite swatches visivi nel popup.

---

## 🚀 Installazione e Uso

### Metodo 1: Apertura Diretta

Scarica il file HTML singolo e aprilo direttamente nel browser. Non richiede installazione o server.

### Metodo 2: Server Locale

Avvia un server locale (es. `python -m http.server 8000`) e apri il file tramite `http://localhost:8000/epubreader645.html`. Consigliato per evitare eventuali restrizioni CORS del browser.

### Metodo 3: Node.js

Installa `http-server` via npm e avvia il server locale per servire il file.

---

## 📱 Compatibilità Browser

| Browser     | Versione Minima | Note                                            |
| ----------- | --------------- | ----------------------------------------------- |
| **Chrome**  | 90+             | ✅ Completamente supportato                      |
| **Firefox** | 88+             | ✅ Completamente supportato                      |
| **Safari**  | 14+             | ⚠️ IndexedDB potrebbe avere limitazioni storage |
| **Edge**    | 90+             | ✅ Completamente supportato                      |
| **Opera**   | 76+             | ✅ Basato su Chromium                            |

**Requisiti Minimi:**

- ES6+ (Promises, async/await, arrow functions)
- IndexedDB API
- FileReader API
- Blob/URL APIs
- Canvas API (per PDF export)

---

## 🐛 Risoluzione Problemi

### Libro non si carica

**Problema**: Dopo import, il libro non appare in libreria. **Soluzione**: Verifica IndexedDB in DevTools → Application → Storage → IndexedDB → EpubLibraryDB → books.

### Posizione non salvata

**Problema**: Il libro riparte dall'inizio ogni volta. **Soluzione**: Usa il pulsante **Save State** (`bi-floppy`) per salvare esplicitamente le preferenze. Verifica in DevTools → Application → Storage → Local Storage le chiavi `epub-[bookTitle]-position`.

### PDF Export fallisce

**Problema**: Errore durante export PDF in capitolo estratto. **Soluzione**: Verifica connessione internet (librerie CDN). Controlla console browser per errori CORS. Prova la stampa diretta tramite il pulsante Print come alternativa.

### Sidebar non si apre

**Problema**: Click su toggle sidebar non funziona. **Soluzione**: Verifica che il TOC sia popolato aprendo la console browser e controllando `book.navigation.toc`.

---

## 🎓 Come Usare - Tutorial Rapido

### 1. Prima Apertura

1. Apri `epubreader645.html` nel browser
2. Vedrai la schermata libreria vuota
3. Click su "Import Book" (pulsante blu)
4. Seleziona un file .epub dal tuo computer
5. Attendi il caricamento (spinner)
6. Il libro appare nella griglia

### 2. Leggere un Libro

1. Click sulla card del libro desiderato
2. Si apre la finestra di lettura
3. Usa i pulsanti freccia flottanti per sfogliare (o attiva scroll mode)
4. Click sugli elementi dell'indice laterale per saltare capitoli
5. Personalizza font e tema con i pulsanti Typography e Theme nella toolbar

### 3. Estrarre un Capitolo

1. Durante la lettura, arriva al capitolo desiderato
2. Click su pulsante "Extract Chapter" (icona download)
3. Scegli se estrarre solo il capitolo corrente o anche i sottolivelli
4. Si apre nuova finestra con capitolo isolato
5. Usa Print, DOCX o PDF Viewer per esportare

### 4. Eliminare un Libro

1. Torna alla libreria (pulsante "Library" in alto a sinistra)
2. Passa il mouse sulla card del libro
3. Appare pulsante X rosso in alto a destra
4. Click su X → Conferma eliminazione
5. Il libro viene rimosso permanentemente

---

## 💡 Esempi Pratici d'Uso

### 📖 Caso d'Uso 1: Lettore Comune - Leggere Libri in Qualsiasi Lingua

**Scenario:** Vuoi leggere un bestseller appena uscito in inglese, ma non sei fluente

**Il Problema Tradizionale:**

- ❌ Aspettare mesi/anni per la traduzione italiana ufficiale
- ❌ Leggere in inglese con difficoltà e dizionario alla mano
- ❌ Perdere il piacere della lettura per lo sforzo linguistico
- ❌ Non capire sfumature e giochi di parole

**La Soluzione con Questo Lettore:**

**Workflow Semplice:**

1. **Import** del libro EPUB in inglese (es. "The Midnight Library")
2. **Apri il libro** e inizia a leggere normalmente
3. **Quando trovi difficoltà**: Click destro sulla pagina → Seleziona **"Traduci in Italiano"** → ⚡ In 2-3 secondi l'intera pagina è tradotta
4. **Continua a leggere** nella tua lingua madre!

**Funzionalità Bonus:**

- 🔄 **Switch istantaneo**: Click destro → "Mostra originale" per vedere la versione inglese
- 📖 **Paragone diretto**: Apri due tab (originale + tradotto) per confrontare
- 🎯 **Parole chiave**: Impara i termini originali mentre leggi tradotto
- 📚 **Qualsiasi lingua**: Funziona per EN→IT, FR→IT, ES→IT, DE→IT, ecc.

**Vantaggi Rispetto alle Alternative:**

| Metodo                             | Tempo         | Qualità  | Costo      | Esperienza |
| ---------------------------------- | ------------- | -------- | ---------- | ---------- |
| **Attesa traduzione ufficiale**    | 6-24 mesi     | ⭐⭐⭐⭐⭐    | €15-25     | Frustrante |
| **Google Translate copia-incolla** | Lentissimo    | ⭐⭐⭐      | Gratis     | Orribile   |
| **Leggere in originale**           | Immediato     | ⭐⭐⭐⭐⭐    | €5-15      | Difficile  |
| **📚 Questo Lettore EPUB**         | **2 secondi** | **⭐⭐⭐⭐** | **Gratis** | **Fluida** |

**Tipi di Lettori che Ne Beneficiano:**

**🎓 Lo Studente di Lingue**: legge romanzi in lingua target, traduce quando si blocca, impara nel contesto reale.

**👴 Il Lettore Senior**: vuole leggere classici in originale senza lo sforzo del dizionario, traduzione istantanea = accessibilità.

**🌍 L'Expat/Immigrato**: vive in Italia ma madrelingua straniera, vuole leggere libri italiani tradotti in propria lingua per comprensione piena.

**🚀 L'Early Adopter**: legge libri il giorno del lancio globale senza aspettare traduzioni, accesso immediato a contenuti mondiali.

**💼 Il Professionista**: legge manuali tecnici in lingue straniere e traduce sezioni complesse risparmiando ore di lavoro.

**Limitazioni da Conoscere:**

⚠️ **Traduzione automatica** (non umana):

- ✅ Ottima per comprensione generale (~85-90% accuratezza)
- ⚠️ Può perdere giochi di parole e sfumature culturali
- ⚠️ Nomi propri a volte tradotti erroneamente
- ⚠️ Poesia e prosa altamente stilizzata: meglio l'originale

**Pro Tip Avanzato:**

Per la miglior esperienza: leggi il capitolo in traduzione automatica per la velocità; se qualcosa non è chiaro, guarda l'originale; per i passaggi cruciali (climax, rivelazioni), leggi entrambe le versioni; copia le frasi memorabili in originale nella collection; crea un report bilingue con l'editor.

**⚡ Impatto sulla Cultura della Lettura:**

Questa funzionalità **democratizza l'accesso** alla letteratura mondiale:

- 📚 **Milioni di libri** mai tradotti in italiano diventano accessibili
- 🌍 **Autori indie internazionali** raggiungono pubblico italiano
- 🚀 **Lanci sincronizzati**: Leggi bestseller USA lo stesso giorno dell'uscita
- 💰 **Risparmio**: EPUB inglesi costano 30-50% meno delle traduzioni italiane
- 📖 **Più lettura**: Rimuove barriere linguistiche = più libri letti

---

### 📚 Caso d'Uso 2: Studente Universitario

**Scenario:** Preparazione esame di letteratura inglese

**Workflow:**

1. **Import del libro** (es. "Pride and Prejudice")
2. **Lettura capitoli** con modalità sepia (meno affaticamento)
3. **Estrazione capitolo corrente** prima di studiarlo
4. **Traduzione** in italiano per confronto
5. **Highlighting** dei passaggi chiave in giallo
6. **Copy** citazioni importanti (auto-raccolte)
7. **Dictionary lookup** per termini complessi
8. **Create Report** → Ottieni documento Summernote con tutte le citazioni
9. **Editing in Summernote**: Aggiungi note personali, commenti, analisi
10. **Export PDF** → Stampa o consegna al professore

**Tempo risparmiato:** ~2 ore rispetto a copia manuale + formattazione

---

### 🔬 Caso d'Uso 3: Ricercatore Scientifico

**Scenario:** Lettura paper tecnico in formato EPUB

**Workflow:**

1. **Import EPUB** del paper/manuale
2. **Modalità Dual Page** per vedere grafici affiancati al testo
3. **Estrazione capitolo** "Methodology"
4. **Add Selection manuale** di ogni figura/grafico importante
5. **Copy** paragrafi rilevanti per ogni immagine
6. **Highlight** in verde le formule matematiche
7. **Create Report** → 15 chunks raccolti (immagini + testo)
8. **Summernote editing**: riordina chunks logicamente, aggiungi intestazioni per sezioni, inserisci tabelle comparative, formatta formule in grassetto
9. **Export PDF** → Allegato per presentazione

**Vantaggio:** Immagini già in base64, nessun problema di path o linking

---

### 📖 Caso d'Uso 4: Lettore Multilingue - Apprendimento Lingue

**Scenario:** Imparare lo spagnolo leggendo romanzi

**Workflow:**

1. **Import** romanzo in spagnolo
2. **Lettura** con modalità scroll (meno interruzioni)
3. **Estrazione capitolo**
4. **Dictionary lookup** per parole sconosciute (apre WordReference)
5. **Highlight verde** per nuove parole imparate
6. **Traduzione intera pagina** in italiano per comprensione
7. **Confronto** versione spagnola ↔ italiana (due tab aperte)
8. **Copy frasi idiomatiche** interessanti
9. **Create Report** → Vocabolario personalizzato
10. **Summernote**: Organizza per categoria (verbi, sostantivi, modi di dire)

**Beneficio:** Dizionario + traduzione + raccolta vocaboli in un'unica app

---

### 📝 Caso d'Uso 5: Blogger/Content Creator

**Scenario:** Creare review di un libro

**Workflow:**

1. **Import libro** da recensire
2. **Lettura completa** con annotazioni mentali
3. **Secondo passaggio**: estrai capitolo 1 → Copy intro memorabile; estrai capitolo 5 → Copy plot twist; estrai capitolo finale → Copy conclusione
4. **Highlight rosa** delle migliori citazioni
5. **Ogni chapter** → Add Selection delle citazioni + cover images
6. **Create Report** → 12 chunks raccolti
7. **Summernote editing**: aggiungi rating personale, commenti su stile narrativo, Pro/Contro con liste puntate, link a Amazon/Goodreads
8. **Copy HTML** da Summernote
9. **Paste** nel CMS del blog (WordPress, Ghost, ecc.)

**Tempo risparmiato:** ~3 ore rispetto a rilettura + screenshots + trascrizione manuale

---

### 🎓 Caso d'Uso 6: Insegnante

**Scenario:** Preparare materiale didattico da un manuale

**Workflow:**

1. **Import** manuale didattico EPUB
2. **Navigazione** tramite indice (sidebar) ai capitoli rilevanti
3. **Per ogni argomento**: estrai capitolo, highlight giallo per concetti base, highlight verde per esempi pratici
4. **Copy** ogni sezione evidenziata (auto-raccolte)
5. **Create Report** → 30+ chunks organizzati
6. **Summernote editing**: riordina logicamente per lezione, aggiungi domande di verifica personalizzate, inserisci link a video YouTube correlati, formatta con intestazioni H2/H3 per leggibilità
7. **Export PDF** → Dispense per studenti
8. **Print** → Copie cartacee per classe

**Vantaggio:** Materiale originale + personalizzazione in 1/3 del tempo

---

### 🧳 Caso d'Uso 7: Viaggiatore

**Scenario:** Preparare viaggio con guida turistica EPUB

**Workflow:**

1. **Import** "Lonely Planet - Tokyo"
2. **Estrazione capitoli** per quartiere: Shibuya → Copy ristoranti consigliati; Asakusa → Copy templi da visitare; Shinjuku → Copy vita notturna
3. **Highlight** attrazioni must-see in giallo
4. **Add Selection** mappe presenti nel libro
5. **Traduzione** sezioni in giapponese
6. **Create Report** → Itinerario personalizzato
7. **Summernote**: Giorno 1: Shibuya chunks; Giorno 2: Asakusa chunks; aggiungi note su orari apertura; inserisci link Google Maps
8. **Export PDF** → Guida tascabile offline sul telefono

**Portabilità:** PDF leggibile ovunque, anche senza internet

---

## 🎯 Best Practices per l'Uso Ottimale

### ✅ Raccolta Chunks Efficace

**DO:**

- ✅ Seleziona **porzioni auto-contenute** (paragrafo completo, non mezza frase)
- ✅ Includi **contesto sufficiente** (titolo sezione se necessario)
- ✅ Raccogli **immagini con didascalia** insieme
- ✅ Usa **highlighting** per categorizzare chunks visivamente
- ✅ **Periodicamente** crea report intermedi per non perdere lavoro

**DON'T:**

- ❌ Non copiare frasi spezzate senza senso
- ❌ Non raccogliere troppo (>50 chunks diventa difficile da gestire)
- ❌ Non dimenticare di **clear collection** quando cambi progetto
- ❌ Non fare report con chunks da libri diversi (confusione)

### ✅ Organizzazione Libreria

**DO:**

- ✅ Usa nomi file EPUB descrittivi prima di importare
- ✅ Elimina duplicati regolarmente
- ✅ Tieni libri finiti vs. in corso in librerie separate (usa browser profiles)

**DON'T:**

- ❌ Non sovraccaricare IndexedDB (limite ~50-100 libri a seconda browser)
- ❌ Non importare EPUB corrotti (controlla prima)

### ✅ Performance & Storage

Per monitorare lo spazio usato, apri DevTools → Console e usa l'API `navigator.storage.estimate()`. Per pulire completamente tutti i dati, elimina il database IndexedDB (`EpubLibraryDB`) e svuota localStorage dalle DevTools → Application → Storage.

---

## 🔐 Privacy e Sicurezza

### 🔒 Dati Locali

- **Tutti i dati** sono memorizzati localmente nel browser
- **Nessuna comunicazione** con server esterni (eccetto CDN per librerie)
- **Nessun tracking** o analytics
- **Puoi usare offline** dopo primo caricamento delle librerie

### 🗑️ Pulizia Dati

Per eliminare tutti i dati: apri DevTools → Application → Storage e cancella IndexedDB (`EpubLibraryDB`) e localStorage. In alternativa usa la console del browser per eseguire le operazioni di pulizia database direttamente.

---

## 🤝 Contribuire

Questo progetto è open source. Contributi benvenuti!

### Idee per Miglioramenti

#### 🎨 UI/UX

- [ ] Drag & drop per import libri (File API)
- [ ] Dark mode automatico (rispetta system preference via `matchMedia`)
- [ ] Gesture swipe per navigazione pagine (Touch Events API)
- [ ] Animazioni transizione tra pagine (Web Animations API)

#### 📚 Funzionalità Lettura

- [ ] Ricerca full-text nei libri (con IndexedDB full-text search)
- [ ] Annotazioni persistenti con posizione CFI
- [ ] Highlights persistenti salvati in IndexedDB
- [ ] Statistiche lettura (tempo, pagine lette) via Performance API

#### 🔄 Sincronizzazione

- [ ] Sync con cloud storage (Google Drive, Dropbox) via OAuth
- [ ] Export annotazioni in Markdown
- [ ] Import/Export backup libreria (JSON format)
- [ ] Sync posizione lettura multi-device (Cloud Storage API)

#### 🎙️ Audio & Accessibilità

- [ ] Supporto TTS (Text-to-Speech) via SpeechSynthesis API
- [ ] Controlli vocali via SpeechRecognition API
- [ ] Modalità ad alto contrasto
- [ ] Dimensioni font accessibili (min 150%, max 300%)

#### 🔍 Ricerca & Analisi

- [ ] Dizionario integrato con pop-up on-hover
- [ ] Traduzione selezione inline (senza cambiare pagina)
- [ ] AI summary dei capitoli (con API esterne)
- [ ] Word frequency analysis
- [ ] Export glossario termini chiave

#### 📦 Raccolta Chunks Avanzata

- [ ] **Tag e categorie** per chunks raccolti
- [ ] **Filtri e ricerca** nella collection
- [ ] **Export chunks singoli** (HTML, PDF, TXT)
- [ ] **Anteprima chunks** prima di creare report
- [ ] **Riordino drag-and-drop** dei chunks
- [ ] **Merge automatico** chunks duplicati
- [ ] **Statistiche collection** (total words, images count)

#### 🔗 Integrazione Browser

- [ ] **Web Share API**: Condividi chunks sui social
- [ ] **Background Sync**: Sync collection quando torna online
- [ ] **Service Worker**: Cache intelligente per offline completo
- [ ] **Push Notifications**: Promemoria lettura

#### 📊 Report Avanzati

- [ ] **Template report**: Pre-formattati per uso accademico
- [ ] **Export multipli**: LaTeX, Markdown
- [ ] **Citation generator**: Bibliografia automatica
- [ ] **Table of Contents**: Auto-generato dai chunks
- [ ] **Footnotes & References**: Sistema completo

#### 🧪 Funzionalità Sperimentali

- [ ] **OCR per immagini**: Estrai testo da immagini nei capitoli
- [ ] **AI-powered summary**: Riassunti automatici con LLM
- [ ] **Smart chunking**: AI suggerisce chunk boundaries
- [ ] **Related content**: Suggerimenti basati su chunks raccolti
- [ ] **Collaborative reading**: Condividi collezioni con altri utenti

---

## 📄 Licenza

MIT License - Vedi file LICENSE per dettagli.

---

## 👨‍💻 Autore

Sviluppato con ❤️ per gli amanti della lettura digitale.

**Tecnologie**: HTML5, CSS3, JavaScript ES6+, ePub.js, jsPDF, html2canvas

---

## 🙏 Ringraziamenti

- [ePub.js](https://github.com/futurepress/epub.js/) - Rendering EPUB
- [Bootstrap Icons](https://icons.getbootstrap.com/) - Iconografia
- [jsPDF](https://github.com/parallax/jsPDF) - Generazione PDF
- [html2canvas](https://html2canvas.hertzen.com/) - HTML to Canvas conversion

---

## 📞 Supporto

Per bug report o richieste feature:

- Apri una **Issue** su GitHub
- Includi versione browser e screenshot
- Descrivi passi per riprodurre il problema

---

**Happy Reading! 📖✨**
