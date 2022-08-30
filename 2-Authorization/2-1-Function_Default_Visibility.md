# Function Default Visibility

# Summary

The visibility specifiers govern the method a function is called in the Solidity function. When allowing users to employ derived contracts to call for external functions, the visibility specifier also assumes control. The smart contract may suffer catastrophic consequences if the visibility specifiers are implemented incorrectly. Because functions' default visibility is always public, external contracts can request visibility even when functions don't explicitly mention it. A vulnerability results when developers fail to set the visibility specifier to private.

# How to Test

A function that is not specifically defined as `private` can be called by anyone. Both functions below are accessable.

```sol
contract Test {

    function gainEther() {
        require(uint32(msg.sender) == 0);
        _sendEther();
    }

    function _sendEther() {
        msg.sender.transfer(this.balance);
    }
}   
```

# Remediation

Always use consciously one of the visibility specifier `external`, `public`, `internal` or `private`.

# References

*S. Sayeed, H. Marco-Gisbert and T. Caira, "Smart Contract: Attacks and Protections," in IEEE Access, vol. 8, pp. 24416-24427, 2020, doi: 10.1109/ACCESS.2020.2970495.*