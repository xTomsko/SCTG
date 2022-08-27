#State Variable Default Visibility

#Summary

The visibility specifiers govern the access of a variable in the Solidity. When not specified everyone has access to the variable.

#How to Test

```sol
contract Test {

    bytes16 string1 = "test1";

}   
```

#Remediation

Always use consciously one of the visibility specifier `public`, `internal` or `private`.

#References

*S. Sayeed, H. Marco-Gisbert and T. Caira, "Smart Contract: Attacks and Protections," in IEEE Access, vol. 8, pp. 24416-24427, 2020, doi: 10.1109/ACCESS.2020.2970495.*