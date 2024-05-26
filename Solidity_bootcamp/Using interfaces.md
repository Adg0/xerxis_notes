- Fallback and receive functions
- External calls
- Attaching “mismatched” contracts
- Why some functions work and others don’t because of the “MethodID”
### Restricting access to functions
- Wrapping up contents
    - Modifier
    - Assertion inside modifiers
    - Message Sender
    - Visibility
    - Mutability
- Implementing basic access control on _setText_

### References

[https://docs.soliditylang.org/en/latest/common-patterns.html#restricting-access](https://docs.soliditylang.org/en/latest/common-patterns.html#restricting-access)

[https://docs.soliditylang.org/en/latest/units-and-global-variables.html#block-and-transaction-properties](https://docs.soliditylang.org/en/latest/units-and-global-variables.html#block-and-transaction-properties)

### Code reference

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.25;

contract HelloWorld {
    string private text;
    address public owner;

    constructor() {
        text = "Hello World";
        owner = msg.sender;
    }
    
    modifier onlyOwner()
    {
        require (msg.sender == owner, "Caller is not the owner");
        _;
    }

    function helloWorld() public view returns (string memory) {
        return text;
    }

    function setText(string calldata newText) public onlyOwner {
        text = newText;
    }

    function transferOwnership(address newOwner) public onlyOwner {
        owner = newOwner;
    }
}
```