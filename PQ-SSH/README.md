## Formal analysis of the PQ SSH protocol

In this folder, you can find:

1. `pqssh.cafe`: the CafeOBJ formal specification of the protocol.

2. `invariant.cafe`: the properties and lemmas. Among them,
   - `keySe` specifies the *key secrecy* property,
   - `fwdSe` specifies the *forward secrecy* property,
   - `unique` specifies the *session identifier uniqueness* property,
   - `auth` specifies the strong verion of the *authentication* property, which is not satisfied,
   - `auth'` specifies the weak verion of the *authentication* property, i.e., *weak-authentication* properties, which is proved, and
   - others are lemmas needed to completed the verifications.

3. `check.cafe`: shows that two principals can successfully negotiage a shared secret.
4. `keySe.cafe`: the proof of `keySe`.
5. `fwdSe.cafe`: the proof of `fwdSe`.
6. `unique.cafe`: the proof of `unique`.
7. `auth.cafe`: the proof of `auth'` (specifying the *weak-authentication* property), which uses "the proof method for invariant properties with existential quantifier variables". 
8. `secrecy.cafe`, `inv1.cafe`,..., `inv18.cafe`: the proofs of the corresponding lemmas. Note that `inv16` is an invariant with existential quantifier variables.
9. `learnSS.cafe`: shows that the intruder can learn a shared secret if the private host key of the server is compromised.
10. `auth-counterexample`: shows a counterexample of the predicate `auth` (specifying the strong-authentication property). See README in that folder for more details.
11. `incorrect-HBR_REPLY`: contains the revised CafeOBJ specification in which the HBR_REPLY message no longer contains the server public host key and the signature. A counterexample of the `keySe` property is also shown. See README in that folder for more details.