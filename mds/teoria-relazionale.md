# Teoria relazionale

## Def

- **Dipendenza funzionale**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X, Y \subseteq R(A_1, \ldots, A_n) \mid X, Y \neq \varnothing$
> - $X \rightarrow Y$ è detta **dipendenza funzionale su $R$**
>   - $X$ è detto **determinante**, $Y$ è detto **determinato**
> - $r$ istanza di $R$ **soddisfa** $X \rightarrow Y \iff \forall t_1, t_2 \in R \quad t_1[X] = t_2[X] \implies t_1[Y] = t_2[Y]$

- **Istanza legale**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $r$ **istanza di $R$ legale su $F$** $\iff \forall i \in [1, k] \quad r$ soddisfa $F_i$

## Def

- **Chiusura di un insieme di dipendenze funzionali**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $L = \{r$ istanza di $R \mid r$ legale su $F\}$
> - $F^+ := \displaystyle \bigcap_{r \in L}\{$dipendenze funzionali in $r\}$
>   - ovvero, è l'insieme delle dipendenze funzionali derivabili da ogni istanza legale su $F$
>   - di fatto, ogni istanza legale in $L$ soddisferà ogni dipendenza funzionale in $F^+$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $F \subseteq F^+$

## Oss

- **Hp**
    - $n, k \in \mathbb{n}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X, Y \subseteq R(A_1, \ldots, A_n) \mid Y \subseteq X$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow Y \in F^+$
- **Dim**
    - $\forall r$ istanza di $R$ legale su $F \mid \exists t_1, t_2 \in r : t_1[X] = t_2[X]$, poiché $Y \subseteq X$ si ha necessariamente che $t_1[Y] = t_2[Y]$, allora $t_1[X] = t_2[X] \implies t_1[Y] = t_2[Y] \implies X \rightarrow Y$ è soddisfatta da $r \implies X \rightarrow Y \in F^+$ per definizione di $F^+$

****

# Assiomi di Armstrong

## Def

- **Assiomi di Armstrong**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $F^A$ è l'**insieme delle dipendenze funzionali ottenute partendo da $F$ applicando gli assiomi di Armstrong**
> - $\forall X, Y \subseteq R(A_1, \ldots, A_n) \quad X \rightarrow Y \in F \implies X \rightarrow Y \in F^A$
> - $\forall X, Y \subseteq R(A_1, \ldots, A_n) \quad Y \subseteq X \implies X \rightarrow Y \in F^A$ è detto **assioma della riflessività**
> - $\forall X, Y, Z \subseteq R(A_1, \ldots, A_n) \quad X \rightarrow Y \in F^A \implies XZ \rightarrow YZ \in F^A$ è detto **assioma dell'aumento**
> - $\forall X, Y \subseteq R(A_1, \ldots, A_n) \quad X \rightarrow Y, Y \rightarrow Z \in F^A \implies X \rightarrow Z \in F^A$ è detto **assioma della transitività**

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $F \subseteq F^A$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X, Y, Z \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow Y, X \rightarrow Z \in F^A \implies X \rightarrow YZ \in F^A$ è detta **regola dell'unione**
- **Dim**
    - per aumento $X \rightarrow Z \in F^A \implies XX \rightarrow XZ \in F^A \implies X \rightarrow XZ \in F^A$
    - per aumento $X \rightarrow Y \in F^A \implies XZ \rightarrow YZ \in F^A$
    - allora, per transitività $X \rightarrow XZ, XZ \rightarrow YZ  \in F^A \implies X \rightarrow YZ \in F^A$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X, Y, Z \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow Y \in F^A \land Z \subseteq Y \implies X \rightarrow Z \in F^A$ è detta **regola della decomposizione**
- **Dim**
    - per riflessività $Z \subseteq Y \implies Y \rightarrow Z \in F^A$
    - per transitività $X \rightarrow Y, Y \rightarrow Z \in F^A \implies X \rightarrow Z \in F^A$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X, Y, Z \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow Y, WY \rightarrow Z \in F^A \implies XW \rightarrow Z \in F^A$ è detta **regola della pseudotransitività**
- **Dim**
    - per aumento $X \rightarrow Y \in F^A \implies XW \rightarrow YW \in F^A$
    - per transitività $XW \rightarrow YW, WY \rightarrow Z \in F^A \implies XW \rightarrow Z \in F^A$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $i, j \in [1, n] \mid i \lt j$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $A_i, \ldots, A_j \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow A_i \ldots A_j \in F^A \iff \forall h \in [i, j]\quad X \rightarrow A_h \in F^A$
- **Dim**
    - per regola di decomposizione $X \rightarrow A_i \ldots A_j \in F^A \implies\forall h \in [i, j] \quad X \rightarrow A_h \in F^A$
    - per regola dell'unione $\forall h \in [i, j] \quad X \rightarrow A_h \in F^A \implies X \rightarrow A_i \ldots A_j$

## Def

- **Chiusura di un insieme di attributi**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X \subseteq R(A_1, \ldots, A_n)$
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $X^+_F := \{A \in R(A_1, \ldots, A_n) \mid X \rightarrow A \in F^A\}$ è detta **chiusura di $X$ rispetto ad $F$**
>   - ovvero, è l'insieme degli attributi funzionalmente dipendenti da $X$ attraverso l'applicazione degli assiomi di Armstrong

## Lem

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X, Y \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow Y \in F^A \iff Y \subseteq X^+_F$
- **Dim**
    - siano $i, j \in [1, n], i \lt j \mid Y := A_i \ldots A_j$
    - $X \rightarrow Y \in F^A \iff X \rightarrow A_i \ldots A_j  \in F^A$, allora per dimostrazione precedente $X \rightarrow A_i \ldots A_j \in F^A \iff \forall h \in [i, j] \quad X \rightarrow A_h \in F^A$, allora per definizione di $X^+_F$ si ha che $\forall h \in [i, j] \quad X \rightarrow A_h \in F^A \iff \forall h \in [i, j] \quad A_h \in X^+_F \iff A_i \ldots A_j \subseteq X^+_F \iff Y \subseteq X^+_F$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \subseteq X^+_F$
- **Dim**
    - per assioma della riflessività $X \subseteq X \implies X \rightarrow X \in F^A$
    - allora per lemma precedente $X \rightarrow X \in F^A \implies X \subseteq X^+_F$

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $F^+ = F^A$
- **Dim**
    - $F^+ \supseteq F^A$
        - siano $X, Y \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow Y \in F^A$
        - _caso base_
            - per definizione $F \subseteq F^A$, allora avendo applicato $0$ assiomi di Armstrong $X \rightarrow Y \in F^A \implies X \rightarrow Y \in F$, e per definizione $F \subseteq F^+$, allora necessariamente $X \rightarrow Y \in F^+$
        - _ipotesi induttiva forte_
            - avendo applicato al più $n$ assiomi di Armstrong per ottenere $X \rightarrow Y \in F^A$, si ha che $X \rightarrow Y \in F^+$
        - _passo induttivo_
            - è necessario dimostrare che avendo applicato l'$(n + 1)$-esimo assioma di Armstrong per ottenere $X \rightarrow Y \in F^A$, si ha che $X \rightarrow Y \in F^+$
            - è possibile trovarsi in questa situazione in $3$ possibili casi
            - l'$(n + 1)$-esimo assioma di Armstrong applicato è stato l'assioma della riflessività
                - $X \rightarrow Y \in F^A$ per assioma della riflessività, allora necessariamente $Y \subseteq X$, ma allora $\forall r$ istanza di $R$ legale su $F \quad t_1[X] = t_2[X] \implies t_2[Y] = t_2[Y] \implies X \rightarrow Y \in F^+$
            - l'$(n + 1)$-esimo assioma di Armstrong applicato è stato l'assioma dell'aumento
                - $X \rightarrow Y \in F^A$ per assioma dell'aumento, allora $\exists V, W \subseteq R(A_1, \ldots, A_n) \mid V \rightarrow W \in F^A$, ottenuta applicando al più $n$ assiomi di Armstrong, e $\exists Z \subseteq R(A_1, \ldots , A_n) \mid X := VZ \land Y := WZ$
                - per ipotesi induttiva si ha che $V \rightarrow W \in F^+$, allora $\forall r$ istanza di $R$ legale su $F \quad \exists Z \subseteq R(A_1, \ldots, A_n) \mid VZ \rightarrow WZ \in F^+$, in quanto l'aggiunta di $Z$ rende ancora soddisfatta la dipendenza funzionale
                - $VZ \rightarrow WZ \in F^+ \implies \forall r$ istanza di $R$ legale su $F \quad \forall t_1, t_2 \in r \quad t_1[VZ] = t_2[VZ] \implies t_1[WZ] = t_2[WZ]$
                - allora, poiché si erano posti $X := VZ \land Y := WZ$, si ha che $\forall r$ istanza di $R$ legale su $F \quad \forall t_1, t_2 \in r \quad t_1[X] = t_2[X] \implies t_1[Y] = t_2[Y] \implies X \rightarrow Y \in F^+$ per definizione di $F^+$
            - l'$(n + 1)$-esimo assioma di Armstrong applicato è stato l'assioma della transitività
                - $X \rightarrow Y \in F^A$ per assioma della transitività, allora $\exists Z \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow Z, Z \rightarrow Y \in F^A$, ottenute applicando al più $n$ assiomi di Armstrong
                - allora, per ipotesi induttiva si ha che $X \rightarrow Z, Z \rightarrow Y \in F^+$
                - $X \rightarrow Z \in F^+ \implies \forall r$ istanza di $R$ legale su $F \quad \forall t_1, t_2 \in r \quad t_1[X] = t_2[X] \implies t_1[Z] = t_2[Z]$
                - $Z \rightarrow Y \in F^+ \implies \forall r$ istanza di $R$ legale su $F \quad \forall t_1, t_2 \in r \quad t_1[Z] = t_2[Z] \implies t_1[Y] = t_2[Y]$
                - allora, necessariamente $\forall r$ istanza legale di $R$ su $F \quad \forall t_1, t_2 \in r \quad t_1[X] = t_2[X] \implies t_1[Y] = t_2[Y] \implies X \rightarrow Y \in F^+$ per definizione di $F^+$
    - $F^+ \subseteq F^A$
        - sia $X \subseteq R(A_1, \ldots, A_n)$ e $r$ istanza di $R(X^+_F, R - X^+_F) \mid t_1[X^+_F] = t_2[X^+_F] = (1, \ldots, 1)$, mentre $t_1[R - X^+_F] = (1, \ldots, 1) \land t_2[R - X^+_F] = (0, \ldots, 0)$
            - in particolare $t_1[R - X^+_F]$ è complementare a $t_2[R - X^+_F]$, dunque diverso in ogni colonna
        - $r$ legale su $F \iff \forall V, W \subseteq R(X^+_F, R - X^+_F) \mid V \rightarrow W \in F \quad r$ soddisfa $V \rightarrow W$
        - $\forall V, W \subseteq R(X^+_F, R - X^+_F) \mid V \rightarrow W \in F$ possono verificarsi $3$ possibili casi
            - $V \subseteq R - X^+_F \implies (1, \ldots, 1) = t_1[V] \neq t_2[V] = (0, \ldots, 0)$
            - $V \cap (R - X^+_F) \neq \varnothing \implies \exists A \subseteq V \mid A \subseteq R - X^+_F \implies t_1[V] \neq t_1[V]$ in quanto $t_1[V]$ e $t_2[V]$ sono stati scelti complementari, e dunque diversi in ogni colonna
            - $V \subseteq X^+_F \implies t_1[V] = t_2[V]$ per costruzione di $r$, dunque è necessario controllare che $r$ soddisfi $V \rightarrow W \in F$, e dunque $V \subseteq X^+_F \implies X \rightarrow V \in F^A$ per lemma precedentemente dimostrato, inoltre $F \subseteq F^A \implies V \rightarrow W \in F \implies V \rightarrow W \in F^A$, allora per l'assioma della transitività $X \rightarrow V, V \rightarrow W \in F^A \implies X \rightarrow W \in F^A$, allora per il lemma precedente $W \subseteq X^+_F \implies t_1[W] = t_2[W]$ per costruzione di $r$
        - allora $r$ legale su $R \implies \forall Y \subseteq R(X^+_F, R - X^+_F) \mid X \rightarrow Y \in F^+ \quad r$ soddisfa $X \rightarrow Y \in F^+$
        - per osservazione precedente $X \subseteq X^+_F$, allora $t_1[X] = t_2[X]$ per costruzione di $r$
        - $r$ soddisfa $X \rightarrow Y \in F^+ \implies Y \subseteq X^+_F$ per costruzione di $r$
        - allora per il lemma precedente $Y \subseteq X^+_F \implies X \rightarrow Y \in F^A$

## Alg

- **Input**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Output**
    - $Z = X^+_F$
- **Algoritmo**
    - $Z := X$
    - $S := \{A \in R(A_1, \ldots, A_n) \mid \exists Y, V \subseteq R(A_1, \ldots, A_n), Y \rightarrow V \in F : A \in V \land Y \subseteq Z\}$
    - $\texttt{while}$ $S \nsubseteq Z$$\texttt{:}$
        - $Z = Z \cup S$
        - $S = \{A \in R(A_1, \ldots, A_n) \mid \exists Y, V \subseteq R(A_1, \ldots, A_n), Y \rightarrow V \in F : A \in V \land Y \subseteq Z\}$
- **Oss**
    - l'algoritmo calcola $X^+_F$
    - di fatto, il loop $\texttt{while}$ applica gli assiomi di Armstrong
- **Th**
    - sia $f \mid S^f \subseteq Z^f$, dunque l'iterazione in cui l'algoritmo termina
    - $Z^f = X^+_F$
- **Dim**
    - $Z^f \subseteq X^+_F$
        - _caso base_
            - $Z^0 = X$, per osservazione precedente $X \subseteq X^+_F \implies Z^0 \subseteq X^+_F$
        - _ipotesi induttiva_
            - $Z^i \subseteq X^+_F$
        - _passo induttivo_
            - è necessario dimostrare che $Z^{i + 1} \subseteq X^+_F$
            - sia $A \in Z^{i+1} = Z^i \cup S^i$, allora $A \in Z^i \lor A \in S^i$
            - $A \in Z^i \implies A \in X^+_F$ per ipotesi induttiva
            - $A \in S^i \implies \exists Y, V \subseteq R(A_1, \ldots, A_n), Y \rightarrow V \in F : A \in V \land Y \subseteq Z^i$ per definizione di $S^i$
                - per ipotesi induttiva $Y \subseteq Z^i \subseteq X^+_F$, e per lemma precedente $Y \subseteq X^+_F \implies X \rightarrow Y \in F^A$
                - $Y \rightarrow V \in F \implies Y \rightarrow F^A$, allora $X \rightarrow Y , Y \rightarrow V \in F^A \implies X \rightarrow V \in F^A$, allora per il lemma $X \rightarrow V \in F^A \implies V \subseteq X^+_F$
                - $A \in V \subseteq X^+_F \implies A \in X^+_F$
    - $Z^f \supseteq X^+_F$
        - sia $r$ istanza di $R(Z^f, R - Z^f) \mid t_1[Z^f] = t_2[Z^f] = (1, \ldots, 1)$, mentre $t_1[R - Z^f] = (1, \ldots, 1) \land t_2[R - Z^f] = (0, \ldots, 0)$
        - $r$ legale su $F \iff \forall V, W \subseteq R(Z^f, R - Z^f) \mid V \rightarrow W \in F \quad r$ soddisfa $V \rightarrow W$
        - $\forall V, W \subseteq R(Z^f, R - Z^f) \mid V \rightarrow W \in F$ possono verificarsi $3$ possibili casi
            - $V \subseteq R - Z^f \implies (1, \ldots, 1) = t_1[V] \neq t_2[V] = (0, \ldots, 0)$
            - $V \cap (R - Z^f) \neq \varnothing \implies \exists A \subseteq V \mid A \subseteq R - Z^f \implies t_1[V] \neq t_1[V]$ in quanto $t_1[V]$ e $t_2[V]$ sono stati scelti complementari, e dunque diversi in ogni colonna
            - $V \subseteq Z^f \implies t_1[V] = t_2[V]$, dunque è necessario controllare che $r$ soddisfi $V \rightarrow W \in F$
                - per definizione di $S^f := \{B \in R(A_1, \ldots, A_n) \mid B \in W \land W \subseteq Z^f\}$ ovvero, in $S^f$ sarà interamente contenuto $W$ alla $f$-esima iterazione, e dunque $W \subseteq S^f$
                - poiché il loop **while** continua fintanto che $S^i \nsubseteq Z^i$, allora necessariamente $S^f \subseteq Z^f \implies W \subseteq S^f \subseteq Z^f \implies W \subseteq Z^f \implies t_1[W] = t_2[W]$ per costruzione di $r$
        - allora $r$ legale su $R$
        - per lemma precedente $\forall A \in X^+_F \quad X \rightarrow A \in F^A$, e per dimostrazione precedente $F^A = F^+ \implies X \rightarrow A \in F^+ \implies \forall r'$ istanza legale di $R \quad r'$ soddisfa $X \rightarrow A \in F^+$ per definizione di $F^+$
        - $r$ legale $\implies r$ soddisfa $X \rightarrow A \in F^+$
        - per costruzione dell'algoritmo $X = Z^0 \subseteq Z^f \implies t_1[X] = t_2[X]$ per costruzione di $r$, e poiché $r$ legale si ha che $t_1[A] = t_2[A]$, allora $A \in Z^f$ per costruzione di $r$

## Def

- **Insiemi di dipendenze funzionali equivalenti**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k, G_1, \ldots, G_h$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $G = \{G_1, \ldots, G_h\}$
> - $F \equiv G \iff F^+ = F^+$, e $F$ e $G$ sono detti **equivalenti**

## Oss

- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k, G_1, \ldots, G_h$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $G = \{G_1, \ldots, G_h\}$
- **Th**
    - $F \xrightarrow{A} G \iff G \subseteq F^+$
- **Dim**
    - per definizione $F \xrightarrow{A} G$ implica che è possibile ottenere $G$ a partire da $F$ applicando assiomi di Armstrong
    - per dimostrazione precedente $F^+ = F^A$
    - allora, poiché $G$ deve essere raggiungubile tramite l'applicazione di un certo numero di assiomi di Armstrong (non necessariamente tutti i possibili), si ha che $G \subseteq F^A$
        - applicandoli tutti, si otterrebbe $G = F^A$
    - allora $G \subseteq F^A = F^+$

# Lem

- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k, G_1, \ldots, G_h$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $G = \{G_1, \ldots, G_h\}$
- **Th**
    - $F \subseteq G^+ \iff F^+ \subseteq G^+$
- **Dim**
    - _prima implicazione_
        - per osservazione precedente $F \subseteq G^+ \iff G \xrightarrow{A} F$
        - trivialmente si ha che $F \xrightarrow{A} F^A = F^+$
        - allora $G \xrightarrow{A} F \xrightarrow{A} F^+ \implies G \xrightarrow{A} F^+ \iff F^+ \subseteq G^+$ per osservazione precedente
    - _seconda implicazione_
        - $F^+ \subseteq G^+ \iff F \subseteq F^+ \subseteq G^+ \implies F \subseteq G^+$

