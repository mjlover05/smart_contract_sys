# smart_contract_sys
Function getBalance(): This function is a view function that returns the current balance of the contract.
Function deposit(uint256 _amount): This function allows the contract owner to deposit funds into the contract.
Function withdraw(uint256 _withdrawAmount): This function allows the contract owner to withdraw funds from the contract.
Function increaseBalance(uint256 _amount): This function allows the contract owner to increase the contract balance. The specified amount is added to the contract balance.
Function decreaseBalance(uint256 _amount): This function allows the contract owner to decrease the contract balance.
## deposit function
Allows the contract owner to deposit funds into the contract.
## Increase Function
Allows the contract owner to programmatically increase the contract balance 

## Getting Started
Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Assessment.sol). Copy and paste the following code into the file:
## Code
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

contract Assessment {
    address payable public owner;
    uint256 public balance;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);

    constructor(uint initBalance) payable {
        owner = payable(msg.sender);
        balance = initBalance;
    }

    function getBalance() public view returns (uint256) {
        return balance;
    }

    function deposit(uint256 _amount) public payable {
        require(msg.sender == owner, "You are not the owner of this account");
        uint256 _previousBalance = balance;
        balance += _amount;
        assert(balance == _previousBalance + _amount);
        emit Deposit(_amount);
    }

    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public {
        require(msg.sender == owner, "You are not the owner of this account");
        uint256 _previousBalance = balance;
        if (balance < _withdrawAmount) {
            revert InsufficientBalance(balance, _withdrawAmount);
        }
        balance -= _withdrawAmount;
        assert(balance == _previousBalance - _withdrawAmount);
        emit Withdraw(_withdrawAmount);
    }

   

    function increaseBalance(uint256 _amount) public payable {
    require(msg.sender == owner, "You are not the owner of this account");
    balance += _amount;
    }

    function decreaseBalance(uint256 _amount) public {
    require(msg.sender == owner, "You are not the owner of this account");
    require(balance >= _amount, "Insufficient balance");

    balance -= _amount;
   }

}
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.9;

contract Assessment {
    address payable public owner;
    uint256 public balance;

    event Deposit(uint256 amount);
    event Withdraw(uint256 amount);

    constructor(uint initBalance) payable {
        owner = payable(msg.sender);
        balance = initBalance;
    }

    function getBalance() public view returns (uint256) {
        return balance;
    }

    function deposit(uint256 _amount) public payable {
        require(msg.sender == owner, "You are not the owner of this account");
        uint256 _previousBalance = balance;
        balance += _amount;
        assert(balance == _previousBalance + _amount);
        emit Deposit(_amount);
    }

    error InsufficientBalance(uint256 balance, uint256 withdrawAmount);

    function withdraw(uint256 _withdrawAmount) public {
        require(msg.sender == owner, "You are not the owner of this account");
        uint256 _previousBalance = balance;
        if (balance < _withdrawAmount) {
            revert InsufficientBalance(balance, _withdrawAmount);
        }
        balance -= _withdrawAmount;
        assert(balance == _previousBalance - _withdrawAmount);
        emit Withdraw(_withdrawAmount);
    }

   

    function increaseBalance(uint256 _amount) public payable {
    require(msg.sender == owner, "You are not the owner of this account");
    balance += _amount;
    }

    function decreaseBalance(uint256 _amount) public {
    require(msg.sender == owner, "You are not the owner of this account");
    require(balance >= _amount, "Insufficient balance");

    balance -= _amount;
   }

}
## Compile

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.9" (or another compatible version), and then click on the "Compile Assessment.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Assessment" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the different function.

Frontend Integration
You need to setup following tools :

Hardhat : Hardhat is a popular development environment for building, testing, and deploying smart contracts on the Ethereum blockchain. It provides a comprehensive set of tools and features to facilitate the development process.
React : React is a popular JavaScript library for building user interfaces. It provides a declarative and component-based approach to building UIs, making it easier to manage complex UIs and update them efficiently.
Metamask : MetaMask is a popular browser extension and digital wallet that allows users to manage their Ethereum accounts and interact with decentralized applications (dApps) on the Ethereum blockchain.
Next : Next.js is a popular React framework for building server-side rendered (SSR) and statically generated (SSG) web applications. It provides several features and optimizations that enhance the development experience and performance of React applications.
## index.js
// set up index.js in react
## deploy.js
// set and update deploy.js in hardhat
## Update contracts in hardhat
//  Move in contracts folder update Lock.sol with Assessment.sol in hardhat
## Update hardhat.config.js in hardhat
// set and update hardhat.config.js in hardhat
## Starter Next/Hardhat Project
After cloning the github, you will want to do the following to get the code running on your computer.

Inside the project directory, in the terminal type: npm i
Open two additional terminals in your VS code
In the second terminal type: npx hardhat node
In the third terminal, type: npx hardhat run --network localhost scripts/deploy.js
Back in the first terminal, type npm run dev to launch the front-end.
After this, the project will be running on your localhost. Typically at http://localhost:3000/

## Authors
Manish kumar
