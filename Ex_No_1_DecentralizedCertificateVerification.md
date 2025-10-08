# Experiment 1: Decentralized Certificate Verification
### Name: NISHANTH J
### Reg no: 212223100040
### Department: CSE(CYBER SECURITY)
## Aim:
To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery
and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Code:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree,
uint256 year) public {
require(msg.sender == university, "Only university can issue
certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree,
uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
return certificates[certHash];
}
}
```
## Expected Output:

● When the university issues a certificate, it gets stored as a hash.

● A student or employer can verify the certificate by entering the details.

● If valid, it returns true; otherwise, false.

## Output:

### True
<img width="1919" height="972" alt="Screenshot 2025-10-08 155428" src="https://github.com/user-attachments/assets/b2f47b93-b821-4246-9a69-f6db1502f6af" />


### False
<img width="1919" height="971" alt="Screenshot 2025-10-08 155449" src="https://github.com/user-attachments/assets/a1a0663c-d9ae-4faa-83e2-42bb0e203932" />

## High-Level Overview:

● Used to prevent fake certificates.

● Enables quick verification by employers or other institutions.

● Shows how blockchain can be used in education and credential verification.

## Result:

Thus the smart contract for issuing and verifying academic certificates on Ethereum is successfully deployed.
