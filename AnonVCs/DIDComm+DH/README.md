# # AnonVCs + DIDCommDH

In this directory, you find the files for a anonymous credential version of the protocol, and it is modified to not use DIDComm/Authcrypt all the way, but instead use Diffie-Hellmann (DH). Anonymous Verifiable Credentials presented as derived credentials using DIDComm with a DH handshake.

## Outline

$Protocol$ | $Property$ | $No.$ | $Relative Path$ | $OK$ | $Attack$ 
---|---|---|---|---|---
|||||
Anon VCs + Diffie-Hellmann | Secrecy | 16 | [ssipv.pv#L312](ssipv.pv#L312) |  [x]  | [ ]
 | | Agreement | 17 | [ssipv.pv#L334](ssipv.pv#L334) |  [x]  | [ ]
|||||