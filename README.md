# MyNotesMyReferences
This Repository is purely to capture my notes to refresh concepts and ideas. Contains following content:

- *Storage Variables*
- *Functions: //Keywords: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external'*
- *Memory Storage and Call Data*
- *Override Functions: //Keywords: Virtual, Override*
- *Transactions - 'msg.value Transfers*
- *Keywords- For Gas Efficiency*

  
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

