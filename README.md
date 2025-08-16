# DVRE Smart Contracts

A comprehensive smart contract system for decentralized collaborative research projects with active learning capabilities.

## Overview

This repository contains smart contracts for managing research projects, user metadata, assets, and active learning workflows on the blockchain. The system supports both traditional research projects and specialized active learning projects with voting mechanisms.

## Architecture

### Core Infrastructure Contracts

- **UserMetadataFactory**: Creates and manages user metadata contracts
- **ProjectTemplateRegistry**: Manages project templates and configurations
- **ProjectFactory**: Creates standard research project contracts
- **AssetFactory**: Manages research assets and data
- **Project**: Base contract for research projects with participant management
- **Asset**: Contract for storing and managing research data assets

### Active Learning (AL) Contracts

- **ALProjectLinker**: Links active learning projects with core infrastructure
- **ALProjectDeployer**: Deploys active learning project instances
- **ALProject**: Enhanced project contract with active learning capabilities
- **ALProjectVoting**: Manages voting sessions for data labeling
- **ALProjectStorage**: Stores labeled data and voting results

## Prerequisites

Before deploying the smart contracts, ensure you have:

1. **Node.js** (v16 or higher)
2. **npm** or **yarn**
3. **Hardhat** development environment
4. Access to an Ethereum-compatible network (local or testnet)

## Environment Setup

1. Create a `.env` file in the project root:

```bash
RPC_URL=http://145.100.135.27:8550  # Your network RPC URL
PRIVATE_KEY=your_private_key_here  # Deployer account private key
```

**Available Network Nodes:**

You can use any of the following RPC endpoints by updating the `RPC_URL` in your `.env` file:

- **Node 1 (Primary)**: `http://145.100.135.27:8550`
- **Node 2 (Secondary)**: `http://145.100.135.39:8550`
- **Node 3 (Tertiary)**: `http://145.100.135.97:8550`
- **Node 4 (Quaternary)**: `http://49.12.44.119:8550`

2. Install dependencies:

```bash
npm install
```

3. Compile the contracts:

```bash
npx hardhat compile
```

## Deployment

### Deploy All Contracts

Run the main deployment script to deploy all core infrastructure and active learning contracts:

```bash
node scripts/deploy-web3.js
```

This script will:

1. Deploy core infrastructure contracts:
   - UserMetadataFactory
   - ProjectTemplateRegistry
   - ProjectFactory
   - AssetFactory

2. Deploy active learning contracts:
   - ALProjectLinker
   - ALProjectDeployer

3. Register all contracts in the FactoryRegistry for frontend discovery

4. Output deployment addresses and summary


## Post-Deployment: Copy ABIs

After deploying the contracts, you need to copy the compiled ABIs to the `jupyter-extension` folder of the Jupyter Client Application for frontend integration:

```bash
node scripts/copy-abis.js
```

This script will:

- Copy all contract ABIs from `artifacts/contracts/` to `../jupyter-extension/src/abis/`
- Copy ABIs to `../jupyter-extension/lib/abis/` for runtime usage
- Show detailed results of new, changed, and unchanged files
- Skip duplicate interface files automatically

