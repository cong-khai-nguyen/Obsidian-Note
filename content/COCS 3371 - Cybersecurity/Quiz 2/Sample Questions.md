---
title: Sample Questions
date: 2024-10-09
---
1.  # Elliptic Curve Point Mirroring

## Question

Let E be the elliptic curve y² = x³ + x + 3 defined over F₁₇, and let P be a base point = (2,8). The multiples of P are, in order (N = 17 including O):

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

## Answer

The correct answer is (16,1).
### Explanation:

1. For any point (x,y) on an elliptic curve defined over a finite field Fₚ, its mirror point is (x,-y mod p).
2. The given point is (16,16), and the curve is defined over F₁₇.
3. To find the mirror point:
   - Keep the x-coordinate: 16
   - Negate the y-coordinate: -16
   - Take this modulo 17: -16 ≡ 1 (mod 17)
4. Therefore, the mirror point of (16,16) is (16,1).

This can be verified in the given list of point multiples, where we see that 14P = (16,1).