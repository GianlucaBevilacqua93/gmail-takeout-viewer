# gmail-takeout-viewer
# Visualizzatore offline di Gmail — Google Takeout

> **Un file HTML singolo per leggere la tua posta Gmail esportata, completamente in locale. Zero rischi per la privacy: nessun dato inviato a nessun server.**

**[🇮🇹 Italiano](#-italiano) | [🇬🇧 English](#-english)**

---

## 🇮🇹 Italiano

### 🔒 Privacy prima di tutto

> **I tuoi dati non lasciano mai il tuo dispositivo.**
>
> Questo strumento gira interamente nel browser. Nessuna email, nessun allegato, nessun metadato viene trasmesso a server esterni. Il codice sorgente è aperto e verificabile riga per riga. Ideale per scuole, enti pubblici e chiunque debba gestire archivi di posta con il massimo riserbo.

---

### 📖 Panoramica

Questo progetto nasce da un'esigenza concreta: un docente che deve **trasferirsi in una nuova scuola o su un nuovo sistema di posta** e ha necessità di consultare l'archivio storico delle email esportate da Google Takeout, senza doversi affidare a software di terze parti o servizi cloud.

Un singolo file `.html` — nessuna installazione, nessuna dipendenza, nessun server.

### Architettura del Sistema

```
┌──────────────────┐      ┌───────────────────────┐       ┌─────────────────┐
│  Google Takeout  │─────▶│  Browser (100% locale)│─────▶ │  Visualizzatore │
│   (.zip / .mbox) │      │  Nessuna connessione  │       │   Gmail Offline │
└──────────────────┘      └───────────────────────┘       └─────────────────┘
                                      ▲
                               ZERO dati inviati
                               a server esterni
```

### 📦 Struttura del Progetto

```
gmail-takeout-viewer/
├── gmail-offline.html     
├── LICENSE
└── README.md
```

---

## 🚀 Caratteristiche principali

* 🔒 **Privacy assoluta** — tutto gira nel browser, nessun dato inviato a server
* ⚡ **Caricamento streaming** — file `.mbox` da più di 1,5 GB supportati senza crash
* 📁 **ZIP e MBOX** — importa direttamente l'export di Google Takeout
* 🗂️ **Etichette ad albero** — sottoetichette espandibili nella sidebar
* 📅 **Anno scolastico** — raggruppamento automatico da settembre ad agosto
* 📖 **Conversazioni** — visualizzazione thread con badge singolo/multiplo
* 🖨️ **Stampa selettiva** — scegli quali messaggi di una conversazione stampare
* 📎 **Allegati inline** — anteprima di immagini, PDF, video direttamente nel browser
* 🔍 **Ricerca rapida** — cerca per mittente, oggetto, anteprima del testo
* 📄 **Paginazione** — 50 messaggi per pagina con navigazione frecce
* 📱 **Interfaccia Gmail** — design familiare, sidebar collassabile
* 🌐 **Zero installazione** — un file HTML, apri e usa

---

## 📋 Requisiti

* **Browser moderno** — Chrome 90+, Firefox 88+, Edge 90+, Safari 15+
* **File Google Takeout** — `.zip` (≤ 400 MB) oppure `.mbox` diretto (qualsiasi dimensione)
* **Nessuna connessione internet** richiesta dopo il primo caricamento della pagina

---

## 🎯 Utilizzo

### Opzione A — Usa direttamente online (consigliato)

Nessun download necessario. Apri la pagina GitHub Pages e importa il tuo file:

**[➡️ Apri Gmail Offline Viewer](https://gianlucabevilacqua93.github.io/gmail-takeout-viewer/)**

> ⚠️ Anche usando la versione online, **i tuoi file non lasciano mai il browser**. La pagina viene scaricata una sola volta; tutto il processing avviene localmente.

### Opzione B — Scarica e usa offline

1. Scarica `gmail-takeout-viewer.html` da questo repository
2. Aprilo con il tuo browser (doppio click o `File → Apri`)
3. Clicca **"Importa Mail"** e seleziona il tuo file

### Passo 1: Esporta da Google Takeout

1. Vai su [takeout.google.com](https://takeout.google.com)
2. Seleziona solo **Gmail**
3. Scarica il file `.zip`

### Passo 2: Importa nel visualizzatore

| Tipo file | Dimensione | Procedura |
|-----------|-----------|-----------|
| `.zip` | ≤ 400 MB | Importa direttamente |
| `.zip` | > 400 MB | Estrai lo ZIP → importa il `.mbox` |
| `.mbox` | qualsiasi | Importa direttamente (streaming) |

> 💡 **Consiglio per archivi grandi**: estrai lo ZIP e importa il file `.mbox` contenuto in `Takeout/Mail/`. Il file `.mbox` viene letto in streaming a blocchi da 32 MB — nessun limite di dimensione, nessun crash.

### Passo 3: Naviga la posta

* **Sidebar sinistra**: cartelle standard (Posta in arrivo, Inviati, Spam) + anno scolastico + etichette
* **Anno scolastico**: clicca su un anno (es. `2024/25`) per vedere tutta la posta di quell'anno
* **Etichette**: le sottoetichette sono raggruppate ed espandibili con `›`
* **Ricerca**: barra in alto, con `✕` per cancellare il filtro
* **Paginazione**: 50 thread per pagina, frecce di navigazione in basso

---

## 🔐 Dettagli Tecnici sulla Privacy

| Aspetto | Comportamento |
|---------|--------------|
| Trasmissione dati | ❌ Nessuna — il browser non apre connessioni durante l'uso |
| Storage locale | ❌ Nessuno — nessun dato scritto su localStorage, cookie o IndexedDB |
| Log/analytics | ❌ Assenti |
| Dipendenze esterne | ✅ Solo JSZip e DOMPurify (caricati da CDN al primo avvio, poi il browser li memorizza nella cache) |
| Codice sorgente | ✅ Un singolo file HTML, leggibile e verificabile |

Per uso in ambienti completamente air-gapped (senza Internet), è sufficiente scaricare il file HTML e modificare i due `<script src="...">` con copie locali di JSZip e DOMPurify.

---

## 💡 Vantaggi

* 🏫 **Scuole e PA** — gestione archivi email senza dipendenza da software commerciali
* 🔒 **Dati sensibili** — email di minori, dati personali, comunicazioni riservate restano sul dispositivo
* 💾 **Senza installazione** — funziona su qualsiasi computer senza privilegi di amministratore
* 🌐 **Cross-platform** — Windows, macOS, Linux, Chromebook
* 📴 **Offline** — funziona senza connessione internet

---

## ⚠️ Limitazioni Note

* `.zip` > 400 MB: il browser non supporta decompressione streaming dei ZIP → estrai e usa il `.mbox`
* Allegati > 800 KB: caricati in memoria solo quando aperti (lazy loading)
* La ricerca full-text opera su anteprima del messaggio (200 caratteri), non sul testo completo

---

## 🔮 Sviluppi Futuri

* [ ] Ricerca full-text sul corpo completo dei messaggi
* [ ] Esportazione filtrata (es. tutti i messaggi di un anno in PDF)
* [ ] Tema scuro
* [ ] Supporto multi-account (più file `.mbox` contemporaneamente)
* [ ] Modalità stampa migliorata con intestazione personalizzata
* [ ] Supporto a `EML` e altri formati di export

---

## 🤝 Contribuire

I contributi della community open source sono benvenuti e incoraggiati! Il progetto è nato da un'esigenza scolastica reale e può migliorare grazie all'esperienza di tutti.

### Come contribuire

1. **Fork** del repository
2. Crea un branch (`git checkout -b feature/NuovaFeature`)
3. Commit delle modifiche (`git commit -m 'Aggiunta NuovaFeature'`)
4. Push sul branch (`git push origin feature/NuovaFeature`)
5. Apri una **Pull Request**

### Aree in cui contribuire

* 🐛 **Segnalazione bug** — apri una Issue con il file `.mbox` (o una versione anonimizzata) che causa il problema
* 🌍 **Traduzioni** — aggiungi il supporto per altre lingue
* 🎨 **UI/UX** — miglioramenti all'interfaccia
* ⚡ **Performance** — ottimizzazioni per archivi molto grandi
* 📚 **Documentazione** — guide, tutorial, casi d'uso

### Linee guida

* Mantieni il progetto come **singolo file HTML** (nessuna build step, nessuna dipendenza npm)
* Nessun dato deve mai lasciare il browser — ogni modifica deve rispettare questo principio
* Testa con file `.mbox` reali di varie dimensioni (piccoli, medi, > 1 GB)
* Aggiorna la documentazione per ogni nuova funzionalità

---

## ✉️ Contatti e supporto

* **Email**: [gianlucabevilacqua.93@gmail.com](mailto:gianlucabevilacqua.93@gmail.com)
* **GitHub Issues**: [Segnala un problema o proponi una feature](https://github.com/GianlucaBevilacqua93/gmail-takeout-viewer/issues)

---

**Made with ❤️ per la comunità scolastica italiana e la community Open Source**

*Se questo strumento ti è stato utile, lascia una ⭐ — aiuta altri a trovarlo!*

---

## 🇬🇧 English

### 🔒 Privacy First

> **Your data never leaves your device.**
>
> This tool runs entirely in the browser. No emails, attachments, or metadata are transmitted to external servers. The source code is open and auditable line by line.

---

### 📖 Overview

This project was born from a concrete need: a teacher **migrating to a new school or email system** that needed to consult the historical email archive exported from Google Takeout, without relying on third-party software or cloud services.

A single `.html` file — no installation, no dependencies, no server.

### System Architecture

```
┌──────────────────┐      ┌───────────────────────┐      ┌─────────────────┐
│  Google Takeout  │─────▶│  Browser (100% local) │─────▶│  Gmail Offline  │
│   (.zip / .mbox) │      │  No network calls     │      │     Viewer      │
└──────────────────┘      └───────────────────────┘      └─────────────────┘
                                      ▲
                            ZERO data sent to
                            external servers
```

---

## 🚀 Key Features

* 🔒 **Absolute privacy** — runs entirely in the browser, no data sent to servers
* ⚡ **Streaming loading** — `.mbox` files over 1.5 GB supported without crashes
* 📁 **ZIP and MBOX** — import Google Takeout exports directly
* 🗂️ **Tree-style labels** — expandable sub-labels in the sidebar
* 📅 **School year grouping** — automatic grouping from September to August
* 📖 **Thread view** — conversation display with single/multiple message badge
* 🖨️ **Selective printing** — choose which messages in a conversation to print
* 📎 **Inline attachments** — preview images, PDFs, videos directly in the browser
* 🔍 **Quick search** — search by sender, subject, message preview
* 📄 **Pagination** — 50 messages per page with arrow navigation
* 📱 **Gmail-like UI** — familiar design, collapsible sidebar
* 🌐 **Zero installation** — one HTML file, open and use

---

## 🎯 Usage

### Option A — Use directly online (recommended)

No download needed. Open the GitHub Pages and import your file:

**[➡️ Open Gmail Takeout Viewer](https://gianlucabevilacqua93.github.io/gmail-takeout-viewer/)**

> ⚠️ Even when using the online version, **your files never leave the browser**. The page is downloaded once; all processing happens locally.

### Option B — Download and use offline

1. Download `gmail-takeout-viewer.html` from this repository
2. Open it in your browser (double-click or `File → Open`)
3. Click **"Importa Mail"** and select your file

### Step 1: Export from Google Takeout

1. Go to [takeout.google.com](https://takeout.google.com)
2. Select only **Gmail**
3. Download the `.zip` file

### Step 2: Import

| File type | Size | Procedure |
|-----------|------|-----------|
| `.zip` | ≤ 400 MB | Import directly |
| `.zip` | > 400 MB | Extract ZIP → import the `.mbox` |
| `.mbox` | any | Import directly (streaming) |

### Step 3: Browse

* **Left sidebar**: standard folders + school year + labels
* **School year**: click a year (e.g. `2024/25`) to see all mail for that year
* **Labels**: sub-labels are grouped and expandable with `›`
* **Search**: top bar, with `✕` to clear the filter
* **Pagination**: 50 threads per page, navigation arrows at the bottom

---

## 🤝 Contributing

Contributions from the open source community are welcome and encouraged!

1. Fork the project
2. Create a branch (`git checkout -b feature/NewFeature`)
3. Commit your changes (`git commit -m 'Add NewFeature'`)
4. Push to the branch (`git push origin feature/NewFeature`)
5. Open a Pull Request

### Key Contribution Areas

* 🐛 Bug reports with test `.mbox` files
* 🌍 Translations
* ⚡ Performance improvements for large archives
* 🎨 UI/UX enhancements
* 📚 Documentation and tutorials

### Guidelines

* Keep the project as a **single HTML file** (no build step, no npm dependencies)
* No data must ever leave the browser — every change must respect this principle
* Test with real `.mbox` files of various sizes

---

## ✉️ Contact & support

* **Email**: [gianlucabevilacqua.93@gmail.com](mailto:gianlucabevilacqua.93@gmail.com)
* **GitHub Issues**: [Report a bug or suggest a feature](https://github.com/GianlucaBevilacqua93/gmail-takeout-viewer/issues)

---

**Made with ❤️ for the Italian school community and the Open Source community**

*If this tool was useful to you, leave a ⭐ — it helps others find it!*

## About

### License

GPL-2.0 license
