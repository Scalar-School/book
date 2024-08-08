# 4. P2P Network

## 4.1 Bitcoin Nodes

Bitcoin operates on a peer-to-peer (P2P) network of computers. Any computer connected to the network is called a node. Anyone can download and install the open-source Bitcoin software to become a node. All nodes are treated equally, and no node is trusted by default. The system assumes that the majority of nodes (if mining nodes, then the hash power) will be honest, meaning they will not retransmit false or malformed transactions and blocks. However, in response to such behavior, a node may choose to discourage (flag its inappropriate behavior and perhaps disconnect in favor of new peers), disconnect, or ban the peer.

Due to the cryptographic architecture of the blockchain, Bitcoin software can verify whether received information over the network is intact. Each block in the blockchain contains a cryptographic hash of the previous block, creating a chain of interlinked blocks. This ensures that any alteration in a previous block would invalidate all subsequent blocks, making forgery impractical.

Full nodes are responsible for verifying and maintaining all ownership records according to consensus rules. Mining nodes also process transactions and add new blocks to the blockchain in exchange for a reward. Pruned nodes verify transactions and blocks but do not store a full copy of the blockchain. SPV (Simple Verification Nodes) rely on third-party full nodes for information about specific addresses and transactions on the network. Wallet software usually operates as SPV nodes.

Nodes are computers that participate in the Bitcoin network, running Bitcoin software. They perform several essential functions to keep the network secure, decentralized, and operating correctly. The primary roles of nodes include:

- **Transaction Verification:** Nodes verify that transactions follow all Bitcoin protocol rules, such as cryptographic signature verification and ensuring bitcoins are not double-spent.
- **Transaction and Block Propagation:** Nodes transmit (or retransmit) transactions and blocks to other nodes on the network, helping to disseminate information efficiently.
- **Blockchain Storage:** Nodes store a full or partial copy of the blockchain, ensuring that historical data is maintained and accessible.
- **Consensus Participation:** Nodes participate in the consensus process, helping validate new blocks and maintain the system's integrity.

There are different types of nodes on the Bitcoin network, each with its own functions and characteristics:

- **Full Nodes:** A full node maintains a complete copy of the blockchain and verifies all transactions and blocks according to Bitcoin rules. They are the backbone of the network, ensuring that all rules are followed and the blockchain is consistent across the network. They offer the highest level of security and privacy as they do not rely on third parties to verify transactions. They require more resources (storage space, bandwidth, and processing power) to operate efficiently. Full nodes ensure that the Bitcoin network remains secure and decentralized. The more full nodes there are, the harder it becomes for any malicious entity to compromise the network.
- **Mining Nodes:** Besides verifying transactions and blocks, they also participate in the mining process, adding new blocks to the blockchain and receiving rewards for it.
- **Pruned Nodes:** They verify the entire transaction and block history but delete the verified blocks, thus not storing a complete copy of the blockchain, only keeping the most recent blocks to save disk space. In the Bitcoin Core's bitcoin.conf file, you can determine how many blocks you want the system to keep on disk. The pruned node limits some RPC operations since you don't have the indexed copy of all transactions, but depending on your needs, it can be a great option.
- **SPV Nodes (Simplified Payment Verification):** Also known as "light nodes," they do not store a full copy of the blockchain. Instead, they download only the block headers and verify transactions based on inclusion proofs provided by full nodes. These nodes are ideal for devices with limited resources, like smartphones, as they consume fewer resources and bandwidth. Most Bitcoin wallets use light nodes in their composition. They rely on full nodes to obtain these inclusion proofs and therefore need to trust these full nodes for the correct verification of transactions.

You can run a Bitcoin node using Bitcoin Core, which is the reference implementation. In the ```bitcoin.conf``` file, you can choose the characteristics of this node, whether it will be full, pruned, etc.

- [Bitcoin Network Map](https://medium.com/@gloriazhao/map-of-the-bitcoin-network-c6f2619a76f3)
- [Full-node Projects](https://bitcoiner.guide/node/diy/)

There are also ways to create these nodes in the cloud, built from scratch or through systems that facilitate this process, such as:

- [Voltage](https://voltage.cloud/)
- [Clovyr](https://clovyr.app/)

## 4.2 Mempool

Bitcoin operates using two main network concepts for data transmission. One network is for the relay of pending transactions, called the mempool, and the other is for the relay of mined blocks with confirmed transactions, which is the blockchain itself.

The mempool is a space where pending (unconfirmed) transactions are stored by each node in the Bitcoin network. When a transaction is broadcast to the network, it first enters the mempool of the nodes until it is included in a mined block.

The mempool, short for "memory pool," is a crucial component of the Bitcoin system. It functions as a waiting area for unconfirmed transactions before they are included in a block and added to the blockchain. When a user makes a Bitcoin transaction, it is initially verified by nodes (computers participating in the Bitcoin network) and then sent to the mempool.

Here are some key points about the mempool:

- **Transaction Reception:** All transactions that have not yet been confirmed by miners are stored in the mempool. Each node in the Bitcoin network has its own version of the mempool, which may vary slightly between nodes.
- **Initial Verification:** Before a transaction is added to the mempool, it undergoes an initial verification to ensure it follows Bitcoin protocol rules (e.g., if the transaction inputs are valid and the transaction does not attempt to spend non-existent Bitcoins).
- **Transaction Priority:** Transactions in the mempool are prioritized based on transaction fees. Transactions with higher fees are generally selected first by miners, as miners are incentivized to maximize their profits by including transactions with higher fees in the blocks they mine.
- **Space Limitation:** Each node can set a size limit for its mempool. When the mempool reaches this limit, transactions with lower fees may be discarded to make room for newer transactions with higher fees.
- **Confirmation:** Once a miner includes a transaction in a block and the block is added to the blockchain, the transaction is removed from the mempool. This process confirms the transaction, ensuring it cannot be reversed or duplicated.

The mempool is essential for the efficient functioning of the Bitcoin network, ensuring that transactions are verified and prioritized before being permanently recorded on the blockchain.

## 4.3 Mainnet

The mainnet is the main Bitcoin network where real transactions occur, and bitcoins have monetary value. Developers and companies need to use the mainnet for production operations and final product launches.

Transactions are confirmed by miners and permanently recorded on the blockchain, ensuring high security and immutability. Developers and users interact through full nodes, wallets, and third-party APIs to carry out and monitor real transactions.

### Use Cases for Developers

#### Scenario 1: Launch of a New Bitcoin Wallet
A fintech company has developed a new Bitcoin wallet with advanced security and privacy features. After extensive testing on Testnet and Signet, they are ready to launch the wallet to the public. The company launches the new wallet on the mainnet, allowing users to start making real transactions with real bitcoins. The marketing team promotes the wallet, and developers monitor user feedback to adapt and improve the user experience based on real interactions. The company provides customer support to resolve any issues that may arise during wallet usage on the mainnet.

#### Scenario 2: Implementation of a Bitcoin Payment Service
An e-commerce platform decides to accept Bitcoin as a payment method and needs to integrate a secure and efficient Bitcoin payment service. The technical team integrates a Bitcoin payment service that allows customers to pay for goods and services using real bitcoins. The platform starts processing real transactions on the mainnet, receiving payments from customers and verifying the confirmation of transactions on the blockchain. The company implements accounting and reporting systems to track Bitcoin payments, ensuring compliance with financial regulations.

#### Scenario 3: Implementation of an International Remittance System
A financial services company launches an international remittance system that uses Bitcoin to transfer money between countries quickly and with low fees. The company processes remittances from customers, using Bitcoin to transfer funds from one country to another. Real bitcoins are used to carry out transactions on the mainnet. The platform automatically converts customers' fiat currencies into Bitcoin for transfer and then converts back to the recipient's fiat currency after the transaction. The company keeps detailed records of all remittance transactions, ensuring compliance with international money transfer regulations.

## 4.4 Regtest

Regtest (Regression Test) is a local test network that allows developers to create a fully controlled testing environment. It is not a public network and is controlled by the user. It is fully configurable by the user, allowing adjustments to mining difficulty and block time.

Ideal for initial development, regression testing, and fine-tuning functionalities without waiting for network confirmations. Coins in Regtest have no monetary value, facilitating safe and fast testing. Developers configure a Bitcoin node in Regtest mode and use RPC commands to create and manipulate blocks and transactions manually.

### Scenario 1: Initial Development of a New Protocol or Functionality
A team of developers is working on implementing a new protocol for Bitcoin, such as a new type of digital signature or a proposed update to the consensus system. The team can create blocks instantly in Regtest, allowing for rapid testing without the need to wait for block confirmations as would be necessary on Testnet or Mainnet.

- Regtest allows developers to adjust the mining difficulty and block time, creating specific conditions to test the new functionality in different scenarios.
- As Regtest is a local network, there is no interference from transactions or blocks from other developers. This allows for more focused and controlled testing.
- Allows for a rapid development cycle with immediate feedback.
- Enables the simulation of different network conditions in a controlled manner.
- Ideal for initial tests and fine-tuning new functionalities.

### Scenario 2: Integration and Automation Testing
A software company is developing a set of automated tools to monitor and manage Bitcoin transactions, including fraud detection and compliance audits.

- The company can automate the creation and verification of transactions in Regtest, ensuring that their monitoring scripts function correctly in various situations.
- They can create specific transactions and blocks to test the responses of the monitoring system, verifying that it correctly detects anomalous or suspicious behavior.
- Developers can simulate attacks or fraud attempts in Regtest without any risk, testing the effectiveness of their detection systems.
- The network facilitates the creation of an automated testing environment for continuous integration.
- Allows for detailed testing of monitoring and security systems, providing a safe environment for attack simulations and responses.

### Scenario 3: Development of Custom Applications
A startup is developing a custom micropayments application that uses Bitcoin transactions to facilitate payments between users. The startup can simulate thousands of transactions in a short period, testing the application's ability to handle a large volume of micropayments.

- Allows for testing the user experience (UX) when making transactions, adjusting the confirmation time and mining difficulty to evaluate different usage scenarios.
- Regtest facilitates an iterative development cycle, enabling the startup to make quick changes and immediately see the effects of those changes.

### Scenario 4: Regression Testing
A development team is implementing updates to an existing Bitcoin wallet software and needs to ensure that the new changes do not introduce bugs or failures. The team can create a set of automated tests that execute transactions, create blocks, and check the blockchain state to ensure everything works as expected after the updates.

- Regtest provides a consistent testing environment where the same tests can be repeated multiple times, ensuring that new changes do not negatively impact existing functionalities.
- Allows for the creation of specific conditions that may be difficult to reproduce on Testnet or Mainnet, such as network failures or specific attacks.

## 4.5 Testnet

Testnet (Test Network) is a public test network that mimics the behavior of the Mainnet. Bitcoins on Testnet have no monetary value, allowing for risk-free testing. Anyone can mine blocks and conduct transactions on Testnet. Testnet simulates the conditions of Mainnet, offering a realistic environment for development and testing. Coins on Testnet have no financial value, enabling secure tests. Developers use full nodes, wallets, and APIs specifying Testnet to simulate real operations without financial risk.

### Scenario 1: Development of a Bitcoin Wallet with Multisig Transaction Support
A fintech startup is developing a new Bitcoin wallet with multisig transaction support. They want to test the functionality of creating and spending a multisig transaction to ensure everything works as expected before launching the product to the public.

- Developers can create multisig addresses on Testnet without the risk of losing real funds.
- They can experiment with different M-of-N configurations (e.g., 2-of-3 or 3-of-5).
- Using Testnet, the team can send and receive test transactions to and from the multisig addresses. Since Testnet bitcoins have no real value, there is no financial risk involved.
- Testnet allows the team to simulate real network conditions, such as transaction propagation, variable transaction fees, and confirmation times. They can adjust transaction fees to see how this affects the confirmation speed.
- The team can easily obtain Testnet bitcoins from faucets to fund their test transactions, allowing for extensive testing without real financial costs.

### Scenario 2: Development of a New Wallet Feature
A software company is developing a new feature for its Bitcoin wallet that allows the automatic conversion of fiat transactions to Bitcoin. Developers can test the automatic conversion functionality, verifying that exchange rates are correctly applied and that Bitcoin transactions are sent and received without issues.

- Using Testnet, the team can adjust and test different levels of transaction fees to ensure the wallet automatically selects the most appropriate fee under varying network conditions.
- The company can simulate various real-use scenarios, such as high and low transaction frequencies, to ensure the new feature operates efficiently and stably.

### Scenario 3: Implementation of SegWit Transaction Support
A development team is implementing Segregated Witness (SegWit) transaction support in its Bitcoin payment application. Developers can create and send SegWit transactions on Testnet to ensure that the implementation is correct and that transactions are valid. The team can verify that their application is compatible with other wallets and services that support SegWit, ensuring interoperability.

- Using Testnet, the team can measure the performance of SegWit transactions compared to non-SegWit transactions, analyzing aspects such as confirmation speed and block space usage.

## 4.6 Signet

Signet is a proposed test network for Bitcoin that uses digital signatures instead of Proof-of-Work (PoW) for block validation. This approach enhances predictability and stability, providing an optimal environment for developers to test features and protocols.

The existing test networks like Testnet and Regtest have limitations. Testnet is notoriously unreliable due to frequent large reorganizations and irregular block generation. Regtest allows any participant to create blocks freely, which undermines its suitability for long-term multi-party testing. Signet aims to provide a more predictable and controlled environment, addressing these issues.

- **Block Validation:** Signet requires blocks to include a digital signature based on a specific challenge (scriptPubKey). This signature ensures that only authorized entities can create valid blocks.
- **Proof-of-Work Compatibility:** While Signet uses signatures for block validation, it retains the PoW block headers, allowing compatibility with existing software that supports PoW.
- **Custom Networks:** Users can create their own Signet networks by generating a key pair and a challenge scriptPubKey. This flexibility enables tailored testing environments for various protocols and features.
- **Signature-Based Validation:** Each block includes a signature that must be verified to validate the block. This process involves creating virtual transactions that ensure the block meets the challenge requirements.
- **Simplified Mining:** The signature process does not commit to the nonce value, allowing miners to generate PoW without repeatedly signing the block.
- **Genesis Block and Message Start:** A standardized genesis block and message start ensure consistency across different Signet networks.
- **Compatibility:** Signet is designed to work with existing Bitcoin software with minimal modifications. It can be integrated into current systems by adding network parameters without changing the fundamental block validation logic.
- **Protocol Testing:** Signet is ideal for testing new protocols like Eltoo or Taproot, providing a stable environment for integration testing over extended periods.
- **Exchange Testing:** Exchanges can use Signet to test their systems against realistic reorg scenarios, ensuring their software handles such events correctly.
- **Wallet Testing:** Signet allows wallet developers to test their software in a controlled environment, verifying their reorg handling and other critical functionalities.
- **Centralized Control:** The centralized nature of Signet enables easy execution of global tests, such as scheduled reorgs, making it more predictable than Testnet.
- **Community Usage:** While anyone can create a custom Signet, having a default, trusted Signet network can foster a common testing ground, reducing fragmentation and enhancing the effectiveness of community testing efforts.

Signet offers a robust, predictable alternative to existing test networks, addressing their limitations and providing a flexible, controlled environment for extensive testing of Bitcoin features and protocols.

### Use Cases for Controlled Testing on Signet

#### Scenario 1: Implementation of a Risk Management System for a Large Exchange
A large exchange is implementing a new risk management system involving complex transactions and smart contracts. The reliability and predictability of the test environment are crucial to ensure the system functions flawlessly. Signet allows the exchange to conduct tests with complex transactions and smart contracts in a controlled environment.

- Transactions can include custom scripts or advanced features that need rigorous validation.
- With blocks signed by trusted entities, the exchange can be confident that the testing environment will be stable and free of unexpected behaviors like spam attacks or sudden changes in mining difficulty.
- Signet ensures that test transactions are confirmed predictably, allowing the development team to focus on validating functionalities without worrying about network failures.
- It offers an environment where security audits and compliance checks can be reliably conducted, ensuring the risk management system meets necessary standards before launch.

#### Scenario 2: Security and Resilience Testing
A cybersecurity company is developing a new security solution for Bitcoin transactions and needs to conduct extensive tests to ensure its solution withstands various types of attacks. On Signet, the company can simulate attacks such as double spending, replay attacks, and others, knowing the environment is controlled and predictable.

- The security solution can be tested against simulated attacks to ensure all defenses work correctly.
- Signet allows detailed monitoring and logging of all activities, facilitating the analysis of how the security solution responds to different threats.

#### Scenario 3: Development of Advanced Smart Contracts
A blockchain company is developing advanced smart contracts for complex financial applications, such as decentralized loans and derivatives. The company can develop and test complex smart contracts on Signet, ensuring that all functions and conditions execute correctly.

- Signet provides an environment where testing conditions are stable and predictable, allowing rigorous testing of contract logic and security.
- Developers can validate that the smart contracts interact correctly with other parts of the system and that all transactions are recorded as expected.

## 4.7 Forks

A fork is a change or divergence in the software, blockchain, or network consensus. Forks can be categorized into two main types: hard forks and soft forks. Forks refer to changes in the Bitcoin protocol that result in a split in the blockchain, leading to the creation of a new path or a new blockchain. These changes can be classified as hard forks or soft forks, depending on backward compatibility. Soft forks are backward compatible, whereas hard forks create a new type of cryptocurrency incompatible with the original Bitcoin.

### Hard Forks

Hard forks are non-backward-compatible divergences in the Bitcoin protocol or block history. In a hard fork, nodes must adopt new consensus rules, which can be looser or different from the previous rules. Nodes that do not update their software will see blocks produced under the new rules as invalid. A hard fork is a permanent change in the consensus rules that old nodes cannot follow.

On August 1, 2017, while the Bitcoin network was about to activate Segregated Witness (SegWit), a part of the network followed an alternative scaling path that was not backward compatible, increasing the base block size without SegWit. This resulted in the creation of the forked cryptocurrency known as Bitcoin Cash (BCH).

### Soft Forks

Soft forks are backward-compatible changes to the Bitcoin protocol. In a soft fork, nodes opt for tightening or restricting the consensus rules. Nodes that do not update will continue to receive new blocks and recognize them as valid as long as these blocks follow the old rules.

#### Examples of Soft Forks

- **Segregated Witness (SegWit):** Introduced as a soft fork, SegWit changes how transaction data is stored, increasing transaction capacity without increasing block size.
- **Pay to Script Hash (P2SH):** A soft fork that resulted in the implementation of multi-signature wallets on the Bitcoin network.

Soft fork updates can cause temporary splits in the blockchain, but enforcement by a majority of hash power ensures eventual convergence on the same transaction history.

### Types of Soft Forks

- **Miner Activated Soft Fork (MASF):** A soft fork activated by the miners' hash power. Miners signal their support for the change, and when a certain threshold of support is reached, the change is activated.
- **User Activated Soft Fork (UASF):** A soft fork activated by users. Nodes that wish to enforce the new consensus rules opt to implement the update, regardless of miner support. A notable example is the activation of SegWit through a UASF.

#### Importance of UASF

The User Activated Soft Fork (UASF) is significant because it demonstrates the power of Bitcoin users to influence protocol changes independently of miner support.

On August 1, 2017, the UASF was used to activate SegWit on the Bitcoin network. Despite initial resistance from some miners, user pressure led to the successful implementation of SegWit, showing that user consensus can trigger important protocol changes.

### Detecting Hard Forks or Wrong Networks

To ensure you are on the correct network and not on a hard fork or wrong network, there are several practices and checks that nodes perform:

- **Block Headers:** Nodes check the chain of block headers to ensure they are on the longest and valid chain. The longest chain is the one with the most accumulated work (proof-of-work).
- **Checkpoints:** Certain nodes use checkpoints, which are blocks at specific heights that are well known and accepted by the Bitcoin community. This helps ensure the node is on the correct chain.
- **Software Version:** Using the latest version of Bitcoin Core software (or another reliable implementation) ensures the node follows the most up-to-date consensus rules.
- **Network Connections:** Connecting to known and trusted nodes on the Bitcoin network helps ensure you are on the correct network. Many Bitcoin clients come with a list of pre-configured trusted nodes.

Suppose you set up a Bitcoin node using Bitcoin Core software. When the node connects to the network, it:

- Begins downloading and verifying the blockchain from the genesis block.
- Validates each block and transaction according to the consensus rules.
- Connects to other nodes and receives block headers to ensure it is on the longest chain.
- Uses checkpoints to ensure it is not following an incorrect fork.

The Bitcoin system is designed to operate in a decentralized and secure manner, assuming that most nodes will be honest due to economic incentives and mutual verification of consensus rules. Although no individual node is trusted by itself, the network as a whole maintains its integrity through continuous verification and decentralization.

To ensure you are using a legitimate and secure version of Bitcoin Core software, download it only from the official Bitcoin Core repository on [GitHub](https://github.com/bitcoin/bitcoin).
