```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.25;

contract HelloWorld {
    string private text;

    constructor() {
        text = initialText();
    }
    
    function helloWorld() public view returns (string memory) {
        return text;
    }

    function setText(string calldata newText) public {
        text = newText;
    }

    function initialText() public pure returns (string memory) {
        return "Hello World";
    }

    function _isUnchanged() internal view returns (bool) {
        return keccak256(bytes(text)) == keccak256(bytes(initialText()));
    }

    function textHasChanged() public view returns (bool returnValue_) {
        returnValue_ = !_isUnchanged();
    }

    function _restore() internal {
        text = initialText();
    }
    
    function restore() public returns (bool) {
        if (_isUnchanged()) return false;
        _restore();
        return true;
    }
}
```