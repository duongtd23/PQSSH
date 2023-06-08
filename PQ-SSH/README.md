## Formal analysis of the PQ SSH protocol

In this folder, you can find:

1. `pqssh.cafe`: the CafeOBJ formal specification of the protocol.

2. `invariants.cafe`: the properties and lemmas. Among them,
   - `keySe` specifies the *session key secrecy* property,
   - `fwdSe` specifies the *forward secrecy* property,
   - `unique` specifies the *session identifier uniqueness* property,
   - `auth` specifies the *authentication* property,
   - others are lemmas needed to completed the verifications.

3. `check.cafe`: shows that two principals can successfully negotiage a shared secret.
4. `keySe.cafe`: the proof of `keySe`.
5. `fwdSe.cafe`: the proof of `fwdSe`.
6. `unique.cafe`: the proof of `unique`.
8. `secrecy.cafe`, `inv0.cafe`,..., `inv15.cafe`: the proofs of the corresponding lemmas.
9. `learnSS.cafe`: shows that the intruder can learn a shared secret if the private host key of the server is compromised.
10. `auth-counterexample.cafe`: shows a counterexample of the predicate `auth` (specifying the authentication property). See comments in that file for more details.
11. `inputs`: the input commands to generate the proof scores. It is only helpful in case you want to re-generate the proof scores again.