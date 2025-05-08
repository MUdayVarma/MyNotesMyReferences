# MyNotesMyReferences
This Repository is purely to capture my notes to refresh concepts and ideas


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
