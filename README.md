# MyNotesMyReferences
This Repository is purely to capture my notes to refresh concepts and ideas. Contains following content:

- [*Storage Variables*](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#storage-variables)
- [*Functions: //Keywords: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external'*](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#functions-)
- [_Functions: //Keywords within: 'unchecked' |||| abstract |||| emit_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#functions-keywords-within)
- [*Memory Storage and Call Data*](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#memory-storage-and-call-data) 
- [*Override Functions: //Keywords: Virtual, Override*](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#override-functions-keywords-virtual-override) 
- [*Transactions - 'msg.value Transfers*](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#transactions---msgvalue-transfers) 
- [*Keywords- For Gas Efficiency*](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#keywords--for-gas-efficiency) 
- [_Foundry Keywords/Commands_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#foundry---keywords-and-commands) 
- [_Best Practices (for writing Code, Deploy scripts and for Testing)_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#best-practices-for-for-writing-code-deploy-scripts-and-for-testing)
- [_Code Layout for Solidity_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#code-layout-for-solidity)
- [_Events_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#events)
- [_Cyfrin - Takeaway from each module_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#cyfrin---takeaway-from-each-module)
- [Upgradable Smart Contracts and Proxy pattern](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#upgradable-smart-contracts-and-proxy-pattern)
- [General terms/concepts: //URIs=URLs+URNs](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#general-termsconcepts--uriurlurn--erc721erc20)
- [Climate-tech || Climate action || Climate change || ==>> Terminologies](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#climate-tech--climate-action--climate-change---terminologies)
- [Tokenized Real-World Assets (RWAs)](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#tokenized-real-world-assets-rwas)

  
------------------------------------------------------------------------------
## **Storage Variables**

- Variables declared in contract scope are storage variables
- Solidity stores these in contiguous storage slots
- Things to know about storage slots
  - 🔭 variables stored in contract scope allocate a storage slot (except for constant)
  - 📏 slots are 32 bytes (0x1 means 0x000....001)
  - 🔢 solidity stores variables contiguously (0x0, 0x1, etc...)
  - 💸 reading/writing to storage is relatively super expensive to other opcodes
  - 🎒 variables can be packed together, automatically or manually
    
------------------------------------------------------------------------------

## **FUNctions 🕺** 

**//Keywords meaning: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external'**


contract Example {
    function example1() private pure {
  
          // private: call me within this contract

          // pure: I cannot read/write to storage
    }

    function example2() internal view {

        // internal: call me within this contract (+ inheritance!)
  
        // view: I can read from storage, not write**
    
    }
  
    function example3() public payable {
    
        // public: call me inside and outside this contract
  
        // payable: send me some ether!
  
    }
  

    function example4() external {
    
        // external: call me from outside this contract
    
    }

}

------------------------------------------------------------------------------

## **FUNctions Keywords within** 

- **'unchecked'**: 

- **'abstract'**:

- **'emit'**: 


------------------------------------------------------------------------------

## **Memory Storage and Call Data**

<img width="500" alt="image" src="https://github.com/user-attachments/assets/29a9138f-2a6a-4b8b-b982-3e636426cba6" />

Important Calls: REMEMBER

Calldata: Temporary variables that cannot be modified

Memory: Temporary variables that can be modified

Storage: Permanent variables that can be modified

<img width="500" alt="image" src="https://github.com/user-attachments/assets/a75bc995-de69-4d3f-bed8-cbc482a858fe" />



------------------------------------------------------------------------------

## **Override Functions: //Keywords: Virtual, Override**

- **Virtual**: Any function in base/parent contract which needs to be overridden has to be specified as 'virtual' in its definition
- **Override**: Any function in inherited/child contract that needs to be overide its functionality, needs to be specified as 'override' in its definition



------------------------------------------------------------------------------

## **Transactions - 'msg.value' Transfers**

<img width="400" alt="image" src="https://github.com/user-attachments/assets/cbfa5362-c4da-437e-8d3d-f56069c42936" />

------------------------------------------------------------------------------

## **Keywords- For Gas Efficiency**

- The **'immutable'** keyword allows values to be set at runtime, while the **'constant'** keyword requires values to be set at compile time.
        - Constant: CONSTANT_VARIABLENAME
        - Immutable: i_variablename
- **Revert** (replacing 'require'): error CODENAME

- **Modifier**: If condition no met, revert before proceeding
        - Valid way to add Modifier to a function is: _function myFunction() public onlyAdmin { ... }_
  
- Special Functions:

        -  **receive**:--> receive() external payable {}

        -  **fallback**:--> receive() external payable {}
  
    -  NOTE:
        - The receive function is specifically designed to handle Ether transfers without data and is automatically invoked when Ether.
        - The fallback function is used for handling calls with data or when the receive   function is not defined. The fallback function can also handle Ether transfers with data.


  
------------------------------------------------------------------------------

## **Foundry - Keywords and Commands**

- Commands
  - #foundryup //To check if foundry is installed properly and file path is set for working with the programs
  - #foundryup-zksync //Similar to abobe but specifically needed for running command for ZKSync chain
 
    
  - #forge --version || #cast --version || #anvil --version || #chisel --version //Check the current version of forge
  - #forge --help //To get the list of action commands along with the description
  - #forge init or #forge init --force //Foundry initializes the new project directory with standard Foundry structure i.e. core folders (`src`, `test`, `script`) and the default example contract
  - #forge install path or github url //Is the command we are using to install one or multiple dependencies (e.g. forge install smartcontractkit/chainlink-brownie-contracts@1.3.0 --no-commit)
  - #forge compile or #forge build // To compile/build the solidity files
  - #forge test // Runs all test suits and logs details of what is tested, how the results are displayed, where is the test conducted and many more!
  - #forge script script/DeployContractName.s.sol or #forge script script/DeployContractName.s.sol --rpc-url http://URL // Deploys Contract to either local temporary anvil or on the specified RPC/Blockchain network
  - forge script script/DeployContractName.s.sol:DeployContractName --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY -vvvv
  - **With optimization flags to avoid stack too deep**

    forge script script/StackOptimizedDeploy.s.sol \
    --rpc-url $SEPOLIA_RPC_URL \
    --private-key $PRIVATE_KEY \
    --broadcast \
    --optimize \
    --optimizer-runs 200 \
    --via-ir \
    --verify \
    --etherscan-api-key $ETHERSCAN_API_KEY \
    -vvvv
  - forge coverage --fork-url $SEPOLIA_RPC_URL // This command displays which parts of your code are covered by tests
  - #forge create NameOfContract --rpc-url --intercive // To deploy a contract into anvil (virtuel test blockchain environment) by using the fake address and private key or to any test or main net as well
  - #forge fmt // Formats the solidity code in VSCode editor 


  - #anvil // Local virtual Blockchain environment



  - #cast wallet import defaultkey --interactive // Using Keystore file for not exposing the private key text format in vscode or in .env file or in github repo or in any other format..
      #Enter Private Key:
      #Enter password:
  - #cast wallet list //Lists all those defaultkeys which are encrypted for security (as with above command)

  - **FFI:** In Foundry, the 'ffi = true' setting in your foundry.toml file enables the use of Foreign Function Interface (FFI) — which allows your smart contracts or scripts to call external shell commands during testing or scripting. FFI lets you:

      - Fetch dynamic data during tests (e.g., from an API, CLI, or database)

      - Interact with off-chain systems

      - Run custom scripts (e.g., Python, Bash) that return values used in your tests


  - **.toml:** A '.toml' file is a configuration file written in the TOML (Tom's Obvious, Minimal Language) format — a human-readable format for specifying key-value pairs, tables, and arrays, often used for tool and project settings. .toml files are commonly used in:

      - Build tools (e.g., foundry.toml in Foundry, Cargo.toml in Rust)

      - Package managers

      - Project configuration in a clean and structured way



------------------------------------------------------------------------------


## **Best Practices for (for writing Code, Deploy scripts and for Testing)**

1) Writing Code

    a) **Checks, Effects, Interactions (CEI) Pattern** - To structure Solidity functions for improved security and gas efficiency.

       - Checks: Check condition if need to proceed further in the function i.e. next steps or revert if required
   
       - Efefcts: Internal Contract State changes

       - Interactions: External Contract Interactions
   
    b) More importantly, this is the recommended sequence for structuring operations within a Solidity function to **prevent reentrancy (security atatcks)**

2) Write deploy scripts
   
    ////__Note, this will not work on zksync  

3) Write Tests

    a) Local Chain (Unit/Integrations Tests)

    b) Forked (using Alchemy API node as e.g. )  

    c) staging <- run tests on a mainnet or testnet

    d) Fuzz tests  // Fuzz testing primarily aims to challenge 'Protocol Invariants' aspect of a smart contract

       //fuzzing

       //statefull fuzz

       //stateless fuzz  ---- //Stateful fuzzing retains the contract state between test runs, while stateless fuzzing resets the state.

       //formal verification

4) Key Security and Testing practices

     a) Static analysis tools examines source code for potential bugs, vulnerabilities, and style adherence without actually running the program.

     b) Formal Verification primarily relies on mathematical proofs to verify system correctness.

     c) Tools like Slither, Aderyn, and Mythril fall under static analysis category of smart contract security analysis.

     d) Writing targeted automated tests, including fuzz tests is a technique that complements manual code review by systematically verifying functional correctness and uncovering bugs across diverse inputs.

     e) A significant security risk when running software obtained from untrusted sources directly on your primary computer system is that the software might access and compromise sensitive data or system resources.

------------------------------------------------------------------------------

## **Code Layout for Solidity**

// Layout of Contract:
// License Identfier
// version (pragma)
// imports
// errors
// interfaces, libraries, contracts
// Type declarations
// State variables
// Events
// Modifiers
// Functions

// Layout of Functions:
// constructor
// receive function (if exists)
// fallback function (if exists)
// external
// public
// internal
// private
// view & pure functions

------------------------------------------------------------------------------

## **Events**

- Whenever a Storage variable is updated in the contract, It is important to emit the information (i.e. through Events)
- Why Events are important
  // 1. Makes migration easier
  // 2. Makes front-end 'indexing' easier
  // Emit an event when we update a dynamic array or mapping
  // Named events with the function name reversed
  // 

------------------------------------------------------------------------------

## **Cyfrin - Takeaway from each module**

- Foundry Basic: 
  - Lottery/Raffle Contract: Data types i.e. enum, error, events; Using Tools i.e. Chainlink VRFs, Chainlink Automation; Fuzz Testing; Helper Configuration scripts
  - FundMe Contract: Writing deployment scripts and test cases i.e. Scripts to deploy on testnets, Unit/Integration tests, 'forked' and 'staging' tests Checking Code Coverage
  - Simple Storage Contract: Working with Foiundry i.e. understanding forge/cast/anvil/chesil tools and using them in development/deployment/testing, etc.

- Foundry Adv.:
  - ERC20: Writing ERC contracts
  - NFTs: Writing NFT contracts using IPFS storgae solutions   


------------------------------------------------------------------------------

## **Upgradable Smart Contracts and Proxy pattern**

- Proxy pattern is a design pattern that is commonly used to enable smart contract upgrades by directing user interactions to a stable address that delegates execution to a separate, replaceable logic contract.

- Examples:

  - 'call':  Consider Contract P calling a function in Contract L using a specific low-level mechanism. If the `msg.sender` observed *within* the executed code of Contract L is the address of Contract P itself, then the mechanism used is 'call'.
 
  - When Contract A executes a function in Contract B using `delegatecall`, then Contract A's storage is modified using Contract B's logic.
 
  - Behavior of `delegatecall` differ fundamentally from a standard external `call` (i.e. `delegatecall` executes the target contract's code in the caller's context, modifying the caller's storage, while `call` executes in the target's context, modifying the target's storage.)
 
  - A significant potential drawback or risk introduced by implementing upgradability in smart contracts via proxy patterns is Increased centralization risk, as an administrative entity gains the power to arbitrarily change the contract's logic.
 
  - A key consideration when using low-level assembly language like Yul within smart contracts, as is sometimes done in proxy implementations is, It bypasses many Solidity safety checks, increasing the risk of subtle bugs and security vulnerabilities.


------------------------------------------------------------------------------

## General Terms/Concepts : URI/URL/URN , ERC721/ERC20

- **URI:** A Uniform Resource Identifier (URI), formerly Universal Resource Identifier, is a unique sequence of characters that identifies an abstract or physical resource, such as resources on a webpage, mail address, phone number,books, real-world objects such as people and places, concepts. URIs are used to identify anything described using the Resource Description Framework (RDF), for example, concepts that are part of an ontology defined using the Web Ontology Language (OWL).

- **URL:** URIs which provide a means of locating and retrieving information resources on a network (either on the Internet or on another private network, such as a computer filesystem or an Intranet) are Uniform Resource Locators (URLs). Therefore, URLs are a subset of URIs, i.e. every URL is a URI (and not necessarily the other way around).

- **URN:** Other URIs provide only a unique name, without a means of locating or retrieving the resource or information about it; these are Uniform Resource Names (URNs).

**ERC721/ERC20**

- The ownership tracking of an ERC721 (NFT) token typically differ from an ERC20 token i.e. ERC721 maps unique token IDs to owner addresses, while ERC20 maps addresses to token balances.

- The fundamental difference between decentralized file storage networks and blockchain networks regarding their primary function is that 'Storage networks prioritize decentralized data storage and retrieval, while blockchains prioritize maintaining an immutable ledger and state computation'.

- 
------------------------------------------------------------------------------

## Climate-tech || Climate action || Climate change || ==>> Terminologies

- **Climate action frameworks**:
  
  - Paris Climate Accord
 
  - Task Force on Climate-Related Financial Disclosures (TCFD)
 
  - Taskforce on Nature-Related Financial Disclosures (TNFD)
 
  - The Montreal Protocol
 
  - The Glasgow Financial Alliance for net Zero, and
  
  - The Science-Based Targets Initiative
 
  - Environmental, Social, and Governance (ESG) standards
 
  - Distributed energy resources (DERs)
 
  - Solar Photovoltaics (PV)
 
  - Concentrated solar power (CSP)
 
  - Independent power producers (IPPs)
 
  - Transmission system operators (TSOs)
 
  - Distribution system operators (DSOs)
 
  - International Energy Agency (IEA)
 
  - Center for Climate and Energy Solutions (C2ES)

------------------------------------------------------------------------------

## Tokenized Real-World Assets (RWAs)
Source: https://cll-devrel.gitbook.io/tokenized-rwa-bootcamp-2024 

**Tokenized Real-World Assets (RWAs):** 
Tokenized real-world assets (RWAs) are blockchain-based digital tokens that represent physical and traditional financial assets, such as cash, commodities, equities, bonds, credit, artwork, and intellectual property. The tokenization of RWAs marks a significant shift in how these assets can be accessed, exchanged, and managed, unlocking an array of new opportunities for both blockchain-powered financial services and a wide variety of non-financial use cases underpinned by cryptography and decentralized consensus.

**Tokenizing Real-World Assets**
Tokenizing real-world assets involves representing the ownership rights of assets as onchain tokens. In this process, a digital representation of the underlying asset is created, enabling onchain management of the asset’s ownership rights and helping to bridge the gap between physical and digital assets. 

**Types of Tokenized Assets**

Tokenized assets can be classified by three key traits.

**(A) Asset Location:**

  - (a) OnChain Asset: 👈 These wouldn't be considered real-world assets. These digital assets, like ERC-20 tokens and NFTs, exist natively on a blockchain. They are created, stored, and transferred within the blockchain. 

  - (b) OffChain Asset: These real-world assets exist outside a blockchain, like tokenized real estate, stocks, or commodities, but are represented digitally onchain through tokenization. 

**(B) Collateral Location:** 

  - (a) OnChain Collateral: Collateral is stored directly onchain. These could be cryptocurrencies or tokenized assets held in a smart contract as security. 

  - (b) OffChain Collateral: Collateral involves real-world assets held outside the blockchain but linked to onchain tokens. It could be held by a custodian or in a traditional financial institution. 

**(C) Backing Type:**

  - (a) Direct Backing: The tokenized asset directly represents ownership or a claim on the underlying asset. Each token corresponds to a specific portion of a real-world asset. 

  - (b) Indirect Backing, AKA Synthetic: Tokens that derive their value from the underlying asset but don't represent direct ownership, tracking the value of the assets to represent their value. 

**8 Types of Tokenized Assets**

  - Onchain asset, onchain collateral, direct backing; Example: WETH (Wrapped Ethereum)

  - Onchain asset, onchain collateral, indirect backing (synthetic)[ Example: WBTC (Wrapped Bitcoin)

  - Onchain asset, offchain collateral, direct backing; Hypothetical example: A wrapped BTC ETF

  - Onchain asset, offchain collateral, indirect backing (synthetic); Hypothetical example: A wrapped BTC ETF that represents an ETH ETF

  - Offchain asset, onchain collateral, direct backing; Hypothetical example: A stablecoin backed by other stablecoins

  - Offchain asset, onchain collateral, indirect backing (synthetic); Example: DAI 

  - Offchain asset, offchain collateral, direct backing; Example: USDC (USD Coin) 

  - Offchain asset, offchain collateral, indirect backing (synthetic); Example: USDT (Tether) 

------------------------------------------------------------------------------
