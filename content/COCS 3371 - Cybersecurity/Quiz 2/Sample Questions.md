---
title: Sample Questions
date: 2024-10-09
---
# Elliptic Curve Cryptography Problems and Solutions
## 1. Elliptic Curve Point Mirroring
***Question**:* Let E be the elliptic curve y² = x³ + x + 3 defined over F₁₇, and let P be a base point = (2,8). The multiples of P are, in order (N = 17 including O):

1P = (2,8),  2P = (12,3),  3P = (16,16), 4P = (8,8),   5P = (7,9),
6P = (6,15), 7P = (11,6),  8P = (3,13),  9P = (3,4),   10P = (11,11),
11P = (6,2), 12P = (7,8),  13P = (8,9),  14P = (16,1), 15P = (12,14),
16P = (2,9)

For point (16,16), what is its mirroring point on the curve? Please choose one answer.

- [ ] (2,8)
- [ ] (2,9)
- [ ] (3,4)
- [ ] (3,13)
- [ ] (6,2)
- [ ] (6,15)
- [ ] (7,8)
- [ ] (7,9)
- [ ] (8,8)
- [ ] (8,9)
- [ ] (11,6)
- [ ] (11,11)
- [ ] (12,3)
- [ ] (12,14)
- [x] (16,1)

***Answer***
The correct answer is (16,1).

***Explanation:***
1. For any point (x,y) on an elliptic curve defined over a finite field Fₚ, its mirror point is (x,-y mod p).
2. The given point is (16,16), and the curve is defined over F₁₇.
3. To find the mirror point:
   - Keep the x-coordinate: 16
   - Negate the y-coordinate: -16
   - Take this modulo 17: -16 ≡ 1 (mod 17)
4. Therefore, the mirror point of (16,16) is (16,1).

This can be verified in the given list of point multiples, where we see that 14P = (16,1).

# Elliptic Curve Cryptography Problems and Solutions

## 1. Public Key Corresponding to Private Key 11

**Answer:** (8, 8)

**Solution:**
In Elliptic Curve Cryptography, the public key is calculated by multiplying the private key with the base point P. Given that the private key is 11, we need to perform scalar multiplication: 11P.

To do this, we can use the double-and-add method:
1. P = (2, 8) (assumed base point)
2. 2P = (8, 9)
3. 4P = (16, 1)
4. 8P = (8, 8)
5. 11P = 8P + 2P + P = (8, 8) + (8, 9) + (2, 8) = (8, 8)

Therefore, the public key corresponding to private key 11 is (8, 8).

## 2. Elliptic Diffie-Hellman Shared Secret

**Answer:** (8, 8)

**Solution:**
In Elliptic Diffie-Hellman:
- Alice computes A = KA * P = 3P
- Bob computes B = KB * P = 7P
- The shared secret is R = KA * B = KB * A

Let's calculate:
1. A = 3P = 3 * (2, 8) = (16, 16)
2. B = 7P = 7 * (2, 8) = (7, 9)
3. R = KA * B = 3 * (7, 9) = (8, 8)

Alternatively, R = KB * A = 7 * (16, 16) = (8, 8)

Therefore, the shared secret point R is (8, 8).

## 3. El Gamal Encryption - C2 Calculation

**Answer:** (3, 4)

**Solution:**
In El Gamal encryption:
- C1 = rP
- C2 = M + r(dP)

Given:
- M = (7, 9)
- r = 5
- d = 11 (Alice's private key)

We need to calculate:
1. P (base point) = (2, 8) (assumed)
2. dP (Alice's public key) = 11P = (8, 8) (from question 1)
3. C1 = rP = 5 * (2, 8) = (6, 2)
4. C2 = M + r(dP) = (7, 9) + 5 * (8, 8) = (7, 9) + (3, 4) = (3, 4)

Therefore, C2 after encryption is (3, 4).

## 4. El Gamal Decryption After Eve's Tampering

**Answer:** (3, 4)

**Solution:**
In El Gamal decryption:
M = C2 - d(C1)

Eve modifies C2 by adding (8, 8), so the new C2' = C2 + (8, 8) = (3, 4) + (8, 8) = (11, 6)

Decryption process:
M' = C2' - d(C1) = (11, 6) - 11(6, 2) = (11, 6) - (8, 8) = (3, 4)

Therefore, the decrypted message after Eve's tampering is (3, 4).

## 5. El Gamal Modification to Keep Message Unchanged

**Answer:** (12, 3)

**Solution:**
To keep the decrypted message unchanged, the following must hold:
C2 + (x, y) - d(C1 + (6, 2)) = C2 - d(C1)

This means:
(x, y) = d(6, 2) = 11(6, 2) = (12, 3)

Therefore, (12, 3) should be added to C2 to keep the decrypted message unchanged.

## 6. Two Pieces of Data for Message Recovery (CDH Problem)

**Answer:** (3, 4) and (6, 2)

**Solution:**
The two pieces of data needed to recover Bob's message without Alice's private key are:

1. C2 = (3, 4)
2. C1 = (6, 2)

If Eve can solve the Computational Diffie-Hellman (CDH) problem, she can compute r(dP) from P, rP (which is C1), and dP (Alice's public key). Then, Eve can recover the message M by subtracting r(dP) from C2:

M = C2 - r(dP)

This is why these two pieces of data are crucial for message recovery in this scenario.