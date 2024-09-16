### Definition:
ECB is the simplest mode of operation for block ciphers, where each block of plaintext is encrypted independently using the same key.
### How it works:
1. The plaintext is divided into fixed-size blocks.
2. Each block is encrypted separately using the same encryption key.
3. The encrypted blocks are concatenated to form the final ciphertext.
### Key Characteristics:
- Simple and easy to implement
- **Parallelizable** for both encryption and decryption
- **Deterministic**: identical <u>plaintext blocks</u> always encrypt to identical <u>ciphertext blocks</u>
- No chaining or feedback mechanism between blocks
- Does not require an [[Initialization Vector (IV)]].
- ![[Pasted image 20240915224234.png]]

### Vulnerabilities/Main weaknesses:
1. Pattern preservation:
	- Repetitions in the plaintext show through to the ciphertext
	- This can reveal patterns and structure in the original data, potentially allowing attackers to infer information about the plaintext without decrypting it.
	- Particularly problematic for data with repeating patterns or structures, like images or formatted text.
		- ![[Pasted image 20240912180229.png]]