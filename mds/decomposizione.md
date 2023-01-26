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
>   - $\pi_{R_i}(F)$ è l'insieme delle dipendenze funzionali in $F^+$ che hanno determinante e determinato in $R_i$
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
- **Dim**
    - $Z^f \subseteq X^+_G$
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
        - _omessa dal professore_

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
    - $\forall X \rightarrow Y \in F \mid \exists R_i \in \rho : XY \subseteq R_i \implies X \rightarrow Y \in G^+$
- **Dim**
    - $\forall X \rightarrow Y \in F \mid \exists R_i \in \rho : XY \subseteq R_i \implies X \rightarrow Y \in \pi_{R_i}(F) \subseteq G$
    - per osservazione precedente $G \subseteq G^+$, allora $X \rightarrow Y \in G^+$
    - quest'osservazione implica che nel controllare che $\rho$ preservi $F$ non è necessario controllare tutte le dipendenze di $F$ all'interno del ciclo $\texttt{for}$, ma solamente quelle che non rispettano questa condizione

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
- **Dim**
    - _prima implicazione_
        - $\forall t_i^0 \in r^0 \quad t_i^0[R_i] = (a_{\_}, \ldots, a_{\_})$ per costruzione di $r^0$
        - inoltre, poiché l'algoritmo non varia mai le $a_{\_}$, ma solamente le $b_{i,j}$, allora $t_i^0[R_i] = t_i^f[R_i] = (a_{\_}, \ldots, a_{\_})$, allora $\exists t \in r^f \mid t$ contiene solamente $a_{\_}$
        - sia $t^a$ la tupla che contiene tutte $a_{\_}$ in $r^f$
        - per costruzione di $r$, si ha che $t^a$ deve essere necessariamente nel join naturale delle tuple che hanno tutte $a_{\_}$ in $R_j$, allora si ha che $t^a \in \{t_1^f[R_1]\} \bowtie \ldots \bowtie \{t_h^f[R_h]\}$
        - inoltre $\{t_1^f[R_1]\} \bowtie \ldots \bowtie \{t_h^f[R_h]\} \subseteq \pi_{R_1}(r^f) \bowtie \ldots \bowtie \pi_{R_h}(r^f) =: m_\rho(r^f)$
        - per costruzione dell'algoritmo, si ha che $r^f$ è legale
        - poiché $\rho$ ha un join senza perdita, e $r^f$ è legale, allora $m_\rho(r^f) = r^f$ per definizione di join senza perdita
        - in particolare, $t^a \in r^f \implies \exists t \in r^f \mid t[A_1] = \ldots = t[A_n] =a_{\_}$
    - _seconda implicazione_
        - _omessa dal professore_

## Def

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

## Oss

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

## Alg

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
- **Dim**
    - ⚠️ **?**

## Alg

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
