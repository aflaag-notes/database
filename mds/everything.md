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
> - $\sigma_C(R) \subseteq D_1 \times \ldots \times D_n$ è detta **selezione di $R$**
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
> - $\forall X, Y \subseteq R(A_1, \ldots, A_n) \quad X \rightarrow Y, Y \rightarrow Z \in F^A \implies X \rightarrow Z \in F^A$ è detto **assioma della transitività**



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
    - $X, Y, Z \subseteq R(A_1, \ldots, A_n)$
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

## Definizione 10


- **Insiemi di dipendenze funzionali equivalenti**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $F_1, \ldots, F_k, G_1, \ldots, G_h$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $G = \{G_1, \ldots, G_h\}$
> - $F \equiv G \iff F^+ = F^+$, e $F$ e $G$ sono detti **equivalenti**



## Teorema 15


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



## Teorema 16


- **Hp**
    - $n \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $K \subseteq R(A_1, \ldots, A_n)$
- **Th**
    - $K$ superchiave di $R \iff K \rightarrow R \in F^+$
    - $K$ chiave di $R \iff K$ superchiave di $R \land \nexists K' \subseteq K \mid K' \rightarrow R \in F^+$



## Teorema 17


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

## Teorema 18


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



## Teorema 19


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



## Teorema 20


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



## Teorema 21


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

- **Ricoprimento**

- ⚠️ **DEFINISCI SOTTOSCHEMA**

> - $n, N \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $R_1, \ldots, R_N$ sottoschemi di $R$
> - $R_1, \ldots, R_N$ **ricoprimento di $R$** $\iff \displaystyle \bigcup_{i = 1}^N{R_i} = R$

- **Decomposizione**

> - $n, N \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $C := \{R_1, \ldots, R_N\}$ ricoprimento di $R$
> - $\forall \rho \subseteq C \quad \rho$ è detto **decomposizione di $R$**

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



## Teorema 22


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

## Teorema 23


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
    - $\texttt{for}$ $i$ $\texttt{in}$ $\texttt{range(1, k):}$
        - $S = S \cup (Z \cap R_i)^+_F \cap R_i$
    - $\texttt{while}$ $S \nsubseteq Z$$\texttt{:}$
        - $Z = Z \cup S$
        - $\texttt{for}$ $i$ $\texttt{in}$ $\texttt{range(1, k):}$
            - $S = S \cup (Z \cap R_i)^+_F \cap R_i$
- **Oss**
    - l'algoritmo calcola $X^+_G$ senza calcolare $F^+$
        - il calcolo di $F^+$ ha costo computazionale esponenziale

## Teorema 24


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
    - $\texttt{for}$ $X \rightarrow Y$ $\texttt{in}$ $F$$\texttt{:}$
        - $\texttt{if}$ $Y \nsubseteq X^+_G$$\texttt{:}$
            - $\texttt{return False}$
    - $\texttt{return True}$
- **Oss**
    - l'algoritmo controlla se $\rho$ preserva $F$
    - per calcolare $X^+_G$ viene utilizzato l'algoritmo precedentemente mostrato, che non richiede il calcolo di $F^+$

