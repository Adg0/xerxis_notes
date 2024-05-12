- Part 1:
	- Contract interactions using Remix
	- Viewing state changes through functions
- Part 2: 
	- State changing calls on testnet
	- Using interfaces to interact with other contracts
```solidity
interface HelloWorldInterface {
    function helloWorld() external view returns (string memory);
    function setText(string memory newText) external;
}

contract HelloWorld is HelloWorldInterface {
    ...
}
```
- Part 3: 
	- Payable functions
	- Experimenting with payable calls
```solidity
function setText(string memory newText) public payable {
    text = newText;
}
```
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

    function setText(string memory newText) public {
        text = newText;
    }
}
```

