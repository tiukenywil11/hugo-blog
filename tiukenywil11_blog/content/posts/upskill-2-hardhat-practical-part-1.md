---
title: "Upskill 2 Part 1 (Hardhat): Concepts & Setup"
date: 2022-06-04T13:19:39+08:00
tags: ["upskill", "hardhat", "solidity", "smart contract"]
description: "Upskill 2: Practical research on backend Solidity framework Hardhat"
author: "Kenywil Tiu"
---

# Introduction
  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; I have some practical experience with Solidity already, and was recommended by one of my colleague to try to supplement my knowledge with the Hardhat framework. I checked it out and would like to try it out and create a basic working smart contract. I will be following the official document of Hardhat found [here](https://hardhat.org/tutorial/).
    
# Hardhat Concepts
  
Hardhat is composed of the following concepts.  
  
- Tasks: There are commands that can be ran on the terminal, some are provided by Hardhat upon install (e.g. `npx hardhat compile`). To find out the list of tasks use the following command:
```bash
npx hardhat help [task]
``` 
- Plugins: Tools that can be integrated to Hardhat. Examples of these are 'ethers.js' and 'waffle'.
    - List of plugins can be found here: [Hardhat Plugins](https://hardhat.org/plugins)

# Steps

## Prerequisite
- NodeJS 16.15.1
- NPM 8.11.0(Should have been installed with NodeJS)

## Github Setup
1. I have created a new repository on my Github account, it can be found [here](https://github.com/tiukenywil11/hardhat-demo).
2. Opened Git bash, then used the following commands.
- Cloned the repository to my local machine.
```bash
git clone https://github.com/tiukenywil11/hardhat-demo.git
```
- Navigated to the project.
```bash
cd hardhat-demo
```
- Opened project via VS Code.
```bash
code . 
```

## Environment Setup

1. Open a terminal on VSCode using the following keyboard shortcut `CTRL + SHIFT + ~`.
2. Install Hardhat dependencies using NPM (Node Package Manager).
- Initialize a node project.
```bash
npm init
``` 
- (Optional) Fill up the details after the command
- Install Hardhat to the *dev environment* (Inside project directory only).
```
npm install --save-dev hardhat
```
3. Create a Hardhat config file.
- Run the following command to run hardhat on terminal.
```bash
npx hardhat
```
- Choose the option 'Create an empty hardhat.config.js'. This will create a 'hardhat.config.js' on the same directory as your 'package.json'.

## Installing plugins

1. Install the following plugins.
- **[Ethers.js](https://hardhat.org/plugins/nomiclabs-hardhat-ethers)**: Used to help interact with the Ethereum blockchain.
- **[Waffle](https://hardhat.org/plugins/nomiclabs-hardhat-waffle)**: Used to build smart contracts.
```bash
npm install --save-dev @nomiclabs/hardhat-ethers ethers @nomiclabs/hardhat-waffle ethereum-waffle chai
```
2. Add Installed dependency on `hardhat.config.js`, this should be added on first line of the file. (Adding 'Ethers.js' is not necessary, because 'Waffle' already calls 'Ethers.js')
```javascript
require("@nomiclabs/hardhat-waffle");
```

## Saving changes to Github.
1. Commited changes to Github repository.
```
git add .
git commit -m "Part 1: Environment setup, and base hardhat config"
git push
```

# Outro

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; So with this, we have already set up the environment for Hardhat, and created and installed the basic dependencies of a new Hardhat project. The repository can be found [here](https://github.com/tiukenywil11/hardhat-demo/commit/96a6288c690860398c80a52d6998446cad8a7000). This blog will be resumed in parts, due to my busy schedule, but we stopped at the following section for this post [Hardhat: Creating a new Hardhat project](https://hardhat.org/tutorial/creating-a-new-hardhat-project). 
  
**Read More:**  
Next:  
[Hard Hat Basics: Part 2]({{< ref "upskill-2-hardhat-practical-part-2" >}}) 
  