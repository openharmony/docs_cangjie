# Introduction to Message Digest Calculation and Algorithm Specifications

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

A message digest algorithm is a type of algorithm that can generate a fixed-length digest from an input message of arbitrary length through specific computations. Message digest algorithms are also known as hash algorithms or one-way hash algorithms.

When using the same digest algorithm, the generated digest values exhibit the following key characteristics:

- When the input messages are identical, the generated digest sequences will be the same.
- When the input messages vary in length, the generated digest sequences will have a fixed length (determined by the algorithm). For example, SHA256 generates a 256-bit (32-byte) digest.

## Supported Algorithms and Specifications

When creating an MD (Message Digest), the "Supported Types" column in the table below should be used to specify the MD message digest algorithm specifications.

| Digest Algorithm | Supported Types | Byte Length | API Version |
| ---------------- | --------------- | ----------- | ----------- |
| HASH | SHA1 | 20 | 12+ |
| HASH | SHA224 | 28 | 12+ |
| HASH | SHA256 | 32 | 12+ |
| HASH | SHA384 | 48 | 12+ |
| HASH | SHA512 | 64 | 12+ |
| HASH | MD5 | 16 | 12+ |
| HASH | SM3 | 32 | 12+ |