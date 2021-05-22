### Solidity 


* [Solidity Security](https://timogoosen.github.io/SOLIDITY_SECURITY)


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
