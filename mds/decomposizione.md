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

## Oss

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
- **Dim**
    - poiché $G$ è definito a partire da $F$, pur non conoscendo in che relazione si trovano $G$ ed $F$, sicuramente $F \subseteq F^+$ e $G \subseteq F^+$
    - allora, per lemma precedente $G \subseteq F^+ \implies G^+ \subseteq F^+ \implies \rho$ preserva $F \iff G^+ \supseteq F^+$
    - per lemma precedente $G^+ \supseteq F^+ \implies G^+ \supseteq F$

## Alg

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
- **Dim**
    - sia $f \mid S^f \subseteq Z^f$, dunque l'iterazione in cui l'algoritmo termina

## Alg

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
- **Dim**
    - per lemma precedente $Y \subseteq X^+_G \implies X \rightarrow Y \in G^A = G^+$
    - allora $\exists X \rightarrow Y \in F \mid Y \nsubseteq X^+_G \implies X \rightarrow Y \notin G^+ \implies F \nsubseteq G^+ \implies \rho$ non preserva $F$ per dimostrazione precedente

