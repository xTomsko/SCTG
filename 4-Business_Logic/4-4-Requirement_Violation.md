# Requirement Violation

# Summary

The `require()` construct in Solidity is used to verify external inputs to a function. Such external inputs are typically provided by callers, however callers may also return them in some circumstances.

# How to Test

Require function that involve user input are vulnerable. In this case a integer overflow is possible.

```sol

pragma solidity ^0.4.21;

contract TokenSaleChallenge {

    function buy(uint256 numTokens) public payable {
        require(msg.value == numTokens * PRICE_PER_TOKEN);

        balanceOf[msg.sender] += numTokens;
    }
}
```
# Remediation

Input form users should be checked before using it in conjunction with require statements.

# References

*Maurelian (2018): The use of revert(), assert(), and require() in Solidity, and the new REVERT opcode in the EVM, Medium, [online] https://media.consensys.net/when-to-use-revert-assert-and-require-in-solidity-61fb2c0e5a57 [accessed on 30.08.2022].*

*Marx, Steve (o. D.): Capture the Ether - Token sale, Capture the Ether, [online] https://capturetheether.com/challenges/math/token-sale/ [accessed on 30.08.2022c].*