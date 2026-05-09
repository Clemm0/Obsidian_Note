# Studiare per la prossima lezione
- ## Le basi di dati
	- Definizione basi di dati & differenza da archivi normali
	- Differenza dato & informazione
	- Integrità, Consistenza (Ridondanza, Incongruenza, Inconsistenza)
	- La definizione di DMBS & RDBMS
	- Basi di dati distribuite
		- Maggiore sicurezza & facilitare sistemazioni
		- Collegamento con sistemi e reti
	- DBAdmin
	- Limiti con gli archivi tradizionali
	- Organizzazione di archivi tramite basi di dati
		- Linguaggi usati
		- Facili interrogazioni e aumentata velocità di accesso
	- Modelli per i DB
	- Fasi di progettazione di una base di dati
	- Gli utenti dei DB
	- Concetto di transazioni
		- Proprietà ACID
- ## 5D-01 
	- Introduzione alle basi di dati
	- Sistema informatico e sistema informativo
	- Dati e informazioni
	- Differenza tra istanza e schema di una tabella
		- Istanza -> cambia spesso
		- Schema -> cambia raramente
	- Il DBMS
	- Livelli di astrazione dei DBMS
	- Progettazione di una base di dati
- ## 5D-02 Diagrammi E/R 
	- Creazione E/R
	- Cardinalità/Partecipazione
	- Smontare associazioni ternarie in binarie
- ## 5D-03 Gerarchie di entità 
	- Gerarchie
- ## 5D-04 Associazioni riflessive o ricorsive 
	- Associazioni riflessive
# Studiare quanto possibile
- ## 5D-05a Modello logico relazionale 
- ## 5D-05b Modelli logici gerarchico, reticolare, a oggetti
- ## 5D-06 Trasformazione E/R in tabelle
- ## 5D-07 Vincoli di integrità
- ## 5D-08 Normalizzazione
	- Forme normali
	- Prima forma normale
	- Seconda forma normale
	- Terza forma normale
- ## 5D-09 DDL
- ## 5D-10 DML
- ## 5D-11 QL

# Testo Integrale
## Discorso Approfondito: L'Architettura e la Gestione dei Dati nell'Era Digitale
Oggi ci immergeremo nel cuore pulsante di ogni sistema informativo moderno: le **basi di dati**. Non si tratta solo di un "posto dove mettere i dati", ma di un ecosistema complesso e affascinante, progettato per risolvere problemi secolari legati all'archiviazione e, cosa più importante, alla *fruizione* dell'informazione. Partiremo dai fondamenti, analizzeremo l'architettura, i modelli, le figure professionali e le tecnologie che rendono tutto ciò possibile.

### 1. Dalla Materia Grezza all'Oro: Dato vs. Informazione
Prima di parlare di database, dobbiamo fare una distinzione filosofica e pratica: quella tra **dato** e **informazione**.
-   Il **dato** è la rappresentazione grezza, simbolica, decontestualizzata di un fatto. È la cifra "35", la stringa "Mario Rossi", il booleano "vero". Da solo, il dato non comunica significato.
-   L'**informazione** è il risultato dell'elaborazione e dell'interpretazione del dato, inserito in un contesto che gli conferisce senso e valore.
La lista `[35, 35, 42, 35]` è un insieme di dati. Ma se vi dico che si tratta delle "età dei candidati per il ruolo di DBA" e che la "media è 36.7", quei numeri si trasformano in un'informazione utilizzabile per una decisione gestionale. Il database è la macchina che facilita proprio questa trasformazione, organizzando il caos dei dati in informazioni strutturate.

### 2. Il Superamento degli Archivi Tradizionali: Perché un Database?
Per decenni, i sistemi informativi si sono basati su **archivi tradizionali** (file system, come file CSV o di testo). L'approccio era semplice: ogni applicazione gestiva i propri file. Con la crescita dei volumi e la complessità delle relazioni, questo modello ha mostrato i suoi limiti intrinseci, che un database moderno supera brillantemente:

| Caratteristica                   | Limite degli Archivi Tradizionali                                                                                      | Soluzione delle Basi di Dati                                                                                                                             |
| :------------------------------- | :--------------------------------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ridondanza**                   | Gli stessi dati (es. indirizzo di un cliente) sono duplicati in più file.                                              | Vengono **normalizzati**, evitando duplicazioni non necessarie.                                                                                          |
| **Incongruenza / Inconsistenza** | Conseguenza diretta della ridondanza. Se l'indirizzo cambia in un file ma non in un altro, il dato diventa incoerente. | La struttura centralizzata e le relazioni rendono l'informazione unica e sempre aggiornata.                                                              |
| **Isolamento dei Dati**          | I dati sono sparsi in formati diversi (PDF, TXT, XLS), rendendo difficili le interrogazioni complesse.                 | Si utilizza un unico linguaggio standard (SQL) per interrogare l'intero patrimonio informativo.                                                          |
| **Integrità debole**             | Non esistono meccanismi automatici per garantire che un dato sia corretto (es. un'età negativa).                       | Si definiscono **vincoli di integrità** (entità, referenziale) che il DBMS impone a ogni modifica.                                                       |
| **Accesso concorrente**          | Se due utenti modificano lo stesso file, l'ultimo salvataggio annulla il primo (perdita di aggiornamenti).             | Viene gestito tramite il meccanismo delle **transazioni** e l'**isolamento**.                                                                            |
| **Sicurezza**                    | La sicurezza è delegata al file system dell'OS, con controlli grossolani (lettura/scrittura).                          | Il DBMS offre una **sicurezza granulare** (fino al livello di colonna o di riga) e meccanismi di autorizzazione tramite ruoli e permessi (GRANT/REVOKE). |

### 3. Il Cuore del Sistema: DBMS e RDBMS
Il software al centro di questo ecosistema è il **DBMS (Database Management System)**. Non è il database in sé (che è invece l'insieme strutturato di dati), ma il motore che lo governa. Un DBMS deve offrire funzioni fondamentali: definizione dei dati (DDL), manipolazione (DML), controllo dell'accesso concorrente, gestione della sicurezza, backup e recovery.
Il modello più diffuso e maturo è quello **Relazionale (RDBMS)** , proposto da E.F. Codd negli anni '70. Un RDBMS organizza i dati in **tabelle (relazioni)** , composte da **tuple (righe)** e **attributi (colonne)** , e gestisce le connessioni logiche tra queste tabelle tramite **chiavi primarie (PK)** e **chiavi esterne (FK)**.

### 4. L'Evoluzione Distribuita: Quando un Server Non Basta
Quando il volume dei dati supera i 500 TB o si necessita di operazioni globali, l'architettura centralizzata mostra i suoi limiti: colli di bottiglia, rischio di singolo punto di guasto e latenza per utenti geograficamente distanti. E qui entrano in gioco le **basi di dati distribuite**.
Un database distribuito è un singolo database logico i cui dati sono fisicamente ripartiti (*partizionati* o *shardati*) su più nodi di calcolo, spesso in diverse regioni geografiche.
- **Vantaggi:**
    - **Scalabilità Orizzontale:** Per aumentare la capacità, si aggiungono nodi *commodity*, non si potenzia un super-server. È più economico e lineare.
    - **Alta Disponibilità e Disaster Recovery:** Se un data center va in fiamme, il sistema continua a funzionare. Architetture **multi-master** o **multi-active** garantiscono tempi di ripristino (RTO) prossimi allo zero e perdita di dati (RPO) assente.
    - **Località dei Dati:** I dati possono essere posizionati geograficamente vicino agli utenti che li usano di più, riducendo la latenza.
    - **Tolleranza ai Guasti:** Protocolli come **Paxos** o **Raft** garantiscono la consistenza dei dati anche se alcuni nodi falliscono.
- **La Grande Sfida:** Mantenere la **consistenza** . Garantire che una transazione che coinvolge nodi in continenti diversi sia atomica è complesso. Il teorema **CAP (Consistency, Availability, Partition tolerance)** ci ricorda che in caso di partizione di rete, bisogna scegliere un compromesso. Per questo nascono i database **NewSQL** o **Distribuiti SQL** che tentano di offrire ACID anche su scala globale.

### 5. Il Guardiano dei Dati: Il Database Administrator (DBA)
Gestire queste architetture richiede una figura altamente specializzata: il **Database Administrator (DBA)** . Il DBA non è un semplice "tecnico", ma un professionista strategico. Le sue responsabilità tipiche includono:
- **Installazione e Configurazione:** Setup del software DBMS (Oracle, PostgreSQL, SQL Server) su piattaforme on-premise o cloud.
- **Gestione della Performance (Tuning):** Monitoraggio delle query lente, creazione di **indici** (B-Tree, Hash, Bitmap) per accelerare l'accesso, ottimizzazione del piano di esecuzione delle query.
- **Sicurezza e Permessi (Authorization):** Creazione di utenti e ruoli, assegnazione di privilegi granulari (`SELECT`, `INSERT`, `UPDATE`, `DELETE` su specifiche tabelle o viste).
- **Backup e Recovery:** Definizione e implementazione di strategie di backup (full, incrementale, differenziale) e di piani di ripristino in caso di disastro (`PITR` - Point-In-Time Recovery).
- **Automazione (Scripting):** Automazione di task ripetitivi (backup, monitoraggio, refresh di ambienti di test) tramite script (Shell, Python, SQL procedurale).
- **Gestione delle Transazioni e Concorrenza:** Monitoraggio dei lock e dei deadlock, definizione dei livelli di isolamento delle transazioni.
### 6. Progettare l'Informazione: I Tre Livelli di Astrazione
Costruire un database funzionante non è improvvisazione, ma segue un processo di ingegneria che si articola in tre livelli fondamentali:
1.  **Progettazione Concettuale (Alta Astrazione):** In questa fase, siamo completamente indipendenti dalla tecnologia. Usiamo un linguaggio grafico come il **Modello Entità-Relazione (E/R)** per disegnare il mondo reale. Identifichiamo le **entità** ("Studente", "Corso", "Docente"), i loro **attributi** (Matricola, Nome, CFU) e le **relazioni** ("Iscrizione", "Insegnamento"). Si definiscono le **cardinalità** (quanti corsi può seguire uno studente? 0,N). Qui si gestiscono anche concetti avanzati come le **Gerarchie di entità** (specializzazione/generalizzazione, ad es. "Persona" è supertipo di "Studente" e "Docente") e le **Associazioni riflessive** (una relazione che un'entità ha con se stessa, ad es. "Dipendente" **è capo di** "Dipendente").
2.  **Progettazione Logica (Indipendente dal DBMS):** Traduciamo il modello E/R in uno **schema relazionale** (tabelle, chiavi primarie, chiavi esterne). Applichiamo le **forme normali** (1NF, 2NF, 3NF, BCNF) per eliminare ridondanze e anomalie di aggiornamento. Il risultato è una serie di istruzioni DDL (CREATE TABLE) standard.
3.  **Progettazione Fisica (Dipendente dal DBMS specifico):** È il livello più basso e tecnico. Decidiamo *come* implementare lo schema logico su uno specifico motore (es. Oracle vs. MySQL vs. PostgreSQL). Qui si scelgono:
    - I **tipi di dati** specifici.
    - La creazione di **indici** (B-tree, hash, full-text).
    - Le strategie di **partizionamento** dei dati su più dischi.
    - I **parametri di memoria** (buffer pool, cache).
    - Le **viste materializzate** per accelerare le interrogazioni complesse.
### 7. Il Linguaggio Universale: SQL (Structured Query Language)
L'SQL è il coltellino svizzero dei dati. È un linguaggio dichiarativo: tu dici *cosa* vuoi, e il DBMS decide *come* ottenerlo. Si divide in diversi sottolinguaggi:
- **DDL (Data Definition Language):** Crea e modifica la struttura (`CREATE`, `ALTER`, `DROP`).
- **DML (Data Manipulation Language):** Gestisce i dati dentro le strutture (`INSERT`, `UPDATE`, `DELETE`, `SELECT`). La `SELECT` è la regina delle interrogazioni, capace di fare join, filtri, aggregazioni (`GROUP BY`, `HAVING`) e sottoquery.
- **DCL (Data Control Language):** Gestisce i permessi (`GRANT`, `REVOKE`).
- **TCL (Transaction Control Language):** Gestisce le transazioni (`BEGIN`, `COMMIT`, `ROLLBACK`).
### 8. L'Atomo dell'Elaborazione: La Transazione ACID
Nel mondo dei database, un'operazione di modifica raramente è un singolo passo. Spesso è una sequenza di operazioni che, per avere senso logico, devono riuscire tutte o fallire tutte. Questa unità logica è chiamata **transazione**. L'affidabilità di una transazione è garantita dalle proprietà **ACID**:
- **Atomicità:** *"Tutto o niente"*. Se un bonifico consiste nel "prelevare da conto A" e "accreditare su conto B", e il sistema si blocca dopo il primo passo, il DBMS deve annullare (*rollback*) automaticamente il prelievo, riportando il sistema allo stato precedente.
- **Consistenza:** La transazione porta il database da uno stato valido a un altro stato valido, rispettando tutti i vincoli (es. la somma dei saldi dopo il bonifico è identica a prima). La consistenza è anche responsabilità dell'applicazione, che deve implementare la logica corretta.
- **Isolamento:** Quando centinaia di utenti operano contemporaneamente, le loro transazioni non devono "vedersi" a vicenda finché non sono completate. Per esempio, mentre calcoli la media dei saldi, un contemporaneo bonifico in corso non deve falsare il risultato. I DBMS offrono diversi livelli di isolamento (Read Uncommitted, Read Committed, Repeatable Read, Serializable) come compromesso tra correttezza e performance.
- **Durabilità:** Una volta che il `COMMIT` (conferma) viene dato, la modifica è persistente e sopravvive a qualsiasi guasto immediato (blackout, crash del sistema). Il dato è "al sicuro" su disco.
### 9. Un Mondo di Utenti
Il database non vive in un vuoto. Interagisce con diverse figure:
- **Utenti Naive (o Parametrici):** Sono la maggioranza. Interagiscono con il database tramite interfacce standardizzate (es. il sito delle prenotazioni, il bancomat). Non scrivono mai codice SQL diretto.
- **Utenti Esperti (o Power User):** Interagiscono direttamente con il DBMS tramite shell o tool interattivi (DBeaver, pgAdmin) scrivendo query SQL complesse per l'analisi.
- **Programmatori di Applicazioni:** Sviluppano software in linguaggi come Java, Python o C# che, tramite driver (JDBC, ODBC), incorporano codice SQL per dialogare con il database.
- **DBA (Database Administrator):** Il supervisore e custode del sistema, come descritto sopra.