## Formal analysis of Post-quantum Hybrid Key Exchange SSH Transport Layer Protocol

In this repository, you can find:

1. `SDS`: the formal verification of the SDS protocol, including the protocol formal specification in CafeOBJ, the proof scores to verify the *key secrecy* property and the *authentication* property. Please check README in the folder.

2. `PQ-SSH`: the formal analysis of the original Post-quantum Hybrid Key Exchange SSH Transport Layer Protocol (PQ SSH), including the protocol specification, the proofs verifying the protocol enjoy three properties, and the counterexample of the authentication property. Please check README in the folder.

3. `improved-PQ-SSH`: the formal verification of the improved protocol, which is proposed in order to make the protocol enjoy the authentication property. Please check README in the folder.


## Tools installation
Our verification requires the use of CafeInMaude, which can be downloaded from here: https://github.com/ariesco/CafeInMaude.
To install CafeInMaude, we first need to intall Maude, which we can download its version 3.2 from here: http://maude.cs.illinois.edu/w/index.php/Maude_download_and_installation.
Both installations are simple, with Maude, you just need to download the binary file (and perhaps add the tool to the PATH environment variable to execute the tool from everywhere), while with CafeInMaude, you just need to clone its repo.
After that, move to the next step to execute proof scores.

## Executing proof scores
Proof scores are executable (CafeOBJ code).
Once intalled CafeInMaude, you can try to run the proof score of `inv1` of the SDS case study (a lemma to verify the *key secrecy* property) by the following commands:

```
maude -allow-files path-to-CafeInMaude/src/cafeInMaude.maude
load SDS/sds.cafe .
load SDS/test.cafe .
```

where the first command starts the CafeInMaude environment (`path-to-CafeInMaude` is the path of the CafeInMaude folder),
the second command load the specification and the invariants, respectively,
and the last command loads the proof.
If nothing is wrong, you will get the output result containing `Result: true : Bool`. 
Note that you need to make sure that the paths are correct. You may need to use the absolute paths instead of the relative paths as above.

After that, you do not need to load the specification again, but can continue loading the complete proof scores to verify the *key secrecy* property:

```
load SDS/proof-scores.cafe .
```

In this case, because the file is large, 
CafeInMaude may take a little bit more time to return the result.

*Note also that* we can use CafeOBJ (https://cafeobj.org/) to execute the proof score (instead of CafeInMaude). But it may take a longer time since the rewriting system of the original CafeOBJ normally takes a longer amount of time to reduce a given term than that of CafeInMaude.

### Re-generating proof scores
To re-generate the proof scores again, see `README` in folder `PQ-SSH/inputs`.