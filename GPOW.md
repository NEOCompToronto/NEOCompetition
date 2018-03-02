# General Proof of Work and Share Economy



## I. Abstract

We call a distributed consensus network, regardless which consensus algorithm it based on, a **GPoW compatiable network**, if it:

1. has a list of $n$ types of predefined or later registered tasks: $\Upsilon$ = {$T_n$}, $n \ge 1$. For any $i \in [1, n]$,  we have $T_i \equiv$  {$G_i, E_i, O_i, V_i $}, where $G_i, E_i, O_i$ and $V_i$ (a.k.a **GEOV functions**) have particular characters discussed in *Chapter II*,
2. has a fixed function $P(m)$ to randomly pick up $m$ nodes,
3. optionally supports *Sustainable Symmetric Key* introduced in *Chapter III*,

In Chapter II to Chapter IV, we'll prove that 

## II. GPoW Task life cycle and GECV functions

A typical life cycle of task instance $\tau \in T_i$ is described below:

1. At beginning, node $N_A$ tries to initiate $\tau$ by excuting $G_i$(a.k.a. **Task Generation Function**).

   \begin{aligned}

     $\tau \equiv (\vec{p},\vec{q})=G_i(\vec{r})$. 

   \end{aligned}

   $\vec{r}$ as $N_A$'s input vector is usually private.

2. ​

3. $N_A$ calls $P$ to generate $m$ random nodes {$v_m$}.  Then generate message by following algorithm:

   ``` alignment{center}
   $M= $
   ```

   ​

4. d

## III. Sustainable Symmetric Key  

By leverage the power of distributed ledger, this process of setting up secured connection (HTTPS/SSL) can be drastically simplified. Say we have $N_A$ and $N_B$ with the public key and private key to be ($PU_A$,$PV_A$) and ($PU_B$, $PV_B$) respectively,  the below steps are only required to be excuted only once for all. 

1. $N_A$ generate a symmetric key $K_S$. 
2. $N_A$ uses $PU_B$ and asymmetric encoding algorithm $E$, metadata $\lambda$ and signiture function $Sig$ to generate the message $M = Sig(E(PU_B, \lambda),PV_A)$ , then boardcasts $M$ to blockchain. 

After that, whenever  $N_A$ and  $N_B$ trying to communicate, no matter onchain or offchain, they can directly use $K_S$ to encrypt/decrypt their traffic. We call $K_S$ the **Sustainable Symmetric Key** (SSK).



## IV. Choosing Service Node



## 3. FAQ

1. ​