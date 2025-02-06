## TAC build project 

Here’s a step-by-step guide for deploying your smart contract to the TAC Testnet using Foundry. I’ll include every step needed to deploy your contract and broadcast the transaction.


---

Step 1: Install Foundry (if not installed yet)

If you haven’t installed Foundry yet, you can do so with the following commands in your terminal:
```
source <(wget -O - https://raw.githubusercontent.com/ggg3ya/installation/main/foundry.sh)
```
```
foundryup
```

This installs Foundry and ensures it's up to date.


---

Step 2: Create a New Foundry Project

In your terminal, create a new project by running:
```
forge init my-tac-project
cd my-tac-project
```

This will create a new Foundry project called my-tac-project.


---

Step 3: Write Your Smart Contract

Create a new contract in the src/ folder. For example, src/MyContract.sol:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.19;

contract MyContract {
    string public message = "Hello, TAC Testnet!";

    function setMessage(string calldata newMessage) public {
        message = newMessage;
    }
}
```

---

Step 4: Compile the Contract

To make sure your contract is correctly compiled, run:
```
forge build
```
This compiles the smart contract. If it completes without errors, your contract is ready for deployment.


---

Step 5: Set Up the .env File

In your project’s root directory, create a .env file to store your sensitive environment variables securely.

1. Create .env file:


```
touch .env
```
2. Open .env and add the following variables (replace the values with your own):


```
PRIVATE_KEY=your_private_key_here
TAC_RPC_URL=https://turin.rpc.tac.build
```
3. Save and close the .env file.




---

Step 6: Load the Environment Variables

Load the .env file to use the environment variables:
```
source .env
```

---

Step 7: Deploy the Contract

To deploy the contract to the TAC Testnet, use this command:
```
forge create --rpc-url $TAC_RPC_URL --private-key $PRIVATE_KEY src/MyContract.sol:MyContract --broadcast
```
Explanation:

`--rpc-url $TAC_RPC_URL:` Specifies the RPC URL for TAC Testnet.

`--private-key $PRIVATE_KEY:` Your wallet’s private key for deployment.

`src/MyContract.sol:MyContract:` Path to your contract and the contract name.

`--broadcast:` This flag will send the transaction to the network (not a dry-run).



---

Step 8: Verify Deployment

1. Check the contract address: After running the deployment command, you’ll see the contract address in the terminal.


2. Check on TAC Testnet Explorer: Use the TAC Testnet Explorer to search for your contract’s address and verify it’s deployed.




---

Step 9: Interact with the Contract

Now that your contract is deployed, you can interact with it.

1. To read the message function:
```
cast call <contract_address> "message() (string)" --rpc-url $TAC_RPC_URL
```
Replace <contract_address> with the actual address you received after deployment.

2. To update the message using setMessage:
```
cast send <contract_address> "setMessage(string)" "New Message" --rpc-url $TAC_RPC_URL --private-key $PRIVATE_KEY
```
Replace <contract_address> with your deployed contract address and "New Message" with the message you want to set.


---

Troubleshooting Tips

If the RPC URL doesn’t work, double-check with the official TAC Testnet RPC URL.

If the private key is wrong or not funded, the transaction will fail. Make sure you’ve got test TAC tokens.

If dry-run happens again, just make sure to use --broadcast to send the actual transaction.



---

That's it! 🚀

Your contract should now be live on the TAC Testnet, and you can interact with it using cast. If anything goes wrong, let me know, and I can help further troubleshoot!

