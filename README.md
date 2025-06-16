# MyNotesMyReferences
This Repository is purely to capture my notes to refresh concepts and ideas. Contains following content:

- *Storage Variables*
- *Functions: //Keywords: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external'*
- *Memory Storage and Call Data*
- *Override Functions: //Keywords: Virtual, Override*
- *Transactions - 'msg.value Transfers*
- *Keywords- For Gas Efficiency*
- _Foundry Keywords/Commands_
- _Best Practices (for writing Code, Deploy scripts and for Testing)_
- _Code Layout for Solidity_
- [_Events_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#events)
- [_Cyfrin - Takeaway from each module_](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#cyfrin---takeaway-from-each-module)
- [Upgradable Smart Contracts and Proxy pattern](https://github.com/MUdayVarma/MyNotesMyReferences?tab=readme-ov-file#upgradable-smart-contracts-and-proxy-pattern) 

  
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
  - #forge script script/DeployContractName.sol or #forge script script/DeployContractName.sol --rpc-url http://URL // Deploys Contract to either local temporary anvil or on the specified RPC/Blockchain network
  - forge coverage --fork-url $SEPOLIA_RPC_URL // This command displays which parts of your code are covered by tests
  - #forge create NameOfContract --rpc-url --intercive // To deploy a contract into anvil (virtuel test blockchain environment) by using the fake address and private key or to any test or main net as well
  - #forge fmt // Formats the solidity code in VSCode editor 


  - #anvil // Local virtual Blockchain environment



  - #cast wallet import defaultkey --interactive // Using Keystore file for not exposing the private key text format in vscode or in .env file or in github repo or in any other format..
      #Enter Private Key:
      #Enter password:
  - #cast wallet list //Lists all those defaultkeys which are encrypted for security (as with above command)



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

## **Upgradable Smart Contracts and Proxy pattern]**

- Proxy pattern is a design pattern that is commonly used to enable smart contract upgrades by directing user interactions to a stable address that delegates execution to a separate, replaceable logic contract.

- Examples:

  - 'call':  Consider Contract P calling a function in Contract L using a specific low-level mechanism. If the `msg.sender` observed *within* the executed code of Contract L is the address of Contract P itself, then the mechanism used is 'call'.
 
  - When Contract A executes a function in Contract B using `delegatecall`, then Contract A's storage is modified using Contract B's logic.
 
  - Behavior of `delegatecall` differ fundamentally from a standard external `call` (i.e. `delegatecall` executes the target contract's code in the caller's context, modifying the caller's storage, while `call` executes in the target's context, modifying the target's storage.)
 
  - A significant potential drawback or risk introduced by implementing upgradability in smart contracts via proxy patterns is Increased centralization risk, as an administrative entity gains the power to arbitrarily change the contract's logic.
 
  - A key consideration when using low-level assembly language like Yul within smart contracts, as is sometimes done in proxy implementations is, It bypasses many Solidity safety checks, increasing the risk of subtle bugs and security vulnerabilities.


------------------------------------------------------------------------------
