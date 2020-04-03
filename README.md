# RSA
Problem Definition
The goal is to implement the RSA public-key cryptosystem. The RSA (Rivest-Shamir-Adleman) cryptosystem is widely used for secure communication in browsers, bank ATM machines, credit card machines, mobile phones, smart cards, and the Windows operating system. It works by manipulating integers. To prevent listeners, the RSA cryptosystem must manipulate huge integers (hundreds of digits). The built-in C type int is only capable of dealing with 16 or 32 bit integers, providing little or no security. You will:
1.	Design, implement, and analyze an extended precision arithmetic data type (big integer) that is capable of manipulating much larger integers. 
2.	Use this data type to write a client program that encrypts and decrypts messages using RSA.
Cryptosystem mean encoding and decoding confidential messages.
RSA is a public key cryptosystem algorithm. Public key cryptosystem requires two separate keys, one of which is secret (or private) and one of which is public. Although different, the two parts of this key pair are mathematically linked. The public key is used to encrypt plaintext; whereas the private key is used to decrypt cipher text. Only the one having the private key can decrypt the cipher text and get the original message.
How RSA Works?
Alice wants to send message M to Bob using RSA. How will this happen?
RSA involves three integer parameters d, e, and n that satisfy certain mathematical properties. The private key (d, n) is known only by Bob, while the public key (e, n) is published on the Internet. If Alice wants to send Bob a message (e.g., her credit card number) she encodes her integer M that is between 0 and n-1. Then she computes:

E(M) = Me mod n
and sends the integer E(M) to Bob. When Bob receives the encrypted communication E(M), he decrypts it by computing:
M = E(M)d mod n.

Goal:
Your goal is to
implement the BigInteger data type and use it in
RSA public-key cryptosystem so you can be able to encrypt and decrypt large
integer M.

The RSA cryptosystem is easily broken if the private key d or
the modulus n are too small (e.g., 32 bit integers). The built-in C
types int and long can typically handle only 16, 32 or 64 bit
integers. Your main challenge is to design, implement, and analyze a BIG
INTEGER that can manipulate large (nonnegative) integers. Your data type will
support the following operations: addition, subtraction, multiplication,
division, and mod of power.

1-
The first and most critical step
is to choose an appropriate data structure to represent N-digit big integers. A
natural approach is to store each digit as an element in an array.

2-     
You need to implement this BigInteger class along with its basic functions: addition, subtraction,
multiplication, division, and mod of power. Remember that you’re not working
with int or long

Efficient Multiplication. Implement
the efficient integer multiplication (less than N2) using the Karatsuba algorithm. It should
take two big integers as input and return a third big integer that is the
product of the two. Observe that if a and b are N-digit
integers, the product will have at most 2N digits.

Division. Integer
division is the most complicated of the arithmetic functions. Here is one of
the simplest algorithms to compute the quotient q
= a / b and the remainder r
= a mod b, where a and b are big
integers, with b not equal to 0. 

div(a,b) 
{
    if (a < b)
        return (0, a)
    (q, r) = div(a, 2b)
    q = 2q
    if (r < b)
        return (q, r)
    else
        return (q + 1, r - b)
}

Mod of Power. It is used to calculate: 

Direct
calculation of R = B^P mod m

take O(P) for integer values. However, we can
make use of the following theory to reduce its complexity.

(A × B × C) mod N = [(A mod N) × (B mod N) × (c mod N)] mod N

Since
we want B to the power P and take modulus M, so it is
going to be:

((B mod M) × (B mod M) × (B mod M) × ...(P times)) mod M

3-
After that you’ll design
and implement an efficient
algorithm for the RSA encryption and decryption functions as explained before.
