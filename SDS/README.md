## Formal verification of the SDS protocol

This is a simplified version of the classical key distribution protocol proposed by Denning and Sacco, and it is called SDS (Simplified Denning-Sacco). Digital certificates and timestamps are excluded in our simplified version. The purpose of the protocol is to securely distribute a secret key between principals. Let A and B denote two principals, the message exchanged in the protocol is as follows:


    (i)  A -> B : aenc(PK_B, aenc(SK_A, B ; K)) 
    (ii) B -> A : senc(K, A ; B)

aenc and senc denote asymmetric encryption and symmetric encryption, respectively. Each principal A has a pair of public and private keys denoted by PK_A and SK_A, respectively, that can be used for asymmetric encryption and decryption.
We model the protocol in CafeOBJ with the existence of a generic Dolev-Yao intruder.

## Secrecy property
We formally verify the *key secrecy* property, which states that a secret key can be securely distributed to principals, or in other words, two principals can establish a key that cannot be compromised even by an active attacker placed in the middle of the connection. The property is specified by the invariant:

```
op keySe : Sys Prin Prin Secret Nat -> Bool
eq keySe(S,A,B,K,N) = 
 (not(A = intru or B = intru) and
  msg1(A,A,B, aenc(pubK(B), aenc(priK(A), B || K)), N) \in nw(S))
 implies not(K \in knl(S)) .
```

 The property is proven with eight auxiliary lemmas, namely `inv1`,..., `inv8`. The proof scores of `keySe` and the lemmas are in the file `proof-scores.cafe`.

## Authentication property
We also verify the `authentication` property: If A has sent to B a message (i) and received back a valid message (ii) apparently sent from B, then the message is indeed sent by B. We specify the property by the following invariant:

```
op auth : Sys Prin Prin Prin Secret Nat Nat Nat -> Bool
eq auth(S,B2,A,B,K,N,N2,?T) = 
((not(A = intru or B = intru) and
  msg1(A,A,B, aenc(pubK(B), aenc(priK(A), B || K)), N) \in nw(S) and
  msg2(B2,B,A, senc(K, A || B), N2) \in nw(S))
 implies msg2(B,B,A, senc(K, A || B), ?T) \in nw(S)) .
```

where ?T indicates that this variable is existential quantifier. This ?-symbol prefix is not mandatory from a syntactic point of view, but it helps to distinguish between existential quantifier variables and universal quantifier ones, such as A and N. 
To verify this property, we use "the proof method for invariant properties with existential quantifier variables".
Six more lemmas are required to complete the proof of `auth`, namely `inv9`,...,`inv14`. The proofs of them are saved in files `inv9`,...,`inv14`. Human users are required to resolve some sub-cases in the generated proofs of `auth` and `inv14`, which are saved in files `auth-m.cafe` and `inv14-m.cafe`.