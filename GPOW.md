# General Proof of Work and Share Economy



## 1. Prerequisite

### 1.1 Sustainable Symmetric Key

By leverage the power of distributed ledger, the conventional secured connection techniques such as HTTPS/SSL can be drastically simplified. 

Say we have $N_A$ and $N_B$ with the public key and private key to be ($PU_A$,$PV_A$) and ($PU_B$, $PV_B$) respectively,  the below steps are only required to be excuted only once for all. 

1. $N_A$ generate a symmetric key $K_S$ (a.k.a. **Sustainable Symmetric Key** or **SSK** ). 
2. $N_A$ uses asymmetric algorithm $E$,  $PU_B$, metadata $\lambda$ and signiture function $Sig$ to generate the message $M = Sig(E(PU_B, \lambda),PV_A)$ , then boardcasts $M$ to blockchain. 

After that, $N_A$ and  $N_B$ can use $K_S$ to secure the traffic for unlimited times, without asymmetric handshake, no matter the traffic is onchain or offchain.

To reset SSK due to key leakage or version upgrade, $N_A$ can simple repeat the above steps. $N_B$ always take the latest one.



## 2. Service: Definition, Negotiation, Evaluation and Compensation 

Any service, no matter the consumer and provider parties comes from human community or computer network, can be incontestably processed only when four predefined interactive components achieved accurate consensus. These components are Definition, Negotiation, Evaluation and Compensation. 

**Definition**: Consumer abstracts and refines the requirement from its raw demond,  and 

1. avoid any functional or qualitative dispution caused by indistinction or obscuration.
2. expose enough and just enough information to support the provider's service, in order to maximize privacy protection and minimize the cost of processing.

**Negotiation**: Consumer and the network should be isolated from the complexibility of the service. Since

1. these roles are not required to be professional,
2. providers keep their tactic and resource private unless it's listed in *Definition*. In this way, providers can maintain their competitiveness and are couraged to innovate to increase the profit space.

In free market scheme, Consumers negotiate the price by comparing the bidding from all providers who claim capable to handle the *Definition*. 

**Evaluation**: 

**Compensation**:

A distributed consensus network is **DNEC compatiable**, if

1. every node  $k$ in this network has an asynmmetric key pair ($PU_k, PV_k$), where $PU_k$ is the public key (address) and $PV_k$ is the private key used for signiture. 

2. There's a universial currency to measure the value of service. There's a way to calculate its balance of each account. Denote the balance as $B_k$ for node $k$. 

3. this network has $n$ types of predefined or later registered services {$S_n$}, $n \ge 1$. For any $i \in [1, n]$, define $S_i \equiv$  {$D_{S_i}, N_{S_i}, E_{S_i}, C_{S_i} , PU_{a_i}$}, where $D_{S_i}, N_{S_i}, E_{S_i}$ and $C_{S_i} $ are the Definition, Negotiation, Evaluation and Compensation functions developed to support the particular type of service $S_i$. $PU_{a_i}$ is $S_i$'s auther's address. We also call $Si$ a **DNEC Service**.

   ~~has a fixed function $P$ to randomly pick up some nodes,~~

4. Suggest supports *Sustainable Symmetric Key* introduced in *Chapter III*, but not mandatory.




### 1.2 DNEC Service life cycle
A typical life cycle of service instance $s \in S_i$ in a *DNEC network* is described below:
1. The service provider node $p$ boardcasts an offer message announcing it's capacity and compensation rate. For each type of service $S_i$,  $Cap^{p}_{Si}$  along with its unit compensation $Rate^{p}_{Si}$ respectively. The message is $M_{offer}(PU_{p},\{Cap^{p}_{Sn}\},\{Rate^{p}_{Sn}\} | PV_p) $.

2. Consumer node $c$ creates the service instance $s$ by excuting $D_{S_i}$(a.k.a. **Definition Function**). $(\vec{d_s},\vec{a_s})=D_{S_i}(PU_c, \vec{r_s})$, which takes $c$'s raw input $\vec{r_s}$ and encrypt sensitive data, standalize the data format to generate $\vec{d_s}$. $\vec{a_s}$ is the answer vector, which will be used in evaluation period later.

3. $c$ then calculate $(Vol_s, PU_p,h_e) = N_{S_i}(\vec{d_s}) $, where $Vol_s$ is the common estimation of the volume of $s$, $h_e$(a.k.a. **Evaluation Height**) is the block height (start counting when $s$ is wroten into block) to do evaluation, and $PU_p$ is the recommended provider's address. In most cases, $N_{S_i}$(a.k.a. **Negotiation Function**) create a list $L_{P}^{S_i}$ with the addresses of all the providers of $S_i$ by filtering the nodes with $Cap_{Si} \gt 0$, then iterate every provider $p_j$ with following steps:

   * Filter out $p_j$ if it's available capacity is less than $Vol_s$. Concretely, say $p_j$ is already working on $l_j$ instances of $S_i$ with the volumes of $\{Vol_{l_j}\}$,  filter it out if  $ Cap^{p_j}_{Si} - \Sigma Vol_{k} \lt Vols $ 
   * The fee $p_j$ required for task $s$ is calculated by $F(s,p_j) = Rate_{S_i}^{p_j} \cdot Vol_s$. Filter out $p_j$ if $F(s,p_j) \gt B_c$, since $c$ doesn't have enough balance to pay $p_j$ to run $s$.

   After above steps, one obvious pracise is to pick $p_j$ where $F(s,p_j)$ has the minimum value (The cheapest one). Actually, there are other tactics to make more reasonable $N_{S_i}$ utilizing other information recorded on chain. *e.g.* taking the evaluation result (retrievable by calling $E_{S_i}$) of $p_j$'s last 10 services into account, or weight $p_j$'s experience history, etc.

   Then $c$ boardcasts the message $M_{service}(PU_c, \vec{d_s}, \vec{a_s}|PV_c)$. After confirmation, other nodes including $p$ will get to know $s$ is assigned by calculating $N_{S_i}(\vec{d_s}) $. $c$ also have the option to boardcast $M_{service}'(PU_c, \vec{d_s},\vec{a_s},p'|PV_c)$ instead of $M_{service}$ to manually assign the provider $p'$.

   To verify $M_{service}$ during confirmation, bookkeeper nodes should:

   * Check the signiture. If invalid, return false.
   * Run $(Vol_s, PU_p, h_e) = N_{S_i}(\vec{d_s}) $
   * No matter $p$ or $p'$ is chosen, check if the selected provider has enough available capacity and $c$ has enough balance. if not, return false.

    If everything goes right, $M_{service}$ or $M'_{service}$ is written into ledger on the height $h_0$. 

4. The provider (let's say $p$) is supposed to start running its offchain tactic or resource on $s$ since $h_0$. The target is to give out a vector $\vec{z}$  before $h_0+h_e$ reached.

   1. ​
   2. If $N_A$'s balance $b_A \lt c(\tau)$, return false. 

5. $N_A$ compares the nodes offering service 

6. $N_A$ calls $P$ to pick up $m$ random nodes $N_{v_1},… N_{v_m}$.  Then generate message by following algorithm:

3. ​




We call a distributed consensus network, regardless which consensus algorithm it is based on, a **GPoW network**, if it:

1. ​

In Chapter II to Chapter IV, we'll prove that 



## IV. Choosing Service Node



## Discussion

#### 1. The algorithm of P, best practise

dfea

#### 2. 

