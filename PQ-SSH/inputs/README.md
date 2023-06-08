## How to re-generate the proof scores

First, we need to install the IPSG tool. The tool can be found at this repo: https://github.com/duongtd23/IPSG-tool. From that webpage, you can find the installation guide. Basically, the tool can be easily installed by just cloning the repo if you have already installed Maude. You should first test with the example commands shown on its README.

Once you have successfully installed IPSG, you can execute it to re-generate the proof scores of the PQ SSH case study.
For example, to generate the proof score of `inv0`, we use the following commands:

```
maude -allow-files path-to-IPSG-tool/ipsg.maude
load PQ-SSH/pqssh.cafe .
load PQ-SSH/invariants.cafe .
load PQ-SSH/inputs/input0.cafe .
```

where the first command starts the tool (`path-to-IPSG-tool` is the path of the IPSG-tool folder you have just cloned).
The second and third load commands load the CafeOBJ specification and invariants, respectively.
The last command loads the input file `input0.cafe`, which asks the tool to generate the proof score of `inv0`.
Note that, for the second command, CafeInMaude may take a few seconds to load the specification (due to the large file).
Recall that IPSG is implemented on top of CafeInMaude.
After that, you do not need to load the specification or the invariants again, but you can continuously ask the tool to generate proof scores for the other invariants.
For example, you can continuously ask the tool to generate the proof score of `inv1` by the command:

```
load PQ-SSH/inputs/invput1.cafe .
```