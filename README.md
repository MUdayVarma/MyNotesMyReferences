# MyNotesMyReferences
This Repository is purely to capture my notes to refresh concepts and ideas. Contains following content:

- *Storage Variables*
- *Functions: //Keywords meaning: 'pure', 'view', 'payable' |||| 'private', 'internal', 'public', 'external' *
- *Memory Storage and Call Data*

  
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
