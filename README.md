<h1>Web3 CRU (Create - Read - Update) Blog Project</h1>

## In this project we are using:
- Blockchain: Polygon
- Ethereum development environment: Hardhat
- Front-end framework: Next.js, React.js
- Ethereum web client library: Ether.js
- Storage: IPFS

## Prerequisites
- Node.js installed on your local machine
- MetaMask Chrome extension installed in your browser

## Project setup

First, you need to clone the repo then navigate to "web3-basic-project" folder and install dependencies:

```bash
npm install ethers hardhat @nomiclabs/hardhat-waffle \
ethereum-waffle chai @nomiclabs/hardhat-ethers \
web3modal @walletconnect/web3-provider \
easymde react-markdown react-simplemde-editor \
ipfs-http-client @emotion/css @openzeppelin/contracts
```

Get hardhat test account:
```bash
npx hardhat node
```
Import test account that created by hardhat into Metamask.

Create **".env.local"** file within the folder and add the following code:
```bash
ENVIRONMENT="local"
NEXT_PUBLIC_ENVIRONMENT="local"
NEXT_PUBLIC_PROJECT_ID=""
NEXT_PUBLIC_PROJECT_SECRET=""
```

The *"NEXT_PUBLIC_PROJECT_ID"* and *"NEXT_PUBLIC_PROJECT_SECRET"* are the "PROJECT ID" and "API KEY SECRET" of Infura IPFS project (if you don't have one, just create an IPFS Project in Infura dashboard with [**this link**](https://app.infura.io/dashboard/)). You need these two variables because **the latest IPFS require authentication**.

![image](https://user-images.githubusercontent.com/64829950/228449462-92477087-702b-4282-8480-90553ce337af.png)

About the values of two variables *"ENVIRONMENT"* and *"NEXT_PUBLIC_ENVIRONMENT"* you can switch between "local" / "testnet" as your need.

## Metamask
First enable test network in Metamask.
- **Deploy in local:** Add localhost with port 8545.
- **Deploy in testnet:** We use Mumbai (a test network of Polygon) so we add network with this configuration:
```bash
Network Name: Mumbai
New RPC URL: https://rpc-mumbai.maticvigil.com
Chain ID: 80001
Currency Symbol: MATIC
```

## Deploy Project
**1. Local:**
- Ensure that the value of two variables *"ENVIRONMENT"* and *"NEXT_PUBLIC_ENVIRONMENT"* are "local".
- Deploy network using this command:
```bash
npx hardhat run scripts/deploy.js --network localhost
```
- Run project:
```bash
npm run dev
```
- Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

**2. Testnet:**
- Ensure that the value of two variables "ENVIRONMENT" and "NEXT_PUBLIC_ENVIRONMENT" are "testnet".
- Export the private key of your Metamask account that you import or copy in the terminal that you run the command *"npx hardhat node"*.
- Then save that private key in terminal as an environment variable by using this command:
```bash
export pk=<your private key>
```
- Switch to "Mumbai" network that you added before in Metamask.
- Going to [**this website**](https://faucet.polygon.technology) to get some test token because you need it to pay the fees to deploy.

![image](https://user-images.githubusercontent.com/64829950/228446597-a43cebb3-50a8-4581-9e1c-e1d42aad01c9.png)

- Wait until your account has test token and run this command in the terminal which was added the private key as environment variable:
```bash
npx hardhat run scripts/deploy.js --network testnet
```
- If you successfully deployed, your terminal will return back like this:

![image](https://user-images.githubusercontent.com/64829950/228447824-56e8514f-7a59-401c-958b-29e9287bf091.png)

- Run project:
```bash
npm run dev
```
- Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

