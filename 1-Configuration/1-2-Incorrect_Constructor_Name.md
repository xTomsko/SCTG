#Incorrect Constructor Name

#Summary

Constructors are unique functions that frequently handle privileged, crucial jobs while initializing contracts. Constructors were characterized as functions with the same name as the contract prior to Solidity `v0.4.22`. Therefore, if the function name is left unaltered when a contract name changes during development, the contract becomes a regular, callable function.

#How to Test

Check for mispellings between constructor and contract name.

```sol

contract OwnerWallet {
    address public owner;

    //constructor
    function ownerWallet(address _owner) public {
        owner = _owner;
    }

    // fallback. Collect ether.
    function () payable {}

    function withdraw() public {
        require(msg.sender == owner);
        msg.sender.transfer(this.balance);
    }
}

```

#Remediation

If possible use a compiler version above `0.4.21` or verify spelling before deployment.

#References

*Manning, Adrian (2018): Solidity Security: Comprehensive list of known attack vectors and common anti-patterns, Sigma Prime, [online] https://blog.sigmaprime.io/solidity-security.html#constructors [abgerufen am 27.08.2022].*