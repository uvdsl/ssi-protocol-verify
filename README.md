# SSI Authentication and Authorization Protocol for Web Resource Access; verified using ProVerif (and DeepSec)

This repository contains the formal verification of security properties of the protocol flow for authentication and authorization for Web resource access.
We use [ProVerif](https://bblanche.gitlabpages.inria.fr/proverif/) for proving _secrecy_ and _agreement_, and use [DeepSec](https://doi.org/10.1109/SP.2018.00033) for proving _unlinkability_.

## Repository Outline

The structure of our GitHub repository.  


$Protocol$ | $Property$ | $No.$ | $Relative Path$ | $OK$ | $Attack$ 
---|---|---|---|---|---
|||||
[Plain VCs](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/) | Secrecy | 1 | [ssipv.pv#L287](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv.pv#L287) |  [x]  | [ ]
 | | | 2 | [archive/ssipv_forward_secrecy.pv](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/archive/ssipv_forward_secrecy.pv) |  [x]  | [ ]
 | | Agreement | 3 | [ssipv.pv#L309](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv.pv#L309) |  [x]  | [ ]
 | | | 4 | [ssipv_ok_VP_leaked.pv](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_ok_VP_leaked.pv) |  [x]  | [ ]
 | | | 5 | [ssipv_unforgeable_VC.pv](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_unforgeable_VC.pv) |  [x]  | [ ]
| | | 6 | [ssipv_attack_domain_missing_replay.pv](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_attack_domain_missing_replay.pv) |  [ ] | [x] 
| | | 7 | [ssipv_attack_no_nonce_VP_leaked.pv](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_attack_no_nonce_VP_leaked.pv) |  [ ] | [x] 
| | | 8 | [ssipv_attack_VC_reissued.pv](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_attack_VC_reissued.pv) |  [ ] | [x] 
| | Unlinkability | 9 | [ssipv_unlinkable.dps](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_unlinkable.dps) |  [x]  | [ ]
| | | 10 | [ssipv_attack_verifier_unlinkablity.dps](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv_attack_verifier_unlinkablity.dps) |  [ ] | [x] 
|||||
[Anon VCs](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm/) | Secrecy | 11 | [ssipv.pv#L297](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm/ssipv.pv#L297) |  [x]  | [ ]
 | | Agreement | 12 | [ssipv.pv#L319](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm/ssipv.pv#L319) |  [x]  | [ ]
| | Unlinkability | 13 | [ssipv_unlinkablity_ok_wrt_verifier.dps](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm/ssipv_unlinkablity_ok_wrt_verifier.dps) |  [x]  | [ ]
|||||
[Plain VCs + Diffie-Hellman](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm%2BDH/) | Secrecy | 14 | [ssipv.pv#L302](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm%2BDH/ssipv.pv#L302) |  [x]  | [ ]
 | | Agreement | 15 | [ssipv.pv#L324](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm%2BDH/ssipv.pv#L324) |  [x]  | [ ]
|||||
[Anon VCs + Diffie-Hellmann](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm%2BDH/) | Secrecy | 16 | [ssipv.pv#L312](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm%2BDH/ssipv.pv#L312) |  [x]  | [ ]
 | | Agreement | 17 | [ssipv.pv#L334](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm%2BDH/ssipv.pv#L334) |  [x]  | [ ]
|||||

For a description of the potential attacks when deviating from the protocol, visit the [Plain VCs](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/) parent directory.

For more detailled information, visit the corresponding "protocol directories", i.e., 
- [Plain VCs](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/) for an instance of the protocol using plain/simple Verifiable Credentials (VCs) and DIDComm (which is typically the instance of the protocol we refer to), 
- [Anon VCs](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm/) for an instance of the protocol using anonymous credentials and DIDComm, 
- [Plain VCs + Diffie-Hellmann](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm%2BDH/) for an instance of the protocol using plain/simple Verifiable Credentials (VCs) and a Diffie-Hellmann handshake, and 
- [Anon VCs + Diffie-Hellmann](https://github.com/uvdsl/ssi-protocol-verify/tree/main/AnonVCs/DIDComm%2BDH/) for an instance of the protocol using anonymous credentials and a Diffie-Hellmann handshake.

## Idea

The protocol is indended for a client-server scenario on the Web.
A client desires are Web resource served by the server.
Upon request, access is denied and the client is pointed towards the authentication-authorization endpoint.
The client acts as the prover and the authentication-authorization endpoint acts as the verifier.

The authentication-authorization endpoint enforces predefined access control rules (ACRs).
These ACRs specify which attribute the prover needs to have asserted by which issuer.

## Example
In a nutshell, Verifiable Credentials (VCs) enable an agent (the "holder") to prove to a second agent (the "verifier") that a third agent (the "issuer") has asserted and signed some statements or claims. 
In other words, with a presentation of a VC an agent proves to a verifying agent that 

1. they are in possession of the VC
2. the VC was issued by a particular issuer (agent)
3. the VC contains some claims, e.g., attributes of the holder
4. the VC was presented by the proving agent, e.g., the holder itself

For example, consider the use case of a student accessing online teaching material of some  guest professor.
Here, the student's university, the issuer, provides the student, the holder, a digital student credential, which asserts that the holder is a student signed by the university.
A guest professor at the university has a (private) Web server where online teaching material is accessible only to students of the university they are guest lecturing at.
As the professor does not know all the students, i.e., the group of all students is private, the professor can not grant this group access to the Web resources. 
To gain access to the online teaching material, the students have to prove that they are really enrolled at the university using a presentation, i.e., a VP, of the corresponding digital student credential, i.e., the VC.
This VP includes the VC and some additional meta data, and is typically signed by the holder to prove that the student assertion is really about them.
In this way, the professor's Web server can verify the above mentioned facts (1)-(4).
The use case is generaliseable to general accessing resources on the Web.

How do the students know that they are really talking to the professor (or his Web server) when authenticating online?
The students may look up the personal homepage of the professor where the professor's identifier (the professor's DID) is advertised.
With that, the system relies on the Domain Name System (DNS) and the transport protocol of HTTPS to ensure that agents are able to be identified correctly.
Other approaches, as mentioned below, may include government registries, governed blockchains or smart contracts.

## Assumptions:
- The __Self-Sovereign Identity (SSI) assumption__:  
All agents can mint and manage a keypairs in a self-sovereign manner.
- The __Decentralised Identifier (DID) assumption__:  
All agents assume that the (integrity of the) link between DID of an agent, the thereby advertised public key and corresponding secret key can be trusted, in the sense that we assume that only the controller of the DID (the agent in control of the corresponding secret key) is able to modify/update the public key linked to the DID.
Each agent is thus assumed to keep the link between the DID, the thereby advertised their public key and their corresponding secret key, intact (meaning they use the corresponding secret key in communication).
Possible implementations e.g. via certification using DNS, in government registries, governed blockchains or smart contracts.
- The __Verifier-Issuer assumption__:  
The verifier assumes the issuer to have due diligence on validating the assertions they make, e.g. that Holder is actually a student (which may be out-of-band).
The verifier thus assumes that the issuer behaves honestly according to the protocol (given the context of the use case).

## Interesting: The holder must check the credential after issuance

An interesting observation is that, the holder checking the signature of an anonymous credential after issuance and before usage in a provenance session is not as critical for authentication as it is for regular VCs (in short, because zero-knowledge proofs never reveal the anonymous credential itself, only a proof-of-possession of the anonymous credential). Yet, the holder checking the signature and contents of an anonymous credential after issuance and before usage is critical for unlinkability (in short, because an issuer may attempt to inject unsolicited identifying information into the attributes).

## The Protocol with Plain VCs (not anonymous)

Find a Message Sequence Chart (MSC) of the plain model [here](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/doc/msc-full-protocol.pdf).

Here, we give the corresponding formal model (cf. [Proverif code](https://github.com/uvdsl/ssi-protocol-verify/tree/main/PlainVCs/DIDComm/ssipv.pv)):

### Grammar
$~$ | $~$ | $~$ | $~$ | $~$ 
---|---|---|---|---
M, N, K ::= | x | $\textit{variables}$ | |
$~$ | (M, $\ldots$, N) | $\textit{tuples}$ |
$~$ | $proj_{i}(M)$ | $i^{th} \textit{projection}$ | $proj_{i}\left(M_1, \ldots, M_i, \ldots, M_n \right)$ | $= M_i$
$~$ | $pk(K) $ | $\textit{public key}$ |
$~$ | $\{ M \}_{K}$ | $\textit{encryption}$ |
$~$ | $dec( M , K )$ | $\textit{decryption}$ | $dec( \{ M \}_{K} , K )$ | $= M$  
$~$ | $sig( M , K ) $| $\textit{signature}$ |
$~$ | $check( M , K )$ | $\textit{check signature}$ | $check( sig( M , K ) , K )$ | $= true$

### Part 1 - Issuance

Holder $(P, sk\_P, I, pk\_I, V, pk\_V)$ | Issuer $(I, sk\_I, attr, P, pk\_P)$
--- | ---
$\textit{new } ssk\_{PI}, n\_p, n\_h; $  | $\textit{new } ssk\_I, n\_i; $
$\textit{let } m'\_{0} := (n\_p,pk(ssk\_{PI})) \textit{ in}$  | $\textit{ch}(m\_{0}); $ 
$\textit{let } m\_{0} := \{(m'\_{0},\textit{sig}(m'\_{0},ssk\_{PI}))\}\_{pk\_I} \textit{ in}$  | $\textit{let } ((n\_p,spk\_{PI}),\textit{s}\_0):= \textit{adec}(m\_{0},sk\_I) \textit{ in}$
$\overline{\textit{ch}}(m\_{0}); $  | $\textit{if } \textit{check}((n\_p,spk\_{PI}),\textit{s}\_0, spk\_{PI}) \textit{ then}$
$\textit{ch}(m\_{1}); $  | $\textit{let } m'\_{1} := (n\_p,n\_i,pk(ssk\_I)) \textit{ in}$
$\textit{let } ((n'\_p,n\_i,spk\_I), \textit{s}\_1) := \textit{adec}(m\_{1},ssk\_{PI}) \textit{ in}$  | $\textit{let } m\_{1} := \{(m'\_{1},\textit{sig}(m'\_{1},sk\_I))\}\_{spk\_{PI}} \textit{ in}$
$\textit{if } \textit{check}((n'\_p,n\_i,spk\_I),\textit{s}\_1,pk\_I) \textit{ then}$  | $\overline{\textit{ch}}(m\_{1}); $
$\textit{if } n'\_p = n\_p \textit{ then}$  | $\textit{ch}(m\_{2}); $
$\textit{let } m'\_{2} := ((n\_i,P,I,n\_h),\textit{sig}((n\_i,P,I,n\_h),sk\_P)) \textit{ in}$  | $\textit{let } (((n'\_i,P',I',n\_h),\textit{s}\_P),\textit{s}\_2) := \textit{adec}(m\_{2},ssk\_I) \textit{ in}$ 
$\textit{let } m\_{2} := \{(m'\_{2},\textit{sig}(m'\_{2},ssk\_{PI}))\}\_{spk\_I} \textit{ in}$  | $\textit{if } \textit{check}(((n'\_i,P',I',n\_h),\textit{s}\_P),\textit{s}\_2,spk\_{PI}) \textit{ then}$
$\overline{\textit{ch}}(m\_{2}); $  | $\textit{if } \textit{check}((n'\_i,P',I'),\textit{s}\_P,pk\_P) \textit{ then}$
$\textit{ch}(m\_{3}); $  | $\textit{if } (n'\_i,P',I') = (n\_i,P,I) \textit{ then}$
$\textit{let } (((((P',attr,I'), \textit{s}\_I), P'',n'\_h), s\_H), \textit{s}\_3) := \textit{adec}(m\_{3},ssk\_{PI}) \textit{ in}$  | $\textit{let } {\textit{claims}} := (P, \textit{attr},I) \textit{ in}$
$\textit{if } \textit{check}(((((P',attr,I'), \textit{s}\_I), P'', n'\_h), s\_H)\textit{s}\_3, spk\_I) \textit{ then}$  | $\textit{let } {\textit{VC}} := ({\textit{claims}} ,\textit{sig}({\textit{claims}}, sk\_I)) \textit{ in}$ 
$\textit{if } \textit{check}((((P',attr,I'), \textit{s}\_I), P'', n'\_h), \textit{s}\_H, spk\_I) \textit{ then}$  | $\textit{let } m'\_{3} := ((\textit{VC},P,n\_H),\textit{sig}((\textit{VC},P,n\_H),sk\_I)) \textit{ in}$ 
$\textit{if } \textit{check}((P',attr,I'), \textit{s}\_I, pk\_I) \textit{ then}$  | $\textit{let } m\_{3} := \{(m'\_{3},\textit{sig}(m'\_{3},ssk\_I))\}\_{spk\_{PI}} \textit{ in}$
$\textit{if } (P',I',P''n'\_h) = (P,I,P, n\_h) \textit{ then}$  | $\overline{\textit{ch}}(m\_{3}); $
$!Prover (P, sk\_P, {\textit{VC}}, V, pk\_V) $  |

### Part 2 - Provenance

Prover $(P, sk\_P, \textit{VC}, V, pk\_V)$ | Verifier $(V, sk\_V, {\textit{RULE}}, pk\_P, pk\_I, {\textit{URI}})$ 
--- | ---
$\textit{new } ssk\_{PV}, n\_p; $  | $\textit{new } ssk\_V, n\_i, n\_c, \textit{tkn}; $ 
$\textit{let } m'\_{4} := (n\_p,pk(ssk\_{PV})) \textit{ in}$  | $\textit{ch}(m\_{4}); $
$\textit{let } m\_{4} := \{(m'\_{4},\textit{sig}(m'\_{4},ssk\_{PV}))\}\_{pk\_V} \textit{ in}$  | $\textit{let } ((n\_p,spk\_{PV}),\textit{s}\_4) := \textit{adec}(m\_{4},sk\_V) \textit{ in}$
$\overline{\textit{ch}}(m\_{4}); $  | $\textit{if } \textit{check}((n\_p,spk\_{PV}),\textit{s}\_4,spk\_{PV}) \textit{ in}$
$\textit{ch}(m\_{5}); $  | $\textit{let } m'\_{5} := (n\_p,n\_v,pk(ssk\_V)) \textit{ in}$
$\textit{let } ((n'\_p,n\_v,spk\_V),\textit{s}\_5) := \textit{adec}(m\_{5},ssk\_{PV}) \textit{ in}$  | $\textit{let } m\_{5} := \{ (m'\_{5},\textit{sig}(m'\_{5},sk\_V)) \}\_{spk\_{PV}} \textit{ in}$ 
$\textit{if } \textit{check}((n'\_p,n\_v,spk\_V),\textit{s}\_5,pk\_V) \textit{ then}$  | $\overline{\textit{ch}}(m\_{5}); $ 
$\textit{if } n'\_p := n\_p \textit{ then}$  | $\textit{ch}(m\_{6}); $
$\textit{let } m'\_{6} := (n\_v, {\textit{URI}}) \textit{ in}$  | $\textit{let } ((n'\_v,uri'),\textit{s}\_6)  := \textit{adec}(m\_{6},ssk\_V) \textit{ in}$ 
$\textit{let } m\_{6} := \{(m'\_{6},\textit{sig}(m'\_{6},ssk\_{PV}))\}\_{spk\_V} \textit{ in}$  | $\textit{if } \textit{check}((n'\_v,uri'),\textit{s}\_6,spk\_{PV}) \textit{ then}$  
$\overline{\textit{ch}}(m\_{6}) $ | $\textit{if} (n'\_v,{\textit{URI} \'}) = (n\_v,{\textit{URI}}) \textit{ then}$
$\textit{ch}(m\_{7}); $  | $\textit{let } m'\_{7} := (n\_c,{\textit{RULE}}) \textit{ in}$ 
$\textit{let } ((n\_c,\textit{RULE} ),\textit{s}\_7) := \textit{adec}(m\_{7},ssk\_{PV}) \textit{ in}$  | $\textit{let } m\_{7} := \{(m'\_{7},\textit{sig}(m'\_{7},ssk\_V))\}\_{spk\_{PV}} \textit{ in}$
$\textit{if } \textit{check}((n\_c,\textit{RULE} ),\textit{s}\_7,spk\_V) \textit{ then}$  | $\overline{\textit{ch}}(m\_{7}); $ 
$\textit{let } (\textit{claims},\textit{s}\_{I}):=\textit{VC}  \textit{ in}$  | $\textit{ch}(m\_{8}); $
$\textit{if } \textit{claims}=\textit{RULE} \textit{ then}$  | $\textit{let } (((((P',attr',I'), \textit{s}\_I),n'\_c,V'), \textit{s}\_P ),\textit{s}\_8) := \textit{adec}(m\_{8},ssk\_V) \textit{ in}$
$\textit{let } {\textit{VP}} := (({\textit{VC}},n\_c,V), \textit{sig}(({\textit{VC}},n\_c,V),sk\_P)) \textit{ in}$  | $\textit{if } \textit{check}(((((P',attr',I'), \textit{s}\_I),n'\_c,V'), \textit{s}\_P ),\textit{s}\_8,spk\_{PV}) \textit{ then}$
$\textit{let } m\_{8} := \{{\textit{VP}},\textit{sig}({\textit{VP}},ssk\_{PV})\}\_{spk\_V} \textit{ in}$  | $\textit{if } \textit{check}((((P',attr',I'), \textit{s}\_I),n'\_c,V'), \textit{s}\_P, pk\_P) \textit{ then}$
$\overline{\textit{ch}}(m\_{8}) $  | $\textit{if } \textit{check}((P',attr',I'), \textit{s}\_I, pk\_I) \textit{ then}$
$\textit{ch}(m\_{9}) $  | $\textit{if } ((P',attr',I'),n'\_c,V') = ((P,attr,I),n\_c,V) \textit{ then}$
$\textit{let }((\textit{tkn},\textit{s}\_\textit{tkn}),\textit{s}\_9) := (\textit{adec}(m\_{9},ssk),spk\_V) \textit{ in}$  | $\textit{let } m'\_{9} := (\textit{tkn},\textit{sig}(\textit{tkn},sk\_V)) \textit{ in}$ 
$\textit{if } \textit{check}((\textit{tkn},\textit{s}\_\textit{tkn}),\textit{s}\_9,spk\_V) \textit{ then}$  | $\textit{let } m\_{9} := \{\textit{sig}(m'\_{9},ssk\_V)\}\_{spk\_{PV}} \textit{ in}$
$\textit{if } \textit{check}(\textit{tkn},\textit{s}\_\textit{tkn},pk\_V) \textit{ then}$  | $\overline{\textit{ch}}(m\_{9}); $ 
### Setup


Issuer $(I, sk\_I, attr, P, pk\_P)$ | Holder $(P, sk\_P, I, pk\_I, V, pk\_V)$ |  Verifier $(V, sk\_V, {\textit{RULE}=(P,attr,I)}, pk\_P, pk\_I, {\textit{URI}})$ 
--- | --- | ---
$\textit{let } pk\_I := \textit{getPubKey}(I) \textit{ in}$ | $\textit{let } pk\_P := \textit{getPubKey}(P) \textit{ in}$ | $\textit{let } pk\_V := \textit{getPubKey}(V) \textit{ in}$ 
$\textit{let } pk\_I = \textit{getPubKey}(proj\_{2}({\textit{VC} \'})) $ | $\textit{let } pk\_P := \textit{getPubKey}(proj\_{1}(m'\_{2})) \textit{ in}$ 


### Configuration

$~$ | $~$
--- | ---
$\textit{new } sk\_I, sk\_P, sk\_V; $ | 
$\overline{ch}((pk(sk\_I), pk(sk\_P), pk(sk\_V))); $ |
$!\textit{Issuer}^{honest}(I, sk\_I, \textit{attr}, P, pk(sk\_P))    \mid      $ |
$!\textit{Holder}^{honest}(P, sk\_P, I, pk(sk\_I), V, pk(sk\_V))          \mid  $ |
$!\textit{Verifier}^{honest}(V, sk\_V, {(  P,   attr,   I  )}, pk(sk\_P), pk(sk\_I), {\textit{URI}})     \mid  $ |
$connect(EasP, pk\_{EasP}); $ |
$\textit{Issuer}^{open}(I, sk\_I, \textit{attr}, EasP, pk\_{EasP}) ~\mid$ |
$connect(EasI, pk\_{EasI}, EasV, pk\_{EasV}); $ |
$\textit{Holder}^{open}(P, sk\_P, EasI, pk\_{EasI}, EasV, pk\_{EasV})          \mid $ |
$connect(EasP, pk\_{EasP}, EasI, pk\_{EasI}); $
$\textit{Verifier}^{open}(V, sk\_V, {(  EasP,   attr,   EasI )}, pk\_{EasP}, pk\_{EasI}, {\textit{URI}}); $ |

