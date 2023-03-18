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

3. `keySe.cafe`: the proof of `keySe`.
4. `fwdSe.cafe`: the proof of `fwdSe`.
5. `unique.cafe`: the proof of `unique`.
6. `auth-ctx.cafe`: shows a counterexample of the predicate `auth` (specifying the strong-authentication property).
7. `check.cafe`: shows that two principals can successfully negotiage a shared secret.
8. `learnSS.cafe`: shows that the intruder can learn a shared secret if the private host key of the server is compromised.
9. `secrecy.cafe`, `inv1.cafe`,...,`inv15.cafe`: the proof scores of the corresponding lemmas.
10. `auth.cafe`: the proof of `auth'` (specifying the *weak-authentication* property)., which uses "the proof method for invariant properties with existential quantifier variables". Human users are required to resolve some sub-cases in the generated proof, which are saved in file `auth-m.cafe`.
11. `inv16.cafe`: the proof of `inv16`, which uses "the proof method for invariant properties with existential quantifier variables". Human users are required to resolve some sub-cases in the generated proof, which are saved in file `inv16-m.cafe`.