# PlainVCs + DIDComm

In this directory, you find the files for the protocol instance. Plain Verifiable Credentials (VCs) presented in Verifiable Presentations (VPs) using DIDComm with session key pairs.

## Outline

$Protocol$ | $Property$ | $No.$ | $Relative Path$ | $OK$ | $Attack$ 
---|---|---|---|---|---
|||||
Plain VCs | Secrecy | 1 | [ssipv.pv#L287](ssipv.pv#L287) |  [x]  | [ ]
 | | | 2 | [archive/ssipv_forward_secrecy.pv](archive/ssipv_forward_secrecy.pv) |  [x]  | [ ]
 | | Agreement | 3 | [ssipv.pv#L309](ssipv.pv#L309) |  [x]  | [ ]
 | | | 4 | [ssipv_ok_VP_leaked.pv](ssipv_ok_VP_leaked.pv) |  [x]  | [ ]
 | | | 5 | [ssipv_unforgeable_VC.pv](ssipv_unforgeable_VC.pv) |  [x]  | [ ]
| | | 6 | [ssipv_attack_domain_missing_replay.pv](ssipv_attack_domain_missing_replay.pv) |  [ ] | [x] 
| | | 7 | [ssipv_attack_no_nonce_VP_leaked.pv](ssipv_attack_no_nonce_VP_leaked.pv) |  [ ] | [x] 
| | | 8 | [ssipv_attack_VC_reissued.pv](ssipv_attack_VC_reissued.pv) |  [ ] | [x] 
| | Unlinkability | 9 | [ssipv_unlinkable.dps](ssipv_unlinkable.dps) |  [x]  | [ ]
| | | 10 | [ssipv_attack_verifier_unlinkablity.dps](ssipv_attack_verifier_unlinkablity.dps) |  [ ] | [x] 
|||||

For a description of the potential attacks when deviating from the protocol, visit the [Plain VCs](../README.md) parent directory.

A short description of the other files, marked as OK (the security properties are formally verified):

- __No. 1 & 3__, [ssipv.pv](ssipv.pv), is the instance of the protocol that we commonly refer to as "our instance of the protocol". We use the notation as introduced in the top-level [README.md](../../README.md). The protocol is illustrated by this [MSC](../doc/msc-full-protocol.pdf). 
- __No. 2__, [archive/ssipv_forward_secrecy.pv](archive/ssipv_forward_secrecy.pv), proves that forward secrecy holds for the protocol, even when long-term private keys are leaked. This model of the protocol uses an old notation, and is archived. Nonetheless, the formal verification of the security property holds.
- __No. 4__, [ssipv_ok_VP_leaked.pv](ssipv_ok_VP_leaked.pv), models the protocol in the case that the Verifiable Presentation (VP) of the credential, which is used for authentication, is later leaked to an attacker. It proves that even with a leaked VP _secrecy_ and _agreement_ still hold, and that an attack is not able to capitalise on the leaked VP.
- __No. 5__, [ssipv_unforgeable_VC.pv](ssipv_unforgeable_VC.pv), proves that a Verifiable Credential (VC), which is issued by a particular actor, i.e. the issuer, can not be forged by an attacker mimicking the specific issuer.
- __No. 6__, [ssipv_attack_domain_missing_replay.pv](ssipv_attack_domain_missing_replay.pv), illustrates a replay attack on the protocol, when the `domain`, i.e., the intended recipient, of the VP is omitted. It is illustrated by this [MSC](../doc/msc-mitm-attack.pdf), and a description is available in the [Plain VCs](../README.md) parent directory.
- __No. 7__, [ssipv_attack_no_nonce_VP_leaked.pv](ssipv_attack_no_nonce_VP_leaked.pv), illustrates a replay attack on the protocol, when the `nonce` of the VP is omitted, and the VP is leaked. A description is available in the [Plain VCs](../README.md) parent directory.
- __No. 8__, [ssipv_attack_VC_reissued.pv](ssipv_attack_VC_reissued.pv), illustrates a replay attack on the protocol, when the holder, i.e., the recipient of a freshly issued credential does not check and verify the received credential. It is illustrated by this [MSC](../doc/msc-njagreement-attack.pdf), and a description is available in the [Plain VCs](../README.md) parent directory.
- __No. 9__, [ssipv_unlinkable.dps](ssipv_unlinkable.dps), illustrates _unlinkability_ from the perspective of the issuer. It proves that, after issuing a credential, it is impossible for the issuer to track how it is used with honest verifier.
- __No. 10__, [ssipv_attack_verifier_unlinkablity.dps](ssipv_attack_verifier_unlinkablity.dps), illustrates a stronger property, i.e., _unlinkability from the perspective of both the issuer
and verifier_, which further ensures that verifiers cannot link two uses of the
same credential. This __property cannot be achieved for plain Verifiable Credentials__, since the identifier of the holder appears in each Verifiable Presentation.