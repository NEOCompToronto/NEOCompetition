# General Proof of Work and Share Economy



## 1. Prerequisite

### 1.1 Sustainable Symmetric Key

By leverage the power of distributed ledger, the conventional secured connection techniques such as HTTPS/SSL can be drastically simplified. 

Say we have $N_A$ and $N_B$ with the public key and private key to be ($PU_A$,$PV_A$) and ($PU_B$, $PV_B$) respectively,  the below steps are only required to be excuted only once for all. 

1. $N_A$ generate a symmetric key $K_S$ (a.k.a. **Sustainable Symmetric Key** or **SSK** ). 
2. $N_A$ uses $PU_B$ and asymmetric encoding algorithm $E$, metadata $\lambda$ and signiture function $Sig$ to generate the message $M = Sig(E(PU_B, \lambda),PV_A)$ , then boardcasts $M$ to blockchain. 

After that, $N_A$ and  $N_B$ can directly use $K_S$ to encrypt/decrypt the traffic without asymmetric handshake, no matter onchain or offchain.



## 2. GPoW Network and GECV functions

### 2.1 Definition

We call a distributed consensus network, regardless which consensus algorithm it based on, a **GPoW compatiable network**, if it:

1. has a set $\Upsilon$ with $n$ types of predefined or later registered tasks: $\Upsilon$ = {$T_n$}, $n \ge 1$. For any $i \in [1, n]$,  we have $T_i \equiv$  {$G_i, E_i, O_i, V_i $}, where $G_i, E_i, O_i$ and $V_i$ (a.k.a **GEOV functions**) are functions with particular characters discussed in *Session 1.2*,
2. has a fixed function $P$ to randomly pick up some nodes,
3. optionally supports *Sustainable Symmetric Key* introduced in *Chapter III*,

In Chapter II to Chapter IV, we'll prove that 


### 1.2 GEOV Task life cycle and GECV functions
A typical life cycle of task instance $\tau \in T_i$ is described below:
1. At beginning, node $N_A$ tries to initiate $\tau$ by excuting $G_i$(a.k.a. **Task Generation Function**) with input $\vec{r}$: $(\vec{p},\vec{q})=G_i(\vec{r})$.
2. $N_A$ calls $P$ to pick up $m$ random nodes $N_{v_1},… N_{v_m}$.  Then generate message by following algorithm:
3. ​






## IV. Choosing Service Node



## Discussion

#### 1. The algorithm of P, best practise

dfea

#### 2. 

