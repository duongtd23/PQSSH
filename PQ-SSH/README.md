## Formal analysis of Post-quantum Hybrid Key Exchange SSH Transport Layer Protocol

This folder contains materials of the formal analysis of the original Post-quantum Hybrid Key Exchange SSH Transport Layer Protocol, including the CafeOBJ formal specification of the protocol, the desired properties formalized in CafeOBJ, and the proof scores verifying those properties.

In this folder, you can find:

1. `pqssh.cafe`: the CafeOBJ formal specification of the protocol.

2. `invariants.cafe`: the properties and lemmas. Among them,
   - `keySe` specifies the *session key secrecy* property,
   - `fwdSe` specifies the *forward secrecy* property,
   - `unique` specifies the *session identifier uniqueness* property,
   - `auth` specifies the *authentication* property,
   - others are lemmas needed to completed the verifications.

3. `keySe.cafe`: the proof of `keySe`.
4. `fwdSe.cafe`: the proof of `fwdSe`.
5. `unique.cafe`: the proof of `unique`.
6. `secrecy.cafe`, `inv0.cafe`,..., `inv15.cafe`: the proofs of the corresponding lemmas.
7. `auth-counterexample.cafe`: shows a counterexample of the predicate `auth` (specifying the authentication property). See comments in that file for more details.
8. `inputs`: the input commands to generate the proof scores. It is only helpful in case you want to re-generate the proof scores again. See README in that folder.
9. `others`: see README in that folder.