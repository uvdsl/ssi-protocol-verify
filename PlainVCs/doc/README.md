
## Documentation (doc)

Here, you find Message Sequence Charts (MSCs) that illustrate the protocol and variations of the protocol that are prone to attacks. 
For a more detailled description of the attacks, visit the parent directory's [README.md](../README.md).

$MSC$ | $Description$
---|--- 
[msc-full-protocol.pdf](msc-full-protocol.pdf) | An illustration of the protocol, using the current notation (as introduced in the top-level [README.md](../../README.md)). It corresponds to the Proverif code in [DIDComm/ssipv.pv](DIDComm/ssipv.pv), and the DeepSec code in [DIDComm/ssipv_unlinkable.dps](DIDComm/ssipv_unlinkable.dps).
[msc-protocol.pdf](msc-protocol.pdf) | An illustration of the protocol, using an old notation. It corresponds to the archived Proverif code in [DIDComm/archive/ssipv_multiparty_agreement.pv](DIDComm/archive/ssipv_multiparty_agreement.pv).
[msc-mitm-attack.pdf](msc-mitm-attack.pdf) | An illustration of an attack on the protocol, when the domain, i.e., the intended verifier, of an credential presentation, is omitted. An attack is able to replay a credential presentation. The MSC uses the old notation and corresponds to the Proverif code in __No. 6__, [DIDComm/ssipv_attack_domain_missing_replay.pv](DIDComm/ssipv_attack_domain_missing_replay.pv), which we already updated to the new notation. (Updating the MSC notation is on the TODO list.)
[msc-njagreement-attack.pdf](msc-njagreement-attack.pdf.pdf) | An illustration of an attack on the protocol, when the holder, i.e., the recipient of a freshly issued credential, does not check and verify the received credential. This results in a potential re-issuance by an attacker using an already issued credential by an honest issuer, thereby violating multi-party agreement. The MSC uses the old notation and corresponds to the Proverif code in __No. 8__, [DIDComm/ssipv_attack_VC_reissued.pv](DIDComm/ssipv_attack_VC_reissued.pv), which we already updated to the new notation. (Updating the MSC notation is on the TODO list.)
[msc_anon_multiparty_agreement_dh.pdf](msc_anon_multiparty_agreement_dh.pdf) | A hand-scribbled concept on how to use a Diffie-Hellmann (DH) handshake within the protocol. This was the basis for exploring DIDComm+DH where we do not use DIDComm's _authcrypt_ on every message but instead use a DH handshake to then use a shared secret for encrypting messages.

