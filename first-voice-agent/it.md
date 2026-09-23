# Crea il tuo primo agente vocale dall’interfaccia

[Tutte le guide](../toc_it.md) · [English (US)](en.md) · [Español (España)](es.md) · **Italiano**

Un agente vocale Orbitali combina una voce, un ruolo, istruzioni e le informazioni necessarie per aiutare chi chiama. In questo tutorial preparerai un semplice agente per le domande frequenti dall’interfaccia web e scoprirai dove configurarlo e provarlo.

Ti serve l’accesso a un’organizzazione Orbitali e alla pagina **Agents** (Agenti). Per seguire la configurazione di un agente statico non servono codice o un numero di telefono. Il test vocale nel browser richiede un agente salvato e attivo e l’accesso al microfono.

**Informazioni sul percorso:** ci fermiamo prima di premere **Create agent** (Crea agente), poi esploriamo l’interfaccia usando l’agente esistente **FAQ English**. Non è stato creato alcun agente, non sono state modificate le impostazioni esistenti e non è stata avviata alcuna chiamata di prova. Le schermate mostrano l’interfaccia inglese acquisita il 23 settembre 2026; gli agenti e le opzioni della tua organizzazione potrebbero essere diversi. Manteniamo i nomi dei comandi in inglese per aiutarti a trovarli nelle immagini.

## 1. Scegli il tipo di agente

Apri **Agents** nella barra laterale e premi **New agent** (Nuovo agente). Seguiremo il percorso manuale; **Create with AI** è un punto di partenza alternativo.

![Finestra del nuovo agente con Static selezionato](images/01-agent-type.jpg)

La prima scelta riguarda il modo in cui l’agente riceve le istruzioni ed esegue azioni personalizzate:

| Tipo | Come funziona | Quando sceglierlo |
| --- | --- | --- |
| **Static** | Usa istruzioni salvate in Orbitali, senza strumenti HTTP o webhook personalizzati. | Un primo agente informativo o FAQ senza backend. |
| **HTTP Tooling** | Usa istruzioni salvate; ogni strumento personalizzato chiama il proprio endpoint HTTP. | Azioni collegate ad API separate. |
| **Webhook Tooling** | Invia le chiamate agli strumenti personalizzati a un unico endpoint e può ricevere istruzioni dinamiche. | Flussi controllati dal tuo backend. |

Scegli **Static**, poi **Next** (Avanti). Il tipo non può essere cambiato dopo la creazione: sceglilo in base alle azioni che prevedi di utilizzare. Gli agenti statici possono comunque usare funzionalità integrate, come la ricerca nella base di conoscenza quando i documenti sono pronti.

## 2. Parti da un modello

Seleziona **FAQ Concierge - English**, poi **Continue** (Continua).

![Selezione del modello FAQ Concierge - English](images/02-template.jpg)

Il modello precompila personalità, saluto e istruzioni. Puoi modificarli prima di salvare. **Blank** permette di partire da un prompt vuoto; gli altri modelli offrono una base per reception, assistenza clienti e vendite.

## 3. Controlla la configurazione non salvata

Nella scheda **Agent**, assegna un nome riconoscibile, per esempio `My first FAQ agent`. Lascia **Status** su **draft** (bozza) durante la preparazione. Per questo esempio scegli **English (US)** e seleziona una voce.

![Configurazione non salvata con il pulsante Create agent visibile](images/03-unsaved-agent.jpg)

| Impostazione | Cosa controlla |
| --- | --- |
| **Name** | Il nome che identifica l’agente nell’organizzazione. |
| **Status** | Lo stato: bozza, attivo o inattivo. Il test nel browser richiede lo stato attivo. |
| **Language** | La lingua e la variante regionale della conversazione. |
| **Voice** | Il profilo vocale, qui **Eve - Warm female**. |
| **AI identity disclosure** | La frase obbligatoria pronunciata da Orbitali prima del saluto per identificarsi come IA. |
| **Ambient sound** | Audio di sottofondo facoltativo riprodotto in loop durante la sessione. |
| **Tool-calling sound** | Audio facoltativo riprodotto durante l’esecuzione di uno strumento. |
| **Inbound numbers** | I numeri collegati all’agente per le chiamate in entrata. Puoi lasciarli scollegati per il primo test nel browser. |

La lingua della guida non determina quella dell’agente. Nell’interfaccia acquisita sono disponibili inglese degli Stati Uniti, spagnolo della Spagna e spagnolo degli Stati Uniti. Questa traduzione italiana non implica la disponibilità di un’opzione vocale in italiano: l’esempio resta configurato in inglese.

## 4. Assegna un compito chiaro

Apri **Instructions**. Il modello ha già compilato i campi principali.

![Identità e saluto del modello nell’editor non salvato](images/04-template-instructions.jpg)

Usa **Identity** per definire chi è l’agente, il suo ruolo e il tono. **Greeting** contiene il saluto iniziale. Più in basso, **Instructions** descrive cosa deve fare e quali regole deve seguire.

Per un primo agente FAQ, adatta questo esempio alla tua organizzazione. Manteniamo il testo in inglese per coerenza con **English (US)**:

**Identità**

```text
You are the friendly FAQ assistant for [organization].
Speak in clear American English. Keep answers brief and ask one question at a time.
```

**Saluto statico**

```text
Thanks for calling [organization]. What can I help you with today?
```

**Istruzioni**

```text
Answer questions about our services, hours, and policies using the knowledge base.
Search the knowledge base before answering factual questions.
If information is missing or unclear, say you do not have a confirmed answer.
Do not invent prices, opening hours, or commitments.
Do not promise a booking, transfer, or follow-up unless the required capability is configured.
Ask whether the answer helped before ending the conversation.
```

Queste istruzioni chiedono all’agente di consultare le fonti, ammettere quando manca una risposta e non promettere azioni non configurate. Sostituisci il segnaposto con il nome della tua organizzazione. Prepara anche il documento FAQ: le istruzioni definiscono il comportamento, mentre i documenti della base di conoscenza forniscono i fatti.

**Il percorso di creazione si ferma qui.** **Create agent** salverebbe il nuovo agente. Non lo premiamo e torniamo a **Agents**. Quando crei il tuo agente, salvarlo come bozza permette di caricare documenti e continuare la configurazione; le schermate successive usano invece un agente esistente.

## 5. Esplora un agente salvato: FAQ English

Apri **FAQ English** dall’elenco degli agenti.

![Configurazione e navigazione di FAQ English](images/05-faq-config.jpg)

Questo esempio è già **active**, usa **English (US)** e **Eve** e non ha numeri in entrata collegati. La scheda **Config** corrisponde ad **Agent** nell’editor di creazione.

FAQ English è un agente **Webhook Tooling**, a differenza dell’agente statico preparato prima. Ha quindi impostazioni aggiuntive per il backend, tra cui **Server URL**, più in basso nella pagina. Non servono per un semplice agente FAQ statico. Non copiare le impostazioni di integrazione di questo agente dimostrativo nella tua configurazione.

La navigazione superiore separa **Config**, **Instructions**, **Knowledge**, **Tools** e **Web chat**. **History** e **Logs** permettono di consultare l’attività.

### Istruzioni: personalità, saluto e comportamento

![Identità e saluto di FAQ English](images/06-faq-instructions.jpg)

L’identità di FAQ English descrive il suo ruolo di assistente del sito Orbitali. Il saluto apre la conversazione; le istruzioni più in basso spiegano come rispondere alle domande e usare gli strumenti configurati.

Per gli agenti webhook, le istruzioni possono essere **Static** o **Dynamic**. Quelle statiche sono salvate nell’editor; quelle dinamiche arrivano dal server all’inizio della chiamata. Un primo agente statico usa istruzioni salvate. **Outbound greeting** riguarda le chiamate in uscita; se è vuoto, viene usato il saluto statico.

### Conoscenze: fornisci informazioni affidabili

![Modulo di caricamento e documento FAQ pronto](images/07-faq-knowledge.jpg)

La scheda **Knowledge** accetta file TXT, Markdown e PDF. FAQ English contiene un documento **Orbitali FAQ** contrassegnato come **ready** (pronto). I *chunk* sono le sezioni più piccole create durante l’indicizzazione per recuperare le informazioni pertinenti.

Nel tuo agente salvato, inserisci il nome del documento e una descrizione di quando usarlo, scegli il file e attendi l’elaborazione. Poi controlla e salva i dettagli. Verifica che lo stato sia **ready** prima di usarlo in un test. Il caricamento dei documenti è disponibile solo dopo aver salvato l’agente.

Inizia con un solo documento mirato, contenente servizi, orari, politiche e risposte approvate. Chiedi all’agente di consultarlo e di riconoscere quando mancano informazioni.

### Strumenti: scopri cosa può fare l’agente

![Strumenti integrati e strumenti MCP collegati](images/08-faq-tools.jpg)

Gli strumenti integrati spiegano le funzionalità principali:

- **hang_up** termina la chiamata correttamente ed è sempre disponibile.
- **transfer_call** richiede un numero di trasferimento configurato.
- **search_knowledge** richiede documenti pronti nella base di conoscenza.

**MCP Tools** elenca gli strumenti dei server MCP collegati. Le caselle selezionate indicano quelli abilitati per questo agente. Connessioni e strumenti disponibili dipendono dall’organizzazione.

![Strumenti webhook per disponibilità, prenotazioni e notifiche dei contatti interessati](images/08b-faq-webhook-tools.jpg)

FAQ English dispone anche di strumenti webhook personalizzati: **check_availability**, **create_booking** e **send_slack_lead**. Sono esempi di azioni collegate: scrivere i loro nomi in un prompt non aggiunge queste funzionalità. Un primo agente statico non ne ha bisogno. La configurazione delle integrazioni backend esula da questo tutorial.

## 6. Prova l’agente nel browser quando è pronto

Su un agente salvato e attivo, apri **Config → Test agent**.

![Finestra del test vocale prima di avviare la sessione](images/09-test-agent.jpg)

Per provare il tuo agente:

1. Salva le modifiche sia alla configurazione sia alle istruzioni e imposta l’agente su **active**. Modifiche non salvate o uno stato diverso da attivo disabilitano il test nel browser.
2. Premi **Test agent**, poi **Start test**.
3. Consenti l’accesso al microfono, se richiesto, e parla. La trascrizione compare nella finestra.
4. Fai una domanda coperta dal documento FAQ e una a cui il documento non risponde. Verifica che l’agente usi le fonti e ammetta ciò che non sa.
5. Controlla la dichiarazione di identità IA, il saluto, la voce e il ritmo. Termina con **Stop test**.

La nostra schermata si ferma prima di **Start test**. **Test call**, nella sezione delle istruzioni, è un test telefonico in uscita distinto dal test con il microfono del browser.

## 7. Controlla il risultato e scegli un canale

Usa **History** per consultare l’attività delle chiamate e della chat web e **Logs** per esaminare gli eventi di esecuzione. Dopo i test, migliora le istruzioni poco chiare o le informazioni mancanti e ripeti le stesse domande.

Per ricevere chiamate telefoniche, collega il tuo operatore e associa un numero adatto tramite **Inbound numbers → Link number**. Per un sito, **Web chat** offre le impostazioni del pulsante di apertura e un codice da incorporare, in base al piano. Nessuna delle due opzioni è necessaria per seguire il flusso di creazione o provare nel browser un agente salvato e attivo.

Prima di proseguire, verifica che l’agente abbia un ruolo chiaro, una voce e un saluto adatti, documenti pronti e risposte ragionevoli sia alle domande note sia a quelle senza risposta nelle fonti.
