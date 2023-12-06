# ETCswap Swap Router

[![Tests](https://github.com/ETCswap/swap-router-contracts/workflows/Tests/badge.svg)](https://github.com/ETCswap/swap-router-contracts/actions?query=workflow%3ATests)
[![Lint](https://github.com/ETCswap/swap-router-contracts/workflows/Lint/badge.svg)](https://github.com/ETCswap/swap-router-contracts/actions?query=workflow%3ALint)

This repository contains smart contracts for swapping on the ETCswap V2 and V3 protocols.

## Bug bounty

This repository is subject to the ETCswap V3 bug bounty program,
per the terms defined [here](./bug-bounty.md).

## Local deployment

In order to deploy this code to a local testnet, you should install the npm package
`@etcswap/swap-router-contracts`
and import bytecode imported from artifacts located at
`@etcswap/swap-router-contracts/artifacts/contracts/*/*.json`.
For example:

```typescript
import {
  abi as SWAP_ROUTER_ABI,
  bytecode as SWAP_ROUTER_BYTECODE,
} from '@etcswap/swap-router-contracts/artifacts/contracts/SwapRouter02.sol/SwapRouter02.json'

// deploy the bytecode
```

This will ensure that you are testing against the same bytecode that is deployed to
mainnet and public testnets, and all ETCswap code will correctly interoperate with
your local deployment.

## Using solidity interfaces

The swap router contract interfaces are available for import into solidity smart contracts
via the npm artifact `@etcswap/swap-router-contracts`, e.g.:

```solidity
import '@etcswap/swap-router-contracts/contracts/interfaces/ISwapRouter02.sol';

contract MyContract {
  ISwapRouter02 router;

  function doSomethingWithSwapRouter() {
    // router.exactInput(...);
  }
}

```

## Tests

Some tests use Hardhat mainnet forking and therefore require an archive node.
Either create a `.env` file in the workspace root containing:

```
ARCHIVE_RPC_URL='...'
```

Or set the variable when running tests:

```
export ARCHIVE_RPC_URL='...' && npm run test
```
