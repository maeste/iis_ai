# L'Arte del Prompt Engineering

## Introduzione

Benvenuti a questa lezione sul **Prompt Engineering**, l'arte e la scienza di comunicare efficacemente con i modelli di intelligenza artificiale generativa. Dopo aver esplorato come funzionano i Large Language Models (LLM), ora ci concentreremo su come formulare i nostri input ("prompt") per ottenere risultati migliori.

Il prompt engineering è diventato una competenza fondamentale nell'era dell'IA generativa. È come imparare un nuovo linguaggio di comunicazione: non con altre persone, ma con sistemi di intelligenza artificiale avanzati.

In questo notebook:
1. Scopriremo cos'è il prompt engineering e perché è importante
2. Esploreremo le tecniche fondamentali per creare prompt efficaci
3. Vedremo esempi pratici di come lo stesso modello può dare risposte completamente diverse in base al prompt
4. Sperimenteremo con l'interfaccia web di Hugging Face Playground
5. Analizzeremo alcuni prompt "wow effect" che mostrano le capacità avanzate dei modelli più recenti

## 1. Cos'è il Prompt Engineering?

Il **Prompt Engineering** è l'arte di formulare istruzioni, domande o input ("prompt") per un modello di intelligenza artificiale in modo da ottenere il miglior risultato possibile. È simile a imparare come porre domande precise a un esperto per ottenere le informazioni di cui abbiamo bisogno.

### Perché è importante?

I modelli linguistici come GPT, Claude, LLaMA o BLOOM sono potenti ma "letterali": rispondono esattamente a ciò che viene chiesto loro, nel modo in cui viene chiesto. Un prompt ben progettato può fare la differenza tra:
- Una risposta generica e poco utile
- Una risposta dettagliata, accurata e personalizzata alle nostre esigenze

### Il concetto di "modello mentale"

Per fare prompt engineering efficace, è utile avere un modello mentale di come funziona un LLM:
- L'IA non "sa" davvero cose come noi
- Ha appreso pattern statistici da enormi quantità di testo
- Cerca di continuare il testo in modo coerente con ciò che ha visto durante l'addestramento
- Il prompt è come l'inizio di una storia che l'IA cerca di completare in modo plausibile

## 2. Principi Fondamentali del Prompt Engineering

Prima di vedere esempi specifici, esploriamo i principi generali che rendono efficace un prompt:

### Chiarezza e specificità

- **Sii specifico**: Più il prompt è dettagliato, più la risposta sarà mirata.
- **Una richiesta per prompt**: Evita di chiedere più cose contemporaneamente.
- **Usa un linguaggio preciso**: Evita termini ambigui o vaghi.

### Struttura e contesto

- **Fornisci contesto**: I modelli non conoscono il contesto a meno che non lo specifichi.
- **Usa formati strutturati**: Elenchi, passaggi numerati o tag XML possono guidare la risposta.
- **Definisci il formato di output**: Specifica come vuoi che la risposta sia strutturata.

### Guidare il comportamento del modello

- **Definisci un "ruolo"**: Ad esempio, "Agisci come un professore di fisica" o "Sei un poeta del '900".
- **Specifica lo stile**: Formale, informale, tecnico, semplice, etc.
- **Indica il pubblico**: "Spiegalo come lo faresti a un bambino di 5 anni" o "Parlami come a uno specialista del settore".

### Tecniche avanzate

- **Few-shot learning**: Fornisci esempi di ciò che vuoi prima di fare la richiesta principale.
- **Chain of Thought**: Chiedi al modello di "pensare passo dopo passo" per problemi complessi.
- **Priming**: Influenza il tono o lo stile della risposta con l'inizio del prompt.

## 3. Esperimenti di Prompt Engineering con Hugging Face Playground

Vediamo come lo stesso modello può generare risposte completamente diverse in base a come formuliamo il prompt. Per questi esperimenti, utilizzeremo l'interfaccia web di Hugging Face Playground.

### Come accedere a Hugging Face Playground

1. Vai al sito: https://huggingface.co/playground
2. Se non hai già un account, registrati (è gratuito)
3. Una volta loggato, sarai nella pagina principale del Playground

### Esperimento 1: Livello di specificità

#### Istruzioni:

1. Accedi a Hugging Face Playground
2. Seleziona un modello di testo nella categoria LLM (ad esempio "dolly-v2-3b" o un altro modello disponibile)
3. Nella sezione "Parameters", imposta:
   - **Max length/tokens**: 250
   - **Temperature**: 0.7 (valore predefinito)
4. Prova i seguenti prompt uno alla volta:

**Prompt generico:**
```
Parla del cambiamento climatico.
```

**Prompt specifico:**
```
Fornisci una spiegazione di 150 parole sulle tre principali cause del cambiamento climatico, 
concentrandoti sui dati scientifici più recenti e includendo le percentuali di contribuzione di ciascuna causa.
Organizza la risposta in paragrafi chiari con un'introduzione e una conclusione.
```

5. Confronta i risultati ottenuti e nota come il prompt specifico genera una risposta più strutturata e informativa

### Esperimento 2: Definire un ruolo e un tono

#### Istruzioni:

1. Nel Playground, mantieni lo stesso modello
2. Prova i seguenti prompt uno alla volta:

**Prompt base:**
```
Spiega cos'è la fotosintesi.
```

**Prompt con ruolo di uno scienziato:**
```
Sei un biologo molecolare esperto. 
Spiega in modo dettagliato e tecnico il processo della fotosintesi, 
includendo le reazioni chimiche coinvolte e i meccanismi cellulari.
```

**Prompt per spiegare a un bambino:**
```
Sei un insegnante di scuola primaria molto paziente e creativo.
Spiega cos'è la fotosintesi a un bambino di 7 anni, usando metafore semplici e un linguaggio adatto ai bambini.
Evita termini tecnici e rendi la spiegazione divertente e coinvolgente.
```

3. Confronta le tre risposte e nota come il tono, il livello di dettaglio e il linguaggio cambiano in base al ruolo assegnato

### Esperimento 3: Few-shot learning (apprendimento con pochi esempi)

#### Istruzioni:

1. Nel Playground, mantieni lo stesso modello
2. Prova i seguenti prompt uno alla volta:

**Prompt senza esempi (zero-shot):**
```
Classifica la seguente recensione di un ristorante come positiva o negativa: 'Il cibo era buono ma il servizio era lento.'
```

**Prompt con esempi (few-shot):**
```
Classifica le seguenti recensioni di ristoranti come positive, negative o neutre.

Recensione: "La pizza era deliziosa e il personale molto cordiale."
Classificazione: Positiva

Recensione: "Ho aspettato 40 minuti e quando è arrivato il cibo era freddo."
Classificazione: Negativa

Recensione: "Il locale è carino ma i prezzi sono un po' alti per quello che offrono."
Classificazione: Neutra

Recensione: "Il cibo era buono ma il servizio era lento."
Classificazione:
```

3. Confronta i risultati e nota come fornire esempi può guidare il modello verso il formato di risposta desiderato

### Esperimento 4: Chain of Thought (Catena di pensiero)

#### Istruzioni:

1. Nel Playground, mantieni lo stesso modello
2. Aumenta il valore di "Max length/tokens" a 300
3. Prova i seguenti prompt uno alla volta:

**Prompt standard per un problema matematico:**
```
Risolvi il seguente problema: 
In una classe ci sono 25 studenti. Il 60% sono ragazze. Quante ragazze e quanti ragazzi ci sono?
```

**Prompt con chain of thought:**
```
Risolvi il seguente problema, ragionando passo dopo passo per arrivare alla soluzione:
In una classe ci sono 25 studenti. Il 60% sono ragazze. Quante ragazze e quanti ragazzi ci sono?
```

4. Confronta i risultati e nota come il secondo prompt incoraggia il modello a mostrare il suo ragionamento, producendo una soluzione più dettagliata e (potenzialmente) più accurata

### Esperimento 5: Formattazione e struttura dell'output

#### Istruzioni:

1. Nel Playground, mantieni lo stesso modello
2. Aumenta il valore di "Max length/tokens" a 350
3. Prova i seguenti prompt uno alla volta:

**Prompt base:**
```
Elenca 5 paesi europei con le loro capitali.
```

**Prompt con formato specifico:**
```
Elenca 5 paesi europei con le loro capitali in questo formato JSON specifico:
[
  {
    "paese": "nome del paese",
    "capitale": "nome della capitale",
    "popolazione": "popolazione in milioni",
    "lingua": "lingua principale"
  }
]

Assicurati che l'output sia un JSON valido e che contenga esattamente 5 paesi.
```

4. Confronta i risultati e nota come specificare il formato desiderato può portare a risposte strutturate e facilmente utilizzabili

## 4. Tecniche avanzate di Prompt Engineering

Ora esploriamo alcune tecniche più avanzate che possono migliorare ulteriormente le risposte dei modelli AI.

### 4.1 Prompt di sistema vs. prompt utente

Molti modelli moderni supportano il concetto di "prompt di sistema" e "prompt utente":
- **Prompt di sistema**: Istruzioni generali su come il modello dovrebbe comportarsi
- **Prompt utente**: La richiesta specifica dell'utente

#### Istruzioni:

1. Nel Playground, seleziona un modello che supporti questa funzionalità (come "dolly-v2-3b")
2. Imposta "Max length/tokens" a 350
3. Usa il seguente prompt che simula la distinzione sistema/utente:

```
[SYSTEM] Sei un assistente esperto di cybersecurity. Fornisci risposte accurate, tecniche ma comprensibili. 
Concentrati sulla sicurezza pratica e sulle migliori pratiche attuali. Non fornire informazioni che potrebbero essere utilizzate per attività dannose.

[USER] Come posso proteggere il mio account online da attacchi di phishing?
```

4. Osserva come il modello assume il ruolo definito nel prompt di sistema e risponde alla domanda specifica dell'utente

### 4.2 Persona e roleplay

Definire una "persona" specifica può produrre risposte con uno stile e un tono distintivi.

#### Istruzioni:

1. Nel Playground, mantieni lo stesso modello
2. Usa il seguente prompt:

```
Tu sei Leonardo da Vinci, il famoso artista e inventore del Rinascimento italiano. 
Parli con uno stile eloquente e filosofico, facendo riferimento alle tue opere e alle tue invenzioni. 
Ti interessa profondamente l'arte, la scienza, l'anatomia e l'ingegneria. 
Rispondi alla seguente domanda mantenendo questo personaggio:

Cosa pensi delle tecnologie moderne come gli smartphone e Internet?
```

3. Osserva come il modello adotta lo stile e la prospettiva del personaggio assegnato

### 4.3 Generazione incrementale e iterativa

Per compiti complessi, può essere utile suddividere il lavoro in passaggi progressivi.

#### Istruzioni:

1. Nel Playground, mantieni lo stesso modello
2. Inizia con la prima iterazione:

```
Fai un brainstorming di 5 possibili temi per un racconto breve ambientato in un futuro distopico.
Per ogni tema, fornisci solo un titolo e una breve descrizione di 1-2 frasi.
```

3. Dopo aver ottenuto la risposta, scegli uno dei temi generati (ad esempio "La Memoria Digitale")
4. Procedi con la seconda iterazione usando il tema scelto:

```
Hai proposto il tema "La Memoria Digitale" per un racconto distopico.
Ora, sviluppa 3 possibili personaggi principali per questa storia.
Per ogni personaggio, fornisci:
1. Nome e età
2. Ruolo nella società
3. Motivazione principale
4. Un conflitto interiore
```

5. Osserva come questo approccio incrementale ti permette di approfondire progressivamente la creazione

## 5. Consigli pratici per utilizzare Hugging Face Playground

### Selezione del modello

1. Nel Playground, esplora i diversi modelli disponibili
2. Per questi esperimenti, puoi utilizzare:
   - **dolly-v2-3b**: Un modello di Databricks ottimizzato per seguire istruzioni
   - **gpt2**: Un modello più semplice ma versatile
   - **bloom** o **bloom-560m**: Modelli multilingue di BigScience
   - **opt-1.3b**: Un modello di Meta AI

### Parametri importanti

1. **Max length/tokens**: Controlla la lunghezza massima della risposta
   - Per risposte brevi: 100-150
   - Per risposte medie: 200-300
   - Per risposte lunghe: 350+

2. **Temperature**: Controlla la casualità/creatività della risposta
   - Valori bassi (0.1-0.3): Risposte più deterministiche e "sicure"
   - Valori medi (0.5-0.7): Un buon equilibrio tra determinismo e creatività
   - Valori alti (0.8-1.0): Risposte più creative e variabili

3. **Top-k** e **Top-p**: Parametri avanzati che controllano la diversità del testo generato
   - Prova a modificarli se vuoi esplorare risposte alternative

### Consigli per sperimentare

1. Inizia con un prompt semplice e perfezionalo gradualmente
2. Confronta lo stesso prompt con modelli diversi
3. Modifica un parametro alla volta per capire il suo effetto
4. Salva i prompt più efficaci per riutilizzarli

## 6. Prompt "Wow Effect" per Claude

Ecco tre prompt particolarmente impressionanti progettati per Claude, che mostrano le capacità avanzate di questo modello. Questi prompt generano risultati sorprendenti e dimostrano il potenziale dei modelli AI più avanzati quando vengono interrogati con prompt ben costruiti.

### Prompt 1: Analisi letteraria creativa

```
Sei un critico letterario con una profonda conoscenza della letteratura mondiale. Ti chiedo di analizzare questo breve estratto che ho inventato come se fosse l'incipit di un romanzo importante:

"Le ombre si allungavano sul pavimento di marmo mentre il vecchio orologio batteva le sei. Maria chiuse il libro polveroso e guardò fuori dalla finestra: la nebbia avvolgeva gli alberi del giardino come un sudario, nascondendo i segreti che presto sarebbero venuti alla luce."

Per la tua analisi:
1. Identifica lo stile e il possibile genere letterario
2. Analizza le tecniche narrative e gli elementi simbolici presenti
3. Suggerisci 3 possibili direzioni in cui la trama potrebbe svilupparsi
4. Confronta lo stile con quello di 2 autori famosi che potrebbero aver scritto un incipit simile
5. Crea un breve paragrafo che potrebbe seguire questo incipit, mantenendo lo stesso stile e tono

Sii dettagliato, profondo e creativo nella tua analisi, come faresti recensendo un'opera letteraria significativa.
```

### Prompt 2: Simulazione di dialogo multidisciplinare

```
Immagina una tavola rotonda con Albert Einstein, Leonardo da Vinci e Ada Lovelace che discutono di come l'intelligenza artificiale avrebbe potuto influenzare il loro campo di studi. 

Crea un dialogo realistico tra questi tre geni, mantenendo fedelmente:
- Il loro stile di espressione e personalità storiche
- Le conoscenze e le scoperte che hanno fatto nel loro campo
- La loro reazione alle moderne tecnologie e all'IA

Immagina come potrebbero interagire, discutere e confrontare le loro idee in un dialogo stimolante e illuminante. 

Sii creativo e realistico nel tuo dialogo, tenendo conto delle conoscenze e delle personalità di questi tre grandi personaggi della storia.
```

### Prompt 3: Progettazione di un esperimento scientifico

```
Sei un ricercatore di fama mondiale nel campo della fisica quantistica. Hai appena ricevuto un finanziamento illimitato per progettare e condurre un esperimento rivoluzionario che potrebbe cambiare il nostro modo di comprendere l'universo. 

Descrivi in dettaglio il tuo esperimento, includendo:
- L'obiettivo principale e le domande di ricerca
- I metodi e le tecnologie innovative che utilizzerai
- Le ipotesi e le previsioni che vuoi testare
- I possibili risultati e le implicazioni per la scienza

Sii creativo, ambizioso e rigoroso nella progettazione del tuo esperimento, come se dovessi presentarlo a una conferenza scientifica di alto livello.
```

## 7. Conclusioni e risorse aggiuntive

Il prompt engineering è una competenza che si affina con la pratica. Sperimentare con diversi prompt, modelli e parametri ti aiuterà a sviluppare un'intuizione su come ottenere i risultati desiderati.

### Suggerimenti finali:

1. **Documentazione**: Tieni traccia dei prompt che funzionano bene
2. **Iterazione**: Raffinare i prompt in base ai risultati ottenuti
3. **Contesto**: Fornire sempre contesto sufficiente
4. **Specificità**: Essere il più specifici possibile sui requisiti
5. **Esempi**: Utilizzare esempi quando appropriato

### Risorse utili:

- [Hugging Face Playground](https://huggingface.co/playground)
- [Prompt Engineering Guide](https://www.promptingguide.ai/)
- [Hugging Face Documentation](https://huggingface.co/docs)
- [Anthropic Claude Documentation](https://docs.anthropic.com/claude/docs)

Ricorda che ogni modello ha caratteristiche diverse, e ciò che funziona con un modello potrebbe non funzionare allo stesso modo con un altro. Sperimenta e divertiti!
