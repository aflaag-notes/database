# Algebra relazionale

## Def

- **Dominio**

> - $A$ insieme finito o infinito
> - $A$, in algebra relazionale, è detto **dominio**

## Def

- **Prodotto cartesiano**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $D_1 \times \ldots \times D_n := \{v_1, \ldots, v_n) \mid v_1 \in D_1, \ldots , v_n \in D_n\}$ è detto **prodotto cartesiano dei domini $D_1, \ldots D_n$**

## Def

- **Relazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots , D_n$ domini
> - $k \in [1, n]$
> - $R \subseteq D_1 \times \ldots \times D_k$ è detta **relazione di grado $k$**
>   - $(t_1, \ldots, t_k) \in R$ è detta **tupla di cardinalità $k$**
>   - $\forall i \in [1, k] \quad (t_1, \ldots, t_k)[i] = t_i$
>   - $\forall a, b \in [1, k] \mid a \lt b \quad (t_1, \ldots, t_k)[a, b] = (t_a, \ldots, t_b)$

## Def

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

## Def

- **Chiave di una relazione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X = \{A_i \mid A_i \in R(A_1, \ldots, A_n)\}$ è detta **chiave di $R$** $\iff \forall r$ istanza di $R \quad \forall t_1, t_2 \in r \quad t_1[X] = t_2[X] \implies t_1 = t_2$
> - $X$ è detta **chiave primaria di $R$** $\iff X$ è la chiave di $R$ con minor numero di attributi

## Def

- **Dipendenza funzionale**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n$ domini
> - $R \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R(A_1, \ldots, A_n)$ schema relazionale
> - $X = \{A_i \mid A_i \in R(A_1, \ldots, A_n)\} \mid X \neq \varnothing$
> - $Y = \{A_i \mid A_i \in R(A_1, \ldots, A_n)\} \mid Y \neq \varnothing$
> - $X \rightarrow Y$ è detta **dipendenza funzionale**
> - $r$ istanza di $R$ **soddisfa** $X \rightarrow Y \iff \forall t_1, t_2 \in R \quad t_1[X] = t_2[X] \implies t_1[Y] = t_2[Y]$

## Def

- **Proiezione**

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

- **Unione**

> - $n \in \mathbb{N}$
> - $D_1, \ldots, D_n, D_1' \times \ldots \times D_n'$ domini \mid $\forall i \in [1, n] \quad D_i = D_i'$
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
> - $D_1, \ldots, D_n, D_1' \times \ldots \times D_n'$ domini \mid $\forall i \in [1, n] \quad D_i = D_i'$
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
> - $D_1, \ldots, D_n, D_1' \times \ldots \times D_n'$ domini \mid $\forall i \in [1, n] \quad D_i = D_i'$
> - $R_1 \subseteq D_1 \times \ldots \times D_n$ relazione
> - $R_2 \subseteq D_1' \times \ldots \times D_n'$ relazione
> - $R_1(A_1, \ldots, A_n)$ schema relazionale
> - $R_2(A_1', \ldots, A_n')$ schema relazionale
> - $r_1$ istanza di $R_1$
> - $r_2$ istanza di $R_2$
> - $r_1 \cap r_2 := r_2 - (r_2 - r_1)$

- **Prodotto cartesiano**


