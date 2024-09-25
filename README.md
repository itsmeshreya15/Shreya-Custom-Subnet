Here’s a combined README that incorporates both the details of your custom Avalanche subnet `shreyablockchain` and the `MagicShowToken` smart contract:

---

# Shreyablockchain - Custom Avalanche Subnet with MagicShowToken

## Introduction
`shreyablockchain` is a custom blockchain deployed using Avalanche's Subnet framework. This blockchain uses the `Subnet-EVM` virtual machine (VM) and has a unique configuration with a custom token, `MagicShowToken` (MST). The project leverages Avalanche's highly scalable and secure blockchain platform to create a localized, customizable environment for developers to test and run decentralized applications (dApps).

## Features
- **Custom Token**: MagicShowToken (MST)
- **Token Prefunding**: 1,000,000 MST for the main funded account (`EWOQ`)
- **VM**: Subnet-EVM (Avalanche Virtual Machine)
- **Chain ID**: 10079
- **Teleporter**: Messenger and Registry smart contracts for cross-chain interoperability

## Smart Contract Overview

### MagicShowToken Contract
The `MagicShowToken` smart contract is an ERC20 token with additional functionalities to manage magical items. It includes the following features:

- **Minting Tokens**: Only the owner can mint new tokens.
- **Burnable Tokens**: Tokens can be burned to redeem magical items.
- **Redeem Magical Items**: Players can redeem tokens for various magical items (Wand, Hat, Cloak, Potion).
- **Player Items Tracking**: Keeps track of each player's magical items balance.

### Key Functions
- **mintTokens**: Mints new tokens to a specified address (only callable by the owner).
- **transferTokens**: Allows users to transfer tokens to another address.
- **redeemItem**: Redeems tokens for a magical item, burning the cost in tokens.
- **burnTokens**: Burns tokens from the caller's balance.
- **checkBalance**: Allows users to check their token balance.

## Prerequisites
To work with this project, you will need:
- **Ubuntu (20.04 or later)** or **WSL 2** with Ubuntu installed on Windows
- **curl**: To install packages
- **Avalanche CLI**: Command-line interface for working with Avalanche Subnets
- **MetaMask** (optional): To interact with the custom blockchain

### Installing Dependencies
Before starting, ensure your system has the necessary packages and dependencies installed.

1. **Install Curl**:
    ```bash
    sudo apt-get update
    sudo apt-get install curl
    ```

2. **Install Avalanche CLI**:
    Run the following command to install the Avalanche CLI:
    ```bash
    curl -sSfL https://raw.githubusercontent.com/ava-labs/avalanche-cli/main/scripts/install.sh | sh
    ```

3. **Verify Installation**:
    Once installed, verify that `avalanche` is working by checking the version:
    ```bash
    avalanche --version
    ```

## Blockchain Creation Process
### 1. Create a Custom Blockchain (`shreyablockchain`)
Once the Avalanche CLI is installed, create your custom blockchain `shreyablockchain`.

1. **Run the Blockchain Creation Command**:
    ```bash
    avalanche blockchain create shreyablockchain
    ```
    - Select `Subnet-EVM` as the VM.
    - Token Symbol: `MST`
    - Chain ID: `10079`
    - Prefunding Address: `0x8db97C7cEcE249c2b98bDC0226Cc4C2A57BF52FC`
    - Initial Token Supply: `1,000,000 MST`

2. **Confirm Blockchain Configuration**:
    Example Output:
    ```plaintext
    ✓ Successfully created blockchain configuration
    ```

### 2. Deploying the Subnet Locally
After creating the blockchain, deploy the subnet locally.

1. **Run the Deployment Command**:
    ```bash
    avalanche subnet deploy shreyablockchain
    ```

2. **Wait for Network Deployment**:
    Example Output:
    ```plaintext
    Network ready to use.
    Teleporter Messenger successfully deployed to shreyablockchain
    Blockchain ready to use
    ```

### 3. Network and Blockchain Information
Once deployed, the local network configuration will be displayed, including:
- **VM Version**: v0.6.10
- **Chain ID**: `10079`
- **Blockchain ID (HEX)**: `0xd60f52643aeb6f1ef4e6b7ed67490d02b5297daa3c684299a1e32ec0db0ad6b2`
- **Local Node URLs**:
    - Node 1: `http://127.0.0.1:9650`
    - Node 2: `http://127.0.0.1:9652`
- **Teleporter Contracts**:
    - Messenger Address: `0x253b2784c75e510dD0fF1da844684a1aC0aa5fc`
    - Registry Address: `0x5a313c1A34A342DE0f0833820300991Cd1c452E3`

### 4. Accessing the Local Network
You can interact with your local network using the provided RPC URLs, connecting your blockchain with wallets like MetaMask for testing.

- **Localhost RPC URL**:
    ```bash
    http://127.0.0.1:9650/ext/bc/shreyablockchain/rpc
    ```

## Interacting with the Blockchain
Once the blockchain is deployed, interact with it through the Avalanche platform's supported methods, including using the Teleporter smart contracts or integrating it into dApps. Key interactions include:

- **Token Interactions**: Use the prefunded accounts to transfer, mint, or burn the custom MST token.
- **Redeem Magical Items**: Players can redeem their tokens for magical items by calling the `redeemItem` function.

### Connect to MetaMask
To use MetaMask with your custom network:
1. **Open MetaMask** and click on the Network dropdown.
2. **Select "Custom RPC"** and enter the following details:
    - **Network Name**: Shreyablockchain
    - **New RPC URL**: `http://127.0.0.1:9650/ext/bc/shreyablockchain/rpc`
    - **Chain ID**: `10079`
    - **Currency Symbol**: `MST`

## Additional Information
### Logs and Debugging
Check the logs generated during the deployment process for debugging:
- **Node Logs**:
    ```bash
    /home/hrishikesh/.avalanche-cli/runs/network_<timestamp>/node<node_number>/logs
    ```
- **Backend Logs**:
    ```bash
    /home/hrishikesh/.avalanche-cli/runs/server_<timestamp>/avalanche-cli-backend.log
    ```

### Teleporter Messenger and Registry
The `Teleporter` contracts allow for cross-chain messaging and interoperability, enabling advanced cross-chain functionalities for decentralized applications.


