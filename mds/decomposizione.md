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
>   - $\rho$ è una _buona_ decomposizione se:
>     - ogni sottoschema di $\rho$ è in terza forma normale
>     - $\rho$ preserva $F$
>     - $\rho$ permette di ricostruire ogni istanza legale di $R$, attraverso il join naturale delle istanze legali $r_1, \ldots, r_h$ dei sottoschemi di $\rho$, senza perdita di informazioni

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
    - ⚠️ **13.20-21-22**
- **Th**
    - sia $f \mid S^f \subseteq Z^f$, dunque l'iterazione in cui l'algoritmo termina
    - $Z^f = X^+_G$
- **Dim**
    - $Z^f \subseteq Z^+_G$
        - _caso base_
            - $Z^0 = X$, per osservazione precedente $X \subseteq X^+_G \implies Z^0 \subseteq X^+_G$
        - _ipotesi induttiva_
            - $Z^i \subseteq X^+_G$
        - _passo induttivo_
            - è necessario dimostrare che $Z^{i + 1} \subseteq X^+_G$
            - sia $A \in Z^{i + 1} = Z^i \cup S^i$, allora $A \in Z^i \lor A \in S^i$
            - $A \in Z^i \implies A \in X^+_G$ per ipotesi induttiva
            - $A \in S^i \implies \exists j \le h \mid A \in (Z^i \cap R_j)^+_F \cap R_j$ per definizione di $S^i$
                - $Z^i \cap R_j \subseteq R_j$, e inoltre $A \in (Z^i \cap R_j)^+_F \cap R_j \implies A \in R_j$
                - allora, per definizione di $\pi_{R_j}(F) := \{X \rightarrow Y \in F^+ \mid XY \subseteq R_j\}$ si ha che $(Z^i \cap R_j) \rightarrow A \in \pi_{R_j}(F)$
                - per osservazione precedente $G \subseteq G^+$
                - per definizione di $G$ si ha che $\pi_{R_j}(F) \subseteq G$, allora in particolare $(Z^i \cap R_j) \rightarrow A \in G \subseteq G^+ \implies (Z^i \cap R_j) \rightarrow A \in G^+$
                - $Z^i \cap R_j \subseteq Z^i$, e per ipotesi induttiva $Z^i \subseteq X^+_G \implies Z^i \cap R_j \subseteq X^+_G$, allora per lemma precedente si ha che $Z^i \cap R_j \subseteq X^+_G \implies X \rightarrow (Z^i \cap R_j) \in G^A$
                - allora $X \rightarrow (Z^i \cap R_j), (Z^i \cap R_j) \rightarrow A \in G^A \implies X \rightarrow A \in G^A$ per assioma della transitività
                - allora, per definizione di $X^+_G$ si ha che $X \rightarrow A \in G^A \implies A \in X^+_G$
    - $Z^f \supseteq Z^+_G$
        - ⚠️ **falla se c'hai voglia**

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
    - $\texttt{for}$ $X \rightarrow Y$ $\texttt{in}$ $F \texttt{:}$
        - $\texttt{if}$ $Y \nsubseteq X^+_G$$\texttt{:}$
            - $\texttt{return False}$
    - $\texttt{return True}$
- **Oss**
    - l'algoritmo controlla se $\rho$ preserva $F$
    - l'algoritmo ha costo polinomiale, poiché per calcolare $X^+_G$ viene utilizzato l'algoritmo precedentemente mostrato, che non richiede il calcolo di $F^+$
- **Th**
    - $\rho$ preserva $F \iff \forall X \rightarrow Y \in F \quad Y \subseteq X^+_G$
- **Dim**
    - la tesi è equivalente a dimostrare che $\exists X \rightarrow Y \in F \mid Y \nsubseteq X^+_G \iff \rho$ non preserva $F$
    - per lemma precedente $Y \subseteq X^+_G \iff X \rightarrow Y \in G^A = G^+$
    - allora $\exists X \rightarrow Y \in F \mid Y \nsubseteq X^+_G \iff X \rightarrow Y \notin G^+$
    - $\exists X \rightarrow Y \in F \mid X \rightarrow Y \notin G^+ \iff F \nsubseteq G^+ \iff \rho$ non preserva $F$ per dimostrazione precedente

## Def

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

## Oss

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
- **Dim**
    - $\forall t \in r \quad t \in \{t[R_1]\} \bowtie \ldots \bowtie \{t[R_h]\} \subseteq \pi_{R_1}(r) \bowtie \ldots \bowtie \pi_{R_h}(r) =: m_\rho(r)$
        - sostanzialmente, ogni tupla di ogni istanza di $R$ legale su $F$ apparterrà al join delle parti di tutta la riga della tupla

## Oss

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
- **Dim**
    - $\pi_{R_i}(m_\rho(r)) \subseteq \pi_{R_i}(r)$
        - $\forall t_{R_i} \in \pi_{R_i}(m_\rho(r)) \quad \exists t' \in m_\rho(r) \mid t_{R_i} = t'[R_i]$ per definizione di $\pi_{R_i}(m_\rho(r))$
        - allora $\forall t' \in m_\rho(r) \quad \exists t_1, \ldots, t_h \in r \mid \forall j \in [1, h] \quad t'[R_j] = t_j[R_j]$
        - in particolare, si ha che $t_{R_i} = t'[R_i] = t_i[R_i] \in \pi_{R_i}(r)$
    - $\pi_{R_i}(m_\rho(r)) \supseteq \pi_{R_i}(r)$
        - per osservazione precedente $m_\rho(r) \supseteq r \iff \pi_{R_i}(m_\rho(r)) \supseteq \pi_{R_i}(r)$

## Oss

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
- **Dim**
    - per definizione $m_\rho(m_\rho(r)) = \pi_{R_1}(m_\rho(r)) \bowtie \ldots \bowtie \pi_{R_h}(m_\rho(r)) = \pi_{R_1}(r) \bowtie \ldots \bowtie \pi_{R_h}(r)$ per osservazione precedente, che equivale proprio alla definizione di $m_\rho(r)$

## Alg

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
    - $\texttt{if}$ $\exists t \in r \mid t[A_1] = \ldots = t[A_n] =a_j \texttt{:}$
        - $\texttt{return True}$
    - $\texttt{else:}$
        - $\texttt{return False}$
- **Oss**
    - l'algoritmo controlla se $\rho$ ha un join senza perdita
    - di fatto, l'algoritmo modifica $r \mid \forall X \rightarrow Y \in F \quad r$ soddisfa $X \rightarrow Y \in F \implies r$ è divenuta un istanza di $R$ legale su $F$
        - vengono modificate le tuple che sono uguali nei determinanti ma diverse nei determinati
    - l'algoritmo ha costo polinomiale
- **Th**
    - $\rho$ ha un join senza perdita $\iff \exists t \in r \mid t[A_1] = \ldots = t[A_n] =a_j$
- **Dim**
    - _prima implicazione_
        - sia $r^0$ lo stato iniziale di $r$, e $r^f$ lo stato finale
        - $\forall t_i^0 \in r^0 \quad t_i^0[R_i]$
        - ⚠️ **continua da qua**
    - _seconda implicazione_
        - ⚠️ **falla se c'hai voglia**
