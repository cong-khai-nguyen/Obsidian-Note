---
title: Chosen-plaintext attack (CPA)
date: 2024-09-15
---
### Definition:
The attacker can choose arbitrary plaintexts and obtain their corresponding ciphertexts. 

### How it works:
1. Attacker get to submit plaintexts of your choice to an encryption oracle (black box) and receive the ciphertexts in return.
2. Analyzes the resulting ciphertexts to deduce information about the key or cipher.

### Key Characteristics:
- More powerful than KPA.
- Provides more information to the attacker than KCA.
