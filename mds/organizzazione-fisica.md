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

- **Caratteristiche**
    - un database è un insieme di file
    - ogni file può essere visto come collezione di _pagine_
    - ogni pagina contiene dei _record_
    - ogni record consiste in un _insieme di campi_

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
        - ricerca binaria: $\left \lceil \log_2\left(\#BlocksInIndex\right) \right \rceil + 1$ rba
            - $\#BlocksInIndex \lt \lt \#Blocks$
            - il $+1$ è dato dal tempo di accesso al file principale
- **Lista di dati**
    - non le abbiamo fatte, kek direi

## B-tree

- **Struttura**
    - un B-tree è una generalizzazione di un albero binario, in cui ogni nodo è una collezione, ordinata in ordine crescente o decrescente, di sequenze $p, k$, dove $p$ è un puntatore ad un figlio e $k$ è una chiave
    - in particolare, si ha $(p, k, \ldots, p, k, p)$, dunque un B-tree con $M$ vie avrà $M$ puntatori ed $M - 1$ chiavi
        - avendo $\ldots, k_{i - 1}, p_i, k_i, \ldots$, allora $p_i$ punterà al figlio che avrà i valori compresi tra $k_{i -1}$ e $k_i$
- **Caratteristiche**
    - l'albero è sempre bilanciato, dunque le foglie sono tutte sempre allo stesso livello, e ogni nodo è pieno almeno per $\dfrac{M}{2}$ slot (ad eccezione della radice)
        - questo implica che una ricerca, nel caso peggiore, implicherà la visita completa dell'albero in altezza, e dunque il costo dell'algoritmo di ricerca è maggiorabile con $cost \le h$, dove $h$ è l'altezza dell'albero
        - tecnicamente, si avrebbe $h - 1$ a sinistra della disequazione, per via del fatto che la radice è salvata nella RAM, che permette un accesso particolarmente veloce, ma tale fattore è controbilanciato con $h - 1 + 1$ fornito dal tempo di accesso al file dei dati, nel caso in cui si utilizza una struttura di file sequenziale indicizzato
    - $N$: numero di nodi nell'albero
    - $m$: numero massimo di figli che un nodo può avere
        - $m$ dovrebbe essere scelto in modo da far combaciare la massima lunghezza del nodo con la dimensione di un blocco del disco
        - **caro lettore, ti faccio notare che questa definizione di $m$ è inconsistente con quello che c'è scritto dopo, io ho solamente ricopiato quel che c'era scritto nelle slide ma nessuno è stato in grado di capire cosa il professore intendesse davvero**
    - $d := \left \lceil \dfrac{m}{2} \right \rceil$, minimo numero di figli che un nodo può avere
    - $N = m ^{h +1} - 1$, quando l'albero ha ogni nodo riempito
    - $h_{min}=\left\lceil \log_m(N + 1) - 1 \right\rceil$
    - $h_{max}=\left\lfloor \log_d\left(\dfrac{N + 1}{2}\right) \right\rfloor$
    - il numero di entry di un nodo può variare in $[d; 2d]$
        - $2d$ prende il nome di _ordine dell'albero_
    - il numero di nodi figli che ogni nodo ha è pari a $m + 1$, e in particolare varia in $[d + 1; 2d + 1]$
    - $b_{max}$: raggiunto quando ogni nodo dell'albero ha $2d + 1$ nodi figli
    - $b_{min}$: raggiunto quando ogni nodo dell'albero ha $2d$ nodi figli
        - **nelle slide non è stato specificato cosa $b_{min}$ e $b_{max}$ siano**
    - $b_{max} = \displaystyle \sum_{i = 0}^{h - 1}{(2d + 1)^i} = \dfrac{(2d + 1)^h - 1}{2d}$
    - $b_{min} = \displaystyle 1 + 2 \sum_{i = 0}^{h - 2}{(d + 1)^i} = 1 + 2 \dfrac{(d + 1)^{h - 1} - 1}{d}$
    - $N_{max}$: massimo numero di nodi
    - $N_{max}$: minimo numero di nodi
    - $N_{max} = 2d \cdot b_{max} = (2d + 1)^h - 1$
    - $N_{min} = 1 + d(b_{min} -1) = 2(d + 1)^{h - 1} -1$
    - allora $N_{min} \le N \le N_{max} \iff (2d + 1)^h - 1 \le N \le 2(d + 1)^{h - 1} -1 \iff \left\lceil \log_{2d + 1}(N + 1) \right\rceil \le h \le \left\lfloor \log_{d + 1}\left(\dfrac{N +1}{2}\right) \right\rfloor +1$
    - $\textrm{get}(k): O(h)$ (al massimo $h$ accessi al disco)
    - $\textrm{put}(k): O(h)$ (al masimo $3h + 1$ accessi al disco)
    - $\textrm{remove}(k): O(h)$ (al masimo $3h$ accessi al disco)
- **Misc**
    - i B-tree possono essere utilizzati come metodo di organizzazione del file principale
        - al posto di puntatori, i nodi contengono **QUALCOSA CHE NON ABBIAMO CAPITO**

## B<sup>+</sup>-tree

- **Caratteristiche**
    - solo le foglie contengono i puntatori ai dati
        - tutte le chiavi presenti in nodi non foglie sono ripetuti nelle foglie, di modo che ogni chiave sia in almeno un nodo foglia, col corrispettivo puntatore ai dati
        - generalmente l'altezza è minore di un B-tree
    - ogni nodo ha un puntatore che punta a suo fratello
- **Caratteristiche**
    - generalmente sono più performanti dei B-tree, per via delle loro caratteristiche

## Formulario

- **ISAM** (indexed sequential access memory)
    - **Definizioni**
        - $\#Records$: numero di records del file principale
        - $\#Blocks$: numero di blocchi del file principale
        - $\#RecordsPerBlock$: numero di record in ogni blocco del file principale
        - $\#KPs = \#Blocks$: numero di coppie chiave-puntatore nel file index, sempre pari a $\#Blocks$
        - $\#BlocksInIndex$: numero di blocchi del file index
        - $\#KPsPerBlockInIndex$: numero di coppie chiave-puntatore in ogni blocco del file index
        - $\#AccessessForRecord$: numero di accessi necessari per cercare un record nel file principale
        - $\dim(Block) = \dim(BlockInIndex)$: dimensione di un blocco, sia nel file index che nel file principale
        - $\dim(Record)$: dimensione di un record nel file principale
        - $\dim(K)$: dimensione di una chiave del file index
        - $\dim(P)$: dimensione di un puntatore del file index
        - $\dim(KP) = \dim(K) + \dim(P)$: dimensione di una coppia chiave-valore del file index
        - $p\%$: percentuale di capienza massima/minima per blocco del file principale e del file index
    - **Formule**
        - $p\%$ è la capienza _massima_, oppure $p\% = 100\%$
            - $\#RecordsPerBlock = \left \lfloor \dfrac{\dim(Block) \cdot p\%}{\dim(Record)} \right \rfloor$
            - $\#KPsPerBlockInIndex = \left \lfloor \dfrac{\dim(BlockInIndex) \cdot p\%}{\dim(KP)} \right \rfloor$
        - $p\%$ è la capienza _minima_
            - $\#RecordsPerBlock = \left \lceil \dfrac{\dim(Block) \cdot p\%}{\dim(Record)} \right \rceil$
            - $\#KPsPerBlockInIndex = \left \lceil \dfrac{\dim(BlockInIndex) \cdot p\%}{\dim(KP)} \right \rceil$
        - $\#Blocks = \left \lceil \dfrac{\#Records}{\#RecordsPerBlock} \right \rceil$
        - $\#BlocksInIndex = \left \lceil \dfrac{\#KPs}{\#KPsPerBlockInIndex} \right \rceil$
        - ricerca sequenziale
            - $\#AccessessForRecord = \left \lceil \dfrac{\#Blocks}{2} \right \rceil$
        - ricerca binaria
            - $\#AccessessForRecord = \left \lceil \log_2\left(\#BlocksInIndex\right)\right \rceil + 1$
- **B<sup>+</sup>-tree**
    - **Definizioni**
        - $\#Records$: numero di records del file principale
        - $\#Blocks$: numero di blocchi del file principale
        - $\#RecordsPerBlock$: numero di record in ogni blocco del file principale
        - $\#BlocksInIndex$: numero di blocchi del file index
        - $\#ChildrenPerBlockInIndex$: numero di figli per ogni blocco del file index
        - $\#BlocksPer(i)thLevel$: numero di blocchi del file index dell-$i$ livello dell'albero, dove lo $0$-esimo livello sono le foglie
        - $h$: altezza dell'albero del file index
        - $\#AccessessForRecord$: numero di accessi necessari per cercare un record nel file principale
        - $\dim(Block) = \dim(BlockInIndex)$: dimensione di un blocco, sia nel file index che nel file principale
        - $\dim(Record)$: dimensione di un record nel file principale
        - $\dim(K)$: dimensione di una chiave del file index
        - $\dim(P)$: dimensione di un puntatore del file index
        - $\dim(KP) = \dim(K) + \dim(P)$: dimensione di una coppia chiave-valore del file index
        - $p\%$: percentuale di capienza massima/minima per blocco del file principale
    - **Formule**
        - $p\%$ è la capienza _massima_, oppure $p\% = 100\%$
            - $\#RecordsPerBlock = \left \lfloor \dfrac{\dim(Block) \cdot p\%}{\dim(Record)} \right \rfloor$
            - $\#ChildrenPerBlockInIndex = \left \lfloor \dfrac{\dim(Block) \cdot p\% - \dim(P)}{\dim(KP)} \right \rfloor + 1$
        - $p\%$ è la capienza _minima_
            - $\#RecordsPerBlock = \left \lceil \dfrac{\dim(Block) \cdot p\%}{\dim(Record)} \right \rceil$
            - $\#ChildrenPerBlockInIndex = \left \lceil \dfrac{\dim(Block) \cdot p\% - \dim(P)}{\dim(KP)} \right \rceil + 1$
        - $\#Blocks = \left \lceil \dfrac{\#Records}{\#RecordsPerBlock} \right \rceil$
        - $\#BlocksPer(0)thLevel = \#Blocks$
        - $\#BlocksPer(i)thLevel = \left \lceil \dfrac{\#BlocksPer(i-1)thLevel}{\#ChildrenPerBlockInIndex} \right \rceil$
        - $\#BlocksPer(h - 1)thLevel = 1$
        - $\#BlocksInIndex = \displaystyle \sum_{i = 0}^{h - 1} {\#BlocksPer(i)thLevel}$
        - $\#AccessessForRecord = h$
