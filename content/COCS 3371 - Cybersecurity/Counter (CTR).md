### Definition:
CTR is a block cipher encryption mode that turns a block cipher into a stream cipher. It generates a keystream by encrypting successive values of a counter and XORing this keystream with the plaintext to produce the ciphertext.
### How it works:
1. **Initialization**: A counter is initialized with a nonce - N (an arbitrary number used only once). The nonce can be a random value or an [[Initialization Vector (IV)]].
2. **Counter Generation**: The counter is encrypted using the block cipher(algorithm like AES) and the encryption key.
3. **XOR with Plaintext**: The resulting encrypted block is XORed with a block of plaintext to produce a block of ciphertext.
4. **Counter Increment**: The counter is incremented for the next block.
5. Steps 2-4 are repeated for each block of plaintext.
### Key Characteristics:
- Converts a block cipher into a stream cipher
- **Parallelizable**: Parallelizable for both encryption and decryption
- **Random access:** ability to decrypt any block without processing previous blocks
- **Nonce Importance**: The nonce must be unique for each encryption session. Reusing a nonce leads to vulnerabilities.
- ![[Pasted image 20240915135853.png]]

### Vulnerabilities/Main weaknesses:
1. Nonce Reuse:
	- Reusing the same nonce and key combination for different messages can lead to severe vulnerabilities. An attacker can perform a **known plaintext attack** because if two ciphertexts are generated with the same key and nonce, they can be XORed to reveal information about the plaintexts.
	- Ex: Repeated Keystream in WEP

### Additional Resources:
- https://www.youtube.com/watch?v=zX0PZtqerCI