# Terza forma normale

## Def

- **Chiave e superchiave di una relazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X \subseteq R(A_1, \ldots, A_n)$ è detta **superchiave di $R$** $\iff \forall r$ istanza di $R \quad \forall t_1, t_2 \in r \quad t_1[X] = t_2[X] \implies t_1 = t_2$
> - $X$ è detta **chiave di $R$** $\iff X$ è la chiave di $R$ con minor numero di attributi

## Oss

- **Hp**
    - $n \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $K \subseteq R(A_1, \ldots, A_n)$
- **Th**
    - $K$ superchiave di $R \iff K \rightarrow R \in F^+$
    - $K$ chiave di $R \iff K$ superchiave di $R \land \nexists K' \subseteq K \mid K' \rightarrow R \in F^+$

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
    - $X^+_F = R \iff X$ superchiave di $R$
- **Dim**
    - $X^+_F := \{A \subseteq R(A_1, \ldots, A_n) \mid X \rightarrow A \in F^A = F^+\}$, allora $X^+_F = R \iff \forall Y \subseteq R(A_1, \ldots, A_n) \quad X \rightarrow Y \in F^A = F^+$, ovvero $X \rightarrow R \in F^+$, e per osservazione precedente $X \rightarrow R \in F^+ \iff X$ superchiave di $R$

## Oss

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

## Def

- **Attributo primo**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X \in R(A_1, \ldots, A_n)$ è **primo** $\iff \exists K \subseteq R(A_1, \ldots, A_n)$ chiave di $R \mid X \in K$

## Def

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

## Oss

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

## Def

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

## Oss

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

## Def

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

## Oss

- **Hp**
    - $n, k \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale $\mid R$ in forma normale di Boyce-Codd
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
- **Th**
    - $R$ in terza forma normale

## Def

- **Decomposizione**

- ⚠️ **DEFINISCI SOTTOSCHEMA**

> - $n, N \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $R_1, \ldots, R_N$ sottoschemi di $R \mid C := \displaystyle \bigcup_{i = 1}^N{R_i} = R$ ricoprimento di $R$
> - $\rho \subseteq C$ è detto **decomposizione di $R$**

- **Proiezione di un insieme di dipendenze su un sottoschema**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $i \in [1, h]$
> - $R_i \in \rho$ sottoschema di $R$ in $\rho$
> - $\pi_{R_i}(F) = \{X \rightarrow Y \in F^+ \mid XY \subseteq R_i\}$ è detta **proiezione di $F$ su $R_i$**
>   - $\pi_{R_i}(F)$ è l'insieme delle dipendenze funzionali in $F$ che hanno determinante e determinato in $R_i$

- **Preservazione di un insieme di dipendenze funzionali**

> - $n, k, h \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
> - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
> - $F = \{F_1, \ldots, F_k\}$
> - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
> - $\rho$ **preserva $F$** $\iff F \equiv G$

## Oss

- **Hp**
    - $n, k, h \in \mathbb{N}$
    - $D_1, \ldots, D_n$ domini
    - $R \subseteq D_1 \times \ldots \times D_n$ relazione
    - $R(A_1, \ldots, A_n)$ schema relazionale
    - $\rho = R_1, \ldots, R_h$ decomposizione di $R$
    - $F_1, \ldots, F_k$ dipendenze funzionali su $R$
    - $F = \{F_1, \ldots, F_k\}$
    - $G = \displaystyle \bigcup_{i=1}^h{\pi_{R_i}(F)}$
- **Th**
    - $\rho$ preserva $F \iff G^+ \supseteq F$
- **Dim**
    - poiché $G$ è definito a partire da $F$, pur non conoscendo in che relazione si trovano $G$ ed $F$, sicuramente $F \subseteq F^+$ e $G \subseteq F^+$
    - allora, per lemma precedente $G \subseteq F^+ \implies G^+ \subseteq F^+ \implies \rho$ preserva $F \iff G^+ \supseteq F^+$
    - per lemma precedente $G^+ \supseteq F^+ \implies G^+ \supseteq F$
