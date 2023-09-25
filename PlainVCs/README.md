# Plain VCs - SSI Protocol for Web Resource Access

In this directory, you find the files for the protocol instance: Plain Verifiable Credentials (VCs) presented in Verifiable Presentations (VPs) using DIDComm with session key pairs.
In addition, there is a modified verision of the protocol that is modified to not use DIDComm/Authcrypt all the way, but instead use Diffie-Hellmann (DH): Plain Verifiable Credentials (VCs) presented in Verifiable Presentations (VPs) using DIDComm with a DH handshake.


## Outline

$Protocol$ | $Property$ | $No.$ | $Relative Path$ | $OK$ | $Attack$ 
---|---|---|---|---|---
|||||
[Plain VCs](DIDComm/) | Secrecy | 1 | [ssipv.pv#L287](DIDComm/ssipv.pv#L287) |  [x]  | [ ]
 | | | 2 | [archive/ssipv_forward_secrecy.pv](DIDComm/archive/ssipv_forward_secrecy.pv) |  [x]  | [ ]
 | | Agreement | 3 | [ssipv.pv#L309](DIDComm/ssipv.pv#L309) |  [x]  | [ ]
 | | | 4 | [ssipv_ok_VP_leaked.pv](DIDComm/ssipv_ok_VP_leaked.pv) |  [x]  | [ ]
 | | | 5 | [ssipv_unforgeable_VC.pv](DIDComm/ssipv_unforgeable_VC.pv) |  [x]  | [ ]
| | | 6 | [ssipv_attack_domain_missing_replay.pv](DIDComm/ssipv_attack_domain_missing_replay.pv) |  [ ] | [x] 
| | | 7 | [ssipv_attack_no_nonce_VP_leaked.pv](DIDComm/ssipv_attack_no_nonce_VP_leaked.pv) |  [ ] | [x] 
| | | 8 | [ssipv_attack_VC_reissued.pv](DIDComm/ssipv_attack_VC_reissued.pv) |  [ ] | [x] 
| | Unlinkability | 9 | [ssipv_unlinkable.dps](DIDComm/ssipv_unlinkable.dps) |  [x]  | [ ]
| | | 10 | [ssipv_attack_verifier_unlinkablity.dps](DIDComm/ssipv_attack_verifier_unlinkablity.dps) |  [ ] | [x] 
|||||
[Plain VCs + Diffie-Hellman](DIDComm%2BDH/) | Secrecy | 14 | [ssipv.pv#L302](DIDComm%2BDH/ssipv.pv#L302) |  [x]  | [ ]
 | | Agreement | 15 | [ssipv.pv#L324](DIDComm%2BDH/ssipv.pv#L324) |  [x]  | [ ]
|||||

## Documentation (doc)

In [doc](doc), you will find Message Sequence Charts (MSCs) that illustrate the protocol and variations of the protocol that are prone to attacks. 

$MSC$ | $Description$
---|--- 
[msc-full-protocol.pdf](doc/msc-full-protocol.pdf) | An illustration of the protocol, using the current notation (as introduced in the top-level [README.md](../README.md)). It corresponds to the Proverif code in [DIDComm/ssipv.pv](DIDComm/ssipv.pv), and the DeepSec code in [DIDComm/ssipv_unlinkable.dps](DIDComm/ssipv_unlinkable.dps).
[msc-protocol.pdf](doc/msc-protocol.pdf) | An illustration of the protocol, using an old notation. It corresponds to the archived Proverif code in [DIDComm/archive/ssipv_multiparty_agreement.pv](DIDComm/archive/ssipv_multiparty_agreement.pv).
[msc-mitm-attack.pdf](doc/msc-mitm-attack.pdf) | An illustration of an attack on the protocol, when the domain, i.e., the intended verifier, of an credential presentation, is omitted. An attack is able to replay a credential presentation. The MSC uses the old notation and corresponds to the Proverif code in __No. 6__, [DIDComm/ssipv_attack_domain_missing_replay.pv](DIDComm/ssipv_attack_domain_missing_replay.pv), which we already updated to the new notation. (Updating the MSC notation is on the TODO list.)
[msc-njagreement-attack.pdf](doc/msc-njagreement-attack.pdf.pdf) | An illustration of an attack on the protocol, when the holder, i.e., the recipient of a freshly issued credential, does not check and verify the received credential. This results in a potential re-issuance by an attacker using an already issued credential by an honest issuer, thereby violating multi-party agreement. The MSC uses the old notation and corresponds to the Proverif code in __No. 8__, [DIDComm/ssipv_attack_VC_reissued.pv](DIDComm/ssipv_attack_VC_reissued.pv), which we already updated to the new notation. (Updating the MSC notation is on the TODO list.)
[msc_anon_multiparty_agreement_dh.pdf](doc/msc_anon_multiparty_agreement_dh.pdf) | A hand-scribbled concept on how to use a Diffie-Hellmann (DH) handshake within the protocol. This was the basis for exploring DIDComm+DH where we do not use DIDComm's _authcrypt_ on every message but instead use a DH handshake to then use a shared secret for encrypting messages.

---

# Description of Attacks 

When not following the protocol but, e.g., omitting fields that are marked as "optional" by SSI specifications, the following attacks may be possible.

## No. 6 - Replay Attack when omitting `domain`.
According to the W3C recommendation on the VC data model, including the `domain`, e.g., the receiving agent or a Web domain to authenticate with, is optional.
Moreover, the function or meaning of `domain` is not even explained in the specification which may lead implementors to just skip over a seemingly unimportant element.

In doing so, however, authentication protocols are prone to replay attacks as illustrated in the [MSC](doc/msc-mitm-attack.pdf) and the Proverif [code](DIDComm/ssipv_attack_domain_missing_replay.pv):
A holder, e.g., a student wants to authenticate to Eve, e.g., for some student discount at some online shop. 
In the authentication process, Eve also authenticates to the holder; the holder knows that they are communicating with Eve and present to them a Verifiable Presentation (VP) of the student credential.
This process may even complete successfully and the student may even receive their student discount.
During this authentication process, however, Eve starts a second authentication process with another verifier, e.g., a university to prove that she is a student, except she is not.
Eve replays content of transmitted messages from the university to the student and vice versa.
For example, Eve is able to replay the challenge nonce $\texttt{n}_\texttt{c}$ from the university to the holder. 
Subsequently, this nonce is included in the presentation of the student VC and signed by the holder.
After receiving this presentation, Eve replays this presentation to the university.
With the matching nonce and the signature of the holder on this VP, the university may be tempted to believe that they were communication with the holder the whole time, except they were communicating with Eve posing to be the actual holder.


By including the `domain` in the VP, such replay attacks are prevented.
When the holder specifies Eve to be the intended recipient of the VP, Eve can not re-use that VP to authenticate to the university as the university will check if they are really the intended recipient of that VP. 


## No. 7 - Replay Attack when omitting `nonce`.
According to the W3C recommendation on the VC data model, including the `nonce`, e.g., a cryptographic challenge from a potential verifier, is optional.
Moreover, the function or meaning of `nonce` is not even explained in the specification which may lead implementors to just skip over a seemingly unimportant element.

In doing so, however, authentication protocols are prone to replay attacks as illustrated in the Proverif [code](DIDComm/ssipv_attack_no_nonce_VP_leaked.pv).
A holder, e.g., a student wants to authenticate to their university, e.g., to get access to online course material. 
The student signs a VP and authenticates to the university using it.
If this VP is leaked, e.g., because the log files of the university were exposed (line 192 in the code), any agent in possession of that student's VP is now able to authenticate to the university as that agent; the VP is not longer tied to a particular communication session. 


## No. 8 - Replay Attack when not checking VC as holder.

There even exist non-trivial attacks on the protocol when considering the multi-party aspect in particular as illustrated in the [MSC](doc/msc-njagreement-attack.pdf) and the Proverif [code](DIDComm/ssipv_attack_VC_reissued.pv):
During the issuance of a VC, the holder must authenticate the issuer and check that the received VC is actually what they expected.
Otherwise, the security property of multiparty non-injective agreement is not met.

In a nutshell, the attack begins with a non-altered full execution of the protocol:
The VC is issued by an issuer to the holder and used to authenticate to a verifier.
Then, however, the verifier, i.e., Eve, re-issues the received VC to the holder again.
When the holder simply acknowledges the "new" credential without any checks, i.e., lines 225 and 226 are commented out in the [code](DIDComm/ssipv_attack_VC_reissued.pv#L225), and then proceeds to use it, the desired security property does not hold.
By simply checking that the received VC was received from the desired agent,  laissued by the desired agent and includes the desired attributes, this attack can be mitigated.


