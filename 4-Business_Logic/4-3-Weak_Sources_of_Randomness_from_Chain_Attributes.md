# Weak Sources of Randomness from Chain Attributes


# Summary

In a wide range of applications, having the ability to create random numbers is quite helpful. Gambling DApps, which choose the winner using a pseudo-random number generator, are one clear example. Nevertheless, it is challenging to build an adequate, reliable source of randomness for Ethereum. A miner may choose to submit any timestamp within a few seconds and still have his block accepted by others, making the use of block.timestamp, for instance, insecure. Since the miner controls block hash, block.difficulty, and other fields, their use is equally risky. If the stakes are high, the miner can quickly mine a large number of blocks using rental hardware, choose the block with the requisite block hash, and dump all other blocks.

# How to Test

```sol

pragma solidity ^0.4.21;

contract GuessTheNewNumberChallenge {
    function guess(uint8 n) public payable {
        require(msg.value == 1 ether);
        uint8 answer = uint8(keccak256(block.blockhash(block.number - 1), now));

        if (n == answer) {
            msg.sender.transfer(2 ether);
        }
    }
}
```

# Remediation

Using commitment scheme, e.g. RANDAO or external sources of randomness
# References

*Marx, Steve (o. D.): Capture the Ether - Guess the new number, Capture The Ether, [online] https://capturetheether.com/challenges/lotteries/guess-the-new-number/ [abgerufen am 30.08.2022b].*

*Coleman, Jeff (2016): When can BLOCKHASH be safely used for a random number? When would it be unsafe?, Ethereum Stack Exchange, [online] https://ethereum.stackexchange.com/questions/419/when-can-blockhash-be-safely-used-for-a-random-number-when-would-it-be-unsafe [abgerufen am 30.08.2022].*