# chromite-bug-bounty



**Why do immediates have such weird encodings ?**

The main reason the immediate fields have weird encoding schemes is that different instructions have different sized immediate fields.The RISC-V ISA keeps the source (rs1 and rs2) and destination (rd) registers at the same position in all formats to simplify decoding.

The chosen encodings line up very nicely with other encodings, simplifying the hardware at the expense of software that has to generate instructions, software that has to decode instructions, and, programmers learning or working with RISC V.

For example:

The S-Format breaks up the immediate into imm[11:5] and imm[4:0].  The reason this immediate is broken up is to keep the other fields, namely the register fields, rs2 and rs1, in the same position as with the two source register fields in R-Type instructions. 

The only difference between the S and B formats is that the 12-bit immediate field is used to encode branch offsets in multiples of 2 in the B format. Instead of shifting all bits in the instruction-encoded immediate left by one in hardware as is conventionally done, the middle bits (imm[10:1]) and sign bit stay in fixed positions, while the lowest bit in S format (inst[7]) encodes a high-order bit in B format.

Similarly, the only difference between the U and J formats is that the 20-bit immediate is shifted left by 12 bits to form U immediates and by 1 bit to form J immediates. The location of instruction bits in the U and J format immediates is chosen to maximize overlap with the other formats and with each other.



**List all ratified extensions of the unprivileged spec**

1. RVWMO - Version 2.0
2. RV32I - Version 2.1
3. RV64I - Version 2.1
4. Zifencei - Version 2.0
5. Zicsr - Version 2.0
6. M - Version 2.0
7. F - Version 2.2
8. D - Version 2.2
9. Q - Version 2.2
10. C - Version 2.0


**List at-least 4 unratified extensions of the unprivileged spec**

1. RV32E - Version 1.9 (Draft)
2. RV128I -  Version 1.7 (Draft)
3. Ztso -  Version 0.1 (Frozen)
4. A - Version 2.0 (Frozen)





