---
title: Elliptic Curve Cryptography (ECC)
date: 2024-10-07
---
### Definition:
Elliptic Curve Cryptography (ECC) is an approach to public-key cryptography based on elliptic curve theory that can be used as **faster**, **smaller**, and **more efficient** cryptosystems.  It is designed to create faster, smaller, and more efficient cryptosystems with equivalent security strength compared to other public-key systems like RSA but using significantly smaller key sizes.

### How it works:
![[Pasted image 20241007201335.png]]
![[Pasted image 20241007201626.png]]![[Pasted image 20241007203218.png]]![[Pasted image 20241007204547.png]]![[Pasted image 20241008193452.png]]![[Pasted image 20241008122627.png]]![[Pasted image 20241008122645.png]]![[Pasted image 20241008122711.png]]![[Pasted image 20241008122736.png]]
![[Pasted image 20241008122914.png]]

#### 1. Mathematical Foundations

An **elliptic curve** is represented by an equation of the form:

<center>
y<sup>2</sup> = x<sup>3</sup> + ax + b
4a<sup>3 </sup> + 27b<sup>2</sup> != 0
</center>
<center>
4a<sup>3 </sup> + 27b<sup>2</sup> != 0
</center>

where \(a\) and \(b\) are constants. For ECC to work, the values of \(a\) and \(b\) must satisfy a condition that ensures the curve doesn’t have any singularities (i.e., it has no cusps or self-intersections).

**Elliptic curves over finite fields** (usually denoted as \(E(F_p)\), where \(p\) is a prime number) have points that are constrained to a finite set of values. The curve points are pairs \((x, y)\) such that the equation holds under a modulo operation, effectively limiting the domain to numbers between 0 and \(p - 1\).

#### 2. Key Generation

- **Private Key ( k<sub>priv</sub>)**: This is a randomly chosen integer, typically in the range between 1 and \(n-1\), where \(n\) is the order of the base point on the elliptic curve. This key is kept secret.
- **Public Key (K<sub>public</sub>)**: The public key is derived by multiplying the **base point** \(G\) (a predefined point on the curve that everyone knows) by the private key:

<center>  [  K<sub>public</sub> = k<sub>priv</sub> · G  ] </center>

  Here, the "multiplication" operation is actually **repeated point addition**. Adding a point \(G\) to itself repeatedly creates a new point on the elliptic curve. This operation is computationally efficient to perform but extremely difficult to reverse (i.e., deducing \(k<sub>priv</sub>\) from \(K<sub>public</sub>)).

#### 3. Point Addition and Multiplication

- **Point Addition (P + Q)**: Given two points \(P\) and \(Q\) on the elliptic curve, the result of adding them is another point on the curve.
- **Point Doubling (2P)**: This is a special case of point addition where a point \(P\) is added to itself.

The resulting new point is determined by drawing a line through \(P\) and \(Q\) (or a tangent line if (P = Q) and finding where the line intersects the elliptic curve. The x-coordinate of the third intersection is reflected about the x-axis to get the final result. This makes it hard for an attacker to derive the original points simply from their sum.
#### 4. Encryption Process

- **Input Elements**:
  - **Base Point (G\): A known point on the curve.
  - **Receiver’s Public Key (K<sub>public</sub>)**: Publicly available.
  - **Message (m)**: The message needs to be encrypted and is represented as a point on the curve.

- **Steps**:
  - The sender selects a random number \(r\) (called an ephemeral key).
  - Calculate two points:
    - **Ciphertext point 1 (C<sub>1</sub>)**: Multiply the base point by \(r\):
	<center>
      C<sub>1</sub> = r  · G
    </center>
    - **Ciphertext point 2 (\(C_2\))**: Calculate \(C_2\) as:

	<center>
      C<sub>2</sub> = m + r · K<sub>public</sub>
    </center>

  - Here, \(m\) is the point representing the message, and (r · K<sub>public</sub>) is the shared secret derived by multiplying the receiver’s public key by the random value \(r\).
  - The ciphertext is the combination of the points (C<sub>1</sub>, C<sub>2</sub>).
#### 5. Decryption Process

- The receiver, who has the **private key (k<sub>priv</sub>)**, receives the ciphertext (C<sub>1</sub>,C<sub>2</sub>).
- **Shared Secret Calculation**: Calculate the shared secret *S* by multiplying the received C<sub>1</sub>​ with the private key:

<center>
S=k<sub>priv</sub>⋅C1​=k<sub>priv</sub>⋅(r⋅G)
</center>

  Using properties of elliptic curves, this is equal to \(r \cdot K_{public}\), which is the same shared secret used in the encryption process.

- **Decrypt the Message**:
<center>
  m = C<sub>2</sub> - S
</center>

  The receiver subtracts the shared secret from \(C<sub>2</sub>\) to get back the original message point \(m\).
#### 6. Security Basis

The security of ECC relies on the **Elliptic Curve Discrete Logarithm Problem (ECDLP)**, which states that, given points \(P\) and \(Q = k \cdot P\), it is computationally infeasible to determine the value of \(k\) if \(P\) and \(Q\) are points on an elliptic curve.

---

### Example: Encryption and Decryption Using ECC

**Scenario**: Alice wants to send an encrypted message to Bob using ECC.

**1. Key Generation**:
- **Elliptic Curve**: Let’s use a simple elliptic curve: \(E: y<sup>2</sup> = x<sup>3</sup> + 2x + 3).
- **Base Point (G)**: Let’s choose G = (2, 7) (a predefined point on the curve).
- **Bob’s Private Key (k<sub>priv</sub>)**: Bob randomly chooses (k<sub>priv</sub> = 7\).
- **Bob’s Public Key (K<sub>public</sub>):

<center>
  K<sub>public</sub>=k<sub>priv</sub>⋅G=7⋅(2,7)=(7,2) (after 7 point additions)
</center>

**2. Encryption (by Alice)**:
- **Message Point (m)**: The message is represented as the point m = (10, 9) on the curve.
- **Random Ephemeral Key (r): Alice chooses a random value r = 3.
- **Calculate Ciphertext**:
  - C1​=r ⋅ G =3⋅(2,7)=(8,3)
  - C2​=m+r⋅K<sub>public</sub>=(10,9)+3⋅(7,2)=(10,9)+(3,5)=(10,2)

- **Ciphertext**: Alice sends Bob (C_1, C_2) = ((8, 3), (10, 2)).

**3. Decryption (by Bob)**:
- **Bob Receives**: (C1, C2) = ((8, 3), (10, 2)).
- **Calculate Shared Secret (S**):

<center>
	S=k<sub>priv</sub>⋅C1​=7⋅(8,3)=(3,5)
</center>

- **Decrypt the Message**:
<center>
m = C<sub>2</sub>​−S=(10, 2) − (3, 5)=(10, 9)
</center>

- **Result**: Bob successfully recovers the original message point \((10, 9)\).

---
### Key Characteristics:
* Advantages of ECC:
	- Provides similar security to traditional systems (like RSA) with much smaller key sizes. For example, a 256-bit ECC key provides roughly the same security as a 3072-bit RSA key.
	- Fast key generation
	- Efficient encryption and decryption
	- Suitable for constrained environments (e.g., mobile devices, smart cards)
	- Used for encryption, digital signatures, and key agreement protocols
- Disadvantages of ECC:
	- Complex Implementation
	- Susceptibility to Quantum Attacks

