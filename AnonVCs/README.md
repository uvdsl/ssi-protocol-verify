# AnonVCs - Anonymous Version of the SSI Protocol for Web Resource Access

In this directory, you find the files for a anonymous version of the protocol:
Anonymous Verifiable Credentials presented as derived credentials using DIDComm with session key pairs.
In addition, there is a modified verision of the protocol that is modified to not use DIDComm/Authcrypt all the way, but instead use Diffie-Hellmann (DH): Anonymous Verifiable Credentials presented as derived credentials using DIDComm with a DH handshake.

## Outline

$Protocol$ | $Property$ | $No.$ | $Relative Path$ | $OK$ | $Attack$ 
---|---|---|---|---|---
|||||
[Anon VCs](DIDComm/) | Secrecy | 11 | [ssipv.pv#L297](DIDComm/ssipv.pv#L297) |  [x]  | [ ]
 | | Agreement | 12 | [ssipv.pv#L319](DIDComm/ssipv.pv#L319) |  [x]  | [ ]
| | Unlinkability | 13 | [ssipv_unlinkablity_ok_wrt_verifier.dps](DIDComm/ssipv_unlinkablity_ok_wrt_verifier.dps) |  [x]  | [ ]
|||||
[Anon VCs + Diffie-Hellmann](DIDComm%2BDH/) | Secrecy | 16 | [ssipv.pv#L312](DIDComm%2BDH/ssipv.pv#L312) |  [x]  | [ ]
 | | Agreement | 17 | [ssipv.pv#L334](DIDComm%2BDH/ssipv.pv#L334) |  [x]  | [ ]
|||||