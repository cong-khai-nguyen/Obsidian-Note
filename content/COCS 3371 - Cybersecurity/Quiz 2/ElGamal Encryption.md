---
title: ElGamal Encryption
date: 2024-10-09
---
# ElGamal Encryption

## Definition
ElGamal encryption is a public-key cryptosystem based on the Diffie-Hellman key exchange. Security depends on: Elliptic Curve Computational Diffie-Hellman (CDH), very difficult to compute: S = d (r alpha) given d alpha and r alpha


## How it works
![[Pasted image 20241010091900.png]]![[Pasted image 20241010092417.png]]![[Pasted image 20241010092651.png]]
1. **Key Generation**:
   - Choose a large prime `p` and a generator `g` of the multiplicative group Z*p
   - Select a random integer `d` (private key)
   - Compute `e = g^d mod p` (public key)
   - Public key is (p, g, e), private key is d

2. **Encryption**:
   To encrypt a message `m`:
   - Choose a random `r`
   - Compute `c1 = g^r mod p`
   - Compute shared secret `S = e^r mod p`
   - Compute `c2 = m * S mod p`
   - Ciphertext is (c1, c2)

3. **Decryption**:
   To decrypt ciphertext (c1, c2):
   - Compute shared secret `S = c1^d mod p`
   - Compute `m = c2 * S^(-1) mod p`

## Characteristics

1. **Security**: Based on the difficulty of the Discrete Logarithm Problem (DLP) and the Diffie-Hellman problem
2. **Probabilistic**: The same plaintext encrypts to different ciphertexts
3. **Malleable**: Multiplicatively homomorphic
4. **Key size**: Typically 2048 bits or larger for the prime p
5. **Performance**: Slower than symmetric encryption, used for key exchange or small messages
6. **Randomness**: Requires a good source of randomness for security

## Additional Details

- **Homomorphic Property**: Given E(m1) and E(m2), one can compute E(m1 * m2) without decrypting
- **Vulnerability**: Reusing the random value r compromises security
- **Variants**: Elliptic Curve ElGamal uses elliptic curve groups instead of multiplicative groups mod p

# Elliptic Curve ElGamal
## Definition
A variant of ElGamal encryption that operates on elliptic curve groups instead of multiplicative groups modulo a prime.

## How it works

1. **Key Generation**:
   - Choose an elliptic curve E and a base point G of order n
   - Select a random integer d < n (private key)
   - Compute e = d * G (public key)

2. **Encryption**:
   To encrypt a message point M:
   - Choose a random r < n
   - Compute C1 = r * G
   - Compute shared secret S = r * e
   - Compute C2 = M + S
   - Ciphertext is (C1, C2)

3. **Decryption**:
   To decrypt ciphertext (C1, C2):
   - Compute shared secret S = d * C1
   - Compute M = C2 - S

## Characteristics
1. **Security**: Based on the Elliptic Curve Discrete Logarithm Problem (ECDLP)
2. **Key size**: Smaller keys compared to traditional ElGamal (e.g., 256-bit keys offer comparable security to 3072-bit RSA)
3. **Performance**: Faster than traditional ElGamal for equivalent security levels
4. **Malleable**: Additively homomorphic over the curve
5. **Message encoding**: Requires encoding messages as points on the curve

## Additional Details
- **Point compression**: Public keys and ciphertexts can be compressed to save space
- **Curves**: Commonly used curves include secp256k1 (used in Bitcoin) and Curve25519
# Malleability in Cryptography

## Definition
Malleability in cryptography refers to the ability to transform a valid ciphertext into another valid ciphertext that decrypts to a related plaintext, without knowing the original plaintext or the decryption key.

## How it works

1. **In ElGamal**:
   Given ciphertext (c1, c2) = (g^r, m * e^r):
   - Multiply c2 by a constant k: (c1, k * c2)
   - This new ciphertext decrypts to k * m
   
2. **In EC ElGamal**:
   Given ciphertext (C1, C2) = (r * G, M + r * e):
   - Add a point P to C2: (C1, C2 + P)
   - This new ciphertext decrypts to M + P

## Characteristics
1. **Preventable**: Techniques like encrypt-then-MAC can prevent malleability

## Additional Details

- **Impact on digital signatures**: Malleable signatures can lead to transaction malleability attacks in cryptocurrencies
- **CCA security**: Malleability typically implies vulnerability to chosen-ciphertext attacks
- **Homomorphic encryption**: Intentionally malleable to allow computations on encrypted data

# ECDSA (Elliptic Curve Digital Signature Algorithm)

## Definition
ECDSA is a digital signature algorithm that uses elliptic curve cryptography.

## How it works

1. **Key Generation**:
   - Choose curve parameters: curve E, base point G of order n
   - Select private key d < n
   - Compute public key Q = d * G

2. **Signing**:
   To sign message m:
   - Compute e = HASH(m)
   - Choose random k < n
   - Compute R = k * G, let r be the x-coordinate of R
   - Compute s = k^(-1) * (e + d * r) mod n
   - Signature is (r, s)

3. **Verification**:
   To verify signature (r, s) for message m:
   - Compute e = HASH(m)
   - Compute u1 = e * s^(-1) mod n and u2 = r * s^(-1) mod n
   - Compute R' = u1 * G + u2 * Q
   - Signature is valid if x-coordinate of R' equals r

## Characteristics
1. **Security**: Based on ECDLP, offers same security as DSA with smaller keys
2. **Key size**: Typically 256 or 384 bits
3. **Performance**: Faster than RSA for equivalent security levels
4. **Randomness**: Requires good random k for each signature
5. **Malleability**: (r, -s mod n) is also a valid signature
## Additional Details

- **Low-s normalization**: To prevent malleability, require s < n/2
- **Recovery ID**: Additional information (v) can be added to allow public key recovery from signature
- **Batch verification**: Multiple signatures can be verified more efficiently in a batch
- **Deterministic ECDSA**: RFC 6979 describes a deterministic k generation method to improve security
6. Hashed Elliptic Curve ElGamal:
- Uses a hash function but is still malleable
7. Cramer-Shoup Encryption:
- Extension of ElGamal
- Proven secure against adaptive chosen ciphertext attacks under DDH assumption
- Adds elements to ensure non-malleability

8. Diffie-Hellman Assumptions:

- Computational Diffie-Hellman (CDH): Hard to compute g^xy given g^x and g^y
- Decisional Diffie-Hellman (DDH): Hard to distinguish g^xy from a random group element
- DDH is a stronger assumption than CDH

9. Digital Signatures:
- RSA signatures without hashing are vulnerable to malleability
- Hashing before signing helps prevent certain attacks

10. ECDSA Signatures:
- Verification only checks x-coordinate
- Vulnerable to signature malleability
- Can lead to unauthorized actions, tampering, and false attribution
- Addressed by requiring low-s values (s < n/2)

11. ECDSA Signature Malleability Demo:
- Showed how modifying s and v values can produce valid signatures for different or same signers

12. Public Key Recovery:
- v (recovery parameter) is needed to recover the correct public key from a signature
- Multiple candidate public keys can be recovered from a signature
- Signers can ensure only one viable public key is recoverable

13. Public Key recovery_id:
- Explains how different v values (27-34) correspond to different public key representations and coordinate properties