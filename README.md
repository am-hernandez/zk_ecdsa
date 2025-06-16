# ZK ECDSA

A Noir program that verifies ECDSA signatures and recovers Ethereum addresses using zero-knowledge proofs. This project demonstrates how to verify ECDSA signatures in a zero-knowledge context, which can be useful for privacy-preserving authentication and transaction signing.

## Overview

The program takes the following inputs:

- Public key components (x, y coordinates)
- ECDSA signature
- Hashed message
- Expected Ethereum address

It verifies that:

1. The signature is valid for the given public key and message
2. The recovered address matches the expected address

## Prerequisites

- [Noir](https://noir-lang.org/getting_started/installation/)
- [Foundry](https://book.getfoundry.sh/getting-started/installation)

## Setup

1. Clone the repository:

```bash
git clone <your-repo-url>
cd zk_ecdsa
```

2. Install dependencies:

```bash
nargo check
```

## Usage

### Generating a Proof

To generate a proof, you'll need:

- Public key (x, y coordinates)
- ECDSA signature
- Hashed message
- Expected Ethereum address

```bash
nargo prove
```

### Verifying a Proof

```bash
nargo verify
```

### On-chain Verification

The project includes a Solidity verifier contract located at `./target/Verifier.sol`. This contract can be deployed to any EVM-compatible blockchain to verify proofs on-chain.

To use the verifier:

1. Deploy the verifier contract
2. Call the `verify` function with your proof

Example:

```solidity
// Deploy the verifier
Verifier verifier = new Verifier();

// Verify a proof
bool isValid = verifier.verify(proof, publicInputs);
```

## Project Structure

- `src/main.nr`: Main Noir program
- `target/verifier.sol`: Solidity verifier contract
- `Nargo.toml`: Project configuration and dependencies

## Dependencies

- `ecrecover-noir`: Local fork of the ecrecover library for ECDSA signature verification

## License

MIT
