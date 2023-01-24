# Everything

## DISCLAIMER

Questo è un file che contiene una lista di tutti i teoremi, osservazioni, definizioni, esempi, lemmi, corollari, formule e proposizioni **senza alcuna dimostrazione**, di conseguenza molte informazioni risulteranno essere senza alcun contesto se già non si conosce la materia. Detto questo, buona lettura.

****
# Algebra relazionale



## Definizione 1


- **Dominio**

> - $A$ insieme finito o infinito
> - $A$, in algebra relazionale, è detto **dominio**



## Definizione 2


- **Prodotto cartesiano**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $D_1 \times \ldots \times D_n := \{v_1, \ldots, v_n) \mid v_1 \in D_1, \ldots , v_n \in D_n\}$ è detto **prodotto cartesiano dei domini $D_1, \ldots D_n$**



## Definizione 3


- **Relazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots , D_n$ domini
> - $k \in [1, n]$
> - $R \subseteq D_1 \times \ldots \times D_k$ è detta **relazione di grado $k$**
>   - $(t_1, \ldots, t_k) \in R$ è detta **tupla di cardinalità $k$**
>   - $\forall i \in [1, k] \quad (t_1, \ldots, t_k)[i] = t_i$
>   - $\forall a, b \in [1, k] \mid a \lt b \quad (t_1, \ldots, t_k)[a, b] = (t_a, \ldots, t_b)$



## Definizione 4


- **Schema relazionale**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ è detto **schema relazionale**
>   - $R$, in algebra relazionale, è categorizzata tramite **attributi**, denotati con $A_i$, nomi con i quali si etichettano le colonne della tabella, dunque uno schema relazionale è l'insieme delle etichette
>   - $\forall i \in [1, n] \quad \textrm{dom}(A_i) := D_i$ è detto **dominio di $A_i$**
>   - $\forall i \in [1, n] \quad A_i \in \textrm{dom}(A_i)$

- **Istanza di una relazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $k \in [1, n]$
> - $R \subseteq D_1 \times \ldots \times D_k$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $D_1, \ldots , D_k$, l'insieme delle tuple di $R$, è detta **istanza della relazione $R$**

****

# Operazioni



## Definizione 5


- **Proiezione**

- ⚠️ **RISCRIVI**
> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $a, b \in [1, n] \mid a \lt b$
> - $\pi_{A_a, \ldots, A_b}(R) := D_a \times \ldots \times D_b$ è detta **proiezione di $R$**, associata ad uno schema relazionale $R(A_a, \ldots, A_b)$

- **Selezione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $C$ espressione booleana
> - $r$ istanza di $R$
> - $\sigma_C(r) \subseteq D_1 \times \ldots \times D_n$ è detta **selezione di $r$**
>   - corrisponde all'insieme delle righe della tabella che rendono la condizione $C$ vera

- **Rinominazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $R' = \rho_{A_1' \leftarrow A_1}(R)$, dove $\rho$ è detto **operatore di rinominazione**
>   - $R'$ sarà uno schema relazionale con la stessa istanza di $R$, ma con $A_1$ rinominato con $A_1'$

- **Unione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n, D_1' ,\ldots, D_n'$ domini $\mid \forall i \in [1, n] \quad D_i = D_i'$
> - $R_1 \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R_2 \subseteq D_1' \times \ldots \times D_n'$ relazione
> - $R_1(A_1, \ldots, A_n)$ schema relazionale
> - $R_2(A_1', \ldots, A_n')$ schema relazionale
> - $r_1$ istanza di $R_1$
> - $r_2$ istanza di $R_2$
> - $r_1 \cup r_2 := \{t \mid t \in r_1 \lor t \in r_2\}$ è detta **unione delle istanze $r_1$ e $r_2$**
>   - dunque, l'unione di istanze è definita solamente per istanze con stesso numero di attributi, e attributi con stesso dominio

- **Differenza**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n, D_1' , \ldots , D_n'$ domini $\mid \forall i \in [1, n] \quad D_i = D_i'$
> - $R_1 \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R_2 \subseteq D_1' \times \ldots \times D_n'$ relazione
> - $R_1(A_1, \ldots, A_n)$ schema relazionale
> - $R_2(A_1', \ldots, A_n')$ schema relazionale
> - $r_1$ istanza di $R_1$
> - $r_2$ istanza di $R_2$
> - $r_2 - r_1 := \{t \mid t \in r_2 \land t \notin r_1\}$ è detta **differenza delle istanze $r_1$ e $r_2$**
>   - dunque, la differenza di istanze è definita solamente per istanze con stesso numero di attributi, e attributi con stesso dominio

- **Intersezione**

> - $n \in \mathbb{N}$
> - $D_1 , \ldots , D_n , D_1' , \ldots , D_n'$ domini $\mid \forall i \in [1, n] \quad D_i = D_i'$
> - $R_1 \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R_2 \subseteq D_1' \times \ldots \times D_n'$ relazione
> - $R_1(A_1, \ldots, A_n)$ schema relazionale
> - $R_2(A_1', \ldots, A_n')$ schema relazionale
> - $r_1$ istanza di $R_1$
> - $r_2$ istanza di $R_2$
> - $r_1 \cap r_2 := r_2 - (r_2 - r_1)$ è detta **intersezione delle istanze $r_1$ e $r_2$**
>   - dunque, la differenza di istanze è definita solamente per istanze con stesso numero di attributi, e attributi con stesso dominio

- **Prodotto cartesiano**

> - $n \in \mathbb{N}$
> - $D_1 ,  \ldots , D_n, D_1' , \ldots , D_n'$ domini $\mid \forall i \in [1, n] \quad D_i = D_i'$
> - $R_1 \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R_2 \subseteq D_1' \times \ldots \times D_n'$ relazione
> - $R_1(A_1, \ldots, A_n)$ schema relazionale
> - $R_2(A_1', \ldots, A_n')$ schema relazionale
> - $r_1$ istanza di $R_1$
> - $r_2$ istanza di $R_2$
> - $r_1 \times r_2 := \{(t_1, t_2) \mid t_1 \in r_1 \land t_2 \in r_2\}$ è detto **prodotto cartesiano delle istanze $r_2$ e $r_2$**



## Teorema 1


- **Hp**
    - $n \in \mathbb{N}$
    - $D_1 , \ldots, D_B , \ldots , D_n, D_1' , \ldots , D_B' , \ldots , D_n'$ domini $\mid \forall i \in [1, n] \quad D_i = D_i'$
    - $R_1 \subseteq D_1 \times \ldots \times D_B \times \ldots \times D_n$ relazione
    - $R_2 \subseteq D_1' \times \ldots \times D_B' \times \ldots \times D_n'$ relazione
    - $R_1(A_1, \ldots, B, \ldots, A_n)$ schema relazionale
    - $R_2(A_1', \ldots, B, \ldots, A_n')$ schema relazionale
    - $r_1$ istanza di $R_1$
    - $r_2$ istanza di $R_2$
- **Th**
    - $r_1 \times r_2$ contiene tuple senza significato
    - il prodotto cartesiano cercato è $\pi_{A_1, \ldots, B, \ldots, A_n, A_1', \ldots, \hat B', \ldots, A_n'}(\sigma_{B=B'}(r_1 \times r_2'))$

## Teorema 2


- ⚠️ **4.30**



## Teorema 3


- **Hp**
    - $n \in \mathbb{N}$
    - $D_1, \ldots, D_n, D_1' , \ldots , D_n'$ domini $\mid \forall i \in [1, n] \quad D_i = D_i'$
    - $R_1 \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R_2 \subseteq D_1' \times \ldots \times D_n'$ relazione
    - $R_1(A_1, \ldots, A_n)$ schema relazionale
    - $R_2(A_1', \ldots, A_n')$ schema relazionale
    - $\nexists A \in \{A_1, \ldots, A_n, A_1', \ldots, A_n'\} \mid \exists A' \in \{A_1, \ldots, A_n, A_1', \ldots, A_n'\} : A = A'$, dunque gli attributi di $R_1$ ed $R_2$ sono tutti distinti
    - $r_1$ istanza di $R_1$
    - $r_2$ istanza di $R_2$
- **Th**
    - $r_1 \times r_2 = r_1 \bowtie r_2$


****
# Teoria relazionale



## Definizione 6


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



## Definizione 7


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



## Teorema 4


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $F \subseteq F^+$



## Teorema 5


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

****

# Assiomi di Armstrong


## Definizione 8


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
> - $\forall X, Y, Z \subseteq R(A_1, \ldots, A_n) \quad X \rightarrow Y, Y \rightarrow Z \in F^A \implies X \rightarrow Z \in F^A$ è detto **assioma della transitività**



## Teorema 6


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $F \subseteq F^A$



## Teorema 7


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

## Teorema 8


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

## Teorema 9


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X, Y, Z, W \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X \rightarrow Y, WY \rightarrow Z \in F^A \implies XW \rightarrow Z \in F^A$ è detta **regola della pseudotransitività**

## Teorema 10


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

## Definizione 9


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



## Teorema 11


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

## Teorema 12


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

## Teorema 13


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $F^+ = F^A$

## Teorema 14


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

## Teorema 15


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $Z \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $\forall X \rightarrow Y \in F \mid X \subseteq Z \quad Y \subseteq Z^+_F$

## Definizione 10


- **Insiemi di dipendenze funzionali equivalenti**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k, G_1, \ldots, G_h$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $G = \{G_1, \ldots, G_h\}$
> - $F \equiv G \iff F^+ = G^+$, e $F$ e $G$ sono detti **equivalenti**



## Teorema 16


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

## Teorema 17


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


****
# Terza forma normale



## Definizione 11


- **Chiave e superchiave di una relazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X \subseteq R(A_1, \ldots, A_n)$ è detta **superchiave di $R$** $\iff \forall r$ istanza di $R \quad \forall t_1, t_2 \in r \quad t_1[X] = t_2[X] \implies t_1 = t_2$
> - $X$ è detta **chiave di $R$** $\iff X$ è la chiave di $R$ con minor numero di attributi



## Teorema 18


- **Hp**
    - $n \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $K \subseteq R(A_1, \ldots, A_n)$
- **Th**
    - $K$ superchiave di $R \iff K \rightarrow R \in F^+$
    - $K$ chiave di $R \iff K$ superchiave di $R \land \nexists K' \subseteq K \mid K' \rightarrow R \in F^+$



## Teorema 19


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $X^+_F = R \iff X$ superchiave di $R$

## Teorema 20


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali
    - $F = \{F_1, \ldots, F_k\}$
    - $X = \displaystyle \bigcap_{F_i:= A \rightarrow B \in F}{R - (B - A)}$
- **Th**
    - $X^+_F=R \iff X$ chiave unica in $R$



## Definizione 12


- **Attributo primo**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X \in R(A_1, \ldots, A_n)$ è **primo** $\iff \exists K \subseteq R(A_1, \ldots, A_n)$ chiave di $R \mid X \in K$



## Definizione 13


- **Terza forma normale**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $K \subseteq R(A_1, \ldots, A_n)$ chiave di $R$
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $R$ è in **terza forma normale** $\iff \forall A \in R(A_1, \ldots, A_n), X \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow A \in F^+, A \notin X \quad A \in K \lor K \subseteq X$
>   - ovvero, per ogni dipendenza funzionale non banale in $F^+$, o il determinante è superchiave, o il determinato è primo
>   - la terza forma normale garantisce che non ci siano problemi di ridondanza, dunque non vi sono problemi di inserimento, di aggiornamento e di eliminazione



## Teorema 21


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $K \subseteq R(A_1, \ldots, A_n)$ chiave di $R$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $R$ in terza forma normale $\iff \forall X, Y \subseteq R(A_1, \ldots, A_n) \mid Y:= A_i \ldots A_j, X \rightarrow Y \in F^+, Y \nsubseteq X \quad \forall h \in [i, j] \quad A_h \in K \lor K \subseteq X$, dunque basta decomporre $X \rightarrow Y \in F^+$ e controllare gli $A_i \ldots A_j$



## Definizione 14


- **Dipendenza parziale**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $K \subseteq R(A_1, \ldots, A_n)$ chiave di $R$
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $A \in R(A_1, \ldots, A_n)$
> - $X \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow A \in F^+, A \notin X$
> - $X \rightarrow A \in F^+$ è detta **dipendenza parziale su $R$** $\iff A$ non primo e $X \subset K$
>   - in particolare $X \neq K$

- **Dipendenza transitiva**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $A \in R(A_1, \ldots, A_n)$
> - $X \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow A \in F^+, A \notin X$
> - $X \rightarrow A \in F^+$ è detta **dipendenza parziale su $R$** $\iff A$ non primo e $\forall K \subseteq R(A_1, \ldots, A_n)$ chiave di $R \quad K \cap X = \varnothing \lor X \subset K$
>   - in particolare $\forall K \subseteq R(A_1, \ldots, A_n)$ chiave di $R \quad X \neq K$



## Teorema 22


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $K \subseteq R(A_1, \ldots, A_n)$ chiave di $R$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $R$ in terza forma normale $\iff \nexists X, Y \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow Y \in F^+$ dipendenza parziale o $X \rightarrow Y \in F^+$ dipendenza transitiva



## Definizione 15


- **Forma Normale di Boyce-Codd**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $K \subseteq R(A_1, \ldots, A_n)$ chiave di $R$
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $R$ è in **forma normale di Boyce-Codd** $\iff \forall X \subseteq R(A_1, \ldots, A_n), X$ determinante $\exists K \subseteq R(A_1, \ldots, A_n)$ superchiave $\mid X \subseteq K$
>   - questa forma normale preserva le dipendenze funzionali soddisfatte da ogni istanza legale di ogni sottoschema di $R$, senza perdita di informazioni
>   - inoltre, permette di ricostruire attraverso il join naturale ogni istanza legale di ogni sotto schema di $R$, senza aggiunta di informazioni



## Teorema 23


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale $\mid R$ in forma normale di Boyce-Codd
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $R$ in terza forma normale




****
# Decomposizione

- **Decomposizione**

- ⚠️ **DEFINISCI SOTTOSCHEMA**

> - $n, N \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $R_1, \ldots, R_N$ sottoschemi di $R$
> - $R_1, \ldots, R_N$ è detta **decomposizione di $R$** $\iff R_1, \ldots, R_N$ ricoprimento di $R$
>   - $R_1, \ldots, R_N$ ricoprimento di $R \iff \displaystyle \bigcup_{i = 1}^N R_i = R$

- **Proiezione di un insieme di dipendenze su un sottoschema**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
> - $i \in [1, h]$
> - $R_i \in \rho$ sottoschema di $R$ in $\rho$
> - $\pi_{R_i}(F) := \{X \rightarrow Y \in F^+ \mid XY \subseteq R_i\}$ è detta **proiezione di $F$ su $R_i$**
>   - $\pi_{R_i}(F)$ è l'insieme delle dipendenze funzionali in $F$ che hanno determinante e determinato in $R_i$
>   - di fatto, data $r$ istanza di $R$ legale su $F$, $\pi_{R_i}(F)$ sono le dipendenze funzionali in $F^+$ di $\pi_{R_i}(r)$

- **Preservazione di un insieme di dipendenze funzionali**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
> - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
> - $\rho$ **preserva $F$** $\iff F \equiv G$
>   - $\rho$ è una _buona_ decomposizione di $R$ se:
>     - ogni sottoschema di $\rho$ è in terza forma normale
>     - $\rho$ preserva $F$
>     - $\rho$ permette di ricostruire ogni istanza legale di $R$, attraverso il join naturale delle istanze legali $r_1, \ldots, r_h$ dei sottoschemi di $\rho$, senza perdita di informazioni



## Teorema 24


- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
- **Th**
    - $\rho$ preserva $F \iff G^+ \supseteq F$

## Teorema 25


- **Input**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $X \subseteq R(A_1, \ldots, A_n)$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
- **Output**
    - $Z = X^+_G$
- **Algoritmo**
    - $Z := X$
    - $S := \varnothing$
    - $\texttt{for}$ $i$ $\texttt{in}$ $\texttt{range(1, h):}$
        - $S = S \cup \left((Z \cap R_i)^+_F \cap R_i\right)$
    - $\texttt{while}$ $S \nsubseteq Z$$\texttt{:}$
        - $Z = Z \cup S$
        - $\texttt{for}$ $i$ $\texttt{in}$ $\texttt{range(1, h):}$
            - $S = S \cup \left((Z \cap R_i)^+_F \cap R_i\right)$
- **Oss**
    - l'algoritmo calcola $X^+_G$ senza calcolare $F^+$
        - il calcolo di $F^+$ ha costo computazionale esponenziale
        - ⚠️ **SCRIVI IL PERCHÉ**
    - ⚠️ **13.20-21-22**
- **Th**
    - sia $f \mid S^f \subseteq Z^f$, dunque l'iterazione in cui l'algoritmo termina
    - $Z^f = X^+_G$

## Teorema 26


- **Input**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
- **Output**
    - $\texttt{True/False}$
- **Algoritmo**
    - $\texttt{for}$ $X \rightarrow Y$ $\texttt{in}$ $F \texttt{:}$
        - $\texttt{if}$ $Y \nsubseteq X^+_G$$\texttt{:}$
            - $\texttt{return False}$
    - $\texttt{return True}$
- **Oss**
    - l'algoritmo controlla se $\rho$ preserva $F$
    - l'algoritmo ha costo polinomiale, poiché per calcolare $X^+_G$ viene utilizzato l'algoritmo precedentemente mostrato, che non richiede il calcolo di $F^+$
- **Th**
    - $\rho$ preserva $F \iff \forall X \rightarrow Y \in F \quad Y \subseteq X^+_G$

## Teorema 27


- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
- **Th**
    - $\forall X \rightarrow Y \in F \mid \exists R_i \in \rho : XY \subseteq R_i \implies X \rightarrow Y \in G^+$

## Definizione 16


- **Join senza perdita**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
> - $\rho$ **ha un join senza perdita** $\iff \forall r$ istanza di $R$ legale su $F \quad r = \pi_{R_1}(r) \bowtie \ldots \bowtie \pi_{R_h}(r)$
>   - $m_\rho(r) := \pi_{R_1}(r) \bowtie \ldots \bowtie \pi_{R_h}(r)$



## Teorema 28


- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $r$ istanza di $R$ legale su $F$
- **Th**
    - $r \subseteq m_\rho(r)$

## Teorema 29


- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $r$ istanza di $R$ legale su $F$
- **Th**
    - $\pi_{R_i}(m_\rho(r))=\pi_{R_i}(r)$

## Teorema 30


- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $r$ istanza di $R$ legale su $F$
- **Th**
    - $m_\rho(m_\rho(r))=m_\rho(r)$

## Teorema 31


- **Input**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
- **Output**
    - $\texttt{True/False}$
- **Algoritmo**
    - viene costruita $r$ istanza di $R$ legale su $F$, avente $h$ righe $\mid \forall i \in [1, h], j \in [1, n] \quad r_{i, j} = \left\{\begin{array}{cc} a_j & A_j \in R_i\\b_{i, j} & A_j \notin R_i\end{array}\right.$
    - $\texttt{unchanged = False}$
    - $\texttt{while not unchanged:}$
        - $\texttt{unchanged = True}$
        - $\texttt{for}$ $X \rightarrow Y$ $\texttt{in}$ $F \texttt{:}$
            - $\texttt{for}$ $t_1$ $\texttt{in}$ $r \texttt{:}$
                - $\texttt{for}$ $t_2$ $\texttt{in}$ $r \texttt{:}$
                    - $\texttt{if}$ $t_1[X] == t_2[X]$ $\texttt{and}$ $t_1[Y] \neq t_2[Y] \texttt{:}$
                        - $\texttt{unchanged = False}$
                        - $\texttt{for}$ $A_j$ $\texttt{in}$ $Y \texttt{:}$
                            - $\texttt{if}$ $t_1[A_j] == a_j \texttt{:}$
                                - $t_2[A_j] = t_1[A_j]$
                            - $\texttt{else:}$
                                - $t_1[A_j] = t_2[A_j]$
    - $\texttt{if}$ $\exists t \in r \mid t[A_1] = \ldots = t[A_n] =a_{\_} \texttt{:}$
        - $\texttt{return True}$
    - $\texttt{else:}$
        - $\texttt{return False}$
- **Oss**
    - l'algoritmo controlla se $\rho$ ha un join senza perdita
    - di fatto, l'algoritmo modifica $r \mid \forall X \rightarrow Y \in F \quad r$ soddisfa $X \rightarrow Y \in F \implies r$ è divenuta un istanza di $R$ legale su $F$
        - vengono modificate le tuple che sono uguali nei determinanti ma diverse nei determinati
    - l'algoritmo ha costo polinomiale
- **Th**
    - sia $r^0$ lo stato iniziale di $r$, e $r^f$ lo stato finale
    - sia $a_{\_}$ una qualsiasi $a_j$
    - $\rho$ ha un join senza perdita $\iff \exists t \in r^f \mid t[A_1] = \ldots = t[A_n] =a_{\_}$

## Definizione 17


- **Copertura minimale**

> - $n, k \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $G$ insieme di dipendenze funzionali $\mid F \equiv G$
> - $G$ è detto **copertura minimale di $F$** $\iff \forall X \rightarrow Y \in G \quad Y$ è un singleton, $\forall X \rightarrow A \in G \quad \nexists X' \subseteq X \mid G \equiv G - \{X \rightarrow A \} \cup \{X' \rightarrow A\}$ e infine $\nexists X \rightarrow A \in G \mid G \equiv G - \{X \rightarrow A \}$
>   - dunque, $G$ è copertura minimale di $F$ se $F \equiv G$, e in ogni dipendenza funzionale di $G$ i determinati non sono ridondanti, i determinanti non sono ridondanti, e la dipendenza stessa non è ridondante



## Teorema 32


- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $G$ copertura minimale di $F$
- **Th**
    - $G \subseteq F^+$



## Teorema 33


- **Input**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Output**
    - $F$ è minimale
- **Algoritmo**
    - $\forall X, Y:= A_i, \ldots, A_j \subseteq R(A_1 ,\dots, A_n) \mid X \rightarrow Y \in F \quad \forall h \in [i, j] \quad F := F \cup \{X \rightarrow A_h\}$
        - ogni dipendenza funzionale in $F$ viene decomposta in singleton
    - $\forall A_i \ldots A_{h - 1}A_hA_{h + 1} \ldots A_j \rightarrow A \mid F \equiv F - \{A_i \ldots A_{h -1 }A_hA_{h + 1} \ldots A_j \rightarrow A\} \cup \{A_i \ldots A_{h -1 }A_{h + 1} \ldots A_j \rightarrow A \} \quad F :=  F - \{A_i \ldots A_{h -1 }A_hA_{h + 1} \ldots A_j \rightarrow A\} \cup \{A_i \ldots A_{h -1 }A_{h + 1} \ldots A_j \rightarrow A\}$
        - $A_h$ viene rimosso dalla dipendenza funzionale, poiché ridondante
        - il processo viene applicato ricorsivamente
    - $\forall X \rightarrow A \in F \mid F \equiv F - \{X \rightarrow A\} \quad F := F - \{X \rightarrow A\}$
        - ogni dipendenza funzionale che lascia invariata $F^+$ viene rimossa da $F$, poiché ridondante
- **Oss**
    - ⚠️ **super boring, e non ho manco capito niente onestamente**
- **Th**
    - ⚠️ **?**

## Teorema 34


- **Input**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$ insieme minimale di dipendenze funzionali
- **Output**
    - $\rho$ decomposizione di $R \mid \forall R \in \rho \quad R$ in terza forma normale, $\rho$ preserva $F$ e $\rho$ ha un join senza perdita
    - dunque, $\rho$ è una _buona_ decomposizione di $R$
- **Algoritmo**
    - $S := \varnothing$
    - $\rho := \varnothing$
    - $\texttt{for}$ $A$ $\texttt{in}$ $R \texttt{:}$
        - $\texttt{if}$ $\nexists X \rightarrow B \in F \mid A \in X \lor A = B \texttt{:}$
            - $S = S \cup A$
    - $\texttt{if}$ $S \neq \varnothing \texttt{:}$
        - $R = R - S$
        - $\rho = \rho \cup S$
    - $\texttt{if}$ $\exists X \rightarrow A \in F \mid X \cup A = R \texttt{:}$
        - $\rho = \rho \cup R$
    - $\texttt{else:}$
        - $\texttt{for}$ $X \rightarrow A$ $\texttt{in}$ $F \texttt{:}$
            - $\rho = \rho \cup \{XA\}$
- **Oss**
    - l'algoritmo ha costo polinomiale


