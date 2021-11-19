# ERC20 101

## Introduction
Welcome! This is an automated workshop that will explain how to deploy and ERC20 token, and customize it to perform specific functions.
It is aimed at developpers that have never written code in Solidity, but who understand its syntax.

## How to work on this TD
The TD has two components:
- An ERC20 token, ticker TD02, that is used to keep track of points 
- An evaluator contract, that is able to mint and distribute TD02 points

Your objective is to gather as many TD02 points as possible. Please note :
- The 'transfer' function of TD02 has been disabled to encourage you to finish the TD with only one address
- You can answer the various questions of this workshop with different ERC20 contracts. However, an evaluated address has only one evaluated ERC20 contract at a time. To change the evaluated ERC20 contract associated with your address, call `ex2_testErc20TickerAndSupply()`  with that specific address.
- In order to receive points, you will have to do execute code in `Evaluator.sol` such that the function `TDERC20.distributeTokens(msg.sender, n);` is triggered, and distributes n points.
- This repo contains an interface `IExerciceSolution.sol`. Your ERC20 contract will have to conform to this interface in order to validate the exercice; that is, your contract needs to implement all the functions described in `IExerciceSolution.sol`. 
- A high level description of what is expected for each exercice is in this readme. A low level description of what is expected can be inferred by reading the code in `Evaluator.sol`.

## Points list
### Setting up
- Create a git repository and share it with the teacher (1 pts)
- Install truffle and create an empty truffle project (2 pts)
These points will be attributed manually if you do not manage to have your contract interact with the evaluator, or automatically in the first question.

### ERC20 basics
- Call  `ex1_getTickerAndSupply()` in the evaluator contract to receive a random ticker for your ERC20 token, as well as an initial token supply (1 pt)
- Create an ERC20 token contract with the proper ticker and supply (2 pt)
- Deploy it to the Rinkeby testnet (2 pts)
- Call `ex2_testErc20TickerAndSupply()` in the evaluator to receive your points (all remaining 7 points are attributed at that step)

### Distributing and selling tokens
- Create a `getToken()` function in your contract, deploy it, and call the `ex3_testGetToken()` function that distributes token to the caller (2 pts).
- Create a `buyToken()` function in your contract, deploy it, and call the `ex4_testBuyToken()` function that lets the caller send an arbitrary amount of ETH, and distributes a proportionate amount of token (2 pts).

### Creating an ICO allow list
- Create a customer allow listing function. Only allow listed users should be able to call `getToken()`
- Call `ex5_testDenyListing()` in the evaluator to show he can't buy tokens using `buyTokens()` (1 pt)
- Allow the evaluator to buy tokens
- Call `ex6_testAllowListing()`in the evaluator to show he can now buy tokens `buyTokens()` (2 pt)

### Creating multi tier allow list
- Create a customer multi tier listing function. Only allow listed users should be able to call `buyToken()`; and customers should receive a different amount of token based on their level
- Call `ex7_testDenyListing()` in the evaluator to show he can't buy tokens using `buyTokens()` (1 pt)
- Add the evaluator in the first tier. He should now be able to buy N tokens for Y amount of ETH
- Call `ex8_testTier1Listing()` in the evaluator to show he can now buy tokens(2 pt)
- Add the evaluator in the second tier. He should now be able to buy 2N tokens for Y amount of ETH 
- Call `ex9_testTier2Listing()` in the evaluator to show he can now buy more tokens(2 pt)

### Extra points
Extra points if you find bugs / corrections this TD can benefit from, and submit a PR to make it better.  


## Installing
> npm install 
