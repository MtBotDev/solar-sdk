# SOLAR SDK

An SDK for building applications on top of Solar .

## Usage Guide

### Installation

```
$ yarn add solar-sdk
```

## Trade API
Solar trade API is the fastest and easiest way to interact with solar liquidity. It allows you to swap for any asset with 2 requests and a signature.

### Get quote parameters

| Parameter    | Type   | Required | Description                                               |
|--------------|--------|----------|-----------------------------------------------------------|
| inputMint    | string | yes      | Input token mint address                                  |
| outputMint   | string | yes      | Output token mint address                                 |
| amount       | number | yes      | Either inputAmount or outputAmount depending on the swap mode. |
| slippageBps  | number | yes      | Slippage tolerance in base points (0.01%).               |


### Post parameters

| Parameter                     | Type    | Required | Description                                                                                                                       |
|-------------------------------|---------|----------|-----------------------------------------------------------------------------------------------------------------------------------|
| version                       | string  | yes      | Use 'V0' for versioned transaction, and 'LEGACY' for legacy transaction (for now only supports 'LEGACY').                                                          |
| wrapSol                       | boolean | no       | Set to true to accept ETH as `inputToken`.                                                                                        |
| unwrapSol                     | boolean | no       | Set to true to unwrap `wETH` received as `outputToken`.                                                                           |
| computeUnitPriceMicroLamports  | string  | yes      | You can manually set this or use Solar priority fee API to set an automatic amount with `String(data.data.default.h)`. The 'h' stands for high priority. 'vh' for very high and 'm' for medium are also accepted values. |
| wallet                        | string  | yes      | Public key of the wallet.                                                                                                         |
| inputTokenAccount             | string  | no       | Defaults to ATA (Associated Token Account).                                                                                       |
| outputTokenAccount            | string  | no       | Defaults to ATA (Associated Token Account).                                                                                       |


### Get quote (https://api.solarstudios.co/compute/$) & and define the swap type.

### Serialize (https://api.solarstudios.co/transaction/$)

Our apis schema and working is same as raydium's api. For now our api only supports LEGACY tx.

#### Raydium Trade api guide - https://docs.raydium.io/raydium/traders/trade-api
#### Demo Implimentations - https://github.com/raydium-io/raydium-sdk-V2-demo/blob/master/src/api/swap.ts#L21

#### BASE API URL - https://api.solarstudios.co

# API Endpoints

## Main
Main API endpoints for general information and configuration.

| Method | Endpoint               | Description                        |
|--------|-------------------------|------------------------------------|
| GET    | `/main/version`         | UI V3 current version             |
| GET    | `/main/rpcs`            | UI RPCs                           |
| GET    | `/main/chain-time`      | Chain Time                        |
| GET    | `/main/info`            | Total Value Locked (TVL) and 24-hour volume |
| GET    | `/main/auto-fee`        | Transaction auto fee              |
| GET    | `/main/clmm-config`     | CLMM Config                       |
| GET    | `/main/cpmm-config`     | CPMM Config                       |

## Mint
Endpoints related to mint information.

| Method | Endpoint               | Description                        |
|--------|-------------------------|------------------------------------|
| GET    | `/mint/list`            | Default Mint List                 |
| GET    | `/mint/ids`             | Mint Info                         |
| GET    | `/mint/price`           | Mint Price                        |

## Pools
Endpoints for pool information, keys, and historical data.

| Method | Endpoint               | Description                        |
|--------|-------------------------|------------------------------------|
| GET    | `/pools/info/ids`       | Pool Info                         |
| GET    | `/pools/info/lps`       | Pool Info by LP Mint              |
| GET    | `/pools/info/list`      | Pool Info List                    |
| GET    | `/pools/info/mint`      | Pool Info by Token Mint           |
| GET    | `/pools/key/ids`        | Pool Key                          |

#### For query parameters refer - https://api-v3.raydium.io/docs/#/