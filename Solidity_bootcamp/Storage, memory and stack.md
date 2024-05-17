- Storage locations
    - Account storage
- Replacing memory with calldata for saving gas

### References

[https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#storage-memory-and-the-stack](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html#storage-memory-and-the-stack)

[https://docs.soliditylang.org/en/latest/types.html#bytes-and-string-as-arrays](https://docs.soliditylang.org/en/latest/types.html#bytes-and-string-as-arrays)

### Code reference
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.25;

contract HelloWorld {
    string private text;

    constructor() {
        text = "Hello World";
    }

    function helloWorld() public view returns (string memory)  {
        return text;
    }

    function setText(string calldata newText) public {
        text = newText;
    }
}
```
