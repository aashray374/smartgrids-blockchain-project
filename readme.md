# P2P Energy Trading System

A blockchain-based Peer-to-Peer Energy Trading System that integrates **Hardhat**, **Remix**, **Solidity Smart Contracts**, and a **Python Market Engine**.

---

# Project Structure

```text
project/
│
├── server/                  # Hardhat blockchain server
├── remix/                   # Smart contract project
├── energy-trading/          # Python market engine
├── setup/                   # User registration & blockchain setup
└── README.md
```

---

# Prerequisites

Install the following before starting:

* Node.js (v18 or later)
* npm
* Python 3.10+
* pip
* Hardhat
* Remix IDE (Desktop or Browser)

Install Python dependencies:

```bash
pip install -r requirements.txt
```

---

# Step 1: Configure Hardhat

Before starting the blockchain server, replace the existing `hardhat.config.ts` inside the `server` folder with the provided configuration file.

This configuration:

* Creates 30 deterministic accounts.
* Gives each account 10,000 ETH.
* Saves all generated accounts into:

```text
local-accounts.txt
```

---

# Step 2: Start the Hardhat Server

Navigate to the server folder.

```bash
cd server
```

Initialize Hardhat (only required once):

```bash
npx hardhat --init
```

Start the local blockchain:

```bash
npx hardhat node
```

Keep this terminal running throughout the execution.

---

# Step 3: Deploy Smart Contracts

Open the Remix project in the Remix IDE.

Compile and deploy the smart contracts to the local Hardhat network.

After successful deployment:

* Copy the deployed contract address.
* Copy the contract ABI.

Save the ABI as:

```text
energy-trading/
    contract_abi.json
```

---

# Step 4: Save Contract Artifact

After compiling the contract, locate:

```text
artifacts/
    CentralSmartContract.json
```

Inside the project root, create an `artifacts` folder (if it does not already exist):

```text
project/
    artifacts/
```

Copy:

```text
CentralSmartContract.json
```

into this folder.

Final structure:

```text
project/
    artifacts/
        CentralSmartContract.json
```

---

# Step 5: Run Blockchain Setup

Navigate to the setup folder.

```bash
cd setup
```

Run:

```bash
python setup.py
```

This script performs the initial blockchain configuration by:

* Registering all users.
* Funding the registered users.
* Setting the Python Engine address.
* Setting the Oracle address.

> **Note:** The Python Engine address and Oracle address should be the **same address**.

Wait until the setup script finishes successfully.

---

# Step 6: Run the Python Energy Trading Engine

Navigate to:

```bash
cd energy-trading
```

Run:

```bash
python run.py
```

This starts the energy trading engine and begins processing market windows.

---

# Complete Startup Order

Always follow this order:

1. Replace `hardhat.config.ts` with the provided configuration.
2. Navigate to `server`.
3. Run:

```bash
npx hardhat --init
```

4. Start the blockchain:

```bash
npx hardhat node
```

5. Deploy the smart contract using Remix.
6. Copy the contract ABI and save it as:

```text
energy-trading/contract_abi.json
```

7. Copy:

```text
artifacts/CentralSmartContract.json
```

to:

```text
project/artifacts/CentralSmartContract.json
```

8. Navigate to the `setup` folder and execute:

```bash
python setup.py
```

9. Ensure the Python Engine address and Oracle address are identical.
10. Navigate to `energy-trading` and execute:

```bash
python run.py
```

---

# Notes

* Do **not** stop the Hardhat node while the Python engine is running.
* The smart contract must be deployed before running the setup script.
* The setup script must complete successfully before starting the Python engine.
* Ensure `contract_abi.json` and `CentralSmartContract.json` are copied before executing `run.py`.

