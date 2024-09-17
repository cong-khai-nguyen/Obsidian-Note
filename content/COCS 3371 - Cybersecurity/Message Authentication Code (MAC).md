---
title: Message Authentication Code (MAC)
date: 2024-09-16
---
### Definition:
A Message Authentication Code (MAC) is a short piece of information used to authenticate a message and ensure its integrity. It's a cryptographic checksum that combines a message and a secret key. 

A MAC is an algorithm which accepts a message M, a key K, and possibly some state (like a nonce N), and outputs a short string called a “tag”.

### How it works:
1. The **sender** creates a MAC by applying a MAC algorithm to the message and a secret key.
2. The MAC is then appended to the message.
3. The **receiver** uses the same secret key and MAC algorithm on the received message.
4. The receiver compares the computed MAC with the received MAC.
5. If they match, the message is authenticated and its integrity is verified.

### Key Characteristics:
- Provides data integrity and authentication
- Uses a secret key shared between sender and receiver
- Typically produces a fixed-size output regardless of input size
- Often used in combination with encryption for secure communication
- ![[Pasted image 20240916192059.png]]

### Example:
1. Alice computes tag = MACK(M, N) and sends Bob the message (M, N, tag)
2. Bob receives (M’, N’, tag’) and checks if MAC<sub>K</sub>(M’, N’) == tag’
	If YES, he accepts M’ as authentic
	If NO, he rejects M’ as an attempted forgery
### Vulnerabilities/Main weaknesses:
- Shared key requirement:
    - Both parties must securely share and protect the secret key.
    - Key management can be challenging, especially in large systems.