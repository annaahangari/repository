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

### Events for Pause/Unpause

```solidity
event Paused(address account);
event Unpaused(address account);

function pause() public onlyOwner {
    paused = true;
    emit Paused(msg.sender);
}

### Useful View Functions

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

function getOwner() public view returns (address) {
    return owner;
}

### Receive Function

```solidity
receive() external payable {
    emit FundsReceived(msg.sender, msg.value);
}

event FundsReceived(address sender, uint256 amount);

### Fallback Function

```solidity
fallback() external payable {
    emit FallbackCalled(msg.sender, msg.value, msg.data);
}

event FallbackCalled(address sender, uint256 value, bytes data);

### ERC165 supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public view virtual override returns (bool) {
    return interfaceId == type(IERC721).interfaceId || super.supportsInterface(interfaceId);
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Renounce Ownership

```solidity
function renounceOwnership() public onlyOwner {
    owner = address(0);
    emit OwnershipRenounced(msg.sender);
}

event OwnershipRenounced(address previousOwner);

### Version Function

```solidity
string public version = "1.0";

function getVersion() public view returns (string memory) {
    return version;
}

### isOwner View Function

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Owner Function

```solidity
function getOwner() public view returns (address) {
    return owner;
}

### ERC165 supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public view virtual returns (bool) {
    return interfaceId == 0x01ffc9a7; // ERC165
}

### Receive Function

```solidity
receive() external payable {
    emit Received(msg.sender, msg.value);
}

event Received(address sender, uint256 value);

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public view virtual returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Withdraw Function

```solidity
function withdraw() public onlyOwner {
    payable(owner).transfer(address(this).balance);
}

### Fallback Function

```solidity
fallback() external payable {
    emit FallbackCalled(msg.sender, msg.value);
}

event FallbackCalled(address sender, uint256 value);

### Transfer Ownership

```solidity
function transferOwnership(address newOwner) public onlyOwner {
    require(newOwner != address(0), "Invalid address");
    owner = newOwner;
}

### Balance Mapping

```solidity
mapping(address => uint256) public balances;

function deposit() public payable {
    balances[msg.sender] += msg.value;
}

### Total Deposits Tracking

```solidity
uint256 public totalDeposits;

function deposit() public payable {
    balances[msg.sender] += msg.value;
    totalDeposits += msg.value;
}

### Deposit Limit

```solidity
uint256 public maxDeposit = 1 ether;

function deposit() public payable {
    require(msg.value <= maxDeposit, "Exceeds max deposit");
    balances[msg.sender] += msg.value;
}

### Minimum Deposit

```solidity
uint256 public minDeposit = 0.01 ether;

function deposit() public payable {
    require(msg.value >= minDeposit, "Below minimum");
    balances[msg.sender] += msg.value;
}

### Total Users Tracking

```solidity
uint256 public totalUsers;

function deposit() public payable {
    if (balances[msg.sender] == 0) {
        totalUsers += 1;
    }
    balances[msg.sender] += msg.value;
}

### Emergency Pause for Deposits

```solidity
bool public depositsPaused = false;

function deposit() public payable {
    require(!depositsPaused, "Deposits are paused");
    balances[msg.sender] += msg.value;
}

### Blacklist Feature

```solidity
mapping(address => bool) public isBlacklisted;

function deposit() public payable {
    require(!isBlacklisted[msg.sender], "Address is blacklisted");
    balances[msg.sender] += msg.value;
}

### Whitelist Feature

```solidity
mapping(address => bool) public isWhitelisted;
bool public whitelistEnabled = false;

function deposit() public payable {
    if (whitelistEnabled) {
        require(isWhitelisted[msg.sender], "Not whitelisted");
    }
    balances[msg.sender] += msg.value;
}

### Fee on Deposit

```solidity
uint256 public depositFee = 1; // 1%

function deposit() public payable {
    uint256 fee = (msg.value * depositFee) / 100;
    uint256 amount = msg.value - fee;
    balances[msg.sender] += amount;
}

### Withdraw Fee

```solidity
uint256 public withdrawFee = 1; // 1%

function withdraw(uint256 amount) public {
    require(balances[msg.sender] >= amount, "Insufficient balance");
    uint256 fee = (amount * withdrawFee) / 100;
    uint256 netAmount = amount - fee;
    balances[msg.sender] -= amount;
    payable(msg.sender).transfer(netAmount);
}

### Claim Fees

```solidity
function claimFees() public onlyOwner {
    uint256 amount = totalFeesCollected;
    totalFeesCollected = 0;
    payable(owner).transfer(amount);
}

### Basic Referral System

```solidity
mapping(address => address) public referrer;

function deposit(address _referrer) public payable {
    if (referrer[msg.sender] == address(0) && _referrer != msg.sender) {
        referrer[msg.sender] = _referrer;
    }
    balances[msg.sender] += msg.value;
}

### Claim Referral Rewards

```solidity
mapping(address => uint256) public pendingReferralRewards;

function claimReferralRewards() public {
    uint256 reward = pendingReferralRewards[msg.sender];
    require(reward > 0, "No rewards");
    pendingReferralRewards[msg.sender] = 0;
    payable(msg.sender).transfer(reward);
}

### Max Referral Reward Limit

```solidity
uint256 public maxReferralReward = 0.1 ether;

function deposit(address _referrer) public payable {
    if (referrer[msg.sender] != address(0)) {
        uint256 reward = (msg.value * referralReward) / 100;
        if (reward > maxReferralReward) {
            reward = maxReferralReward;
        }
        pendingReferralRewards[referrer[msg.sender]] += reward;
    }
    balances[msg.sender] += msg.value;
}

### Referral Leaderboard Idea

A simple mapping to track top referrers can be added later:

```solidity
mapping(address => uint256) public referralScore;

### Simple Staking Idea

```solidity
mapping(address => uint256) public stakedAmount;
mapping(address => uint256) public stakeTimestamp;

function stake() public payable {
    stakedAmount[msg.sender] += msg.value;
    stakeTimestamp[msg.sender] = block.timestamp;
}

### Claim Staking Rewards

```solidity
mapping(address => uint256) public pendingStakeRewards;

function claimStakeRewards() public {
    uint256 reward = pendingStakeRewards[msg.sender];
    require(reward > 0, "No rewards");
    pendingStakeRewards[msg.sender] = 0;
    payable(msg.sender).transfer(reward);
}

### Lock Period for Staking

```solidity
uint256 public lockPeriod = 7 days;

function unstake(uint256 amount) public {
    require(block.timestamp >= stakeTimestamp[msg.sender] + lockPeriod, "Still locked");
    require(stakedAmount[msg.sender] >= amount, "Not enough");
    stakedAmount[msg.sender] -= amount;
    payable(msg.sender).transfer(amount);
}

### Early Unstake Penalty

```solidity
uint256 public earlyPenalty = 10; // 10%

function unstake(uint256 amount) public {
    require(stakedAmount[msg.sender] >= amount, "Not enough");
    
    uint256 penalty = 0;
    if (block.timestamp < stakeTimestamp[msg.sender] + lockPeriod) {
        penalty = (amount * earlyPenalty) / 100;
    }
    
    stakedAmount[msg.sender] -= amount;
    payable(msg.sender).transfer(amount - penalty);
}

### Auto-Compound Idea

```solidity
function compound() public {
    uint256 reward = calculateReward(msg.sender);
    pendingStakeRewards[msg.sender] = 0;
    stakedAmount[msg.sender] += reward;
}

### Total Staked Tracking

```solidity
uint256 public totalStaked;

function stake() public payable {
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
    stakeTimestamp[msg.sender] = block.timestamp;
}

### Average Stake Time Idea

```solidity
uint256 public totalStakeTime;
uint256 public totalStakeActions;

function stake() public payable {
    // existing code
    totalStakeTime += block.timestamp;
    totalStakeActions += 1;
}

### Unstake Event

```solidity
event Unstaked(address indexed user, uint256 amount);

function unstake(uint256 amount) public {
    require(stakedAmount[msg.sender] >= amount, "Not enough");
    stakedAmount[msg.sender] -= amount;
    totalStaked -= amount;
    payable(msg.sender).transfer(amount);
    emit Unstaked(msg.sender, amount);
}

### Minimum Stake Amount

```solidity
uint256 public minStake = 0.01 ether;

function stake() public payable {
    require(msg.value >= minStake, "Below minimum stake");
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
}

### Stake Count per User

```solidity
mapping(address => uint256) public stakeCount;

function stake() public payable {
    stakedAmount[msg.sender] += msg.value;
    stakeCount[msg.sender] += 1;
    totalStaked += msg.value;
}

### Pause Staking

```solidity
bool public stakingPaused = false;

function stake() public payable {
    require(!stakingPaused, "Staking is paused");
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
}

### Blacklist for Staking

```solidity
mapping(address => bool) public isStakeBlacklisted;

function stake() public payable {
    require(!isStakeBlacklisted[msg.sender], "Address blacklisted");
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
}

### Whitelist for Staking

```solidity
mapping(address => bool) public isStakeWhitelisted;
bool public stakeWhitelistEnabled = false;

function stake() public payable {
    if (stakeWhitelistEnabled) {
        require(isStakeWhitelisted[msg.sender], "Not whitelisted");
    }
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
}

### Fee on Stake

```solidity
uint256 public stakeFee = 1; // 1%

function stake() public payable {
    uint256 fee = (msg.value * stakeFee) / 100;
    uint256 netAmount = msg.value - fee;
    stakedAmount[msg.sender] += netAmount;
    totalStaked += netAmount;
    totalFeesCollected += fee;
}

### Fee on Unstake

```solidity
uint256 public unstakeFee = 1; // 1%

function unstake(uint256 amount) public {
    require(stakedAmount[msg.sender] >= amount, "Not enough");
    uint256 fee = (amount * unstakeFee) / 100;
    uint256 netAmount = amount - fee;
    stakedAmount[msg.sender] -= amount;
    totalStaked -= amount;
    totalFeesCollected += fee;
    payable(msg.sender).transfer(netAmount);
}

### Emergency Withdraw for Stakers

```solidity
function emergencyWithdraw() public {
    uint256 amount = stakedAmount[msg.sender];
    require(amount > 0, "Nothing to withdraw");
    stakedAmount[msg.sender] = 0;
    totalStaked -= amount;
    pendingStakeRewards[msg.sender] = 0; // forfeit rewards
    payable(msg.sender).transfer(amount);
}

### Reward Boost for Long Stakers

```solidity
function calculateReward(address user) public view returns (uint256) {
    uint256 timeStaked = block.timestamp - stakeTimestamp[user];
    uint256 baseReward = (stakedAmount[user] * rewardRate * timeStaked) / 1 days;
    
    if (timeStaked > 30 days) {
        baseReward = baseReward * 120 / 100; // 20% boost
    }
    return baseReward;
}

### Multiple Lock Tiers

```solidity
uint256 public shortLock = 7 days;
uint256 public mediumLock = 30 days;
uint256 public longLock = 90 days;

function getLockMultiplier(uint256 duration) public pure returns (uint256) {
    if (duration >= 90 days) return 150;
    if (duration >= 30 days) return 120;
    return 100;
}

### Early Unlock with Higher Penalty

```solidity
function earlyUnlock() public {
    require(stakedAmount[msg.sender] > 0, "Nothing staked");
    uint256 amount = stakedAmount[msg.sender];
    uint256 penalty = (amount * 20) / 100; // 20% penalty
    stakedAmount[msg.sender] = 0;
    totalStaked -= amount;
    totalPenaltiesCollected += penalty;
    payable(msg.sender).transfer(amount - penalty);
}

### Auto-Extend Lock Option

```solidity
mapping(address => bool) public autoExtend;

function setAutoExtend(bool status) public {
    autoExtend[msg.sender] = status;
}

function extendLock() public {
    require(autoExtend[msg.sender], "Auto-extend not enabled");
    stakeTimestamp[msg.sender] = block.timestamp;
}

### Referral Boost for Stakers

```solidity
function calculateReward(address user) public view returns (uint256) {
    uint256 base = (stakedAmount[user] * rewardRate * (block.timestamp - stakeTimestamp[user])) / 1 days;
    
    if (referralCount[user] >= 5) {
        base = base * 110 / 100; // 10% boost for active referrers
    }
    return base;
}

### Total Rewards Distributed

```solidity
uint256 public totalRewardsDistributed;

function claimStakeRewards() public {
    uint256 reward = pendingStakeRewards[msg.sender];
    require(reward > 0, "No rewards");
    pendingStakeRewards[msg.sender] = 0;
    totalRewardsDistributed += reward;
    payable(msg.sender).transfer(reward);
}

### Daily Reward Limit

```solidity
mapping(address => uint256) public dailyClaimed;
mapping(address => uint256) public lastClaimDay;

uint256 public maxDailyReward = 0.1 ether;

function claimStakeRewards() public {
    uint256 today = block.timestamp / 1 days;
    if (lastClaimDay[msg.sender] < today) {
        dailyClaimed[msg.sender] = 0;
        lastClaimDay[msg.sender] = today;
    }
    
    uint256 reward = pendingStakeRewards[msg.sender];
    if (dailyClaimed[msg.sender] + reward > maxDailyReward) {
        reward = maxDailyReward - dailyClaimed[msg.sender];
    }
    
    // claim logic...
}

### Pending Rewards Snapshot

```solidity
function snapshotRewards(address user) public view returns (uint256) {
    return pendingStakeRewards[user] + calculateReward(user);
}

### Contract Stats View

```solidity
function getContractStats() public view returns (
    uint256 totalStakedAmount,
    uint256 totalFees,
    uint256 totalRewards,
    uint256 totalUsersCount
) {
    return (totalStaked, totalFeesCollected, totalRewardsDistributed, totalUsers);
}

### Version History Note

Current contract version: 1.0

Future upgrades may include:
- Better reward formulas
- NFT integration for boosts
- Multi-token support

### Reentrancy Guard Idea

```solidity
bool private locked;

modifier noReentrant() {
    require(!locked, "No reentrancy");
    locked = true;
    _;
    locked = false;
}

function withdraw(uint256 amount) public noReentrant {
    // safe withdraw logic
}

### Ownable Pattern Note

Using a simple Ownable pattern is good for learning, but for production consider OpenZeppelin's Ownable or AccessControl for more flexibility and security.

### Current Features Summary

- Deposit and withdraw with fees
- Staking with lock periods and rewards
- Referral system with bonuses
- Blacklist and whitelist controls
- Pause and emergency functions
- Multiple view functions for transparency

### Project Overview

This repository contains a collection of Solidity examples and patterns useful for building on Base. It covers deposits, staking, referrals, access control, fees, and safety mechanisms.

### Simple NFT Idea

```solidity
// Basic structure for a future NFT contract
mapping(uint256 => address) public ownerOf;
uint256 public nextTokenId;

function mint() public {
    ownerOf[nextTokenId] = msg.sender;
    nextTokenId++;
}

### NFT Approval Idea

```solidity
mapping(uint256 => address) public tokenApproval;

function approve(address to, uint256 tokenId) public {
    require(ownerOf[tokenId] == msg.sender, "Not owner");
    tokenApproval[tokenId] = to;
}

### NFT Balance Tracking

```solidity
mapping(address => uint256) public balanceOf;

function mint() public {
    ownerOf[nextTokenId] = msg.sender;
    balanceOf[msg.sender] += 1;
    nextTokenId++;
}

### NFT Burn Function

```solidity
function burn(uint256 tokenId) public {
    require(ownerOf[tokenId] == msg.sender, "Not owner");
    delete ownerOf[tokenId];
    balanceOf[msg.sender] -= 1;
}
