#Integer Overflow/Underflow

#Summary

This vulnerability manifests itself in transactions that accept untrusted input data or value and is very simple to exploit. Overflow in smart contracts typically happens when the maximum value is exceeded. Since Solidity, the language used to create most of the contracts can handle up to 256-bit values, an increment of 1 would result in an overflow.

#How to Test

```sol
contract Test {

    function batchTransfer(address[] _acceptors, uint256 _value) public whenNotPaused returns (bool) {
        uint cnt = _acceptors.length;
        uint256 total = uint256(cnt) * _value;
        require(cnt > 0 && cnt <= 20);
        require(_value > 0 && balances[msg.sender] >= total);
        balances[msg.sender] = balances[msg.sender].sub(total);

        for (uint i = 0; i < cnt; i++) {
            balances[_acceptors[i]] = balances[_acceptors[i]].add(_value);
            Transfer(msg.sender, _acceptors[i], _value);
        }
        return true;
    }

}   
```

#Remediation

It is advised to regularly apply tested safe math libraries for arithmetic operations across the whole smart contract system.

#References

*S. Sayeed, H. Marco-Gisbert and T. Caira, "Smart Contract: Attacks and Protections," in IEEE Access, vol. 8, pp. 24416-24427, 2020, doi: 10.1109/ACCESS.2020.2970495.*