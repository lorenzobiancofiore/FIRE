# 🔥 FIRE Calculator Italia

> Calcolatore open-source per la pianificazione dell'indipendenza finanziaria — ottimizzato per il contesto fiscale e previdenziale italiano.

**Demo live:** apri `fire-calculator.html` direttamente nel browser. Nessun server, nessun backend, zero dati inviati da nessuna parte.

---

## ✨ Funzionalità

### 💸 Spese mensili & FIRE Number
- Tabella di spese personalizzabile con aggiunta/rimozione dinamica di voci
- Ogni voce supporta una **data di inizio** (spese future, es. acquisto auto) e una **data di fine** (spese temporanee, es. mutuo)
- Le spese temporanee vengono **escluse automaticamente** dal FIRE number; le spese future vengono **incluse**
- Selezione del moltiplicatore SWR: ×240 (5%), ×300 (4%), ×333 (3,6%), ×360 (3,3%), ×400 (3%)
- FIRE number calcolato su tre scenari in parallelo
- Grafico a ciambella della distribuzione delle spese

### 🏖️ Coast FIRE
- Calcolo del capitale minimo da investire oggi per raggiungere il FIRE number senza ulteriori versamenti
- Verifica immediata se si ha già raggiunto il Coast FIRE

### 📅 Anni al FIRE — portafoglio multi-asset
- Tabella di **asset multipli**, ciascuno con valore attuale, contributo mensile e rendimento annuo indipendente
- Simulazione mese per mese del portafoglio aggregato
- Stima dell'anno FIRE e del tasso di risparmio
- **Modulo pensione pubblica italiana**: inserisci la rendita stimata in euro odierni, l'anno di decorrenza (es. 2052) e il tasso di inflazione; il calcolatore rivaluta l'importo futuro e lo converte in capitale equivalente sottraendolo dal FIRE number target

### 🇮🇹 Correzione fiscale italiana
- Aliquota effettiva stimata che tiene conto della quota plusvalenze sul portafoglio
- Distinzione tra asset al 26% (ETF azionari/obbligazionari corporate) e al 12,5% (BTP e titoli di Stato europei)
- FIRE number lordo calcolato per tre scenari SWR

### 📈 Evoluzione del patrimonio
- Grafico multi-asset con area stackata per ogni voce
- Linee: totale portafoglio, contributi versati, FIRE target, offset pensione (attivato dall'anno di decorrenza)

### 🎲 Simulazione Monte Carlo
- 1.000 scenari con rendimenti casuali (distribuzione normale, metodo Box-Muller)
- Visualizzazione dei percentili P10 / P25 / P50 / P75 / P90
- Statistiche: probabilità di successo, anno medio di fallimento

### 💾 Snapshot — salva & ripristina
- Esportazione dell'intera configurazione in un file `.json` con etichetta personalizzata
- Importazione di uno snapshot precedente per ripristinare esattamente la situazione salvata
- Il file include spese, asset, parametri pensione, SWR e tutti i valori calcolati

### 📊 Storico & progressione
- Caricamento di più snapshot in un'unica sessione (anche drag & drop, anche multipli contemporaneamente)
- Grafico patrimonio reale vs piano teorico vs FIRE target
- Statistiche aggregate: patrimonio attuale, % FIRE raggiunto, crescita totale, crescita media mensile
- Tabella con delta tra snapshot e indicatore "In linea col piano" (tolleranza ±5%)

---

## 🚀 Come usarlo

```bash
git clone https://github.com/<tuo-username>/fire-calculator.git
cd fire-calculator
# apri fire-calculator.html nel browser — fine.
```

Non serve nessun `npm install`, nessun build step, nessun server locale.  
L'unica dipendenza esterna è **Chart.js 4.4.1** caricato da CDN (`cdnjs.cloudflare.com`).  
Il calcolatore funziona anche offline una volta che la pagina è stata caricata almeno una volta.

---

## 📁 Struttura del repository

```
fire-calculator/
├── fire-calculator.html   # Tutta l'applicazione in un singolo file (~87 KB)
└── README.md
```

Tutto — HTML, CSS, JavaScript — è contenuto in un unico file autosufficiente.

---

## 🧮 Metodologia

| Componente | Riferimento |
|---|---|
| Safe Withdrawal Rate 4% | Bengen (1994), Trinity Study (1998) |
| SWR 3% per l'Europa | Ricerca Morningstar Retirement |
| Simulazione Monte Carlo | Distribuzione normale log-rendimenti |
| Fiscalità ETF | Aliquota 26% su plusvalenza (art. 26-ter DPR 600/73) |
| Fiscalità BTP | Aliquota agevolata 12,5% (D.Lgs. 239/96) |
| Pensione pubblica | Rivalutazione con inflazione e capitalizzazione rendita |

> ⚠️ **Disclaimer**: questo strumento è a scopo educativo e informativo. Non costituisce consulenza finanziaria, fiscale o previdenziale. I calcoli si basano su ipotesi semplificative. Consulta un professionista abilitato per decisioni di investimento.

---

## 🔧 Personalizzazione

Il file è volutamente un singolo HTML non minificato — puoi aprirlo in qualsiasi editor e modificare:

- **Colori e tema**: variabili CSS in `:root` (es. `--accent: #f5a623`)
- **Asset di default**: array `assets` nello script
- **Spese di default**: array `spese` nello script
- **Valori default pensione**: campi `pensImporto` e `pensAnno`
- **Palette asset**: array `ASSET_COLORS`

---

## 📄 Licenza

MIT — libero di usare, modificare e ridistribuire con attribuzione.
