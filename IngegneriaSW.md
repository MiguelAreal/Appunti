# Ingegneria Del Software

# UML

Vogliamo creare un modello del software che va sviluppato. È uno standard indipendente da metodi, tecnologie, produttori. Possiede una notazione standard ma non è un linguaggio. Si basa principalmente su casi d'uso, è iterativo e incrementale. Esistono più di 30 diagrammi, ognuno si adatta ad un ambito specifico.


### Casi d'uso

Rappresenta come vogliamo usare un sistema. Si rappresentano requisiti, azioni e attori. Un caso d'uso può soddisfare più requisiti e un requisito può generare più casi d'uso.



* **Caso d’uso:** rappresenta una specifica interazione tra un attore e il sistema. In UML viene rappresentato da una ellissi etichettata con il nome del caso d’uso.
* **Attore**: rappresenta un ruolo che caratterizza le interazioni tra utente e sistema. Non è necessariamente una persona. Iin UML viene rappresentato da un omino stilizzato. Possono essere definite delle gerarchie di attori e associare uno o più attori a un attore specializzato.
* **Scenario**: sequenza di azioni che definisce una particolare interazione tra attore e sistema.
* **Descrizione**: testo che descrive lo scenario, l’ordine temporale delle azioni, l’eventuale gestione degli errori, gli attori coinvolti.

**Documentazione**



* **Nome** caso d’uso: ogni use case deve avere un nome. Il nome esprime il goal dell’utente. 
* **Goal**: descrizione sommaria della funzionalità fornita, deve soddisfare una necessità dell’utente cioè è percepita dall’utente come “valore”.
* **Attori**: persona, dispositivo o altro, esterno al sistema che interagisce col sistema. In ogni use case ci deve essere un attore primario, ovvero chi inizia il caso d’uso stesso.
* **Pre-condizioni**: condizioni che devono essere soddisfatte all’inizio del caso d’uso, garanzie fornite dagli attori al sistema che devono essere soddisfatte per poter arrivare lo scenario in questione.
* **Trigger**: evento che attiva il caso d’uso.
* **Descrizione**: descrizione della sequenza di interazioni più comune tra gli attori e il sistema. In particolare la sequenza che porta alla conclusione con successo. Comprende: input forniti dall’attore e risposta del sistema. Il sistema viene trattato come una black-box, importa la risposta all’input, non come viene generata la risposta
* **Alternative** (estensioni): variazione della sequenza dello scenario principale (es. gestione eccezioni).
* **Post-condizioni** - condizioni sempre soddisfatte alla fine del caso d’uso (garanzie fornite dal sistema agli attori).

**Relazioni**



* **Inclusione**: un caso d'uso chiama un altro caso d'uso, utile per scomporre un caso complesso in componenti più semplici e per riutilizzare alcune componenti. Si rappresenta con "&lt;<include>>" e una freccia che parte dal caso chiamante.
    * Es: prelevare e visualizzare saldo includono identificarsi al bancomat.
* **Generalizzazione**: lega un caso generico a casi più particolari. Simile ad ereditarietà tra classi. Si rappresenta con freccia da caso specifico a caso generale.
    * Es: Effettua ordine è un caso generale che si può specializzare in ordina libro, ordina dv, ordina occhiali.
* **Estensione**: continua il comportamento del caso d'uso di base inserendo delle azioni alternative da un certo punto in poi. Simile a gestione delle eccezioni. SI rappresenta con freccia tratteggiata dal caso particolare al caso di partenza e la parola &lt;<extend>.
    * Es: effettua un ordine. Se il cliente non è registrato lo aggiunge. "Aggiungi cliente" extends "effettua ordine".


### Diagramma delle Classi

Rappresenta le classi di oggetti, i loro attributi e i metodi. Mostra la relazione tra le classi.

**Rappresentazione**:



* **Nome: **inizia con la lettera maiuscola, non è sottolineato e non contiene underscore.
* **Attributi**: proprietà i cui valori identificano un oggetto istanza della classe e ne costituiscono lo stato. Iniziano con una lettera minuscola.
* **Operazioni**: proprietà i cui valori identificano un oggetto istanza della classe e ne costituiscono lo stato. Iniziano con una lettera minuscola.

**Relazioni:**



* **Associazione**: linea tra una classe e l'altra. Indica che una classe contiene una variabile che è in realtà un oggetto rappresentato da un'altra classe. Può avere molteplicità (0, 1, N)
* **Aggregazione**: è un tipo particolare di associazione. Esprime il concetto “è parte di” (part of), che si ha quando un insieme è relazionato con le sue parti. Si rappresenta con un diamante vuoto dalla parte della classe che è il contenitore.
* **Composizione**: è un caso particolare dell’aggregazione, la parte componente non può esistere da sola senza la classe composto. Si rappresenta con un diamante pieno dalla parte della classe che è il contenitore.
* **Ereditarietà:** freccia che va dalle sottoclassi alla superclasse. 

Davanti ad attributi e metodi si inserisce - se sono privati e + se sono pubblici.


### Diagramma di sequenza

Si usa per definire la logica di uno scenario (specifica sequenza di eventi) di un caso d’uso. È uno dei principali input per l’implementazione dello scenario. Mostra gli oggetti coinvolti specificando la sequenza temporale dei messaggi che gli oggetti si scambiano. È un diagramma di interazione: evidenzia come un caso d’uso è realizzato tramite la collaborazione di un insieme di oggetti. E’ un diagramma che descrive interazioni tra oggetti che collaborano per svolgere un compito. Gli oggetti collaborano scambiandosi messaggi. Lo scambio di un messaggio in programmazione ad oggetti equivale all’invocazione di un metodo. La chiamata è rappresentata come una freccia dal chiamante al chiamato. La freccia è etichettata con il nome del metodo invocato, i parametri e il valore di ritorno.

L’esecuzione di un metodo può dipendere da una condizione: il metodo viene invocato solo se la condizione risulta vera a run-time. Si disegna aggiungendo la condizione, racchiusa tra parentesi quadre, che definisce quando viene eseguito il metodo.

L’esecuzione ciclica di messaggi si rappresenta aggiungendo un * (asterisco) prima del metodo su cui si vuole iterare. Si può aggiungere la condizione che definisce l’iterazione tra parentesi quadre.

L’esecuzione ciclica di più messaggi si disegna raggruppando con un riquadro (blocco, box) i messaggi (metodi) su cui si vuole iterare. Si può aggiungere la condizione che definisce l’iterazione sull’angolo in alto a sinistra del blocco e si rappresenta al solito tra parentesi quadre.

Auto-chiamata: si rappresenta con una “freccia circolare” che rimane all’interno del life time di uno stesso metodo.

Creazione di un nuovo oggetto non presente nel sistema fino a quel momento: messaggio etichettato new, create.

Distruzione di un oggetto presente nel sistema fino a quel momento: si rappresenta con un X posta in corrispondenza della life-line dell’oggetto. Da quel momento in avanti non è legale invocare alcun metodo dell’oggetto distrutto.


### Diagramma di collaborazione

È un diagramma di interazione: rappresenta un insieme di oggetti che collaborano per realizzare il comportamento di uno scenario di un caso d’uso. A differenza del diagramma di sequenza, mostra i legami (link) tra gli oggetti che si scambiano messaggi, mentre la sequenza di tali messaggi è meno evidente.


### Diagramma di transizioni di stato

Serve a modellare il ciclo di vita degli oggetti di una singola classe. Mostra gli eventi che causano la transizione da uno stato a un altro e le azioni eseguite in seguito a un determinato evento. Quando un oggetto si trova in un certo stato può essere interessato ad alcuni eventi e non ad altri. Va utilizzato solo per le classi che presentano un ciclo di vita complesso e segnato da una successione ben definita di eventi.

Il ciclo di vita è descritto in termini di



* Eventi (equivale a un messaggio in un diagramma di sequenza)
* Stati (insieme di valori degli attributi). Si differenziano stato iniziale e stato finale.
* Transizioni di stato

Lo stato è rappresentato come un rettangolo con i bordi arrotondati con un certo nome.

Un evento si può rappresentare graficamente con una freccia (transizione) etichettata con il nome del metodo o della condizione associata all’evento.

Tipi di eventi:



* Invocazione sincrona di un metodo.
* Ricezione di una chiamata asincrona (“signal”).
* Una condizione predefinita che diventa vera.
* La fine di un “periodo di tempo”.


### Diagramma di attività

Rappresenta sistemi di workflow, oppure la logica interna di un processo (processo di business o processo di dettagli), di un caso d’uso o di una specifica operazione di una classe. Permette di modellare processi paralleli e la loro sincronizzazione, è un caso particolare di diagrammi di stato, in cui ogni stato è uno stato di attività. Un diagramma di attività mostra il flusso di azioni relativo ad un’attività, ovvero una esecuzione non atomica di operazioni all’interno di una macchina a stati. L’esecuzione di un’attività viene decomposta in azioni atomiche e ogni azione può o meno cambiare lo stato del sistema. I diagrammi di attività sono spesso usati per descrivere la logica di un algoritmo (sono l’equivalente UML dei diagrammi di flusso). Graficamente un diagramma di attività è un insieme di archi e nodi.

Un branch è rappresentato da un diamante, ha un flusso entrante, due o più flussi uscenti. Una condizione logica (talvolta implicita) che determina quale dei flussi uscenti verrà eseguito da una particolare esecuzione. Quando due flussi si riuniscono, è possibile usare ancora il simbolo di diamante: in questo caso viene detto merge. Ogni merge ha almeno due flussi entranti e un flusso uscente.

Un join rappresenta la sincronizzazione di due o più flussi di controllo concorrenti. Un join ha due o più flussi entranti e un flusso uscente. La sincronizzazione sul join attende che tutte le attività nei flussi entranti abbiano terminato la loro esecuzione prima di procedere. Fork e Join si rappresentano con una barra orizzontale.


### Diagramma dei componenti

Evidenzia l’organizzazione e le dipendenze tra i componenti software. I componenti (come i casi d’uso o le classi) possono essere raggruppati in package. Un componente è una qualunque porzione fisica riutilizzabile con un’identità e un’interfaccia (dichiarazione dei servizi offerti) ben definite. Un componente può essere costituito dall’aggregazione di altri

componenti.


### Diagramma di distribuzione

Serve per mostrare come sono configurate e allocate le unità hardware e software per un’applicazione, evidenzia la configurazione dei nodi elaborativi in ambiente di esecuzione (run-time) e dei componenti, processi ed oggetti allocati su questi nodi.


# Design Pattern

Pattern: soluzione progettuale assodata (ossia convalidata dal suo utilizzo con successo in più di un progetto) per un problema ricorrente in un determinato contesto. Permettono riuso dell’esperienza di progettazione (propria o altrui), conducono a sistemi più contenibili, aumentano la produttività, aiutano a documentare l’architettura, descrivono astrazioni software. L’approccio utilizzato è descritto in modo indipendente dal linguaggio e dall’architettura. Si implementa secondo le nostre decisioni progettuali. 

Librerie e framework non sono design pattern, sono codice già scritto sulla base di alcuni pattern.

Elementi:



* Nome: identificato in modo univoco per favorire la comunicazione.
* Problema affrontato: descrizione del contesto in cui è possibile applicare il Pattern.
* Soluzione: per la progettazione OO è espressa in termini di classi, responsabilità e collaborazioni.
* Conseguenze: risultati dell’applicazione del pattern (pro e contro), da valutare nella scelta tra più alternative.
* Struttura: diagramma UML

Classificazione:



* Purpose: campo di applicazione del pattern
    * Strutturali: si concentrano sul come classi e oggetti sono combinati per formare strutture più grandi. Pattern strutturali di classi, usano ereditarietà per comporre interfacce o implementazioni, pattern strutturali di oggetti descrivono modi ci comporre oggetti per realizzare nuove funzionalità.
    * Comportamentali: pattern che identificano metodi di comunicazione comuni tra oggetti e li realizzano. Aumentano la flessibilità implementando la comunicazione, sono legati all’interazione e alla responsabilità.
    * Creazione: astraggono il processo di istanziazione (creazione), aiutano a rendere il sistema indipendente da come gli oggetti sono creati, composti e rappresentati (riduce accoppiamento e aumenta flessibilità). Nascondono (information hiding) la conoscenza di quali sono le classi concrete effettivamente istanziate e nascondono dettagli sulla creazione e sulla composizione degli oggetti (p.e. parametri usati al momento della creazione).
* Scope: indica se il pattern specifica relazioni tra classi oppure tra oggetti.


### Singleton

**Problema**: talvolta è necessario garantire che una classe abbia una unica istanza, accessibile attraverso un unico punto di accesso.

**Soluzione**: si rende il costruttore della classe privato, in modo che non sia possibile creare direttamente istanze (al di fuori del codice della classe). Si fornisce un metodo “static” per ottenere l’unica istanza, che viene conservata in un campo statico privato della classe.

**Conseguenze**: accesso controllato all’unica istanza. Non occorre usare variabili globali per accedere all’unica istanza.


### Factory

**Problema**: una classe ha bisogno di creare un oggetto (“prodotto”) che implementa un'interfaccia, ma vuole evitare che dipenda da una specifica implementazione concreta tra quelle disponibili. Oppure, una classe vuole delegare alle sottoclassi la creazione di determinati oggetti.

**Soluzione**: si incapsula la creazione degli oggetti in un metodo.


### Abstract Factory

**Problema**: una classe ha bisogno di creare una serie di oggetti (prodotti) che implementano delle interfacce correlate, ma si vuole evitare che dipenda da una specifica implementazione concreta tra quelle disponibili. Il sistema deve essere configurato con famiglie multiple di prodotti, dove una famiglia è progettata per essere usata nel suo insieme. Si vuole distribuire una libreria di prodotti rivelando solo le interfacce e non le classi concrete che le implementano.

**Soluzione**: si definisce una interfaccia Abstract Factory con metodi per creare diversi prodotti, e una o più classi concrete che implementano questa interfaccia in riferimento a una singola famiglia di prodotti. A run-time si costruisce un’istanza di una “concrete factory” che viene usata per creare i prodotti.

**Conseguenze**: nasconde le classi concrete; solo la factory sa quale classe concreta viene istanziata. Consente di sostituire facilmente una famiglia di prodotti con un’altra e garantisce che i prodotti usati insieme siano della stessa famiglia.



* Factory: si basa su ereditarietà, la creazione è delegata alla sottoclasse che implementa il factory method per creare gli oggetti. Lo scopo è permettere a una classe di rimandare di istanziare alle sue sottoclassi.
* Abstract Factory: si basa su composizione, la creazione è implementata in metodi esposti nella factory interface. Lo scopo è creare famiglie di oggetti correlati senza dover dipendere dalle loro classi concrete.


### Adapter

**Problema**: 

Occorre utilizzare una classe già disponibile (Adaptée) insieme a una libreria di classi sviluppata in modo indipendente. La libreria richiede una particolare interfaccia (Target) che non è presente nelle Adaptée.

**Soluzione**: 

si crea una nuova classe (Adapter) che implementa l’interfaccia Target ed eredita l’implementazione della classe Adaptée. L’implementazione nell’Adapter dei metodi di Target richiama i metodi di Adaptée.

**Conseguenze**:

Se Target non è una interfaccia pura (java “interface”) è necessaria ereditarietà multipla.


### Composite

**Problema**: vogliamo trattare un insieme di oggetti come se fosse l'istanza di un unico tipo di oggetti. Lo scopo è combinare gli oggetti in una struttura gerarchica ad albero.

**Soluzione**: una interfaccia che tratta oggetti complessi e elementari in modo uniforme.

**Conseguenze**:


### Decorator

**Problema**: si vuole aggiungere delle responsabilità ad un oggetto (Component) senza cambiarne l’interfaccia. L’aggiunta deve essere fatta a runtime, oppure ci sono più aggiunte utilizzabili in combinazioni diverse; oppure si deve rimuovere a runtime le responsabilità aggiunte; insomma non è possibile usare l’ereditarietà.

**Soluzione**: si definisce una classe Decorator che implementa l’interfaccia di Component. Decorator mantiene un riferimento al Component che viene “decorato”. L’implementazione delle operazioni di Component nella classe Decorator richiama l’implementazione del componente decorato, ma ha la possibilità di fare delle pre o post elaborazioni.

**Conseguenze**: il comportamento aggiuntivo è trasparente per gli utenti del componente (sostituendo i riferimenti al Decorator al posto dei riferimenti al componente iniziale). È possibile applicare più Decorator in cascata e l’insieme dei Decorator può essere deciso a runtime (ed è possibile rimuovere un decoratore durante l’esecuzione.


### Observer

**Problema**: Spesso i cambiamenti nello stato di un oggetto (Subject) devono riflettersi su uno o più oggetti da esso dipendenti. Si vuole disaccoppiare il Subject dagli oggetti dipendenti.

**Soluzione**: Si definisce una interfaccia Observer, con un metodo che viene richiamato ad ogni modifica dello stato del Subject. Gli oggetti (che implementano Observer) che sono interessati a un determinato Subject devono essere registrati presso il Subject con un apposito metodo. Il Subject provvede a richiamare il metodo di notifica per tutti gli Observer registrati ogni volta che cambia il proprio stato.


# OOA&D

**Head first object oriented analysis & design.**



* Assicurarsi che il software faccia ciò che il cliente vuole. Attenzione alla raccolta e analisi dei requisiti.
* Applicare principi base di OOP e aggiungere flessibilità. Una volta che il codice funziona, eliminare codice duplicato e applicare tecniche consolidate di OOP.
* Puntare a usare un design mantenibile e riusabile. Applicare principi e pattern specifici e consolidati.

**Incapsulamento**: prevenire duplicazione di codice e isolare ciò che varia.

**Cambiamenti**: fanno parte del gioco. Un codice fatto male cade a pezzi al primo cambiamento, un codice fatto bene è facile da cambiare. Per essere resilienti ai cambiamenti bisogna essere sicuri che ogni classe abbia una sola ragione per cambiare.


# Ingegneria dei Requisiti

Attività con cui si stabilisce ciò che il committente chiede al sistema software e i vincoli che il sistema deve soddisfare in fase di sviluppo e in fase operativa. In questa fase non ci  chiediamo come realizzeremo l’applicativo, ma ci concentriamo nell’elencare cosa deve fare.

**Obiettivi:**



* Comprendere precisamente che cosa si richiede dal sistema.
* Comunicare questa comprensione in modo preciso a tutti gli sviluppatori coinvolti.
* Controllare la produzione per assicurarsi che il sistema soddisfi le specifiche (comprese le eventuali variazioni in corso d’opera).

**Ruoli:**



* Customers: spiegano cosa deve essere consegnato (base contrattuale).
* Managers: controllano scheduling e avanzamento lavori.
* Designers: producono le specifiche del design.
* Programmatori: preparano lista di implementazioni accettabili e output.
* QA/testers: pensare a un insieme di test di base, per la validazione, verifica.

**Documenti:**



* **Definizione dei requisiti: **delle frasi in linguaggio naturale, con eventuale aggiunta di diagrammi dei servizi che il sistema deve offrire e dei suoi vincoli operativi. E’ rivolta al cliente.
* **Specifica dei requisiti:** documento strutturato che fissa una descrizione dettagliata dei servizi che il sistema deve offrire; di solito viene scritta come contratto tra il cliente e il fornitore del software.
* **Specifica del software: **una descrizione dettagliata del software che serva come base per il disegno dell’architettura o per l’implementazione. E’ rivolta agli sviluppatori.

**Requisito**: descrizione informale dei servizi che il sistema deve fornire, o dei vincoli che deve soddisfare, a una specifica funzionale dettagliata e formalmente definita.



* **Requisiti funzionali:** descrivono i servizi offerti dal sistema o le sue funzionalità.
* **Requisiti non funzionali:** vincoli sul processo di sviluppo o sul sistema in generale.
    * **Product requirements:** vincoli che specificano il comportamento del prodotto finale (velocità, reliability, …).
    * **Requisiti organizzativi: **sono conseguenza di policy organizzative del cliente, standard di processo da usare, requisiti implementativi.
    * **Requisiti esterni:** sono esterni al sistema e al suo processo di sviluppo (requisiti di interoperabilità, requisiti legislativi, ...).
* **Requisiti di dominio: **
    * **Comprensibilità:** questi requisiti sono formulati nel linguaggio del dominio applicativo, non è affatto detto che gli sviluppatori “parlino” questo linguaggio.
    * **Implicità:** lo specialista di dominio può conoscere la sua area di lavoro così bene da non pensare di dover esplicitamente chiedere alcune cose, per lui sono implicite.

**Problemi:**

I problemi nascono quando i requisiti non sono enunciati con precisione. Requisiti ambigui possono essere interpretati in modo diverso da sviluppatori e utenti. In principio i requisiti dovrebbero essere sia completi che consistenti, completi nel senso che dovrebbero includere la descrizione di tutto ciò che è richiesto, consistenti perché non ci dovrebbero essere conflitti o contraddizioni nelle descrizioni delle funzionalità richieste. In pratica è impossibile produrre un documento dei requisiti completo e consistente: sotto questo aspetto la prototipazione può essere molto utile per chiarire le cose.

**Processo base:**



1. Definizione dei bisogni del committente.
2. Definizione dei requisiti dell’implementazione.
3. Documento di riferimento per la manutenzione.

**Processo dell‘ Ingegneria dei Requisiti:**



1. **Studio fattibilità:** quali sono le necessità che possono essere soddisfatte con la tecnologia e le risorse disponibili.
2. **Analisi dei requisiti:** quali servizi il sistema deve offrire, qual’è il dominio di applicazione, performance richieste, vincoli hw, etc etc.
3. **Definizione dei requisiti:** frasi in linguaggio naturale più eventuali diagrammi dei servizi che il sistema deve offrire e dei suoi vincoli operativi. E’ rivolta al cliente.
4. **Specifica dei requisiti:** documento strutturato che fissa una descrizione dettagliata dei servizi che il sistema deve offrire. E’ alla base del contratto.
5. **Specifica del software:** descrizione dettagliata del software che serva come base per il disegno dell’architettura o per l’implementazione. E’ rivolta agli sviluppatori.

La tecnica più usata per individuare i requisiti consiste nel condurre riunioni o interviste col committente e gli utilizzatori finali. Solitamente si parte da domande che conducano a fissare in termini generali il problema. Serve per identificare gli stakeholder, i benefici misurabili e le alternative.

Si prosegue con un secondo insieme di domande: consente all’analista di acquisire maggiore comprensione del problema, e al committente di comunicare le proprie percezioni riguardo una soluzione.

**Problemi:**



* Problemi di scope: limiti del sistema mal definiti, oppure committente specifica dettagli tecnici non necessari che possono confondere invece di chiarire gli obiettivi generali.
* Problemi di comprensione: committente non è completamente sicuro di ciò che vuole, ha un’idea vaga delle limitazioni e delle possibilità, non conoscono bene il dominio del problema, omettono informazioni che ritengono “ovvie”, hanno problemi a comunicare i bisogni all’analista.
* Problemi di volatilità: cambiano i requisiti nel corso del tempo.

**Controllo:**



* Validità: il sistema fornisce le funzionalità che meglio soddisfano le richieste del committente?
* Consistenza: ci sono requirements in conflitto tra loro?
* Completezza: tutti i requisiti del cliente sono stati individuati?
* Realismo: è fattibile soddisfare tutti i requisiti con la tecnologia e i budget a disposizione?
* Verificabilità: il requisito è realisticamente testabile?
* Comprensibilità: il requisito è stato adeguatamente compreso?
* Tracciabilità: l’origine del requisito è chiaramente indicata?
* Adattabilità: è possibile cambiare il requisito senza grossi impatti su altri requisiti?

**Revisioni:**

E’ necessario svolgere delle revisioni periodiche durante la formulazione dei requisiti. Possono essere sia formali che informali. Le revisioni devono coinvolgere sia il cliente che gli sviluppatori. Lo scopo è sempre avere una adeguata comunicazione tra committente, sviluppatori e utenti finali per individuare e risolvere i problemi appena si manifestano.

**F.A.S.T. - Facilitated Application Specification Tecnique**

Tecnica per la specifica delle applicazioni: consiste nella formazione di un team misto di sviluppatori, clienti e collabori che devono individuare e specificare il problema, specificare un insieme preliminare di requisiti, proporre elementi della soluzione e negoziare strategie diverse per valutarle. Viene indetta una riunione a cui partecipano sia gli ingegneri del software che i clienti. Si stabiliscono delle regole per la preparazione e la partecipazione. Viene proposta una agenda abbastanza formale da coprire tutti i punti importanti e abbastanza informale da incoraggiare l’apporto di nuove idee o punti di vista. Quello che si vuole ottenere è: specificare il problema, proporre eventuali soluzioni, confrontare varie strategie, arrivare ad un insieme preliminare di requisiti.

**Casi d’uso:**

Man mano che i requisiti vengono raccolti l’analista può creare un insieme di scenari che identificano un possibile “modo” di usare il sistema. Gli scenari (Use Cases) descrivono una funzionalità dal punto di vista di chi la utilizza.



* Attori: utenti o altra entità che interagisce col sistema; formalmente è una qualunque cosa che comunica col sistema ma ne è esterno.
* Casi d’uso: descrivono l’interazione tra attori e sistema, ma non la “logica interna” del sistema.


# Analisi dei requisiti

Tecniche per analizzare, definire e specificare i requisiti dei sistemi software.

Coinvolge sicuramente lo staff tecnico: collaborano con il committente per individuare il dominio applicativo, i servizi che il sistema deve offrire e i vincoli operativi. Sono quasi certamente coinvolti anche utenti finali, manager, ingegneri coinvolti nella manutenzione, esperti del dominio, ecc.

**Problemi:**

Gli stakeholders non hanno le idee chiare sul cosa vogliono. Gli stakeholders esprimono i requisiti usando una loro terminologia . Tra gli stakeholders ci possono essere requisiti contrastanti. Possono esserci altri fattori (politica interna, gestione) che influenzano i requisiti del sistema.

**Attività:**



* Comprensione del dominio: gli analisti devono “padroneggiare” il dominio applicativo.
* Raccolta dei requisiti: interagire con gli stakeholders per identificare i loro bisogni (e
* quindi i requisiti).
* Classificazione: prendere l’insieme non strutturato dei requisiti e organizzarli in modo coerente.
* Risoluzione dei conflitti: a causa del numero di stakeholders coinvolti, possono esserci dei conflitti nei requisiti: vanno individuati e risolti.
* Assegnazione delle priorità: non tutti i requisiti sono uguali: alcuni sono più importanti di altri; bisogna stabilire delle classi di priorità.
* Validazione dei requisiti: i requisiti vanno controllati per vedere se sono completi, consistenti e in accordo con quello che i stakeholders vogliono realmente dal sistema.

**Avvio**:

I responsabili della raccolta dei requisiti devono farsi un elenco delle persone a cui sarà richiesto di collaborare alla definizione dei requisiti. I requisiti vengono necessariamente esplorati da più punti di vista. Ogni stakeholder contribuirà con il proprio punto di vista. Potranno esserci requisiti incoerenti o in conflitto tra loro. Lo scopo, in questa fase, è catalogare le informazioni raccolte (incoerenze comprese), non decidere. Si vuole definire una solida conoscenza del problema, di chi vuole una soluzione, della natura della soluzione desiderata, e delle comunicazioni/collaborazioni tra cliente e sviluppatore. Dovrebbero essere domande aperte: non devono influenzare la risposta.

**Raccolta**:

L’approccio più usato è il Facilitated Application Specification Technique (FAST). Prima delle riunioni, i partecipanti devono preparare un elenco di oggetti che fanno parte del sistema, che devono essere prodotti dal sistema, o che vengono utilizzati dal sistema per le proprie funzioni. Elenco non esaustivo, ma deve riflettere la sua percezione del sistema. A questo punto si presentano i singoli elenchi: ogni elemento dovrebbe poter essere manipolato separatamente. No dibattiti e critiche in questa fase. L’obiettivo è arrivare ad un elenco consensuale per ciascun argomento: oggetti, servizi, vincoli, prestazioni.

**Definizione dei requisiti:**

Deve specificare il comportamento che il sistema manifesta verso l’esterno senza definire un modello computazionale. Include requisiti funzionali e non funzionali.

**Motivazione del requisito:**

La motivazione del requisito serve per aiutare lo sviluppatore a capire il dominio di applicazione e a capire perché il requisito è descritto in quella forma. E’ particolarmente importante qualora si debbano modificare i requisiti: la presenza della motivazione di un requisito riduce la probabilità che il cambiamento alteri l’intenzione originaria e che si producano effetti inaspettati.

**Elaborazione:**

Si prendono le informazioni ottenute e le si espandono e raffinano. Occorre descrivere il problema in modo da creare solide basi per la progettazione. Se si oltrepassa questo punto, vuol dire che siamo già partiti a progettare il sistema.

**Negoziazione**:

Può essere necessario valutare compromessi tra funzionalità, prestazioni e altre caratteristiche del prodotto da un lato e costi o tempi di uscita sul mercato dall’altro. Lo scopo di questa fase è sviluppare un piano di progetto che risponda ai bisogni del cliente riflettendo i vincoli del mondo reale.

**Gestione:**

I requisiti possono cambiare, anzi, la necessità di cambiare i requisiti può essere richiesta per tutta la durata del sistema. Bisogna poter identificare, controllare e tracciare i requisiti e i cambiamenti a mano a mano che si procede nello sviluppo del progetto. Si assegna a ogni requisito un identificatore univoco, si sviluppano delle tabelle di tracciabilità. Si vuole anche la tracciabilità delle funzionalità: relazioni tra requisito e funzionalità.

**Validazione**

Esaminare le specifiche per garantire che tutti i requisiti software siano stati descritti in modo non ambiguo. I requisiti devono essere scritti in modo da poter essere facilmente verificati. Devono essere evitati i termini vaghi e bisogna quantificare e rendere oggettiva ogni richiesta.

**Modello VORB - Viewpoint Oriented Requirements Definition**



* Identificazione dei viewpoints: individuare i viewpoint che ricevono servizi dal sistema e identificare i servizi specifici che il sistema deve offrire a ogni viewpoint.
* Strutturazione dei viewpoint: combinare i viewpoint a gruppi, in modo gerarchico; servizi comuni sono forniti al più alto livello della gerarchia.
* Documentazione dei viewpoints: raffinare la descrizione dei viewpoint e i servizi identificati.
* Mapping viewpoint-sistema: definire gli oggetti che rappresentano i viewpoint (modello OO).


# Progettazione

La progettazione è il processo (successivo all'analisi dei requisiti) che porta alla definizione ingegneristica di ciò che deve essere realizzato. Si compone di due fasi:



* Diversificazione: il progettista acquisisce il materiale grezzo del progetto (componenti, possibilità di realizzazione, conoscenze) per individuare le possibilità realizzative.
* Convergenza: il progettista sceglie e combina gli elementi disponibili per arrivare ad un prodotto finale.

Il progetto deve soddisfare tutti i requisiti espliciti contenuti nel modello concettuale e tutti i requisiti impliciti voluti dal cliente. Il progetto deve essere una guida leggibile e comprensibile per chi si occuperà delle fasi di codifica, collaudo e manutenzione. Il progetto deve dare un quadro completo e coerente del software, considerando i domini dei dati, funzionale e comportamentale dal punto di vista dell’implementazione.

L’architettura di progetto deve essere creata con modelli di progettazione riconoscibili, essere costituita da componenti ben progettate, poter essere implementata in modo evolutivo. Il progetto deve essere modulare e contenere una rappresentazione distinta di dati, architettura, interfacce e componenti. Le strutture dei dati devono essere tratte da modelli di dati riconoscibili e devono essere appropriate per i dati da implementare. Le componenti devono avere caratteristiche funzionali indipendenti e le interfacce devono tendere a ridurre la complessità delle comunicazioni tra moduli e verso l’esterno. Il metodo di progetto deve essere ripetibile e pilotato dai requisiti.

**Fasi:**



1. Comprensione del problema: guardare al problema da angolature differenti, identificare una o più soluzioni e valutare le soluzioni possibili e scegliere la più appropriata rispetto all’esperienza del progettista e alle risorse disponibili.
2. Descrivere le astrazioni delle soluzioni: usare notazioni grafiche, formali o altro per descrivere le componenti del progetto.
3. Ripetere lo step per ogni astrazione identificata, finché la progettazione non è espressa in termini primitivi.

Per raffinare utilizziamo tecniche di scomposizione per passare da astrazioni funzionali ad alto livello alle linee di codice. Raffinamento ed astrazione possono essere considerate attività complementari. Mediante l’astrazione il progettista specifica procedure e dati eliminando i dettagli di basso livello. L’astrazione è l’atto di dare una descrizione del sistema ad un certo livello, trascurando i dettagli inerenti i livelli sottostanti.

Fasi del design:



* Architectural Design: identificare e documentare i sottosistemi e le loro relazioni.
* Abstract Specification: specifichiamo i servizi forniti da ciascun sottosistema e i vincoli a cui deve sottostare.
* Interface Design: descriviamo l’interfaccia dei sottosistemi verso altri sottosistemi.
* Component Design: allocare i servizi ai diversi componenti e definire le interfacce di questi componenti.
* Data Structure Design: definire come sono fatte le strutture dati.
* Algorithm Design: specificare gli algoritmi utilizzati.

Strategie di decomposizione



* Top-down: decomposizione del problema, viene partizionato ricorsivamente in sottosistemi fino a che si identificano dei sottoproblemi trattabili.
* Bottom-up: composizione di soluzioni.
* Sandwich soluzione naturale.

Un sistema composto da un unico blocco monolitico di software è sempre difficile da comprendere, implementare e mantenere. L’unico modo per permettere di gestire intellettualmente il programma è suddividerlo in moduli con funzionalità definite e limitate e con interfacce ben definite. Una eccessiva modularità richiede sforzi per l’integrazione.

**Criteri di Meyer**



* Scomponibilità: un metodo che permette la scomposizione del problema in sottoproblemi riduce la complessità.
* Componibilità: un metodo che permette l’assemblamento di componenti preesistenti migliora la produttività.
* Comprensibilità: un modulo le cui interfacce con altri moduli siano minimi è di più facile costruzione e modificabilità.
* Continuità: modifiche ai requisiti di sistema che comportano solo modifiche a singoli moduli sono di facile controllo.
* Protezione: se effetti anomali in un modulo non si propagano la manutenibilità migliora.


# Project Management

Intendiamo tutte le attività necessarie ad assicurare che un progetto software sia sviluppato rispettando le scadenze prefissate e risponda a determinati standard, sia tecnici che economici. Deve conciliare tempi, scopo e budget.

Il software è intangibile. Per valutare i progressi di un progetto bisogna basarsi su qualcosa: la documentazione.

**Motivi principali di un ritardo su un progetto:**



* Deadline non realistica, fissata e/o imposta da qualcuno esterno allo staff tecnico.
* Cambiamenti dei requisiti imposti dal cliente.
* Stima ottimistica (troppo) del lavoro e delle risorse necessarie a compierlo.
* Rischi che non sono stati presi in considerazione all’inizio del progetto.
* Difficoltà tecniche imprevedibili.
* Difficoltà umane imprevedibili.
* Problemi di comunicazione nel gruppo di sviluppo.
* Incapacità dalla direzione del progetto di riconoscere che c’è un ritardo, e mancata attuazione di contromisure.

**Principi fondamentali per la pianificazione:**



* Un progetto deve essere ripartito in attività e compiti di dimensioni ragionevoli.
* Bisogna determinare le dipendenze tra attività e compiti.
* Determinare quali compiti si possono svolgere in parallelo e quali in sequenza.
* Alcune attività dipendono da altre per poter iniziare.
* A ogni compito bisogna assegnare delle “unità di lavoro” (mesi/uomo).
* Ogni compito deve avere una data di inizio e una di fine.
* A ogni progetto è assegnato un numero definito di persone.
* Non bisogna assegnare più persone del necessario.
* Ogni compito deve essere assegnato a qualcuno.
* Ogni compito deve avere un risultato predefinito.
* A ogni compito si deve associare almeno un punto di controllo.
* Un punto di controllo è passato quando la qualità di uno o più compiti è approvata.

**Attori:**



* **Senior managers:** definiscono gli aspetti economici del progetto.
* **Project managers:** pianificano, organizzano, controllano lo sviluppo del progetto.
* **Practitioners:** chi ha le competenze tecniche per realizzare parti del progetto.
* **Customers: **il cliente che stabilisce i requisiti del software.
* **End users**: chi userà il sistema una volta sviluppato.

**Pianificazione:**



1. **Introduzione**: definizione degli obiettivi del progetto, e dei vincoli prefissati.
2. **Organizzazione**: definisce l’organizzazione del team di sviluppo: quali sono le persone e quali sono i loro ruoli.
3. **Analisi dei rischi: **elenco dei rischi previsti, della probabilità che accadano, delle strategie per ridurli o affrontarli.
4. **Risorse HW e SW richieste: **stime di costo per acquisire le risorse.
5. **Suddivisione del lavoro:** suddivisione in attività, vengono identificati i deliverables e le milestones.
6. **Scheduling del progetto: **identificare le dipendenze tra le attività, stima del tempo richiesto per le milestones, assegnazione personale alle attività.
7. **Controllo e rapporto sulle attività:** elenca i rapporti che devono essere prodotti per i manager, quando devono essere prodotti e che meccanismi di controllo sullo stato di avanzamento delle attività sono previsti.
* **Milestones:** sono i punti finali di ogni attività.
* **Deliverables:** sono i risultati del progetto consegnati ai clienti.

**Scheduling: **occorre suddividere il progetto in tasks e stimare il tempo e le risorse necessari per completare ogni compito. Bisogna poi organizzare i compiti concorrentemente per permettere un uso ottimale della forza lavoro e minimizzare le dipendenze tra task ovvero evitare la propagazione a catena dei ritardi. Stimare la difficoltà di un problema e i costi di sviluppo di una soluzione è difficile: la produttività non è proporzionale al numero di persone che lavorano ad un task. 

**Regola del 40-20-40**



* 40% del tempo per l’analisi e la progettazione
* 20% del tempo per la scrittura del codice
* 40% per il collaudo


### Tipologie di team

**Democratico Decentralizzato:**

assenza di un leader permanente, consenso di gruppo sulle soluzioni e sulla organizzazione del lavoro, comunicazione orizzontale.



* **Vantaggi**: attitudine positiva a ricercare presto gli errori, funziona bene per problemi “difficili”.
* **Svantaggi**: difficile da imporre, non è scalabile.

**Controllato Decentralizzato: **un leader riconosciuto che coordina il lavoro. La risoluzione dei problemi è di gruppo, ma l’implementazione delle soluzioni è assegnata dal leader ai vari sottogruppi. Comunicazione orizzontale tra i sottogruppi e verticale con il leader.

**Controllato Centralizzato:** il team leader decide sulle soluzioni e sull’organizzazione. Comunicazione verbale tra team leader e gli altri membri.


### Stima delle tempistiche

Come misurare l’effort (impegno) richiesto per un lavoro? La misura tipica è il **mese-uomo.**

Problema: i progressi compiuti non sono proporzionali a questa unità.

Mesi e uomini sono effettivamente interscambiabili solo per compiti che possono essere perfettamente partizionati tra i lavoratori, e che non richiedono comunicazione tra essi.

**Diagramma di Gantt:** fornisce in maniera grafica informazioni sui tempi, vincoli di precedenza nell’esecuzione delle attività, informazioni sull’avanzamento delle attività, punti di controllo (checkpoint, milestones). Il diagramma di Gantt è uno strumento sia in fase di pianificazione che in fase di monitoraggio. È un  diagramma bi-dimensionale, sull’asse X vi è il tempo (giorni, settimane, mesi), sull’asse Y vi sono le attività di progetto.

**Diagramma di Pert:** contiene le stesse informazioni dei diagrammi Gantt. Di solito non forniscono informazioni sulla posizione temporale esatta delle attività del progetto, ma focalizzano l’attenzione sulla durata e sui vincoli di precedenza.


### Algoritmi di trasformazione e di ottimizzazione

**Piano di Progetto:** indica la sequenza temporale potenziale con cui sono eseguite le attività  dichiarate nel modello di processo. Rappresenta l’ottimizzazione ottimale del progetto: pianifica la sequenza di esecuzione tenendo conto dei soli vincoli di precedenza imposti dal fabbisogno dei manufatti delle attività e non considerando vincoli di tempi, costi e personale.

**Piano Esecutivo:** indica la sequenza temporale reale delle attività, considerati i vincoli di progetto e le decisioni manageriali circa tempi, costi, uomini (risorse). Parte dalla pianificazione ottimale (che deriva dal piano di progetto) e tenendo conto delle precedenze la rimodula sulla base dei vincoli di tempi, costi e uomini.

Il Piano di Progetto è la prima versione del piano esecutivo. Le eventuali modifiche derivano dall’analisi dei tempi, costi e uomini disponibili. Le attività in sequenza nel Piano di Progetto devono rimanere tali anche nel Piano Esecutivo. Le attività in parallelo nel Piano di Progetto  restano in parallelo nel Piano Esecutivo (se ci sono risorse sufficienti) o sono rese sequenziali se non sono disponibili risorse a sufficienza.


### Cammini Critici

Il cammino critico è quello che determina la lunghezza di un progetto. Un qualsiasi ritardo su di esso determina automaticamente uno slittamento dell’intero progetto. Per ottimizzare oltre quanto consentito dai parallelismi, bisogna investigare la possibilità di ristrutturare le attività per ridurre i cammini critici. Il “prima si fa e meno costa” è molto oneroso (e non sempre possibile) farlo quando il progetto è già in esecuzione, andrebbe fatto prima di avviare l’esecuzione del progetto.


# Ingegneria di Sistema

Significa progettare, implementare e installare sistemi che includono hardware, software, informazioni e personale. Trasformare un bisogno operativo in una descrizione di parametri operativi e una configurazione di sistema attraverso un processo iterativo di analisi, sintesi, ottimizzazione, progetto e valutazione. Integrare parametri tecnici correlati e assicurare la compatibilità di tutte le interfacce fisiche e funzionali al fine di ottimizzare il progetto complessivo. Integrare affidabilità, manutenibilità, supporto logistico, sicurezza, fattibilità, integrità strutturale, fattori umani con l’obiettivo di ottimizzare il risultato.

È preferibile scomporre un sistema in tanti piccoli sottosistemi interagenti tra loro. Ogni sottosistema fa riferimento ad un insieme di competenze tecniche e scientifiche diverse e per questo si richiede un approccio multidisciplinare.

Modellazione di un sistema: si definisce una serie di processi che rappresentano entità della

realtà fisica.



1. si definisce il comportamento di ciascun processo
2. si definiscono i dati che guidano il sistema
    1. dati esogeni (che provengono dall’esterno)
    2. dati endogeni (che il sistema si scambia al proprio interno)

L’interdipendenza delle componenti fa sì che gli errori possano propagarsi in tutto il sistema. I fallimenti possono essere dovuti anche a interrelazioni tra componenti di cui non si è tenuto conto. L’affidabilità complessiva dipende da quella dell’hardware, quella del software e quella degli operatori.

**Proprietà di un sistema:**



* Proprietà funzionali: appaiono quando le varie componenti vengono assemblate e lavorano per uno scopo comune (“quello che il sistema deve fare”). 
* Proprietà non-funzionali: hanno a che fare con il comportamento del sistema nel suo ambiente operativo. Possono anche essere vincoli sul sistema (reliability, performance, safety, security)

**Ambiente**

I sistemi non sono indipendenti, ma sono inseriti in un ambiente la cui conoscenza va inclusa nella specifica.  L’obiettivo di un sistema può essere di modificare il proprio ambiente (p.e. sistema di riscaldamento) o l'ambiente che può condizionare il comportamento del sistema (p.e. blackout).

Fasi:



1. Sviluppo dei sottosistemi: Implementare ciascuno dei sottosistemi individuati nella fase precedente. Spesso viene fatto in parallelo da parte di team diversi.
2. Integrazione: E’ il processo di mettere insieme hw, sw e risorse umane. Conviene integrare i sottosistemi in modo incrementale. In questa fase possono emergere problemi di interfaccia tra le diverse componenti.
3. Installazione: Mettere il sistema completo nel suo ambiente operativo. L’ambiente finale può essere diverso da quello di sviluppo/test.
4. Messa in opera: Mette in luce i requisiti non contemplati. Gli utenti possono utilizzare il sistema in modo diverso da quello previsto dai progettisti.
5. Mantenimento e smantellamento: Qualunque sistema ha una sua durata. Deve evolvere per soddisfare l’evoluzione dei requisiti. Ogni cambiamento deve essere accuratamente esaminato e va verificata l’interdipendenza dei sottosistemi.


# Architettura del software

**Proprietà:**



* Proprietà strutturali: come sono assemblate le componenti del sistema e come interagiscono.
* Proprietà extrafunzionali: come sono soddisfatti i requisiti di prestazione, affidabilità, sicurezza.

In generale per progetto (software e non solo) intendiamo un insieme ben definito di attività che ha un inizio, ha una fine, ha uno scopo,  viene portato avanti da un insieme di persone, utilizza un insieme di risorse, non è un lavoro di routine.



* Affinità: deve poter permettere di usare strutture e schemi simili già usati in precedenza.

**Modelli:**



* Modelli strutturali: architettura come collezione di componenti.
* Modelli schematici: individuare schemi progettuali ricorrenti in applicazioni dello stesso tipo.
* Modelli dinamici: mostrano aspetti comportamentali dell’architettura.
* Modelli funzionali: quali funzioni usano quali altre funzioni.

**Gerarchia di controllo:** struttura ad albero call and return. Mostra la gerarchia dei moduli di un programma. 



* Ripartizione orizzontale: vengono definite delle partizioni che effettuano una specifica operazione (es: input, trasformazioni, output).
* Ripartizione verticale: vi è una gerarchia basata su una gerarchia top-bottom in cui i moduli più alti decidono quali moduli più bassi chiamare. Sono i moduli dell’ultimo livello che effettivamente effettuano le operazioni.

**Indipendenza modulare:** i moduli devono essere indipendenti ovvero occuparsi di una singola funzione.



* **Coesione**: un modulo è coeso quando fa un numero di operazioni limitato e idealmente svolge un unico compito. Qualora si dovesse modificare il sistema, permette di mantenere le modifiche limitate in alcune sezioni del codice. Funzionalità simili devono stare nello stesso modulo.
    * Coesione **incidentale**: le parti di un componente sono raggruppate ma non correlate.
    * Associazione **logica**: vengono raggruppate le componenti che svolgono azioni simili.
    * Coesione **temporale**: vengono raggruppate le componenti che sono attivate nello stesso tempo.
    * Coesione **procedurale**: vengono raggruppati gli elementi di una componente che sono attivate in sequenza.
    * Coesione di **comunicazione**: vengono raggruppati gli elementi che operano su uno stesso input o output.
    * Coesione **sequenziale**: l’output di una componente è l’input di un’altra.
    * Coesione **funzionale**: ogni parte di un componente è necessaria solo per l’esecuzione di una singola funzione di quella componente.
    * Coesione **d’oggetto**: ogni operazione fornisce delle funzionalità per osservare o modificare gli attributi di un oggetto.
* **Coupling (accoppiamento):** misura la forza di connessione tra le componenti di un sistema ovvero quanto le componenti si usano tra loro.
* **Comprensibilità:** coesione tra le componenti, naming (significato dei nomi), documentazione, complessità.
* **Adattabilità**: i moduli sono poco accoppiati e possono essere usati da altri componenti.

 \
Il principio dell’information hiding richiede che ciascun modulo sia definito in modo che le sue procedure e le informazioni locali su cui agisce non siano accessibili ad altri moduli. L’interazione con gli altri moduli deve avvenire solo tramite la sua interfaccia.

Vantaggi: facilità di modifica di un modulo, perché non ci si deve preoccupare di effetti collaterali delle modifiche. 


### Architettura a Repository

Architettura basata sui dati. Il sistema è centrato su un archivio di dati. Le componenti accedono all’archivio operando indipendentemente tra loro. L’archivio può essere passivo (tutte le operazioni sono in mano ai client) oppure attivo (l’archivio notifica ai client le variazioni nei dati). Il vantaggio è l'indipendenza tra i vari moduli (integrabilità): si può aggiungere un modulo o intervenire su uno di essi senza che gli altri ne risentano. 

**Vantaggi**: modo efficiente di condividere grandi quantità di dati, i sottosistemi possono disinteressarsi a come i dati vengono condivisi, la gestione è centralizzata (backup, sicurezza. 

**Svantaggi**: i sottosistemi devono concordare su un modello dei dati che inevitabilmente è un compromesso tra esigenze diverse, modificare la struttura (schema) dei dati è difficile e dispendioso, non c’è spazio per politiche specifiche di accesso ai dati, bassa scalabilità: il repository centrale spesso è un collo di bottiglia.


### Architettura Client-Server

Modello per sistemi distribuiti, mostra come dati e processi sono distribuiti su un insieme di componenti. Si tratta di un insieme di server autonomi che offrono servizi specifici e un insieme di clienti che richiedono questi servizi uniti da una rete di comunicazione che permette ai clienti di accedere ai server.



* Presentation layer: si occupa di presentare i risultati della computazione agli utenti del sistema e di gestire gli input da parte degli utenti.
* Application processing layer: si occupa di offrire le funzionalità specifiche dell’applicazione.
* Data management layer: si occupa di gestire la comunicazione con il DBMS.

**Vantaggi**: la distribuzione dei dati è molto semplice, fa un uso effettivo del sistema di rete e può richiedere hw economico (molti nodi a bassa potenza per effettuare computazioni complesse). È facile aggiungere nuovi server o fare l’upgrade dei server esistenti.

**Svantaggi**: non c’è un unico modello condiviso dei dati, quindi ogni sottosistema fa uso di un modello proprio, e lo scambio di dati può essere inefficiente, alcune attività di gestione dei dati devono essere replicate e  non c’è un registro centrale dei nomi e servizi: può essere difficile sapere quali dati/servizi sono disponibili.


### Architettura a Flusso di Dati

Il sistema è modellato sul flusso di dati, dalla fase di input a quella di output. I moduli si comportano da filtri connessi da pipe di dati. Ogni filtro si attende solo dati in input con un certo formato e produce dati in output di formato prefissato. Ogni filtro lavora senza occuparsi di cosa lo precede o lo segue. Se il flusso dati degenera in una unica catena di filtri, allora l’architettura si dice “a filtro batch sequenziale”.

**Vantaggi**: è facile costruire computazioni complesse mediante concatenazione di filtri semplici. Ogni filtro è un “scatola nera” riutilizzabile in altre situazioni. Se ben programmati, i filtri non condividono lo stato (basso accoppiamento).

**Svantaggi**: i formati di dati in input e output di filtri collegati devono essere compatibili. Se la struttura di controllo non può essere “linearizzata”, questo modello non è adeguato.

Architettura a macchina astratta


### Architettura a macchina astratta (a livelli)

Usato per modellare l’interfaccia tra sottosistemi. Organizza il sistema in un insieme di strati (o macchine astratte) ognuno dei quali offre un insieme di servizi. Supporta lo sviluppo incrementale di sottosistemi a livelli diversi: se l’interfaccia di un livello cambia, ne risulta affetto solo il livello adiacente.

**Vantaggi: **supporta lo sviluppo incrementale, livello dopo livello. Se si cambia l’interfaccia di un livello, solo quello adiacente ne risente.

**Svantaggi**

Spesso può essere complicato strutturare il sistema in questo modo, può essere restrittivo pensare che un livello possa interagire solo col precedente o successivo.


### Scomposizione modulare

Ulteriore raffinamento a livello strutturale: i sottosistemi sono scomposti in moduli.

Sottosistema - modulo: un sottosistema è un sistema indipendente: sono composti da moduli, hanno interfacce ben definite per comunicare con altri sottosistemi. Un modulo di è componente sottosistema e fornisce uno o più servizi ad altri moduli, o usa servizi di altri moduli; non è indipendente.

**Scomposizione modulare:**



* **Modello a oggetti**: il sistema è scomposto in oggetti che interagiscono. Si struttura il sottosistema come un insieme di oggetti con accoppiamento lasco e interfacce ben definite. La scomposizione orientata ad oggetti significa identificare le classi degli oggetti, gli attributi (campi) e le operazioni (metodi). Quando vengono implementati, gli oggetti sono istanze di queste classi e qualche modello di controllo è usato per coordinare i metodi.
* **Modello data-flow:** il sistema è scomposto in modelli funzionali che trasformano input in output (modelli pipeline). Trasformazioni funzionali che producono un output a partire da un input. Possono riferirsi ad un modello a “pipe” e a filtri (pensate alla shell di unix). Se c’è un’unica trasformazione sequenziale, è un modello batch sequenziale: molto usato nei sistemi di gestione dei dati. Non si presta bene a sistemi interattivi.

**Modelli di controllo tra sottosistemi: **Descrivono il modo con cui fluisce il controllo tra i sottosistemi.



* **Controllo centralizzato:** un sottosistema ha la responsabilità del controllo globale e attiva e disattiva i sottosistemi.
    * **Modello “call-return”: **gerarchia di procedure, il controllo inizialmente parte dalla routine alla base della gerarchia e si sposta verso il basso. Questo tipo di controllo si può applicare a sistemi sequenziali.
    * **Modello “manager”:** una componente del sistema controlla l’interruzione, l’inizio e il coordinamento degli altri processi. Applicabile a sistemi concorrenti. Può essere implementato in sistemi sequenziali come un blocco “case”.
* **Controllo basato a eventi:** ogni sottosistema può rispondere a eventi generati da altri sottosistemi o dall’ambiente esterno
    * **Modello “broadcast”:** un evento è trasmesso a tutti i sottosistemi. Ogni sottosistema in grado di gestire l’evento può farlo. E’ utile per integrare diversi sistemi collegati in rete.
    * **Modello “interrupt-driven”:** usato nei sistemi real-time dove le interruzioni sono raccolte da un gestore di interruzioni e passate a un componente responsabile per processarle. Usati in sistemi real-time dove la velocità di risposta a un evento e la latenza sono essenziali. Devono essere definiti tutti i tipi di interruzioni noti, e a ciascun tipo occorre associare un modulo capace di gestire quel particolare tipo di interruzione.


# Modelli di processo di sviluppo di software

Insieme coerente di attività per la specifica, il progetto, l’implementazione, la verifica di sistemi software. Un modello di processo è una rappresentazione astratta di un processo, descrive il processo da una particolare prospettiva.

**Modello a cascata:**

Fasi:



* Analisi e definizione dei requisiti.
* Progettazione del sistema e/o del software.
* Implementazione e test delle singole unità.
* Integrazione e test del sistema.
* Installazione e mantenimento del sistema.

Il grosso limite del modello a cascata è la difficoltà a effettuare cambiamenti nel corso del processo. È molto difficile soddisfare i cambiamenti nei requisiti da parte del committente. La suddivisione in fasi può sembrare arbitraria o artificiosa ma in realtà questo modello è derivato dal ben consolidato modello ingegneristico per la risoluzione dei problemi. Il modello a cascata è adeguato quando i requisiti sono ben compresi dall’inizio e non sono soggetti a modifiche. Spesso i requisiti non sono sufficientemente chiari o il committente stabilisce gli scopi generali del sistema software, ma non chiarisce subito i requisiti in modo completo. Oppure gli sviluppatori sono incerti sul significato di alcuni requisiti o su come strutturare l’interfaccia o gli algoritmi. Il vantaggio del modello a cascata è che è semplice e per applicarlo basta essere sicuri dei requisiti iniziali.

Possibilità di procedere per prototipi: dopo la fase di testing, se superata si ritorna all'analisi di requisiti e si fa un colloquio con il committente per stabilire quali sono le prossime modifiche.

**Rapid Application Development**

Modello sequenziale lineare per avere un ciclo di sviluppo molto breve. Lo sviluppo rapido è ottenuto mediante il riuso di componenti. Si applica quando si hanno requisiti chiari e quando il processo di sviluppo è ben vincolato. Nei casi in cui si può applicare, il modello RAD può portare allo sviluppo di software in tempi brevi rispetto al modello a cascata classico. È adatto alle situazioni in cui il sistema da implementare può essere facilmente partizionato fin dall’inizio e in cui  ogni parte deve potere essere sviluppata indipendentemente e in tempi brevi.

Fasi:



1. Comunicazioni: comprendere il problema e i dati che devono essere considerati dal software. 
2. Pianificazione: come suddividere il lavoro tra i vari team.
3. Modellazione: quali dati guidano il processo? quali dati vengono generati? da chi? chi li utilizza? Quali sono le operazioni sui dati?
4. Costruzione: generare l’applicazione con linguaggi di alto livello.
5. Deployment: integrazione dei vari componenti e collaudo finale

Limiti:



* Bisogna avere risorse umane sufficienti a creare il numero corretto di team.
* Sviluppatori e clienti devono essere disponibili a completare il sistema in tempi rapidi.
* RAD non è il modello adatto quando: il sistema non può essere modularizzato correttamente, quando si richiedono alte prestazioni e quando si usano tecnologie innovative con alto rischio di incontrare problemi strada facendo.

**Modello Evolutivo**

L’obiettivo è lavorare con il committente ed evolvere verso il sistema finale a partire da una specifica generale. Lo sviluppo inizia con le parti del sistema che sono già ben specificate, aggiungendo via via nuove caratteristiche.

Prototipazione di tipo usa e getta: ogni singola modifica di un componente viene fatta approvare dal committente e integrata nel sistema evolvendo verso la versione finale.

Limiti: mancanza di visibilità del processo e di documentazione (a che punto sono nei tempi di sviluppo). I sistemi spesso poco strutturati, e bisogna fare attenzione a non trasformare il prototipo in un prodotto da porre in produzione. Al committente il prototipo potrebbe sembrare funzionante, ma può avere tanti e tali problemi da essere inutilizzabile in condizioni reali.

Il modello evolutivo va bene quando: i sistemi sono di piccola o media dimensione, per sistemi con vita attesa corta e per sviluppare prototipi.

**Modello Trasformazionale**

Basato sulla trasformazione di una specifica matematica in un programma eseguibile, attraverso trasformazioni che permettono di passare da una rappresentazione formale ad un altra. Le trasformazioni devono preservare la correttezza, in questo modo è banale verificare che il programma soddisfa la specifica.

Problemi:

Richiede conoscenze specializzate e addestramento per essere applicato. Certe parti del sistema (p.e. l’interfaccia utente) sono difficili da specificare formalmente.

Ideale per: sistemi critici, in cui sicurezza e/o affidabilità sono essenziale e devono non solo essere raggiunti, ma bisogna dimostrare che il sistema li può mantenere. Questo modello ha campi di applicazione estremamente limitati.

**Modello basato sul riutilizzo**

Si basa sul riutilizzo sistematico di componenti off-the-shelf opportunamente integrate.

Fasi del modello:



1. Analisi delle componenti.
2. Adattamento dei requisiti.
3. Progettazione del sistema.
4. Integrazione.

E’ per natura evolutivo: richiede un approccio iterativo allo sviluppo del software.

Vantaggi: netta riduzione del ciclo di sviluppo, netta riduzione dei costi di progetto, maggiore produttività.

Svantaggi: dipende tutto dal trovare componenti che possano servirci e che siano integrabili tra loro.

**Modello a spirale**

Obiettivo principale = minimizzare i rischi.

Il rischio è una misura di incertezza del risultato di una attività.

Meno informazione si ha, più alti sono i rischi quindi bisogna acquisire maggiori informazioni per ridurre l’incertezza.

Il processo di sviluppo è rappresentato come una spirale piuttosto che come una sequenza. Ogni ciclo nella spirale è una fase del processo. Al termine di ogni “giro” il risultato può essere un progetto, un prototipo, un sistema funzionante oppure un prodotto software completo. Non ci sono fasi predefinite: sta al management del progetto decidere come strutturarlo in fasi.

Fasi (spicchi della spirale):



1. Comunicazione con il cliente: specificare gli obiettivi e i vincoli di quella fase, identificare i rischi e eventualmente proporre strategie alternative.
2. Pianificazione: definizione delle scadenze e delle risorse.
3. Analisi dei rischi: stimare i rischi tecnici e di gestione.
4. Strutturazione: costruire una o più rappresentazioni del sistema.
5. Costruzione e rilascio: sviluppo effettuato secondo un modello generico (cascata, evolutivo,..).
6. Valutazione da parte del committente: ricevere le reazioni del cliente su quanto prodotto. Nei primi giri si creano idee o proposte, nei successivi prodotti o prototipi.

Vantaggi:



* Concentra l’attenzione sulle possibilità di riuso.
* Concentra l’attenzione sull’eliminazione degli errori.
* Valutazione esplicita dei rischi.
* Adatto allo sviluppo di progetti di grandi dimensioni.
* Interazione con il cliente a ogni giro della spirale.

Svantaggi



* Richiede esperienza nella valutazione dei rischi.
* Errori nella valutazione dei rischi si ripercuotono nelle fasi successive.
* Richiede raffinamenti per un uso generale.

**Rational Unified Process**

Modello ibrido: prende elementi dai vari modelli generici, aiuta i cicli e illustra buone prassi nella specifica e nella progettazione.

Individua tre prospettive:



1. Prospettiva dinamica: mostra le fasi del modello nel tempo.
2. Prospettiva statica: mostra le attività di processo coinvolte.
3. Prospettiva pratica: suggerisce buone prassi da seguire durante il processo.

Consiste di 4 fasi, separate da milestone che possono essere superate solo se lo stato di avanzamento è sufficiente e l’analisi dei rischi soddisfacente. Se non si supera una milestone, o si abortisce il progetto, oppure la fase viene iterata per raffinare il risultato e risolvere il problema.

Fasi:



1. Inception (avvio): comprende le attività di comunicazione con il cliente, di pianificazione e di identificazione dei requisiti. La pianificazione identifica risorse, rischi principali e stabilisce un piano dei tempi per le fasi successive.
2. Elaboration: comprende comunicazione con il cliente e modellazione. Si ampliano gli use case, si espande la rappresentazione dell’architettura e si ricontrolla la pianificazione.
3. Construction: progettare, programmare e testare il sistema.
4. Transition: spostare il sistema dalla comunità di sviluppo al cliente e farlo funzionare nell’ambiente reale.

E’ possibile che prima della fine di una release sia già iniziato il lavoro per il successivo incremento sw. La ciclicità e l’incremento sono supportati sia in ogni fase, sia come intero insieme di fasi.

**Valutazione dei rischi nei vari modelli**

Modello a cascata



* Alto rischio per sistemi nuovi, per problemi di specifica e di progettazione.
* Basso rischio per sviluppo di problemi se la familiarità è già acquisita.

Modello evolutivo, prototipazione



* Basso rischio per nuovi problemi.
* Alto rischio a causa della scarsa visibilità del processo (antieconomico produrre documentazione a ogni iterazione).

Individuazione dei rischi:



* Lista di errori tipici.
* Analisi del piano di sviluppo.
    * Cammini critici.
    * Membri dello staff critici.
    * Consegne critiche.
    * Milestones critiche.
* Analisi requisiti.
* Analisi della progettazione tecnica.
* Analisi di progetti precedenti.
* Sessioni di brainstorming con lo staff, gli utenti finali, i venditori e il management dedicate all’identificazione dei rischi.

Per ciascun rischio:



* Determina la probabilità che esso si verifichi
* Determinare l’impatto
* Determinare le conseguenze: cosa perdiamo se il rischio si verifica?

**Visibilità del processo software**

C’è bisogno di documentazione per poter valutare i progressi nel processo di sviluppo software. Problema: la programmazione dei tempi di consegna dei “deliverables” può non combaciare con i tempi necessari per completare un'attività, la necessità di produrre documentazione vincola l’iterazione del processo e il tempo necessario per approvare i documenti è significativo.

**Metodologie di sviluppo Agile**

I principi su ci si basa una metodologia leggera che segue i punti indicati dall’Agile Manifesto sono quattro:



1. Le persone e le interazioni sono più importanti dei processi e degli strumenti (ossia le relazioni e la comunicazione tra gli attori di un progetto software sono la migliore risorsa del progetto). 
2. È più importante avere software funzionante che documentazione (bisogna rilasciare nuove versioni del software ad intervalli frequenti, e bisogna mantenere il codice semplice e avanzato tecnicamente, riducendo la documentazione al minimo indispensabile).
3. Bisogna collaborare con i clienti al di là del contratto (la collaborazione diretta offre risultati migliori dei rapporti contrattuali).
4. Bisogna essere pronti a rispondere ai cambiamenti più che aderire al progetto (gli sviluppatori dovrebbero essere autorizzati a suggerire modifiche in ogni momento)

**Programmazione estrema**

Il codice è il prodotto, il codice è la documentazione.

Scrivi prima i casi prova e prosegui con la codifica finché questi non sono stati superati.

Punta sempre al progetto più semplice per superare i test. Inizia con il minimo numero di funzioni desiderate e migliora il risultato mano a mano che procede il lavoro.

Lo sviluppo dell’applicazione accompagnato dalla stesura di un piano di lavoro definito e aggiornato a intervalli brevi e regolari dai responsabili del progetto, secondo le priorità aziendali e le stime dei programmatori. I programmatori partecipano attivamente alla pianificazione che coinvolge sia utenti responsabili del progetto sia sviluppatori per stabilire un equilibrio dinamico tra le esigenze di tutti. Gli utenti finali presentano gli obiettivi descrivendo scenari (storie) e gli sviluppatori stimano il tempo necessario a realizzare ogni storia. Le storie vengono ordinate da utenti e responsabili secondo la loro priorità di realizzazione, dopo che ne è stata stimata la rispettiva difficoltà.

La struttura dell’applicazione deve essere la più semplice possibile, l’architettura del sistema deve essere comprensibile da tutte le persone coinvolte nel progetto. Non devono esserci parti superflue o duplicazioni e le parti che compongono il sistema devono essere solo quelle strettamente necessarie alle esigenze correnti.

Ogni funzionalità va sottoposta a verifica, in modo che si possa acquisire una ragionevole certezza della sua correttezza.  I test di sistema sono costruiti sulla base delle storie concordate con il committente. Ogni ristrutturazione o modifica del codice deve mantenere inalterato il risultato dei test già considerati. I test vengono, solitamente, scritti prima della codifica della funzionalità.

Specie dopo molti cambiamenti nel tempo il codice diventa poco maneggevole. I programmatori spesso continuano a utilizzare codice non più mantenibile perché continua a funzionare. Quando stiamo rimuovendo ridondanza, eliminiamo funzionalità non utilizzate e rinnoviamo un design obsoleto, stiamo facendo refactoring. Il refactoring mantiene il design semplice, evita inutili complessità, mantiene il codice pulito e conciso in modo che sia facilmente comprensibile, modificabile e estensibile.


# Verifica e validazione

Vogliamo garantire che il sistema software sia privo di errori e difetti

Implementazione: passaggio da una visione astratta a una implementazione concreta.

È necessario fare test destinati a “demolire” il software realizzato.

**Verifica**: stiamo costruendo il prodotto nel modo giusto? Deve comportarsi come era previsto.

**Validazione**: stiamo costruendo il prodotto giusto? Deve soddisfare quello che l’utente realmente vuole.

**Verifica statica:** analisi di una rappresentazione statica (non implementata) del sistema per individuare i problemi.

**Verifica e validazione dinamici: **osservare il comportamento del prodotto. Richiede l’esistenza di un prototipo eseguibile su cui fare i test. La validazione può essere solo dinamica.

**Testing**: eseguire un programma al fine di scoprire un errore. Viene rivelata la presenza di errori, non la loro assenza. Un test è riuscito se ha scoperto un errore prima ignoto. Requisiti non funzionali non possono essere verificati, solo validati.

Ogni singola prova deve essere riconducibile ai requisiti del cliente. I difetti più gravi sono quelli che impediscono al programma di soddisfare i requisiti. Si testano inizialmente le singole componenti e successivamente i blocchi di componenti fino all’intero sistema. È impossibile provare tutte le possibili esecuzioni del programma. Per essere efficace, il collaudo va fatto da terze parti, non da chi ha scritto il codice.



* **Operabilità**: meglio funziona, meglio può essere collaudato. Il sistema contiene pochi errori e la scarsità di errori non impedisce l’esecuzione dei collaudi.
* **Osservabilità**: ciò che vedi è ciò che collaudi. Input e output sono correlati, stati e variabili sono osservabili durante l’esecuzione.
* **Controllabilità**: quanto più possiamo controllare il sw, tanto più il collaudo può essere automatizzato e ottimizzato. Tutti i dati di output sono generabili mediante opportuno input.
* **Scomponibilità**: i moduli devono essere collaudati separatamente. Il sw è composto da moduli indipendenti che possono essere collaudati da soli.
* **Semplicità**: meno cose ci sono da controllare, più velocemente si svolgono i collaudi.
* **Stabilità**: meno modifiche si apportano, meno situazioni devono essere collaudate.
* **Comprensibilità**: più informazioni abbiamo, più adeguati sono i collaudi che possiamo svolgere.

**White-box testing:** so come è fatto il codice e scrivo dei test che vadano a testare alcune parti di codice secondo le specifiche progettuali. Si progettano dei casi di prova che testino tutti i cammini indipendenti contenuti in ogni modulo e che esaminino la validità di tutte le strutture dati interne. Per cammini indipendenti si intendono i blocchi di codice che vengono eseguiti in base ad una condizione. La misura del numero di cammini indipendenti in un grafo viene definita **complessità ciclomatica** e misura quantitativamente la complessità logica di un programma. Calcolo complessità ciclomatica: V(G) = E - N + 2 (E = lati, N = nodi). È possibile eseguire un **collaudo per condizioni** in cui si analizzano tutte le condizioni logiche di un programma (operatori e variabili booleane, strutture condizionali, espressioni aritmetiche, etc…).

**Black-box testing**: la struttura del codice è sconosciuta, si parte dai requisiti e se ne testano le funzionalità. Si cercano funzioni errate o mancanti, errori di interfaccia, errori nelle strutture dati o nei DB, comportamenti erronei, problemi prestazionali.

**Debugging: **localizzazione e correzioni degli errori.

Quando finisce un collaudo? Risposte:



1. Mai (il cliente continua a farne
2. Quando finiscono le risorse allocate per il testing (tempo, soldi)
3. Quando la probabilità che si verifichi un bug scende sotto una certa soglia.

Strategie di testing:



* Top-down: dall’insieme dei componenti al componente singolo
* Bottom-up: dal componente singolo al sistema generale
* Regressione: si testano incrementi e modifiche
* Stress test: si testa il sistema sovraccaricando
* Smoke-test: si inserisce il collaudo nel corso dello sviluppo del codice (si usa quando ci sono tempi di consegna ristretti)
* Security testing: testare come reagisce il sistema a tentativi di accesso non autorizzati. Testare i meccanismi di protezione costruiti all'interno del sistema. Con tempo e risorse un sistema potrà sicuramente essere bucato. L’obiettivo è rendere oneroso il tempo e il costo per farlo.

Alpha version: gli utenti usano il sistema sotto diretto controllo degli sviluppatori.

Beta version: gli utenti usano il sistema da soli e segnalano errori e problemi individuati.


# Affidabilità

E’ definita come la probabilità che il sistema funzioni senza errori per un dato intervallo di tempo, in un dato ambiente e per un determinato scopo.

Difficilmente si può definirla in modo oggettivo. Richiede il profilo di utilizzo del sistema per essere definito, il profilo di utilizzo definisce il pattern di utilizzo “tipico” del sistema.  Non è significativo specificare l’affidabilità di un sistema interattivo che viene usato in modi diversi, a meno di non specificare questi modi. Bisogna considerare le conseguenze dei fallimenti,  non tutti i fallimenti sono ugualmente gravi: un sistema è percepito inaffidabile se si verifica un fallimento grave. Un fallimento corrisponde a un comportamento a run time inaspettato (ed errato) osservato da un utente del sistema. Un fault è una caratteristica statica del software che causa il fallimento.

L’affidabilità migliora quando si rimuovono i fault che compaiono nelle parti del sistema che sono più frequentemente usate. Rimuovere l’x% di tutti i fault dal software non necessariamente causa un miglioramento dell’x% dell’affidabilità complessiva. 

L’uso di metodi formali per lo sviluppo del sistema può portare ad un sistema maggiormente affidabile, perché consentono di dimostrare che il sistema si comporta in modo conforme ai suoi requisiti. Lo sviluppo di una specifica formale obbliga ad una analisi dettagliata dei requisiti del sistema che può portare a scoprire anomalie ed omissioni. Tuttavia i metodi formali possono anche non migliorare l’affidabilità del sistema. 

Man mano che aumenta l’affidabilità, l’efficienza tende a diminuire. Per rendere un sistema maggiormente affidabile può essere necessario usare del codice ridondante per effettuare controlli a tempo di esecuzione. Spesso l’affidabilità ci interessa più dell’efficienza e sistemi inaffidabili molto semplicemente non vengono usati.

L’affidabilità dell’hw non è la stessa cosa dell’affidabilità del sw, componenti hw guaste possono essere riparati o sostituiti con altre componenti identiche. Il disegno complessivo dell’hw solitamente è corretto, i difetti sono semplicemente causati da logorio. Fallimenti del sw sono causati spesso da problemi di progettazione e in alcuni casi il sistema continua a funzionare più o meno correttamente.

Metriche:



* Probability of failure on demand (POFOD): probabilità che si verifichi un fallimento quando viene fatta una richiesta al sistema.
* Rate of fault occurrence (ROCOF): frequenza con cui accadono comportamenti anomali.
* Mean time to failure (MTTF): tempo medio tra fallimenti.
* Availability (AVAIL): misura quanto è probabile che il sistema sia operativo in un dato istante. Tiene in considerazione i tempi di riparazione/riavvio.

Le misure di affidabilità non tengono in considerazione le conseguenze dei fallimenti.  Fallimenti transienti possono non avere conseguenze gravi, ma altri tipi di guasti possono causare perdita di dati o interruzione del servizio.

I requisiti di affidabilità raramente sono espressi in modo quantitativo e verificabile. Per verificare i requisiti di affidabilità occorre definire un profilo operazionale come parte del collaudo. L’affidabilità è dinamica: in tutte le specifiche di affidabilità legate al codice sorgente non ha senso dire “non più di N fallimenti ogni 1000 righe di codice”.


<table>
  <tr>
   <td>Transienti
   </td>
   <td>Si verificano solo con certi input.
   </td>
  </tr>
  <tr>
   <td>Permanenti
   </td>
   <td>Si verificano per tutti i possibili input.
   </td>
  </tr>
  <tr>
   <td>Recuperabili
   </td>
   <td>Il sistema può ripartire senza interventi esterni.
   </td>
  </tr>
  <tr>
   <td>Non recuperabili
   </td>
   <td>L’operatore deve intervenire per far ripartire il sistema.
   </td>
  </tr>
  <tr>
   <td>Non corruttivi
   </td>
   <td>Il fallimento non causa corruzione di dati o dello stato del sistema.
   </td>
  </tr>
  <tr>
   <td>Corruttivi
   </td>
   <td>Il fallimento corrompe dati e/o lo stato del sistema.
   </td>
  </tr>
</table>


Usiamo il numero di difetti che vengono scoperti durante la fase di test per fare una predizione sull’affidabilità. In questo senso i casi di prova devono essere scelti in accordo con il profilo operazionale del sistema, non per individuare il maggior numero di errori. 

Generazione del profilo operazionale:

Un insieme di dati di input la cui frequenza si accorda con un uso normale del sistema. Possono essere dati reali raccolti da un sistema esistente o (più spesso) dipendono da assunzioni fatte riguardo l’uso. Se possibile dovrebbe essere generato automaticamente,  può essere difficile per sistemi interattivi, può essere difficile per sistemi nuovi o innovativi: non si sa come verranno usati di preciso. Più facile trovare gli input normali, meno facile individuare gli input improbabili.

Come programmare un software affidabile:



* Fault avoidance: il sistema viene sviluppato in modo da non contenere errori.
* Fault detection: il processo di sviluppo del software è strutturato in modo tale che gli errori sono individuati e corretti prima di consegnare il sistema al cliente.
* Fault tolerance: il software è scritto in modo tale che eventuali errori non necessariamente causano un fallimento totale del sistema.

**Fault avoidance:**

Il software è esente da errori quando è conforme alle specifiche, non significa software che si comporta sempre correttamente, dato che le specifiche stesse possono contenere errori. Il costo di produrre sw privo di errori è molto alto e conviene solo in alcune situazioni. Può risultare economicamente più conveniente sopportare le conseguenze dei fallimenti.



1. Usare programmazione non strutturata (no goto)
2. Attenzione a:
    1. Numeri in virgola mobile
    2. Puntatori
    3. Allocazione dinamica della memoria
    4. Parallelismo
    5. Ricorsione
    6. Interrupts
3. Usare information hiding: le informazioni devono essere rese disponibili solo alle parti del programma che ne hanno effettivamente bisogno. Si riduce la probabilità di modificare “accidentalmente” le informazioni.

**Fault tolerance:**

In situazioni critiche il sistema software deve tollerare i fallimenti ovvero continuare a funzionare a dispetto di errori software.

Il sistema deve:



* Rilevare il guasto: rendersi conto del fallimento.
* Valutare il danno: quali parti del sistema sono affette.
* Recuperare il guasto: ripristinare lo stato a un valore stabile e corretto.
* Riparare il guasto: il sistema deve essere modificato in modo che il guasto non si ripeta in futuro.

Rilevazione



* Rilevazione di guasto preventiva: comincia prima che il cambiamento di stato sia committed: se si rileva un errore, il cambiamento di stato non avviene.
* Rilevazione di guasto retrospettiva: comincia dopo che il sistema ha cambiato stato; si usa se l’altro modo è troppo dispendioso o se è possibile che una sequenza incorretta di azioni corrette comporti uno stato sbagliato.

Recupero



* Recupero preventivo: solo se le informazioni di stato comprendono una ridondanza integrata. Quando i dati codificati sono corrotti: una codifica ridondante permette di accorgersi degli errori e di ripararli. Quando sono corrotte strutture collegate: una struttura dati con puntatori diretti e inversi può essere ricostruita se una quantità sufficiente di puntatori è intatta (vedi filesystem, db, ...). 
* Recupero inverso: più semplice, ripristina lo stato sicuro dopo che è stato individuato un errore.


# UI Design

**Controllo nelle mani dell’utente**

Ci sono tre regole d’oro per la progettazione di una interfaccia utente:

1. lascia che il controllo sia nelle mani dell’utente.

2. limita la necessità per l’utente di usare la propria memoria.

3. usa una interfaccia uniforme per tutta l’applicazione.

Bisogna definire la modalità di interazione in modo da non costringere l’utente ad azioni inutili o indesiderate, inoltre il sistema deve offrire sempre una interazione flessibile.

Ogni azione deve poter essere interrotta o annullata, bisogna anche prevedere modalità d’uso abbreviate (macro o altro) per utenti esperti se serve svolgere ripetutamente certe azioni.

All’utente casuale non serve sapere i dettagli tecnici quindi di buona norma è meglio nasconderli per di più non c’è ragione per cui un utente debba conoscere dettagli interni,

o digitare comandi del sistema operativo della macchina.

Progetta il sistema in modo che consenta la manipolazione diretta degli oggetti che compaiono sullo schermo.

L’utente “sente” di essere in controllo se può manipolare quello che gli serve come se fosse un oggetto fisico.

**Limitare il ricorso alla memoria**

Bisogna tenere in considerazione che più cose deve ricordare l’utente, maggiori saranno le probabilità di errore nelle interazioni col sistema quindi bisogna non fare molto affidamento sulla memoria dell’utente(memoria a breve termine) per cui bisogna ridurre la necessità di usare la memoria a breve termine dell’ utente.

per ridurre l’accesso alla memoria utente si può fare:



* Se operazione complessa, la UI dovrebbe ridurre la necessità di ricordare le azioni fatte e i risultati ottenuti finora.
* Definire delle impostazioni predefinite di validità generale che dovrebbero essere adatte per l’uso medio, ma anche per poter essere modificate (e resettate).
* Definire scorciatoie intuitive(short-cut mnemonico associato all’operazione).
* L’aspetto visivo della UI deve essere una metafora del mondo reale (l’utente “sfrutta” operazioni già note e si orienta rapidamente).
* Fornire le informazioni in modo progressivo cioè  le informazioni relative a un’operazione, un oggetto, ... devono partire da un alto livello di astrazione e raffinare quando l’utente manifesta il suo interesse.
1. Elaborazione delle operazioni:
    1. Capire come digitalizzare le operazioni che venivano fatte a mano
    2. Individuare i punti chiave delle operazioni e renderle più efficienti e veloci
2. Elaborazione degli oggetti:
    3. Si pensa agli use cases e ne si deducono gli oggetti con cui si ha a che fare
    4. Si catalogano gli oggetti in classi
3. Analisi del workflow
4. Creazione gerarchia di operazioni

**Problemi di design**

Tempi di risposta in termini di durata e variabilità rispetto agli standard.

**Sistema di Help**



* Integrato
* Manuale esterno

Deve essere completo, bisogna definire come l’utente vi accede, come si presenta, come si esce e come si organizzano le informazioni. Si possono usare question mark, popup etc etc..

**Messaggi di errore**

Devono essere corti e comprensibili da un utente non informatico. Deve poter dare consigli all’user su come risolverlo. Non deve colpevolizzare l’utente o essere troppo invasivi.

**Menu e comandi**

Deve essere possibile usare il programma sia da riga di comando che tramite finestre. I menù devono spiegarsi da soli ed essere coerenti con le funzionalità che ospitano. 

**Accessibilità e internazionalizzazione**

Facilitare l’utilizzo ad utenti con difficoltà o stranieri. Le lingue non cambiano solo per caratteri e parole ma anche per logica di lettura, il programma deve essere coerente con la lingua che parlano gli utenti.

**Presentazione delle informazioni**

Stabilire che tipo di informazioni ha bisogno l'utente, il grado di precisione e la modalità in cui vengono presentate. Bisogna capire quale significato hanno le informazioni per l’utente e facilitarne la comprensione.
