# NEO of Things (NEOT) 

The IoT Infrastracture powered by NEO



[TOC]



## 0. Abstract

As the Submission of NEO's competiton, we have:

### 0.1 The proposal of NEOT 
This article itself. The project of NEO of Things (a.k.a NEOT ) initiated by [Norchain](www.norchain.io) team aimed to … {TODO}
### 0.2 A prototype of NEOT NEP-5 smart contract 
{TODO: Need discribe what's in there}

### 0.3 A demo of NEO based UBI 

{TODO: Build by Unity} the senario …  

### 0.4 A video 

{TODO}

### 0.5 Intro of the team

Norchain team ….

We are contact with Marham government to do ….

We have relationship with Huawei to utilize NB-IoT … 

We contacted with China mobile ...



## 1. Challenges of IoT and related projects

{TODO: To finish this section, can mainly cite the following two aricles coming from IEEE IoT}

	1. [IoT+BlockChain: Benefits and Challenges](https://iot.ieee.org/newsletter/january-2017/iot-and-blockchain-convergence-benefits-and-challenges.html)
	2. [IoT Trends 2018](https://iot.ieee.org/newsletter/january-2018/iot-trends-in-2018-ai-blockchain-and-the-edge.html?highlight=WyJibG9ja2NoYWluIl0=)

### 1.1 Node capability

Most IoT nodes have limited storage and calculation power. The consensus algorithms
employed in BC (POW or POS) require significant computational resources which are far beyond the capabilities of most IoT devices. {TODO. NOTE: Can also cite some ideas from these two articles in other sessions.} [LINK1](https://arxiv.org/pdf/1712.02969.pdf), [LINK2](https://arxiv.org/pdf/1608.05187.pdf)

Ethereum's light client protocol is still under development [LINK](https://github.com/ethereum/wiki/wiki/Light-client-protocol). 

### 1.2 DDoS attack

IoT has already turned into a serious security concern that hackers can produce DDoS attacks.  {TODO}  [LINK1 ](https://www.iotforall.com/5-worst-iot-hacking-vulnerabilities/) 

Blockchain technology leveraging randomlized peers brings the potiential of DDoS-resistant. {TODO} [LINK](https://venturebeat.com/2017/06/25/how-blockchain-based-apps-and-sites-resist-ddos-attacks/)  ( *Paragram: Attacking the miners directly is close to impossible. They do their work behind a peer-to-peer network designed to resist any sort of direct attack called the Bitcoin protocol. Peer-to-peer networks are notoriously hard to stop or even disrupt. Attacking the transactions is also close to impossible because they are stored in everyone’s copy of the blockchain and cryptographically verified by the mining process.*) 



### 1.3 Connection stability

{TODO} [LINK](https://iot.ieee.org/newsletter/january-2017/iot-and-blockchain-convergence-benefits-and-challenges.html)



### 1.4 Compatibility

{TODO} [LINK](https://iot.ieee.org/newsletter/march-2017/three-major-challenges-facing-iot.html) (Refer to **Standard** session:*Technology standards which include network protocols, communication protocols, and data-aggregation standards, are the sum of all activities of handling, processing and storing the data collected from the sensors* ) 

Blockchain tech provides a chance to make message level standardization. {TODO}



### 1.5 Recent IoT distributed ledger projects  

Some IoT projects are experimenting other decentralized topology. The most famous one is IOTA. However, its light nodes rely on [manual assigning public nodes as servers](https://www.iotasupport.com/lightwallet.shtml), which recently practially failed to resist DDoS attacks {TODO} [LINK](https://freedman.club/en/cryptocurrency-iota-ddos-attack-revealed-the-problem-of-network-scalability/) There are also other concerns of IOTA that we can see from [HERE](https://hackernoon.com/why-i-find-iota-deeply-alarming-934f1908194b)

ITC doesn't have much process on their project {TODO} [LINK](https://steemit.com/blockchain/@smcaterpillar/iot-chain-china-s-new-iota-an-easy-investment-or-should-we-set-off-the-alarm-bells-let-s-do-our-homework). It's based on Ethereum, which means low speed and you need to pay gas for every conversation, which is not applicable for most IoT scenarios. 

Steemr, providing beautiful user interface, is targeted to provide a market for offchain stream data. It's also based on Ethereum. Their network is so far running totally offchain with nothing about the their ERC20 token. {TODO: The last Q/A} [LINK](https://blog.streamr.com/2018/02/faq-streamr-ethereum-network/)



## 2 NEOT: The 1st Practical IoT Blockchain Solution



### 2.1 Key components

![struBasic](pics/struBasic.JPG "Picture 3-1 NEOT Network Basic Node Structure")

Key components in NEOT's network includes following:

#### Sensor 

*Sensor* is the ultimate information capturer of the really world and the terminal of existing IoT networks. A typical *sensor*:

2. has unidirectional **Data** output, with the form of pulsing, streaming, etc. The encoding of *data* may or may not conform to international standards. 
2. has an instruction set for remote configuration and controlling. Some also implement the status query functionalities and the feedback/acknowledge machanism. We define this set as bidirectional **Signals**. 
3. is not designed to handle heavy computational work or persist huge volume of data, in order to reduce the battery consumption and hardware cost.
4. in many scenarios, is exposed in unstable communication environment. 
6. in many scenarios, pair with, or as an element of a *sensor* cluster connect with a **Sensor Delegate**. The *delegate*, which can be a specialized hardware, or an API mounted in a common device, also provides *data* and *signal* interfaces.

NEOT node can attach multiple *sensors* or *sensor delegates*. A node with more than one 

#### Nest

*Nest* is a device equiped with significant computational power (a.k.a. **Computation Nest**) or data storage capacity (a.k.a. **Storage Nest**), or simply providing human-computer interface (a.k.a **HCI Nest**). *Nest* interact with NEOT node with the very similar way of *sensor*/*delegate*. It acts as the service provider in *Private Data* user cases, while the consumer in *Public Data* user cases. Check session 2.2 for these user cases.

#### Adapter

*Adapter* is a customizable component connecting *sensor*/*delegate* and NEOT node. *Adapter* confirms **NEOT Protocol** with a standardized *data* and *signal* interface to communicate with NEOT node via *Tunneo*.

*NEOT Protocol* is open to 3rd party, such as sensor manufacturers and indie developers. Everyone who is willing to connect their IoT devices to NEOT to leverage the power of blockchain is free to join in, no permission necessary. We call these Developers as **Adapter Devs**.

Once released, *NEOT Protocol* will be kept fixed except when serious issue founded, best providing *adapter devs* flexibility and reduce their cost of forced updates or re-deployment of their code.

#### Tunneo

*Tunneo* (a.k.a TN) as a part of NEOT node, provides following functionalities:

* Implement the encryption/decryption of *Sustainable Symmetric Key*. See session 2.2 for more details. 
* Provide *data* and *signal* I/O to *Sensors* and *Delegates*
* Realize the offchain channel between *Nest* and *Sensor* nodes.
* ​


NEOT developer team is responsible for upgrading Tunneo regularly to fix the defects and enhance it's functionality. 

### 2.2 Sustainable symmetric key (SSK)   

In the world of untrustful internet, HTTPS/SSL is widely used to verify the identities of the communication parties and ensure the traffic could not be decrypted by 3rd party. The shortcomings of such protocol are:

* Everytime to establish a new secured connection, a complex procedure comprised of 3 main phases is mandatory -  Hello, Certificate Exchange and Key Exchange.
* The verification of the identities heavily relies on the centralized nodes: Certificate Authorities (CAs).

By leverage the power of distributed ledger, this protocol can be drastically simplified. With the support of *tunneo*, in order to establish secured connection between node N<sub>A</sub> and N<sub>B</sub> with the public key and private key to be (PU<sub>A</sub>,PV<sub>A</sub>) and (PU<sub>B</sub>, PV<sub>B</sub>) respectively,  the below steps are only required to be excuted only once for all. 

1. N<sub>A</sub> generate a symmetric key K<sub>S</sub>. 
2. N<sub>A</sub> uses PU<sub>B</sub> and asymmetric encoding algorithm *E* and some other necessary metadata *Meta* (NEOT version, which decides the supported cypher sets, etc.) to generate and signiture *S* the message *M = S(E(PU<sub>B</sub>, Meta),PV<sub>A</sub>)* , then boardcasts *M* to blockchain. The service of N<sub>B</sub> doesn't have to be live at this moment.


That's all. 

*NEOT Tunneo* helps N<sub>B</sub> to retrieve K<sub>S</sub> from the blockchain. From then on, whenever N<sub>A</sub> and N<sub>B</sub> try to talk, no matter the connection is onchain or offchain, they can directly use K<sub>S</sub> to encrypt/decrypt their traffic. We call K<sub>S</sub> the **Sustainable Symmetric Key** (SSK).

CA is no longer needed. 

If N<sub>A</sub> wants to regenerate SSK, it can repeat above steps. N<sub>B</sub> will take only the latest version.



### 2.3 Tunneo: On-chain part   

Although it's a great aspiration that we put all the *signal* or even *data* generated throughout the network into blockchain, we must admit that it's impratical today due to the reasons discussed in session 1.5, even many chain consensus algorthims partcially sacrifice the character of decentralization to enhance the speed and to reduce the ledger size. The problem is especially serious for IoT applications because of the node capacity limitations.

Nevertheless, we agree that the blockchain performance and IoT node capacity will continue improve in the further. So why not migrate the business onto the chain gradually?

With this approarch, the work of inital versions of *tunneo* will tend to support the less frequent and small sized user cases. Such as transaction and scoring. 

### 2.4 Tunneo: Off-chain part

 Mainly focus on *data*.



### 2.5 Scenario: Public data 

### 2.6 Scenario: Private data

### 2.7 Blockchain: Why NEO

See following table comparing Ethereum, IOTA and NEO, by the means of IoT application.

|                                        | Ethereum                                                     | IOTA                                                         | NEO                        | Comment                                                      |
| -------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------- | :----------------------------------------------------------- |
| Light Node                             | [Developing](https://github.com/ethereum/wiki/wiki/Light-client-protocol) | Supported                                                    | Supported                  | *Light Node* stands for the nodes run without keeping ledger copies or PoW computation, which is suitable for IoT devices. |
| Connection between Light and Full Node | N/A                                                          | [Can Manually Assign](https://www.iotasupport.com/lightwallet.shtml) | Randomly Chosen            | The more connections randomized and decentralized, the more the IoT network can be DDoS resistant. |
| DApp support                           | Supported: Solicity                                          | N/A                                                          | Supported: Major languages | Open and developer-friendly eco-systems can attract more allies, by the means of both technology and investment. Also provides more flexibility to fit particular IoT scenarios. |
| Tx/Messaging Fee                       | GAS                                                          | Free                                                         | Free                       | IoT network requires way more large amount of transactions. Better to reduce   the friction. |
| TPS                                    | 15                                                           | 1000                                                         | 1000                       | IoT requires quicker transaction network                     |
| Number System                          | Binary                                                       | Ternary                                                      | Binary                     | Ternary could be the future of computing [LINK](https://iota.stackexchange.com/questions/8/why-does-iota-use-a-ternary-number-system) rather than just extra computational overhead, only if manifacturers rewrite their binary architectures. However, even the IoT communication standardization couldn't get aligned in the past decades. |
| Bookkeeper Incentive                   | Mining/Transaction reward                                    | No Incentive                                                 | Most by Dev team           | Incentive makes the network more stable                      |

As conclusion, we see NEO has the advantages as...{TODO: A summary of the table above to describe NEO's advantage in implementing IOT}. 



## 3 Smart Economy User Cases 

### 3.1 Usage-based insurance 

Intro of conventional UBI {TODO} [LINK](https://en.wikipedia.org/wiki/Usage-based_insurance) 



Brief user case decription {TODO: Describe the user case in below picture}

1. NEOT node is embeded in the car hooking with sensor 1,2,3,...
2. Algorthim of scoring is coded in Tunneo, the calculation process...
3. Charge through blockchain

![carSensors](/Users/danielpan/Projects/CryptoProjects/NEOCompetition/NEOCompetition/pics/carSensors.JPG)

Technique explaination of how blockchain works in these scenario {TODO: Describe the below picture}

1. Multiple nodes via vehicle, mobile, difficult carrier provider, insurance company
2. Use bluetooth, LTE network, NB-IoT chip, fiber network,etc.. 

![charge](/Users/danielpan/Projects/CryptoProjects/NEOCompetition/NEOCompetition/pics/charge.JPG)

Further expansion {TODO: Describe the below picture}

1. Sensors can be outside of the vehicle. eg. POS machines of repair shop, NFC with traffic camera, etc.
2. Following above bullet, auto payment of the bill and tickets.

![incentive](/Users/danielpan/Projects/CryptoProjects/NEOCompetition/NEOCompetition/pics/incentive.JPG)





### 3.2 Smart Traffic

3.1 is just one corner of the picture. 

{TODO: Tiger, retrieve some idea from the article I shared to you on weChat}

Further, we can  {TODO: Tiger can refer to our wechat conversation to complete this part}

1. The scoring and incident history of the addresses are public on blockchain with standard format. big data experts can use these data for free and help improve our traffic system. 
2. Meanwhile, since the relationship between the blockchain node and real world car is confidential, it will be transparent that individuals' privacy is ensured. 
3. It'll also be a huge save of mantainance cost for the KYC based services, such as banks, insurance company etc. who need to check individual's related history. They just need to temporary ask users to provide the prove of the ownership of the account and retrieve information from blockchain.
4. …. 

{TODO: Tiger, add more content if necessary}



## 

1. ​