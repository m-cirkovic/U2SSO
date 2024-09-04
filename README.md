# U2SSO

Cryptographic library of U2SSO authentication protocol and proof-of-concept example.

## Abstract

Unlinkability in Single-Sign-On (SSO) -- the inability to distinguish whether two accounts in two services were created by the same user or two different users -- is an essential security property that protects the user data across service providers (SPs). However, Federated Single-Sign-On (FSSO) solutions fail to obtain unlinkability in a *weak trust model* of a colluding Identity Provider (IdP), i.e., an IdP who colludes with the SPs learns the entire user profile.

We introduce the concept of **Unlinkable User-issued Single-Sign-On (U2SSO)**, where users create their own Single-Sign-On Identities (SSO-Ids), replacing the IdP, and store them in a distributed immutable Identity Registry (IdR). When signing up for a service, the user generates an unlinkable *service public key* from its SSO-Id and proves in zero-knowledge that it owns one of the SSO-Ids in IdR. The SP then uses this derived public key for future logins. 

U2SSO ensures unlinkability in a weak trust model such that even if the IdR and SPs collude, the unlinkability of service public keys is preserved. Additionally, U2SSO provides Sybil resistance with zero-knowledge proofs, allowing SPs to enforce rules to limit the creation of derived identities from the same SSO-Id to only one account.
Therefore, U2SSO offers the same usability, Sybil resistance, and outsourced key management for SPs as FSSO, with the added benefit of unlinkability.

## Libraries and Proof-of-concept

We provide three constructions: basic U2SSO, SNARK-U2SSO, and DBPoE-U2SSO in `./crypto` and `./crypto-ddh` directories.

Moreover, we implement a proof-of-concept service that allows U2SSO with an IdR built from an Ethereum smart contract to show the practicality of our proposal.

The example and the detailed readme to replicate the experiment is under `./proof-of-concept`.



