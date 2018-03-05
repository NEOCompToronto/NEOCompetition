# General Proof of Work and Share Economy



## 1. Prerequisite

### 1.1 Sustainable Symmetric Key

By leverage the power of distributed ledger, the conventional secured connection techniques such as HTTPS/SSL can be drastically simplified. 

Say we have $N_A$ and $N_B$ with the public key and private key to be ($PU_A$,$PV_A$) and ($PU_B$, $PV_B$) respectively,  the below steps are only required to be excuted only once for all. 

1. $N_A$ generate a symmetric key $K_S$ (a.k.a. **Sustainable Symmetric Key** or **SSK** ). 
2. $N_A$ uses asymmetric algorithm $E$,  $PU_B$, metadata $\lambda$ and signiture function $Sig$ to generate the message $M = Sig(E(PU_B, \lambda),PV_A)$ , then boardcasts $M$ to blockchain. 

After that, $N_A$ and  $N_B$ can use $K_S$ to secure the traffic for unlimited times, without asymmetric handshake, no matter the traffic is onchain or offchain.

To reset SSK due to key leakage or version upgrade, $N_A$ can simple repeat the above steps. $N_B$ always take the latest one.



## 2. Service: Provision, Definition, Negotiation and Evaluation 

### 2.1 Brief

Any service, no matter the consumer and provider parties comes from human community or computer network, can be incontestably processed only when four predefined interactive components achieved accurate consensus. These components are Provision, Definition, Negotiation, Evaluation. 

**Provision**: 

**Definition**: Consumer abstracts and refines the requirement from its raw demond,  and 

1. avoid any functional or qualitative dispution caused by indistinction or obscuration.
2. expose enough and just enough information to support the provider's service, in order to maximize privacy protection and minimize the cost of processing.

**Negotiation**: Consumer and the network should be isolated from the complexibility of the service. Since

1. these roles are not required to be professional,
2. providers keep their tactic and resource private unless it's required in *Definition*. In this way, providers can maintain their competitiveness and are couraged to innovate to increase the profit space.

In free market scheme, Consumers negotiate the price by comparing the bidding from all providers who claim capable to handle the *Definition*. 

**Evaluation**: 



A distributed consensus network is **PDNE compatiable**, if

1. every node  $k$ in this network has an asynmmetric key pair ($PU_k, PV_k$), where $PU_k$ is the public key (address) and $PV_k$ is the private key used for signiture. 
2. There's a universial currency to measure the value of service. There's a way to calculate its balance of each account. Denote the balance as $B_k$ for node $k$. 
3. this network has $n$ types of predefined or later registered services {$S_n$}, $n \ge 1$. For any $i \in [1, n]$, define $S_i \equiv$  {$D_{S_i}, N_{S_i}, E_{S_i} , PU_{a_i}, \vec{\psi_{S_i}}$}, where $D_{S_i}, N_{S_i}$ and $E_{S_i} $ are the Definition, Negotiation and Evaluation functions developed to support the particular type of service $S_i$. $PU_{a_i}$ is $S_i$'s auther's address. $\vec{\psi_{S_i}}$ is $S_i$ specific parameters. We call $S_i$ a **DNE Service**.
4. Suggest supports *Sustainable Symmetric Key* introduced in *Chapter III*, but not mandatory.




### 2.2 PDNE Service life cycle
A typical life cycle of service instance $s \in S_i$ in a *DNEC network* is described below:
1. The service provider node $p$ boardcasts an provision message announcing it's capacity and compensation rate. For each type of service $S_i$,  $Cap^{p}_{Si}$  along with its unit compensation $Rate^{p}_{Si}$ respectively. The message is $M_{provision}(PU_{p},Cap^{p}_{S_i},Rate^{p}_{S_i}, \vec{\rho_{S_i}^p} | PV_p) $, where $\vec{\rho_{S_i}^p} $ is service specific parameters.

2. Consumer node $c$ creates the service instance $s$ by excuting $D_{S_i}$(a.k.a. **Definition Function**). $(id_s,\vec{d_s},\vec{\alpha_s})=D_{S_i}(\vec{r_s})$, which takes $c$'s raw input $\vec{r_s}$ and encrypt sensitive data, standalize the data format to generate $\vec{d_s}$. $id_s$ is $s$'s universal id, $\vec{\alpha_s}$ is the answer vector, which will be used in evaluation period later.

3. $c$ then calculate $(Vol_s, h_e,PU_p) = N_{S_i}(\vec{d_s}) $, where $Vol_s$ is the common estimation of $s$'s volume, $h_e$(a.k.a. **Evaluation Height**) is the block height deadline for evaluation, and $PU_p$ is the recommended provider's address. In most cases, $N_{S_i}$(a.k.a. **Negotiation Function**) create a list $L_{P}^{S_i}$ with the addresses of all the providers of $S_i$ by filtering the nodes with $Cap_{Si} \gt 0$, then iterate every provider $p_j$ with following steps:

   * Filter out $p_j$ if it's available capacity is less than $Vol_s$. Concretely, say $p_j$ is already working on $l_j$ instances of $S_i$ with the volumes of $\{Vol_{l_j}\}$,  filter it out if  $ Cap^{p_j}_{Si} - \Sigma Vol_{k} \lt Vols $ 
   * The fee $p_j$ required for task $s$ is calculated by $F(s,p_j) = Rate_{S_i}^{p_j} \cdot Vol_s$. Filter out $p_j$ if $F(s,p_j) \gt B_c$, since $c$ doesn't have enough balance to pay $p_j$ to run $s$.
   * one straightforward practise is to pick $p_j$ where $F(s,p_j)$ has the minimum value (The cheapest one). Actually, there are other tactics to make more reasonable $N_{S_i}$ utilizing other information recorded on chain. *e.g.* taking the evaluation result (retrievable by calling $E_{S_i}$) of $p_j$'s last 10 services into account, or weight $p_j$'s experience history, etc.

   After all these, $c$ boardcasts the message $M_{service}(PU_c,id_s, \vec{d_s}, \vec{\alpha_s}|PV_c)$. After confirmation, other nodes including $p$ will get to know $s$ is assigned by calculating $N_{S_i}(\vec{d_s}) $. $c$ also have the option to boardcast $M_{service}'(PU_c,id_s, \vec{d_s},\vec{\alpha_s},p'|PV_c)$ instead of $M_{service}$ to manually assign the provider $p'$.

   To verify $M_{service}$ during confirmation (say $p$ is selected as provider) , bookkeeper nodes should:

   * Check the signiture. If invalid, return false.
   * Run $(Vol_s, PU_p, h_e) = N_{S_i}(\vec{d_s}) $, check if $p$ has enough available capacity. If not, return false.
   * Check if $c$ has enough balance. if not, return false.
   * Check if $\vec{d_s}$ is valid. This is a service specific process.

    If everything goes right, $M_{service}$ or $M'_{service}$ is recorded into ledger on the height $h_0$. $F(s,p)$ is frozen from $c$'s account immediately.

4. $p$ is supposed to give out a result vector $\vec{z_s}$  before $h_0+h_e$ reached. $p$ can evaluate it's temporary $\vec{\zeta}$ anytime by running $({\upsilon}_s, c_{p_s},c_{a_s} )= E_{S_i}(\vec{d_s},\vec{\zeta}, \vec{\alpha_s} )$, where ${\upsilon}_s \in [0,1]$ represents the score of $p$'s service. $c_{p_s}$ and $c_{p_s}$ are the presumed service fee deposit to $p$ and $a_i$ 's account. The author $a_i$ can design $E_{S_i}$ to support boolean output 0 and 1 to represent only the status of success and failure. 

   There's no fixed function to restrict what should $p$ process to get $\vec{z_s}$, It's free for $p$ to leverge any offchain solution or resource on $s$. But since $\vec{r}$ is not exposed to the chain, $p$ cannot leverage $D_{S_i}$. 

   Once $p$ thinks $\vec{z}$ is OK, it boardcasts the message $M_{resolve}(id_s, \vec{z}|PV_p) $. 

   Then bookkeepers should check if latest block height is lower than $h_0+ h_e$. If yes, record the message into ledger. Otherwise just ignore it.

   By calculating $(v_s, c_{p_s},c_{a_s} )=E_{S_i}(\vec{d_s},\vec{z_s}, \vec{\alpha_s} ) $, the amount of $F(s,p)$ is unfrozen in $c$'s account, and $ c_{p_s}$ and $c_{a_s}$ are transfered to $p$ and $a_i$ respectively. 

   The whole life cycle of $s$ is finished.


### 2.3 Features of PDNE network



## 3. Solutions of some common scenarios

### 3.1 Large input 

One common challenge is that many types of services requires the consumer to pass large size data to provider to process. Distributed ledger network with the nature of being a "ledger", is neither expected nor feasible to keep large size data. Some off-chain assisted mechanism should be introduced to insure such data is successfully transferred.

Say service $S$ has  $\vec{r} = \{\vec{\gamma},\vec{\tau}\}$ where each element of  $\vec{\tau}$ contains large size data, while each element of  $\vec{\gamma}$ has small size data. $S$ should:

1. Design $D_S$ and $N_S$ to calculate $Vol_s$ irrelative with $\vec{\tau}$.  If $Vol_s$ is related with some features of $\vec{\tau}$ (say the size), just put the feature values as elements of  $\vec{\gamma}$
2. $S$ is better not to support manually provider pick up to avoid DDoS. 
3. Providers should put it's off-chain server addresses into $\vec{\rho_{S}} $ in $M_{provision}$.

When consumer $c$ is creating the new service instance $s$, $D_S$ with input  $\vec{r}$ goes through following steps:

   	1. use the same algorithm of $N_s$ to calculate $Vol_s$ and pick $p$ with an algorithm pseudo-randomized by timestamp $t$.  
   	2. checks if *SSK* (See Chapter 1) between $p$ and $c$ is already created. If not, create it. 
   	3. encrypt $\vec{\tau'} = E(\vec{\tau}, SSK(s,p))$. Post $\vec{\tau'} $ with $p$'s off-chain API, $p$ returns $id'_s$ to track $ \vec{\tau'} $ . If error happens, go to step 1 and another provider will be picked.
   	4. Calculate $\vec{d_s} = \{N'_s(\vec{\gamma}),  id'_s, \epsilon, t\}$.  $N'_s$ is used to process small size parameter $\vec{\gamma}$.  $\epsilon = CS(\vec{\tau'})$ is checksum.

$c$ sends $M_{service}$ out. When bookkeepers verify $M_{service}$, they query $p$'s off-chain API with parameter $id_s'$ and its signiture, and get back  $\vec{\tau'}$, check if the checksum matches with $\epsilon$. Record the $M_{service}$ into blockchain then. If any error, just ignore it. If $c$ cannot find $M_{service}$, it can reinitiate $s$ again.

 $p$ only opens the GET API to the chain node (verified via signatures), and limit the number of queries for particular $id'_s$ with the maxmium confirmations necessary (say 6 for Bitcoin and 12 for Ethereum), except $c$. 

Since $\vec{\tau'}$ is encrypted, bookkeepers can do nothing with it except validation. $p$ can decrypt the data and excute the service.

### 3.2 Privacy with the service provider

From 3.1 we can see SSK can provide good protection from the parites other than $c$ and $p$. But the question is: Is it possible to even protect the privacy from $p$? The answer is yes if the author of the service have a good design to split $\vec{r}$ into subsets, create a set of service instances, and none of the providers can see the whole picture.

### 3.3 Required service duration

Many services requires the providers to keep serving for a particular long time. e.g. $c$ wants to rent $p$'s storage to hold his video for one month. 



## 4. Example Scenarios  

 ### 2.1 Cloud mining 

$c$ wants to mine POW cryptocurrency $\Gamma$, whose block cycle is larger than that of our network. $c$ finds there's a service called $S_{mine}$ to provide general mining service. So $\vec{r_s} = (\Gamma, B_h)$, while $\Gamma$ is the symbol and $B_{h0}$ is the block content of height $h$. $D_{S_{mine}}$ returns standard hash function request, and $\vec{a}$ is the nounce.  

### 2.2 Gradient descent

$c$ is researching deep learning and has a neural network to train. This is a typical Large Input scenario. $c$ pass the encrypted NN structure and training/testing set to $p$ through offchain channel. 









