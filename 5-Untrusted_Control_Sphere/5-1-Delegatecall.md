# Delegatecall

# Summary

The visibility specifiers govern the method a function is called in the Solidity function. When allowing users to employ derived contracts to call for external functions, the visibility specifier also assumes control. The smart contract may suffer catastrophic consequences if the visibility specifiers are implemented incorrectly. Because functions' default visibility is always public, external contracts can request visibility even when functions don't explicitly mention it. A vulnerability results when developers fail to set the visibility specifier to private.

# How to Test

The contract's initialization function in the example below designates the function's caller as its owner. The logic, however, is independent of the person who created the contract and does not remember that it has already been called.

```sol
    function initContract() public {
        owner = msg.sender;
    } 
```

# Remediation

Be careful when using delegatecall and never call into shady contracts. Make care to cross-reference the target address with a whitelist of trusted contracts if it was obtained via user input.

# References

*S. Sayeed, H. Marco-Gisbert and T. Caira, "Smart Contract: Attacks and Protections," in IEEE Access, vol. 8, pp. 24416-24427, 2020, doi: 10.1109/ACCESS.2020.2970495.*