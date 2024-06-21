MyToken Smart Contract


The MyToken smart contract is a simple ERC-20-like token implementation on the Ethereum blockchain. It includes functionality to mint and burn tokens, while maintaining a total supply and tracking the balances of different addresses.

Features

Public Variables: Stores the token name, abbreviation, and total supply.
Balances Mapping: Maps addresses to their token balances.
Mint Function: Increases the total supply and the balance of a specified address.
Burn Function: Decreases the total supply and the balance of a specified address, with necessary checks.

Token Details

Token Name: RaviRao
Token Abbreviation: RR
Total Supply: Initialized to 0

Public Variables

tokenName: The name of the token.
tokenAbbrv: The abbreviation of the token.
totalSupply: The total supply of the token.

Balances Mapping

balances: A mapping from addresses to their token balances.


Mint Function

The mint function allows the creation of new tokens and assigns them to a specified address. This function increases both the total supply and the balance of the given address.

Function Signature: function mint(address _address, uint _value) public

Parameters:

_address: The address to which the newly minted tokens will be assigned.
_value: The amount of tokens to mint.
Behavior:

Increases totalSupply by _value.
Increases balances[_address] by _value.


Burn Function

The burn function allows tokens to be destroyed from a specified address. This function decreases both the total supply and the balance of the given address, ensuring the address has enough tokens to burn.

Function Signature: function burn(address _address, uint _value) public

Parameters:

_address: The address from which the tokens will be burned.
_value: The amount of tokens to burn.
Behavior:

Checks if balances[_address] is greater than or equal to _value.
Decreases totalSupply by _value.
Decreases balances[_address] by _value.

Example Usage
Here is an example of how to interact with the MyToken contract:

Minting Tokens:

myToken.mint(0ac231, 100);

This will mint 100 tokens and assign them to the address 0ac231, increasing the total supply by 100.

Burning Tokens:

myToken.burn(0ac231, 50);

This will burn 50 tokens from the address 0ac231, decreasing the total supply by 50, provided 0x123 has at least 50 tokens.

Solidity Code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.9;

contract MyToken {
    
    // Public variables to store the token details
    string public tokenName = "RaviRao";
    string public tokenAbbrv = "RR";
    uint public totalSupply = 0;

    // Mapping to store the balances of addresses
    mapping(address => uint) public balances;

    // Function to mint new tokens
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Function to burn tokens
    function burn(address _address, uint _value) public {
        // Check if the balance is sufficient to burn
        require(balances[_address] >= _value, "Insufficient balance to burn tokens");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
License
This project is licensed under the MIT License.
