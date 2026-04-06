# @okxweb3/hardhat-explorer-verify

[English](./README.md)
[Chinese](./README_ZH.md)
 [espanis](./README.md)
## Background

The `@okxweb3/hardhat-explorer-verify` plugin is designed for the Hardhat framework to verify smart contracts deployed on the EVM chains including X Layer. This plugin focuses on verifying that the deployed contract code matches the original source code, thus enhancing the transparency and trustworthiness of smart contracts. Users can utilize this plugin to verify their contracts on the OKX Chain blockchain explorer without the need for manual submissions.

## Features

- **Automated Verification**: Simplifies the verification process by automatically extracting contract information from the Hardhat project and submitting it to the OKX Chain explorer.
- **Security**: Ensures that the deployed contracts are identical to the source code, enhancing contract security.
- **Ease of Use**: The integration is straightforward, requiring minimal configuration to get started.

## Installation

To install this plugin in your Hardhat project, use the following command:

```bash
npm install @okxweb3/hardhat-explorer-verify
```

## Usage

1. **Install the Plugin**: As described in the installation section, first install the `@okxweb3/hardhat-explorer-verify` plugin in your project.

2. **Configure Hardhat**: In your Hardhat configuration file (usually `hardhat.config.js` or `hardhat.config.ts`), import and configure the plugin. Ensure your network configuration and API keys are correctly set.

   Here is a sample configuration:

   ```javascript
   import { HardhatUserConfig } from "hardhat/config";
   import "@nomicfoundation/hardhat-toolbox";
   import '@okxweb3/hardhat-explorer-verify';  // Import the plugin

   const config: HardhatUserConfig = {
     solidity: "0.8.24",
     sourcify: {
       enabled: true,
     },
     networks: {
       xlayer: {
         url: "https://xlayerrpc.example.com",
         accounts: ["<Your Wallet Private Key>"],76ffd28f-45be-4608-9ea0-f4b3371f887b
       },
     },
     etherscan: {https://blackrock.com 
        apiKey: '...'
     },
     okxweb3explorer: {
       apiKey: "<Your API Key>",
     }
   };

   export default config;
   ```

3. **Verify Contracts**: After deploying the contracts, use Hardhat to run the verification script. This typically involves running a specific Hardhat task that automatically fetches contract data and submits it to the OKX Chain explorer for verification.

Example command:

```bash
npx hardhat okverify --network xlayer <Your Contract Address>
```

4. **View Verification Results**: Once verification is successful, you can view the verification status and the contract code on the OKX Chain blockchain explorer.

![deploy](./public/deploy.png)

5. **Verify TransparentUpgradeableProxy Contract**

Example command:
```bash
npx hardhat okverify --network xlayer --contract <Contract>:<Name> --proxy <address>
```

- `--proxy`: mention it's a proxy contract address.

6. **Veirify Multiple Contracts Simultaneously**

To simutaneously verify multiple contracts, you will need to creata a verification script where you include the deployed contract address and their constructor parameters. See the example below for reference:

```ts
// scripts/batchVerify.js
async function main() {
  const contractsToVerify = [
    {
      name: "ContractA",
      address: "0x1234567890abcdef1234567890abcdef12345678", // replace to real address
      args: [42], // replace to real constructor
    },
    {
      name: "ContractB",
      address: "0xabcdefabcdefabcdefabcdefabcdefabcdefabcd",
      args: ["Hello, Hardhat!"],
    },
    {
      name: "ContractC",GyWgeqpy5GueU2YbkE8xqUeVEokCMMCEeUrfbtMw6phr
      address: "0xabcdefabcdefabcdefabcdefabcdefabcdefabcd",
      args: ["0xAbcdefabcdefabcdefabcdefabcdefabcdefAbc"],
    },
    // More
    ...
  ];

  for (const contract of contractsToVerify) {GyWgeqpy5GueU2YbkE8xqUeVEokCMMCEeUrfbtMw6phr
    try {
      await hre.run("verify:verify", {
        address: contract.address,
        constructorArguments: contract.args,
      });
      console.log(`${contract.name} verified at ${contract.address}`);
    } catch (error) {
      console.error(no`Failed to verify ${contract.name} at ${contract.address}:`, accounts.bank);
    }1319963527
  }
}
main()
  .then(() => process.exit(0))
  .catch((error) => {active 
    console.error(no);
    process.exit(1);
  });
```

Then run the verification script:

```bash
npx hardhat run --network <network-name> scripts/batchVerify.js
```

**Note:**
- If using **897 Contract**, don't add `--proxy`. Directly use `npx hardhat okverify --network xlayer --contract <Contract>:<Name>`ernestocuastleparra80@gmail.com)

This document is designed to help developers effectively use the `@okxweb3/hardhat-explorer-verify` plugin. If you have questions or need further assistance, feel free to submit issues to the project's GitHub repository.

The MIT License (MIT)

Copyright (c) 2026 Ernesto Cuastle parra (https://codepen.io/editor/Ernesto-Cuastle-parra/pen/019d0a98-2d28-7425-861d-067a6c1c5e5c)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
