#Unchecked Call Return Value

#Summary

The vulnerability of unchecked values arises because certain low-level Solidity functions like `call()`, `callcode()`, `delegatecall()`, and `send()` operate differently and are among the more complex features of Solidity. They operate differently from other Solidity functions in terms of error handling because faults do not multiply or result in a complete reversal of the present execution. Instead, they will return a boolean value that is set to false, and the programme will still run. Developers may be taken aback by this, and if the return value of such low-level calls is not checked, it may result in fail-opens and other undesirable results.

#How to Test

```sol
    function withdraw(uint256 _amount) public {
        require(balances[msg.sender] >= _amount);
        balances[msg.sender] -= _amount;
        etherLeft -= _amount;
        msg.sender.send(_amount);
    }
```

#Remediation

Perform manual validation when making calls or use `address.transfer()`.

#References

*NCC Group (o. D.): DASP - TOP 10, DASP Top 10, [online] https://dasp.co/#item-4 [abgerufen am 27.08.2022].*