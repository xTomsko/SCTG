# Uninitialized Storage Pointer

# Summary
Uninitialized local storage variables may point to unanticipated contract storage locations, creating vulnerabilities that may be deliberate or accidental.
# How to Test
If a struct or other datatype is defined but without a location declaration the default value storage is assumed. The storage is can be read from the blockchain and due no proper initalization the storage location get overwritten everytime the function is called.

```sol
pragma solidity ^0.4.21;

contract DonationChallenge {
    struct Donation {
        uint256 timestamp;
        uint256 etherAmount;
    }
    Donation[] public donations;

    function donate(uint256 etherAmount) public payable {
        // amount is in ether, but msg.value is in wei
        uint256 scale = 10**18 * 1 ether;
        require(msg.value == etherAmount / scale);

        Donation donation;
        donation.timestamp = now;
        donation.etherAmount = etherAmount;

        donations.push(donation);
    }
}
```

# Remediation

Verify that a storage object is required by the contract before proceeding because this is frequently not the case. Mark the variable's storage location explicitly with the `memory` attribute if a local variable is sufficient. If a storage variable is required, initialise it immediately after definition and include the `storage` location.

# References
*Marx, Steve (o. D.): Capture the Ether - Donation, Capture the Ether, [online] https://capturetheether.com/challenges/math/donation/ [abgerufen am 30.08.2022a].*