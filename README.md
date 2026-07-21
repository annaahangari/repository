# My Base Learning Repository

This repository is my personal space to document everything I'm learning about Base - Coinbase's Layer 2 on Ethereum.

Goal: Build knowledge, practice Solidity, and explore the ecosystem step by step.

### What is Base?

Base is Coinbase's Ethereum Layer 2 blockchain. It offers fast transactions and very low fees while inheriting Ethereum's security.

I'm using this repo to document my learning journey and practice building on it.

### First Steps with Solidity on Base

I'm starting to learn Solidity to build smart contracts that can be deployed on Base.

Low fees make it perfect for testing and experimenting without high costs.

### Simple Counter Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Counter {
    uint256 public count = 0;

    function increment() public {
        count += 1;
    }

    function getCount() public view returns (uint256) {
        return count;
    }
}

### Simple Frontend for Counter Contract

```html
<button onclick="increment()">Increment</button>
<p>Count: <span id="count">0</span></p>

<script>
  // Connect to contract on Base and call increment()
</script>

### Adding Events to Counter

```solidity
event CountIncremented(address caller, uint256 newCount);

function increment() public {
    count += 1;
    emit CountIncremented(msg.sender, count);
}

### Listening to Events in Frontend

```javascript
contract.on("CountIncremented", (caller, newCount) => {
  document.getElementById("count").innerText = newCount;
});

### Adding Owner Control

```solidity
address public owner;

constructor() {
    owner = msg.sender;
}

modifier onlyOwner() {
    require(msg.sender == owner, "Not owner");
    _;
}

function reset() public onlyOwner {
    count = 0;
}

### Transfer Ownership

```solidity
function transferOwnership(address newOwner) public onlyOwner {
    require(newOwner != address(0), "Invalid owner");
    owner = newOwner;
}

### Event for Ownership Transfer

```solidity
event OwnershipTransferred(address previousOwner, address newOwner);

function transferOwnership(address newOwner) public onlyOwner {
    emit OwnershipTransferred(owner, newOwner);
    owner = newOwner;
}

### Pause Functionality

```solidity
bool public paused = false;

modifier whenNotPaused() {
    require(!paused, "Contract is paused");
    _;
}

function pause() public onlyOwner {
    paused = true;
}

function unpause() public onlyOwner {
    paused = false;
}
