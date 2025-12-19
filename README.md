# Assessment Winter 25/26 (Year 4️⃣)
**Author:** Tomás Pettit

**Student ID:** G00419414

**Course:** Software Development

**Module:** Computational Theory 💻

## Overview
This repository contains a complete Python implementation of the SHA-256 cryptographic hash function as specified in FIPS 180-4 (Secure Hash Standard). The assessment is divided into 5 problems covering logical functions, mathematical constant generation, message padding, hash computation, and password security analysis.

## Repository Structure
- `README.md` - Project overview and usage instructions
- `requirements.txt` - Python dependencies
- `.gitignore` - Git ignore rules
- `problems.ipynb` - Jupyter Notebook containing all implementations and documentation

## Requirements
- Python 3.9+ (for modern type hints like `list[int]`)

### Dependencies
Install required packages using:  
```bash
pip install -r requirements.txt
```

Main dependencies: `numpy` for 32-bit unsigned integer operations and mathematical functions.

## How To Run

### Using Jupyter Notebook
1. Clone this repository
2. Install dependencies: `pip install -r requirements.txt`
3. Launch Jupyter: `jupyter notebook`
4. Open `problems.ipynb`
5. Run cells sequentially from top to bottom

**Note:** Cells must be run in order as later problems depend on functions from earlier problems.

## Problems Implemented

### Problem 1: Binary Words & Operations
Implementation of seven logical functions used in SHA-256 compression:
- Parity, Choose (Ch), Majority (Maj)
- Big Sigma 0 & 1 (Σ₀, Σ₁)
- Small Sigma 0 & 1 (σ₀, σ₁)
- Helper functions: ROTR (right rotation), SHR (right shift)

All functions operate on 32-bit unsigned integers using bitwise operations.

### Problem 2: Fractional Parts of Cube Roots
Generation of the 64 K constants used in SHA-256:
- Implements prime number generation
- Calculates cube roots of first 64 primes
- Extracts first 32 bits of fractional parts
- Displays results in hexadecimal
- Verifies against FIPS 180-4 constants

### Problem 3: Padding
Message padding implementation using a Python generator function:
- Accepts messages of arbitrary length
- Applies SHA-256 padding scheme (append 1 bit, pad with zeros, append length)
- Yields 512-bit (64-byte) blocks
- Follows FIPS 180-4 Sections 5.1.1 and 5.2.1

### Problem 4: Hashes
Complete SHA-256 hash computation:
- Initial hash values (H⁽⁰⁾) from square roots of first 8 primes
- Message schedule expansion (512-bit blocks → 64 32-bit words)
- Compression function (64 rounds using Problem 1 functions and Problem 2 K constants)
- Main `hash(current, block)` function as specified in FIPS 180-4 Section 6.2.2

### Problem 5: Passwords
Security analysis of password hashing:
- Cracks three SHA-256 password hashes using rainbow tables
- Verifies cracked passwords using the complete SHA-256 implementation from Problems 1-4
- Analyzes why single-pass SHA-256 is inappropriate for password storage
- Recommends security improvements: salting, key derivation functions (bcrypt, Argon2), and iteration counts

## Implementation Notes

- All functions include comprehensive docstrings following PEP 257
- Type hints used throughout for clarity
- Extensive inline comments explain complex operations
- Code structured for readability and educational value
- All implementations verified against FIPS 180-4 test vectors

## References

- [FIPS 180-4: Secure Hash Standard](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- [PEP 257: Docstring Conventions](https://peps.python.org/pep-0257/)
- [NumPy Documentation](https://numpy.org/doc/stable/)
