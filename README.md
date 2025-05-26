# MyNotesMyReferences
This Repository is purely to capture my notes to refresh concepts and ideas. Contains following content:

- *Storage Variables*
- *Functions: //Keywords: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external'*
- *Memory Storage and Call Data*
- *Override Functions: //Keywords: Virtual, Override*
- *Transactions - 'msg.value Transfers*
- *Keywords- For Gas Efficiency*
- _Foundry Keywords/Commands_
- _Best Practices for Deploy scriptrs and Unit/Integrations Tests_

  
------------------------------------------------------------------------------
**Storage Variables**

- Variables declared in contract scope are storage variables
- Solidity stores these in contiguous storage slots
- Things to know about storage slots
  - 🔭 variables stored in contract scope allocate a storage slot (except for constant)
  - 📏 slots are 32 bytes (0x1 means 0x000....001)
  - 🔢 solidity stores variables contiguously (0x0, 0x1, etc...)
  - 💸 reading/writing to storage is relatively super expensive to other opcodes
  - 🎒 variables can be packed together, automatically or manually
    
------------------------------------------------------------------------------

**FUNctions 🕺** //Keywords meaning: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external' 

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

**Memory Storage and Call Data**

<img width="1000" alt="image" src="https://github.com/user-attachments/assets/29a9138f-2a6a-4b8b-b982-3e636426cba6" />

Important Calls: REMEMBER

Calldata: Temporary variables that cannot be modified

Memory: Temporary variables that can be modified

Storage: Permanent variables that can be modified

<img width="878" alt="image" src="https://github.com/user-attachments/assets/a75bc995-de69-4d3f-bed8-cbc482a858fe" />



------------------------------------------------------------------------------

**Override Functions: //Keywords: Virtual, Override**

- Virtual: Any function in base/parent contract which needs to be overridden has to be specified as 'virtual' in its definition
- Override: Any function in inherited/child contract that needs to be overide its functionality, needs to be specified as 'override' in its definition



------------------------------------------------------------------------------

**Transactions - 'msg.value' Transfers**

<img width="791" alt="image" src="https://github.com/user-attachments/assets/cbfa5362-c4da-437e-8d3d-f56069c42936" />

------------------------------------------------------------------------------

**Keywords- For Gas Efficiency**

- The **'immutable'** keyword allows values to be set at runtime, while the **'constant'** keyword requires values to be set at compile time.
        - Constant: CONSTANT_VARIABLENAME
        - Immutable: i_variablename
- Revert (replacing 'require'): error CODENAME
- Modifier: If condition no met, revert before proceeding
        - Valid way to add Modifier to a function is: _function myFunction() public onlyAdmin { ... }_
- Special Functions:
        -  receive:--> receive() external payable {}
        -  fallback:--> receive() external payable {}
    -  NOTE:
        - The receive function is specifically designed to handle Ether transfers without data and is automatically invoked when Ether.
        - The fallback function is used for handling calls with data or when the receive   function is not defined. The fallback function can also handle Ether transfers with data._


  
------------------------------------------------------------------------------

**Foundry - Keywords and Commands**

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


**Best Practices for Unit/Integrations Tests and Deploy scripts**

1) Write deploy scripts
    a) Note, this will not work on zksync  
2) Write Tests
    a) Local Chain
    b) Forked testnet
    c) Forked mainnet
     



------------------------------------------------------------------------------


