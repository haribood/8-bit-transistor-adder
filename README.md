# 8-Bit Transistor Adder

An 8-bit binary adder built entirely from discrete transistors. Eight cascaded full-adder stages combine two 8-bit inputs and propagate the carry from the least significant bit to the most significant bit.

## Project overview

This hardware project explores how transistor-level logic implements binary arithmetic. The build connects individual full-adder stages into an 8-bit ripple-carry architecture, with sum and carry outputs tested on the assembled circuit.

## Architecture

- **Implementation:** discrete transistors.
- **Adder stages:** eight cascaded full adders.
- **Data inputs:** two 8-bit binary values, A and B.
- **Outputs:** eight sum bits and a final carry-out.
- **Carry path:** each stage's carry-out feeds the next stage's carry-in.

```text
A[0], B[0] -> Full adder 0 -> S[0]
                  | carry
A[1], B[1] -> Full adder 1 -> S[1]
                  | carry
                 ...
                  | carry
A[7], B[7] -> Full adder 7 -> S[7], final carry-out
```

## How it works

For each bit position i, a full adder combines A_i, B_i, and the incoming carry C_i:

- Sum: S_i = A_i XOR B_i XOR C_i
- Carry: C_(i+1) = (A_i AND B_i) OR (C_i AND (A_i XOR B_i))

The carry ripples through all eight stages. With the initial carry set to zero, the eight sum bits represent (A + B) modulo 256; the final carry indicates a result above 255.

### Full-adder truth table

| A | B | Carry-in | Sum | Carry-out |
|---|---|----------|-----|-----------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

## Verification

The project's sum and carry outputs were tested. The examples below show expected arithmetic behavior and can serve as reference cases; they are not a recorded measurement log.

| A (binary) | B (binary) | Expected sum | Carry-out | Decimal calculation |
|------------|------------|--------------|-----------|---------------------|
| 00000000 | 00000000 | 00000000 | 0 | 0 + 0 = 0 |
| 00000001 | 00000001 | 00000010 | 0 | 1 + 1 = 2 |
| 00001111 | 00000001 | 00010000 | 0 | 15 + 1 = 16 |
| 01111111 | 00000001 | 10000000 | 0 | 127 + 1 = 128 |
| 11111111 | 00000001 | 00000000 | 1 | 255 + 1 = 256 |

## Repository contents

This repository currently documents the hardware project. Schematics, a bill of materials, build photos, and detailed measurement records have not yet been included.

## Author

[Haridev Nambood](https://github.com/haribood) — electrical engineering student at the University of Houston, interested in embedded systems, robotics, and controls.

[Portfolio](https://haribood.github.io/) · [Other projects](https://github.com/haribood?tab=repositories)
