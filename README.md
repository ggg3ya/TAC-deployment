

---

# TAC Contract Deployment Tutorial

This tutorial will guide you through deploying a simple smart contract on the **TAC Testnet** using **Foundry** and interacting with it using the **cast** tool.

## Prerequisites

Before getting started, ensure you have the following installed:

- [Foundry](https://github.com/foundry-rs/foundry)
- [Cast](https://github.com/gobitfly/cast)
- A **TAC Testnet account** with some testnet tokens (you can get testnet tokens from the TAC faucet).

---

## Step 1: Install Foundry

To install Foundry, run the following command:

```bash
curl -L https://foundry.paradigm.xyz | bash

Once installed, you can verify the installation by running:

forge --version


---

Step 2: Create a New Project

Create a new directory for your project:

mkdir my-tac-project
cd my-tac-project

Initialize a new Foundry project:

forge init

This will create the basic structure for your smart contract.


---

Step 3: Write Your Smart Contract

In the src/ directory, create a new file called MyContract.sol and write a simple smart contract:

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract MyContract {
    string public message = "Hello, TAC Testnet!";

    function setMessage(string memory _message) public {
        message = _message;
    }
}


---

Step 4: Configure Your Project

In the project root, configure the .env file to store sensitive data like your RPC URL and private key.

Create a .env file with the following content:

TAC_RPC_URL=https://turin.rpc.tac.build
PRIVATE_KEY=your_private_key_here

Make sure to replace your_private_key_here with your actual private key.


---

Step 5: Deploy the Contract

Compile and deploy the contract using the following command:

forge create --rpc-url $TAC_RPC_URL --private-key $PRIVATE_KEY src/MyContract.sol:MyContract --broadcast

The output will give you the contract address, which will look something like this:

Deployed to: 0x8c763a59BB2cc9cd532B94c3CBB15541407dE909
Transaction hash: 0x007c3078fecf0de4438e81c9d3954b403ace72477018cdc98853a9e25f3149ab


---

Step 6: Interact with the Contract

Once deployed, you can interact with your contract using cast. To get the current message stored in the contract, run:

cast call 0x8c763a59BB2cc9cd532B94c3CBB15541407dE909 "message() (string)" --rpc-url https://turin.rpc.tac.build

This should return the stored message: "Hello, TAC Testnet!".

To update the message, use the setMessage function:

cast send 0x8c763a59BB2cc9cd532B94c3CBB15541407dE909 "setMessage(string)" "New Message" --rpc-url https://turin.rpc.tac.build --private-key $PRIVATE_KEY


---

Step 7: Verify the Contract on the Explorer

To verify the contract, go to the TAC Testnet Explorer. Enter the contract address (0x8c763a59BB2cc9cd532B94c3CBB15541407dE909) to view the contract's details.


---

Step 8: Conclusion

Congratulations! You've successfully deployed and interacted with a smart contract on the TAC Testnet using Foundry and cast.

For further details on smart contract development with Foundry, visit the Foundry GitHub repository.

If you encounter any issues or have any questions, feel free to open an issue in this repository.


---

License

This tutorial is licensed under the MIT License. See LICENSE for details.

---

### **Step 3: Push the Tutorial to GitHub**

1. Add the files to git:

```bash
git init
git add .
git commit -m "Initial commit for TAC deployment tutorial"

2. Push the files to your GitHub repository:



git remote add origin https://github.com/your-username/tac-contract-deployment-tutorial.git
git push -u origin master


---

Now your GitHub repository is ready with a tutorial to guide others on how to deploy and interact with smart contracts on the TAC Testnet.

Let me know if you need help with any additional steps!
