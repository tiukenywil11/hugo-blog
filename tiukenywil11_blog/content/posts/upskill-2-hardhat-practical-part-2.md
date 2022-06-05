---
title: "Upskill 2 Part 2 (Hardhat): Smart Contract Compiling"
date: 2022-06-05T12:52:13+08:00
tags: ["upskill", "hardhat", "solidity", "smart contract"]
description: "Upskill 2: Practical research on backend Solidity framework Hardhat"
author: "Kenywil Tiu"
---

# Introduction
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; On the last blog post we have set up an initial environment, and created a new Hard hat project. For this blog we will be writing and compiling a smart contract on Hard hat. We will resume with the official hard hat documentation found [here](https://hardhat.org/tutorial/writing-and-compiling-contracts).  
  
# Steps
Assuming we're still on the 'hardhat-demo' directory.

## Writing a Smart Contract
1. Create a directory called 'contracts'.
```bash
mkdir contracts
```
2. Create a file called 'Token.sol'.
```bash
touch Token.sol
```
3. On the smart contract, Input the following codes.
- Solidity dependency used to compile Solidity codes.
```javascript
pragma solidity ^0.7.0;
```
- Create a contract class called 'Token'
```javascript
contract Token {

}
```
- Inside the Token contract class, initialize the required variables.
    - name (string): A string indicating the name of the token.
	- symbol (string): A string indicating the symbol of the token.
	- totalSupply (uint256): An unsigned integer indicating the total supply of the token.
	- owner (address): An address, which contains the owner of the smart contract (The one who deployed the contract).
	- balances (address => uint256): A key pair value listing all addresses that owns the token, and how much token they have.
```javascript
string public name = "Kenny Hardhat Token";
string public symbol = "KHT";

uint256 public totalSupply = 1000000;

address public owner;

mapping(address => uint256) balances;
```
- Below the initialized variables, create a constructor function (A function that is called once when the smart contract is triggered).
``` javascript
 constructor () {
 
 }
```
- Inside the constructor, initialize that the totalSupply will be given to the owner of the contract, and that the contract's owner will be the one who deploys the contract.
```javascript
balances[msg.sender] = totalSupply;
owner = msg.sender;
```
- Create a 'transfer' function: This takes 2 parameters. An address to transfer to, and the amount that would be transferred. This function would have an 'external' tag indicating that it could be accessed by the public.
```javascript
function transfer(address to, uint256 amount) external {

}
```
- Inside the 'transfer' function, do the following.
  - Require that the sender has enough tokens to transfer.
  - remove the balance indicated from sender.
  - increase the balance of indicated receiver.
```javascript
require(balances[msg.sender] >= amount, "Not enough tokens");

balances[msg.sender] -= amount;
balances[to] += amount;
```
- Create a 'balanceOf' function: This takes 1 parameter. The address you want to check the balance of. This function would also have the following tags 'external' meaning it can be accessed by the public, 'view' meaning this function is read-only, and 'returns' meaning this function returns something.
```javascript
 function balanceOf(address account) external view returns (uint256) {
 
 }
```
- Inside the 'balanceOf' function do the following.
	- Return the balance of the address passed to it.
```javascript
return balances[account];
```
  
## Compiling the Smart Contract
  
1. Run the following command on the CLI.
```bash
npx hardhat compile
```
- Error encountered: Cannot find module '@nomiclabs/hardhat-waffle'
	- Solution: 
		- Updated NodeJS version to 16.15.1, updated npm to version 8.11.0.
		- Reinstalled 'Waffles' using the following command.
```bash
npm install --save-dev @nomiclabs/hardhat-ethers ethers @nomiclabs/hardhat-waffle ethereum-waffle chai
```
  
## Saving changes to Github.
1. Commited changes to Github repository.
```
git add .
git commit -m "Part 2: Initial smart contract"
git push
```

# Outro

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; We have encountered an error when compiling the smart contract, I'm thinking of adding a Docker container implementation in the future. We will be stopping with compile for now, and the next post should be about testing. The repository can be found [here](https://github.com/tiukenywil11/hardhat-demo/commit/e3fef835db3b8996c936694ea1211100c8874e7a). We stopped at the following section for this post [Hardhat: Writing and Compiling Smart Contract](https://hardhat.org/tutorial/writing-and-compiling-contracts). 
  
**Read More:**  
Previous:  
[Hard Hat Basics: Part 1]({{< ref "upskill-2-hardhat-practical-part-1" >}}) 
  