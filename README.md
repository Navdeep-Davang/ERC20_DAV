# ERC20-Token-Creation

The purpose of this project is to give idea regarding creation of ERC20 Token by means of Openzeppelin ERC20 contract and solidity language.

## Description

This program is a simple contract written in Solidity, Inherit the parameters from Openzeppelin ERC20 contract. 
1) We first declare that our 'Mytoken' contract inherit propertic of Openzeppelin ERC20 contract.

2) We will declare a function to mint(to create) a token.

3) We will declare a function to burn(to destroy) a token.

4) We will declare a function which will allows us to transfer token from one account to the other.



## Getting Started

### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension.
After that we declare that our Mytoken contract inherit from the Openzeppelin ERC20 contract by using 'is' method.
```javascript
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 { /*  code   */}
```

Once this much is set, we setup the things like initial variable(i.e. address), constructor and modifier as follows,
```javascript
address private _owner;
constructor() ERC20("DAVANG", "DAV") {_owner = msg.sender;}
modifier onlyOwner() {require(msg.sender == _owner, "Only the owner can call this function"); _;}
```
Here `constructor` is of our contract Mytoken while `ERC20` is constructor of Openzeppelin ERC20 contract. ERC20 constructor takes two parameters, first is token name and another is token symbol. 

Afer that we declare three function mint, burn and transfer function which execute _mint, _burn, _transfer function from Openzeppelin ERC20 contract.
```javascript
function mint(address account, uint256 amount) public onlyOwner {
        _mint(account, amount);
    }

    function burn(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function transfer(address recipient, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }
```
Here mint is set with the modifier `onlyOwner` which means only owner is allowed to create(mint) the token. And any individual with token can burn them or tansfer them to other user.


## Authors

Navdeep Davang 


## License

This project is licensed under the MIT License - see the LICENSE.md file for details

 

