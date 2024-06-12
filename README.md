# CustomCoin Contract

This Solidity program is a simple illustration of the generation, minting, and burning of tokens.

## Description

This project is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract defines a token with a name, abbreviation, and total supply. It includes functionalities to mint new tokens and burn existing ones.

## Getting Started

### Installing

To run this program, you can use Remix, an online Solidity IDE.

### Executing Program

1. Go to the Remix website at [Remix Ethereum](https://remix.ethereum.org/).

2. Copy the following code into a new file named `CustomToken.sol` in Remix.

    ```solidity
    // SPDX-License-Identifier: MIT
    pragma solidity 0.8.18;

    /*
           REQUIREMENTS
        1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
        2. Your contract will have a mapping of addresses to balances (address => uint)
        3. You will have a mint function that takes two parameters: an address and a value. 
           The function then increases the total supply by that number and increases the balance 
           of the “sender” address by that amount
        4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
           It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
           and from the balance of the “sender”.
        5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
           to the amount that is supposed to be burned.
    */

    contract CustomToken {

        // public variables here
        string public coinName = "CustomCoin";
        string public coinSymbol = "CCN";
        uint public totalTokens = 0;

        // mapping variable here
        mapping(address => uint) public accountBalances;

        // mint function
        function mint(address _to, uint _amount) public {
            totalTokens += _amount;
            accountBalances[_to] += _amount;
        }

        // burn function
        function burn(address _from, uint _amount) public {
            require(accountBalances[_from] >= _amount, "Insufficient balance to burn");
            totalTokens -= _amount;
            accountBalances[_from] -= _amount;
        }
    }
    ```

3. To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile CustomToken.sol" button.

4. Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "CustomToken" contract from the dropdown menu, and then click on the "Deploy" button.

## Help

If you encounter any issues or have questions, consider checking the Remix documentation or Solidity documentation for guidance.

## Authors

Harsh Gopal  
[@Harsh-Gopal](https://twitter.com/HarshGopalHG)

## License

This project is licensed under the MIT License - see the LICENSE.md file for details.
