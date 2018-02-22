# NEO of Things (NEOT) 

The IoT Infrastracture powered by NEO



[TOC]



## 0. Abstract



## 1. Challenges of IoT

{TODO: To finish this section, can mainly cite the following two aricles coming from IEEE IoT}

	1. [IoT+BlockChain: Benefits and Challenges](https://iot.ieee.org/newsletter/january-2017/iot-and-blockchain-convergence-benefits-and-challenges.html)
	2. [IoT Trends 2018](https://iot.ieee.org/newsletter/january-2018/iot-trends-in-2018-ai-blockchain-and-the-edge.html?highlight=WyJibG9ja2NoYWluIl0=)

### 1.1 Device Capability Limitation

Most IoT nodes have limited storage and calculation power. The consensus algorithms
employed in BC (POW or POS) require significant computational resources which are far beyond the capabilities of most IoT devices. {TODO. NOTE: Can also cite some ideas from these two articles in other sessions.} [LINK1](https://arxiv.org/pdf/1712.02969.pdf), [LINK2](https://arxiv.org/pdf/1608.05187.pdf)

Ethereum's light client protocol is still under development [LINK](https://github.com/ethereum/wiki/wiki/Light-client-protocol). 

### 1.2 DDoS Attack Resistant

IoT has already turned into a serious security concern that hackers can produce DDoS attacks.  {TODO}  [LINK1 ](https://www.iotforall.com/5-worst-iot-hacking-vulnerabilities/) 

Blockchain technology leveraging randomlized peers brings the potiential of DDoS-resistant. {TODO} [LINK](https://venturebeat.com/2017/06/25/how-blockchain-based-apps-and-sites-resist-ddos-attacks/)  ( *Paragram: Attacking the miners directly is close to impossible. They do their work behind a peer-to-peer network designed to resist any sort of direct attack called the Bitcoin protocol. Peer-to-peer networks are notoriously hard to stop or even disrupt. Attacking the transactions is also close to impossible because they are stored in everyone’s copy of the blockchain and cryptographically verified by the mining process.*) 

Some IoT projects are also experimenting other decentralized topology. The most famous one is IOTA. However, its light nodes rely on [manual assigning public nodes as servers](https://www.iotasupport.com/lightwallet.shtml), which recently practially failed to resist DDoS attacks {TODO} [LINK](https://freedman.club/en/cryptocurrency-iota-ddos-attack-revealed-the-problem-of-network-scalability/) 

### 1.3 Connection Stability

{TODO} [LINK](https://iot.ieee.org/newsletter/january-2017/iot-and-blockchain-convergence-benefits-and-challenges.html)



### 1.4 Compatibility

{TODO} [LINK](https://iot.ieee.org/newsletter/march-2017/three-major-challenges-facing-iot.html) (Refer to **Standard** session:*Technology standards which include network protocols, communication protocols, and data-aggregation standards, are the sum of all activities of handling, processing and storing the data collected from the sensors* ) 

Blockchain tech provides a chance to make message level standardization. {TODO}



## 2. Introducing NEOT

### 2.1 IoT blockchain: Why NEO?

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
|                                        | SHA-256                                                      | Curl/SHA-3                                                   | SHA256/RIPEMD160           |                                                              |

As a conclusion, we see {TODO: A summary of the table above }. There are also other concerns we can see from [HERE](https://hackernoon.com/why-i-find-iota-deeply-alarming-934f1908194b)



### 2.2 NEOT: NEO of Things

