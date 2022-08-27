#Floating Pragma

#Summary
Defining the pragma Solidity version is always the first line of any Solidity contract. This defines the version of the Solidity compiler that should be used to compile the code. The contracts may not be deployed with the same version if floating pragma is used.
The most recent compiler version might be chosen if floating pragma is utilized when deploying your contracts.
The likelihood of errors in the latest compiler version is increased. Keeping a  contract to a specific compiler version is, therefore, preferable.

#How to Test

On any Solidity file the pragma is at the top. All possible signs to define a floating pragma are listed below. 

```sol
pragma solidity >=0.4.0 < 0.6.0;
pragma solidity >=0.4.0<0.6.0;
pragma solidity >=0.4.14 <0.6.0;
pragma solidity >0.4.13 <0.6.0;
pragma solidity 0.4.24 - 0.5.2;
pragma solidity >=0.4.24 <=0.5.3 ~0.4.20;
pragma solidity <0.4.26;
pragma solidity ~0.4.20;
pragma solidity ^0.4.14;
pragma solidity 0.4.*;
pragma solidity 0.*;
pragma solidity *;
pragma solidity 0.4;
pragma solidity 0;

contract Test {
    ...
}

```

#Remediation

It is a best practice only to compile the contract with the Solidity version that it has been tested in and to update it manually if necessary.  

```sol
pragma solidity 0.8.0;

contract Test {
    ...
}

```

#References

*Chittoda, J 2019, Mastering Blockchain Programming with Solidity : Write production-ready smart contracts for Ethereum blockchain with Solidity / Chittoda, Jitendra, 1., Packt Publishing Limited, viewed 27 August 2022, <https://search-ebscohost-com.ezproxy-dhma-1.redi-bw.de/login.aspx?direct=true&db=cat08845a&AN=bkm.1751359980&lang=de&site=eds-live>.*