# 📚 EPUB Reader - Lettore EPUB Web Avanzato

Un lettore EPUB moderno, completamente autocontenuto in un singolo file HTML, con supporto nativo per la traduzione browser e interfaccia responsive.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## ✨ Caratteristiche Principali

### 🌐 Traduzione Browser-Friendly
**Caratteristica unica**: A differenza della maggior parte dei lettori EPUB web, questa applicazione è progettata per essere **completamente traducibile** utilizzando i sistemi di traduzione integrati nei browser moderni (Google Translate, Microsoft Translator, etc.). Il contenuto degli EPUB viene renderizzato in modo che i browser possano accedere e tradurre il testo, sia nella modalità paginated che nella sidebar dei segnalibri.

### 📖 Funzionalità Complete di Lettura
- **Indice interattivo a 3 livelli** con espansione/collasso gerarchico
- **Modalità di visualizzazione multiple**: paginated, scroll continuo, doppia pagina
- **4 temi di lettura**: Normal, Sepia, Gray, Dark
- **Controllo tipografia avanzato**: font size (50%-200%) e interlinea (1, 1.2, 1.4, 1.6, 1.8)
- **Navigazione fluida** tramite pulsanti o segnalibri

### 🎨 Interfaccia Moderna
- **Design responsive** ottimizzato per desktop, tablet e smartphone
- **Bottoniera colorata** con icone Bootstrap Icons
- **Header compatto** con gradiente moderno
- **Gruppi logici** di controlli per facilità d'uso
- **Feedback visivo** immediato su tutte le azioni

### 🚀 Tecnologia
- **File singolo autocontenuto**: tutto il codice in un unico file HTML
- **Zero installazione**: apri e usa
- **Funziona offline** dopo il primo caricamento
- **Dipendenze CDN stabili** con versioni fisse garantite

## 📋 Funzionalità Dettagliate

### Controlli Tipografia
| Funzione | Descrizione | Range/Valori |
|----------|-------------|--------------|
| **Font Size +5/-5** | Incremento/decremento rapido | 50% - 200% |
| **Font Size +1/-1** | Controllo fine della dimensione | 50% - 200% |
| **Reset Font** | Ripristino dimensione predefinita | 100% |
| **Interlinea** | Spaziatura tra righe | 1, 1.2, 1.4, 1.6, 1.8 |

### Modalità di Visualizzazione
- **Paginated Mode** (default): Visualizzazione a pagine con pulsanti prev/next
- **Scroll Mode**: Scorrimento continuo verticale del capitolo
- **Dual Page Mode**: Visualizzazione affiancata di due pagine (solo in paginated)

### Temi Colore
1. **Normal**: Sfondo bianco, testo nero (predefinito)
2. **Sepia**: Sfondo beige (#f4ecd8), testo nero - ideale per lettura prolungata
3. **Gray**: Sfondo grigio chiaro (#e5e7eb), testo nero - riduce affaticamento
4. **Dark**: Sfondo nero (#1a1a1a), testo grigio chiaro - lettura notturna

### Navigazione
- **Table of Contents (TOC)**: Sidebar con indice gerarchico a 3 livelli
- **Pulsanti Prev/Next**: Navigazione sequenziale (in paginated mode)
- **Click su segnalibri**: Salto diretto a capitoli/sezioni
- **Toggle Sidebar**: Mostra/nascondi TOC per massimizzare spazio lettura

## 🛠️ Tecnologie Utilizzate

### Librerie Core
- **[epub.js](https://github.com/futurepress/epub.js/) v0.3.93**: Engine di rendering EPUB
- **[JSZip](https://stuk.github.io/jszip/) v3.10.1**: Gestione archivi EPUB
- **[Bootstrap Icons](https://icons.getbootstrap.com/) v1.11.3**: Libreria iconografica

### CDN
Tutte le librerie sono servite da **jsDelivr** con versioni fisse per garantire disponibilità permanente:
```
https://cdn.jsdelivr.net/npm/jszip@3.10.1/dist/jszip.min.js
https://cdn.jsdelivr.net/npm/epubjs@0.3.93/dist/epub.min.js
https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css
```

## 🚀 Come Usare

### Installazione
1. **Scarica** il file HTML
2. **Apri** il file con qualsiasi browser moderno (Chrome, Safari, Edge)
3. Nessuna installazione o configurazione richiesta!

### Utilizzo Base
1. Clicca su **"Scegli file"** per selezionare un file EPUB dal tuo dispositivo
2. L'EPUB verrà caricato automaticamente con l'indice nella sidebar
3. Usa i **controlli nella toolbar** per personalizzare la lettura
4. Clicca sui **segnalibri** per navigare tra i capitoli

### Traduzione del Contenuto
**Caratteristica speciale**: Per tradurre il contenuto EPUB:

#### Desktop (Chrome/Edge):
1. Click destro sul testo → "Traduci in..."
2. Oppure usa l'icona di traduzione nella barra degli indirizzi

#### Mobile (Chrome):
1. Menu browser (⋮) → "Traduci..."
2. Seleziona la lingua di destinazione

**Nota**: La modalità **paginated** offre risultati di traduzione migliori rispetto alla modalità scroll su alcuni browser mobile.

## 📱 Compatibilità

### Browser Supportati
- ✅ Chrome/Edge 90+
- ✅ Safari 14+
- ✅ Opera 76+

### Dispositivi
- ✅ Desktop (Windows, macOS, Linux)
- ✅ Tablet (iPad, Android tablets)
- ✅ Smartphone (iOS, Android)

### Responsive Design
L'interfaccia si adatta automaticamente a:
- **Desktop**: Layout completo con tutti i controlli visibili
- **Tablet**: Sidebar proporzionale, controlli ottimizzati
- **Smartphone**: Layout compatto, header a più righe se necessario

## ⚙️ Configurazione Avanzata

### Impostazioni Predefinite
Le seguenti impostazioni possono essere modificate direttamente nel codice JavaScript:

```javascript
let fontSize = 100;        // Dimensione font iniziale (%)
let lineHeight = 1.2;      // Interlinea iniziale
let scrollMode = false;    // Modalità scroll (false = paginated)
let dualPageMode = false;  // Doppia pagina (false = singola)
let sidebarVisible = true; // Sidebar visibile all'avvio
let currentTheme = 'normal'; // Tema iniziale
```

## 🔒 Privacy e Sicurezza

- ✅ **Nessun tracking**: L'app non raccoglie dati
- ✅ **Nessun server**: Tutto funziona localmente nel browser
- ✅ **I tuoi file rimangono privati**: Gli EPUB non vengono caricati su server esterni
- ✅ **Open source**: Codice completamente ispezionabile

## 🐛 Problemi Noti e Limitazioni

### Traduzione su Mobile
- Su alcuni browser mobile (specialmente in modalità scroll), la traduzione automatica potrebbe tradurre solo porzioni del testo a causa delle limitazioni dei browser nel tradurre contenuti in iframe dinamici
- **Soluzione**: Usa la modalità **paginated** per traduzioni più complete su mobile

### Compatibilità EPUB
- Supporta EPUB 2 e EPUB 3
- Alcuni EPUB con DRM non sono supportati
- EPUB con JavaScript complesso potrebbero non funzionare correttamente

## 🗺️ Roadmap Futura

Possibili funzionalità future:
- [ ] Salvataggio posizione di lettura nel localStorage
- [ ] Annotazioni e highlights
- [ ] Ricerca full-text
- [ ] Esportazione note
- [ ] Integrazione dizionario
- [ ] Supporto formati aggiuntivi (PDF, MOBI)
- [ ] Modalità lettura veloce
- [ ] Sincronizzazione cloud opzionale

## 📄 Licenza

Questo progetto è rilasciato sotto licenza **MIT**. Vedi il file `LICENSE` per i dettagli.

## 🤝 Contributi

I contributi sono benvenuti! Per favore:
1. Fai un fork del progetto
2. Crea un branch per la tua feature (`git checkout -b feature/AmazingFeature`)
3. Commit delle modifiche (`git commit -m 'Add some AmazingFeature'`)
4. Push al branch (`git push origin feature/AmazingFeature`)
5. Apri una Pull Request

## 📧 Contatti

Per bug, suggerimenti o domande, apri una [issue](../../issues) su GitHub.

## 🙏 Ringraziamenti

- [epub.js](https://github.com/futurepress/epub.js/) - Per l'eccellente libreria di rendering EPUB
- [JSZip](https://stuk.github.io/jszip/) - Per la gestione degli archivi
- [Bootstrap Icons](https://icons.getbootstrap.com/) - Per le bellissime icone
- [jsDelivr](https://www.jsdelivr.com/) - Per l'hosting CDN affidabile

---

**Fatto con ❤️ per gli amanti della lettura digitale**
