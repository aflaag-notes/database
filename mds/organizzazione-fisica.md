# Organizzazione fisica

## Gerarchia fisica

- Memoria primaria 
    - caratteristiche
        - volatile
        - costosa
        - veloce
        - dimensione minore
        - contiene codice runtime delle applicazioni e il DBMS
    - composta da
        - Registri della CPU
            - operazioni matematice e logiche
        - Cache ad alta velocità
            - opera quasi alla stessa velocità della CPU
        - Memoria principale
            - RAM
- Memoria secondaria
    - caratteristiche
        - non volatile
        - relativamente economica
        - lenta
        - dimensione maggiore
        - contiene file fisici del database
    - composta da
        - HDD/SSD
            - basati sulla memoria flash
        - Disco ottico

## HDD

- Caratteristiche
    - contiene un hard disk controller
    - è di storage direttamente accessibili (DASDs)
- Organizzazione
    - è composto da piatti/dischi circolari, divisi in settori
    - ogni settore è diviso in blocchi
    - ogni piatto circolare è ricoperto da particelle magnetiche, ed è posto su un perno centrale che ruota a velocità costante
    - l'attuatore, un perno verticale, esegue un movimento orizzontale che permette ai bracci meccanici, posti sull'attuatore perpendicolarmente, di far raggiungere le testine di lettura e scrittura sulle tracce dei piatti
    - **seek time**: tempo di posizionamento delle teste sulla traccia corretta
    - **rotational delay**: tempo di attesa per far ruotare il disco desiderato nel settore di memoria voluto
    - **transfer time**: tempo di trasferimento dei dati, che dipende dalla dimensione del blocco, dalla densità delle particelle magnetiche e dalla velocità di rotazione dei dischi
    - **service time**: seek time + rotation delay + transfer time
    - **queueing time**: ⚠️ NON L'HA DETTO/SCRITTO
    - **response time**: service time + queueing time
    - **transfer rate**: numero di blocchi trasferiti al secondo
    - **rotation time**: ⚠️ NON L'HA DETTO/SCRITTO, forse è uguale
    - **block size**: dimensione di un blocco
    - $t_{rba}$: seek time + rotation time / 2 + block size / transfer rate
        - RBA: random block access
        - tempo per ottenere/scrivere un blocco del disco, indipendentemente dalla scrittura/lettura precedente
    - $t_{sba}$: rotation time / 2 + block size / transfer rate
        - SBA: sequential block access
        - tempo per ottenere sequenzialmente un blocco dal disco con la testina di lettura/scrittura già correttamente posizionata

## Database fisico

⚠️ SLIDE 14 (mesa che è tipo tutto ovvio)

- Caratteristiche
    - un database è un insieme di file
    - ogni file può essere visto come collezione di **pagine**
    - ogni pagina contiene dei **record**
    - ogni record consiste in un **insieme di campi**

## Metodi di organizzazione del file principale

- **File heap**
    - nuovi record aggiunti alla fine del file
    - non c'è relazione tra gli attributi dei record e la loro posizione fisica
    - l'unico metodo di ricerca disponibile è la ricerca lineare
    - in media, è necessario controllare $\dfrac{\#Blocks}{2}$ blocchi per trovare un determinato record tramite una chiave di ricerca univoca
    - è necessario controllare $\#Blocks$ blocchi per una chiave di ricerca non univoca
- **File sequenziale**
    - i record sono salvati in ordine crescente/decrescente di chiave di ricerca
    - è possibile usare la ricerca binaria per trovare il record desiderato utilizzando una chiave di ricerca univoca
    - ricerca lineare: $\dfrac{\#Blocks}{2}$ sba
    - ricerca binaria: $\log_2(\#Blocks)$ rba
    - l'aggiornamento del file va eseguito più cautamente
- **Hashing**
    - viene stabilita una relazione tra il valore della chiave di ricerca e la locazione fisica del record
    - un record può essere trovato con pochi accessi ai blocchi
    - viene stabilita una trasformazione da chiave a indirizzo, ma non è possibile garantire l'assenza di collisioni con la tabella di hashing, quindi vengono usati dei bucket con gli indirizzi
        - se ci sono più collisioni dello spazio disponibile per un singolo bucket, il bucket va in overflow
    - generalmente, come criterio di hashing si utilizza il modulo $\textrm{address}(k) = k \ (\bmod \ M)$
        - spesso $M$ è un numero primo, leggermente più grande del numero di indirizzi disponibile
        - veranno generati $M$ indirizzi, che vanno da $0$ a $M - 1$
    - per ritornare un record che non si trova in una posizione di overflow è necessario $1$ rba per ottenere il bucket, più almeno $1$ sba
    - per i record in overflow sono necessari ulteriori accessi ai blocchi, che dipende dalla percentuale di record in overflow
        - la percentuale di record in overflow dipende dall'algoritmo di hashing scelto, e dall'insieme di chiavi
        - $\#Buckets = \left\lceil \dfrac{\#Records}{\dim(Bucket) \cdot LF} \right\rceil$
            - $LF$ è il loading factor $\dfrac{\dfrac{\#Records}{\#Buckets}}{\dim(Bucket)}$, $\rm GAC$, ed indica quanto è pieno un bucket mediamente
            - per esso viene generalmente scelto un valore $[0.7; 0.9]$
        - vi sono varie tecniche per gestire l'overflow tra i bucket, ad esempio l'**open addressing** che semplicemente pone il record nel prossimo bucket disponibile
- **File indicizzato sequenziale**
    - combina l'organizzazione sequenziale, aggiungendo degli indici
    - il file viene diviso in partizioni/intervalli/blocchi, in cui ogni partizione rappresenta l'_index entry_
        - chiave di ricerca del primo record nella partizione
        - puntatore alla posizione fisica del primo record della partizione
            - il puntatore può essere sia il _block pointer_, sia il _record pointer_
    - viene creato un file che contiene gli indici che puntano alle partizioni del file principale, contenente i record
    - ogni partizione del file principale viene ordinata secondo una chiave univoca
    - _indicizzazione densa_
        - viene creata un index entry per ogni valore possibile della chiave di ricerca
        - generalmente è più veloce, ma richiede più spazio di memoria
        - sono più complesse da mantenere
    - _indicizzazione sparsa_
        - viene creata un index entry solamente per una parte dei valori possibili della chiave di ricerca
        - ogni entry indicizza un gruppo di record, l'indirizzo punta al primo record di un intervallo
        - ricerca: $\log_2\left(\dfrac{\#Blocks}{\#Indexes}\right)$ rba
- **Lista di dati**
    - non le abbiamo fatte, kek direi


