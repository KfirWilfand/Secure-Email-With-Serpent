# Secure Email With Serpent
An Application for secure email exchange: including secure canal generating DH on elliptic curve for delivery of the secret key, encryption-decryption with Serpent

**Authors**:
Tal Tolochinsky, Kfir Willfand,  Dvir Kovalio, Zehavit Otmazgin 

## **Serpent algorithm**

**Introduction**  

The Serpent is a 128-bits block cipher and symmetric key size of 128, 192 or 256 bits. The cipher uses DES (s-box) replacement boxes in a new structure that allows for a fast snowball effect, can be effectively applied in bitslice technique easy and simple to analyze, It objective was to create an algorithm that would guarantee a life cycle of a 100 years.

The algorithm is best suited to implementation in hardware and it slow when implemented in software.

**history**

The Serpent was developed in 1998 by Ross Anderson, Eli Boehm and Lars Knudsen, as a candidate for the Advanced Encryption Standard(AES). It is a code with the highest conservative design and confidence margin of all the other candidates offered during the competition. The Serpent was one of the NIST 5 final selections, USA standardization institute, for communication protection of the US federal agencies, coming second after the AES algorithm.

  

**bitslice technique**

The basic idea behind the bitslice technique is to simulate the processor that implements the cipher as a SIMD. In other words, simulate the implementation of the algorithm by basic logic bits at the bit level, while simultaneously processing 32 or 64 bit integer blocks. In contrary to the conventional method, while processing a small amount of the processor bit CPU is not utilized. This technique was used to attack DES using a parallel brute force method, taking advantage of the free time of thousands of processors.

**The Algorithm**

The Serpent algorithm is a 32-round Substitution Permutation (SP) network operating on four 32-bit words. The algorithm encrypts and decrypts 128-bit input data via a key of 128, 192, or 256 bits in length. The Serpent algorithm consists of three main components and it designed so all operations can be run in parallel .

**Step one - Initial Permutation IP**

The initial permutation does not have any cryptographic significance. it is used to simplify an optimized implementation of the cipher and to improve its computational efficiency.

The initial and final permutations are simply bit mappings. In permutations, each bit on the input is assigned to a different index on the output. There are no operations performed, only reassignments.

**Step two - 32 rounds**

Each round function Ri uses only a single replicated S-box. For example, R0 uses S0, 32 copies of which are applied in parallel. Thus the first copy of S0 takes bits 0,1,2 and 3 of Bˆ0 ⊕ Kˆ0 as its input and returns as output the first four bits of an intermediate vector; the next copy of S0 inputs bits 4–7 of Bˆ0⊕Kˆ 0 and returns the next four bits of the intermediate vector, and so on. The intermediate vector is then transformed using the linear transformation, giving Bˆ1.

**Step three - Final Permutation FP**

In the last round R31, we apply S31 on Bˆ31 ⊕ Kˆ31, and XOR the result with Kˆ32 rather than applying the linear transformation. The result Bˆ32 is then permuted by FP, giving the ciphertext.

  

  

**S-boxes**

S-box is simply a look-up-table. In Serpent, the S-boxes are 4-bit permutations. The advantage of an S-box is that for a 1-bit change of an input value, the output is guaranteed to be altered by more than one bit (at least for the Serpent S-boxes).

  

  

**Linear Transformation**

The linear transformation functions acts on the 128-bit block as four 32-bit words. Each word is linearly adjusted and combined with other words according to the image :

**Linear Transformation - flow chart**

**Key Schedule**

If the keys is less than 256 bits , we padded by appending one “1” bit to the MSB end, followed by as many “0” bits as required to make up 256 bits.

The schedule first creates a set of 32-bit prekeys wi . The starting 8 prekeys numbered from –1 to –8 are simply filled with bits of the external key and then another 132 prekeys w are generated by the following affine recurrence:

**Serpent Encryption flow chart
Serpent Decryption flow chart**

Decryption is different from encryption in that the inverse of the S-boxes must be used, as well as the inverse linear transformation and reverse order of the subkeys.

**Various Serpent attacks**

In 2000, Kohno et al. presents a meet-in-the-middle attack against 6 of 32 rounds of Serpent and an amplified boomerang attack against 9 of 32 rounds in Serpent.

In 2001 attack by Eli Biham, Orr Dunkelman and Nathan Keller presents a linear cryptanalysis attack that breaks 10 of 32 rounds of Serpent-128 .

In 2011 attack by Hongjun Wu, Huaxiong Wang and Phuong Ha Nguyen, also using linear cryptanalysis, breaks 11 rounds of Serpent-128.

**advantage and disadvantage
Summary**

The Serpent is a symmetric-key algorithm based on 32 round substitution–permutation network operating on a block of four 32bit words.

Designed so all operations can be run in parallel.

A Finalist in the Advanced Encryption Standard(AES) contest.

The algorithm is in a public domain software and the optimized code is under GPL.


