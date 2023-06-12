In this folder, you can find:

- `properties.cafe`: specifies some additional predicates.
- `check.cafe`: shows that two principals can successfully negotiage a shared secret.
- `learnEC.cafe`: shows that the intruder can learn an ECDH shared secret.
- `keySe-f1.cafe`: shows that `keySe` is no longer valid if the constraint "(1) the signature of the exchange hash in the KEX_HBR_REPLY message is valid" is eliminated.
- `keySe-f2.cafe`: shows that `keySe` is no longer valid if the constraint "(2) the KEM shared secret is not revealed" is eliminated.
- `keySe-f3.cafe`: shows that `keySe` is no longer valid if the constraint "(3) the two corresponding KEM ephemeral secret keys are not revealed" is eliminated.
- `keySe-f4.cafe`: shows that `keySe` is no longer valid if the constraint "(4) the private host key of the server is not revealed" is eliminated.
