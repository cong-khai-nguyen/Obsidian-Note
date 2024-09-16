### Definition:
CBC is a block cipher encryption mode that uses a chaining mechanism to add randomness to the encryption process.
### How it works:
1. The plaintext is divided into fixed-size blocks.
2. An n-bit "nonce" called initialization vector (IV) is generated for the first block.
3. Each plaintext block is XORed with the previous ciphertext block (or the IV for the first block).
4. The result is then encrypted using the block cipher algorithm and the encryption key.
5. The resulting ciphertext block is used in the XOR operation for the next plaintext block.
### Key Characteristics:
- Slow - No parallelism. Encryption is sequential. Each ciphertext block depends on all preceding plaintext blocks.
- Uses an initialization vector (IV) to randomize the encryption of the first block.
- IV and key must be known to both senders and receivers. 
- ![[Pasted image 20240912184934.png]]

### Vulnerabilities/Main weaknesses:
1. IV reuse/ predictable IV
	- If attacker can predict IV, CBC is not CPA-secure
2. Padding oracle attacks:
	- CBC mode often requires padding to ensure the plaintext fits into complete blocks.
	- If an implementation leaks information about whether decryption padding is correct or not (the "padding oracle"), an attacker can potentially decrypt the ciphertext without knowing the key.
	- This attack works by manipulating ciphertext blocks and observing the system's response to deduce information about the plaintext.

### Additional Resources:
- https://www.youtube.com/watch?v=nnQONZ_DRyk