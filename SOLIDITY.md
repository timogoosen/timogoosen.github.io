## Solidity Concepts:

* [Flash Loans how they work Aave Docs](https://docs.aave.com/faq/flash-loans)
* [Aave Protocol Flash Loans Deveoloper Docs](https://docs.aave.com/developers/guides/flash-loans)


### Solidity Language Reference:

* [Function Modifiers like onlyOwner etc](https://solidity-by-example.org/function-modifier/)

* [Using an interface to call functions from other contracts Cryptokittie Example](https://cryptozombies.io/en/lesson/2/chapter/11)


### Solidity General


* [Solidity Security](https://timogoosen.github.io/SOLIDITY_SECURITY)

### ERC20 Tokens

* [Creating ERC20 Token OpenZeplin Docs](https://docs.openzeppelin.com/contracts/3.x/erc20)


Get and set:

```


pragma solidity 0.7.5;

contract HelloWorld {

    int number;

    function getNumber() public view return(int) {
            return number;
    }

    function setNumber(int _number ) public {

        number = _number;
    }


}

```
