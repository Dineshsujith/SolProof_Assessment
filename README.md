# SolProof_Assessment
---

# MyToken Smart Contract

## Overview

This Solidity smart contract implements a simple ERC20-like token with minting and burning functionalities. The token has a name, abbreviation, and total supply, and it maintains balances for different addresses. 

## Requirements

1. **Public Variables**: The contract has public variables to store the details about the coin:
   - Token Name
   - Token Abbreviation
   - Total Supply

2. **Address to Balance Mapping**: A mapping of addresses to their respective balances is maintained.

3. **Mint Function**: A function that increases the total supply and the balance of a specified address.

4. **Burn Function**: A function that decreases the total supply and the balance of a specified address, with a check to ensure the balance is sufficient.

## Contract Details

### Public Variables

- `string public tokenName = "Dinesh";`
- `string public tokenAbbr = "DK";`
- `uint public totalSupply = 0;`

### Mapping

- `mapping (address => uint) public balances;`

### Mint Function

```solidity
function mint(address _address, uint _value) public {
    totalSupply += _value;
    balances[_address] += _value;
}
```

- **Parameters**:
  - `_address`: The address to which the tokens will be minted.
  - `_value`: The number of tokens to be minted.
- **Functionality**:
  - Increases the `totalSupply` by `_value`.
  - Increases the balance of `_address` by `_value`.

### Burn Function

```solidity
function burn(address _address, uint _value) public {
    require(balances[_address] >= _value, "Funds not sufficient");
    totalSupply -= _value;
    balances[_address] -= _value;
}
```

- **Parameters**:
  - `_address`: The address from which the tokens will be burned.
  - `_value`: The number of tokens to be burned.
- **Functionality**:
  - Checks if the balance of `_address` is greater than or equal to `_value`.
  - Decreases the `totalSupply` by `_value`.
  - Decreases the balance of `_address` by `_value`.

## Usage

To use this contract, deploy it to an Ethereum-compatible blockchain. Once deployed, you can call the `mint` and `burn` functions to manage the token supply.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---
