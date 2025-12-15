# 🧠 AI Brand Strategy e Piani Editoriali

**Video di Spiegazione Dettagliata:** [https://youtu.be/fYTBnUSdQkA](https://youtu.be/fYTBnUSdQkA)

Questo workflow di n8n utilizza **Google Gemini** per agire come un "Brand Strategist Senior" e automatizzare la creazione di asset fondamentali per una campagna di marketing:

1.  **Strategia di Brand:** Definizione del tono di voce (Brand Tone) e dell'argomento.
2.  **Piani Editoriali Multi-fase:** Generazione di un piano editoriale strutturato in tre fasi (Engagement, Hype, Pre-lancio), con obiettivi, canali e CTA specifici.
3.  **Content Creation:** Generazione di copy pubblicitari e suggerimenti per le immagini per ogni fase.

L'intero output è strutturato in formato JSON per garantire l'affidabilità e viene salvato in documenti Google Docs per la condivisione e l'editing.

---

## ⚙️ Architettura del Flusso

Il flusso è composto da tre macro-agenti AI distinti che lavorano in sequenza per costruire l'intera strategia.

### 1. Brand Strategy e Piano Editoriale (AI Agent 1)

* **`When clicking ‘Execute workflow’` (Manual Trigger):** Inizia il processo manualmente.
* **`Converti in stringa` (Code):** (Prepara i dati, se necessario, per l'agente).
* **`Google Gemini Chat Model` & `AI Agent1`:** Questo agente è il **"Brand Strategist"** e genera il cuore della strategia:
    * Definisce l'argomento della campagna.
    * Crea il Brand Tone e il Piano Editoriale suddiviso in Fase 1, 2 e 3.
    * Il **System Prompt** vincola l'output a essere **SOLO JSON** per l'affidabilità.
* **`Structured Output Parser`:** Verifica e normalizza la struttura JSON generata dall'Agente.

### 2. Generazione Copy Pubblicitari (AI Agent 2)

* **`Google Gemini Chat Model2` & `AI Agent2`:** Riceve il JSON del Piano Editoriale (fase 1) dal nodo precedente. Agisce da **"Copywriter"** e genera:
    * Due copy pubblicitari (Long/Short) per i contenuti della Fase 1.
    * Suggerimenti per le immagini o creatività associate.
* **`Create a document` (Google Docs):** Crea il documento finale della strategia (`Report Campagna Pubblicitaria`).
* **`Update a document1` (Google Docs):** Inserisce l'output dell'Agente 2 (Copywriter) all'interno del documento.

### 3. Generazione Contenuti Aggiuntivi (AI Agent 3 & 4)

Questi agenti generano contenuti specifici per le fasi successive del Piano Editoriale, garantendo la copertura completa della strategia in Google Docs:

* **`AI Agent3` & `Create/Update a document1/2`:** Si concentra sulla generazione e inserimento dei contenuti per la **Fase 2 (Mantenere l’Hype)** nel documento.
* **`AI Agent4` & `Create/Update a document2/3`:** Si concentra sulla generazione e inserimento dei contenuti per la **Fase 3 (Pre-lancio)** nel documento.

---

## 🔑 Credenziali Necessarie

Questo workflow richiede la configurazione delle seguenti credenziali in n8n per operare:

1.  **Google Gemini (PaLM) Api account** (per tutti i nodi Chat Model)
2.  **Google Docs account** (OAuth2)

---

