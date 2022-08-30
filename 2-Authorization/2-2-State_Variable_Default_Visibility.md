# State Variable Default Visibility

# Summary

The visibility specifiers govern the access of a variable in the Solidity. When not specified everyone has access to the variable.

# How to Test

The variables that are not properly secured can be accessed thorugh requesting the storage from the blockchain

```sol

pragma solidity ^0.4.21;

contract GuessTheRandomNumberChallenge {
    uint8 answer;

    function GuessTheRandomNumberChallenge() public payable {
        require(msg.value == 1 ether);
        answer = uint8(keccak256(block.blockhash(block.number - 1), now));
    }

}
```

# Remediation

Always use consciously one of the visibility specifier `public`, `internal` or `private` and declare the loctaion of strage either `memory`or `storage`.

# References

*S. Sayeed, H. Marco-Gisbert and T. Caira, "Smart Contract: Attacks and Protections," in IEEE Access, vol. 8, pp. 24416-24427, 2020, doi: 10.1109/ACCESS.2020.2970495.*
*Marx, Steve (o. D.): Capture the Ether - Guess the random number, Capture the Ether, [online] https://capturetheether.com/challenges/lotteries/guess-the-random-number/ [abgerufen am 30.08.2022].*