## ICON FOUNDATION's XCALL Cross-Chain Setup Utility Tool for Developers

This tool helps developers to simplify redundant tasks when implementing the xcall's cross-chain protocol in their projects. This document provides you with an information of installation and API specifications.

## Table of Contents

- [Installation](#installation)
- [API Specification - Introduction](#api-specification---introduction)
- [IconSetupUtils](#iconsetuputils)
- [IconSetupUtils.getIconContractByteCode](#getIconContractByteCode)
- [IconSetupUtils.isDeployed][isDeployed]
- [IconSetupUtils.saveDeployments][saveDeployments]
- [IconSetupUtils.getDeployments][getDeployments]
- [IconSetupUtils.getEvmContract][getEvmContract]
- [IconSetupUtils.getDappContract][getDappContract]
- [IconSetupUtils.getXcallContract][getXcallContract]
- [IconSetupUtils.getIconDappDeploymentsParams][getIconDappDeploymentsParams]
- [IconSetupUtils.getBtpAddress][getBtpAddress]
- [IconSetupUtils.filterEventICON][filterEventICON]
- [IconSetupUtils.filterCallMessageSentEvent][filterCallMessageSentEvent]
- [IconSetupUtils.sleep][sleep]
- [IconSetupUtils.strToHex][strToHex]
- [IconSetupUtils.strToHexPadded][strToHexPadded]
- [IconSetupUtils.isValidEVMAddress][isValidEVMAddress]
- [IconSetupUtils.fileExists][fileExists]
- [IconSetupUtils.parseEventResponseFromTracker][parseEventResponseFromTracker]

## Installation

### Usage in Node.js

Install `icon-crosschain-setup-utils` module using `yarn`.

```bash
yarn add icon-crosschain-setup-utils
```

Import `icon-crosschain-setup-utils` module.

```javascript
const IconSetupUtils = require("icon-crosschain-setup-utils");
```

### Usage in browser

Install `icon-crosschain-setup-utils` module using `yarn`,

```bash
yarn add icon-crosschain-setup-utils
```

```javascript
import IconSetupUtils from "icon-crosschain-setup-utils";
```

### Usage in react-native environment

Install `icon-crosschain-setup-utils` module using `yarn`,

```bash
yarn add icon-crosschain-setup-utils
```

Then, import `icon-crosschain-setup-utils` module.

```javascript
import IconSetupUtils from "icon-crosschain-setup-utils";
```

## API Specification - Introduction

`IconSetupUtils` is a root object of `icon-crosschain-setup-utils`, which provides functions to execute common tasks on the xcall protocol. Details of functions are as below:

## IconSetupUtils

`IconSetupUtils` is an object which all the exported utility functions. To use a function, you can either use the destructure the function from the object by name or use the dot notaion.

#### Example

```javascript
const IconSetupUtils = require("icon-crosschain-setup-utils");

// To use a utility function that checks if a contract is deployed using dot notation
const checkDeploymentStatus = IconSetupUtils.isDeployed(deploymentsPath);

// To use a utility function that checks if a contract is deployed using object destructuring
const { isDeployed } = IconSetupUtils;
```

## IconSetupUtils.getIconContractByteCode

`getIconContractByteCode()` is a function that returns the byte code of a contract specified by the parameter `jarPath`. It throws an error if there is an error reading the contract.

#### Parameters

| Parameter | Type     | Description           |
| --------- | -------- | --------------------- |
| jarPath   | `string` | file path of contract |

### Example

```javascript
const { getIconContractByteCode } = IconSetupUtils;

console.log(getIconContractByteCode(jarPath));
```

## IconSetupUtils.isDeployed

`isDeployed()` is a function that checks if the contract is deployed using the specified parameter `deploymentsPath`. It returns true if the contract is deployed, false if otherwise. It throws an error if there is an error checking the deployments.

#### Parameters

| Parameter       | Type     | Description                  |
| --------------- | -------- | ---------------------------- |
| deploymentsPath | `string` | file path of deployment.json |

### Example

```javascript
const { isDeployed } = IconSetupUtils;

console.log(isDeployed(deploymentsPath));
```

## IconSetupUtils.saveDeployments

`saveDeployments()` is a function that saves the address of the contracts deployed using the specified parameter `deploymentsPath` and `deployments`. It throws an error if there is an error saving the deployments.

#### Parameters

| Parameter       | Type     | Description                     |
| --------------- | -------- | ------------------------------- |
| deploymentsPath | `string` | file path of deployment.json    |
| deployments     | `object` | addresses of deployed contracts |

### Example

```javascript
const { saveDeployments } = IconSetupUtils;

console.log(saveDeployments(deploymentsPath, deployments));
```

## IconSetupUtils.getDeployments

`getDeployments()` is a function gets the deployed contracts using the specified parameter `deploymentsPath`. It throws an error if there is an error reading the deployments. It returns an `object` containing the deployed contracts.

#### Parameters

| Parameter       | Type     | Description                  |
| --------------- | -------- | ---------------------------- |
| deploymentsPath | `string` | file path of deployment.json |

### Example

```javascript
const { getDeployments } = IconSetupUtils;

console.log(getDeployments(deploymentsPath));
```

## IconSetupUtils.getEvmContract

`getEvmContract()` is a function that returns the EVM contract using the specified parameter `abiPath`. It throws an error if there is an error reading the EVM contract. It returns an `object` containing the contract.

#### Parameters

| Parameter | Type     | Description                  |
| --------- | -------- | ---------------------------- |
| abiPath   | `string` | path to the EVM contract abi |

### Example

```javascript
const { getEvmContract } = IconSetupUtils;

console.log(getEvmContract(abiPath));
```

## IconSetupUtils.getDappContract

`getDappContract()` is a function that returns the Dapp contract using the specified parameter `solPath`. It throws an error if reading the Dapp contract wasn't successful. It returns an `object` containing the Dapp contract.

#### Parameters

| Parameter | Type     | Description                                 |
| --------- | -------- | ------------------------------------------- |
| solPath   | `string` | path to the compiled EVM contract json file |

### Example

```javascript
const { getDappContract } = IconSetupUtils;

console.log(getDappContract(solPath));
```

## IconSetupUtils.getXcallContract

`getXcallContract()` is a function that returns the Xcall contract using the specified parameter `xcallAbiPath`. It throws an error if there is an error reading the Xcall contract. It returns an `object` containing the Xcall contract.

#### Parameters

| Parameter    | Type     | Description                |
| ------------ | -------- | -------------------------- |
| xcallAbiPath | `string` | path to xcallAbi.json file |

### Example

```javascript
const { getXcallContract } = IconSetupUtils;

console.log(getXcallContract(xcallAbiPath));
```

## IconSetupUtils.getIconDappDeploymentsParams

`getIconDappDeploymentsParams()` is a function that returns the params for the Icon contract using the specified parameters `label`, `dappContract` and `XCALL_PRIMARY`. It throws an error if there is an error getting the params.

#### Parameters

| Parameter     | Type     | Description                        |
| ------------- | -------- | ---------------------------------- |
| label         | `string` | the label of the network           |
| dappContract  | `string` | the address of the Dapp contract   |
| XCALL_PRIMARY | `string` | the address of the primary network |

### Example

```javascript
const { getIconDappDeploymentsParams } = IconSetupUtils;

console.log(getIconDappDeploymentsParams(label, dappContract, XCALL_PRIMARY));
```

## IconSetupUtils.getBtpAddress

`getBtpAddress()` is a function that returns the BTP address using the specified parameters `label` and `address`. It throws an error if there is an error reading the BTP address.

#### Parameters

| Parameter | Type     | Description                 |
| --------- | -------- | --------------------------- |
| label     | `string` | the label of the network    |
| address   | `string` | the address of the contract |

### Example

```javascript
const { getBtpAddress } = IconSetupUtils;

console.log(getBtpAddress(label, address));
```

## IconSetupUtils.filterEventICON

`filterEventICON()` is a function that returns an `object` of the filtered event logs using the specified parameters `eventlogs`, `sig` and `address`. It throws an error if there is an error filtering the event logs.

#### Parameters

| Parameter | Type     | Description                 |
| --------- | -------- | --------------------------- |
| eventlogs | `object` | the event logs              |
| sig       | `string` | the signature of the event  |
| address   | `string` | the address of the contract |

### Example

```javascript
const { filterEventICON } = IconSetupUtils;

console.log(filterEventICON(eventlogs, sig, address));
```

## IconSetupUtils.filterCallMessageSentEvent

`filterCallMessageSentEvent()` is a function that filters the CallMessageSent event logs and returns an `object` of the filtered event logs using the specified parameters `eventlogs`, and `XCALL_PRIMARY`. It throws an error if there is an error filtering the event logs.

#### Parameters

| Parameter     | Type     | Description                        |
| ------------- | -------- | ---------------------------------- |
| eventlogs     | `object` | the event logs                     |
| XCALL_PRIMARY | `string` | the address of the primary network |

### Example

```javascript
const { filterCallMessageSentEvent } = IconSetupUtils;

console.log(filterCallMessageSentEvent(eventlogs, XCALL_PRIMARY));
```

## IconSetupUtils.sleep

`sleep()` is a function that causes sleep (pause) in the program for the specified time using the parameter, `ms`. It returns an async function.

#### Parameters

| Parameter | Type     | Description       |
| --------- | -------- | ----------------- |
| ms        | `number` | the time to sleep |

### Example

```javascript
const { sleep } = IconSetupUtils;

console.log(sleep(ms));
```

## IconSetupUtils.strToHex

`strToHex()` is a function that converts a string to hex using the parameter, `str`. It returns a hex string and throws an error if there is an error converting the string.

#### Parameters

| Parameter | Type     | Description           |
| --------- | -------- | --------------------- |
| str       | `string` | the string to convert |

### Example

```javascript
const { strToHex } = IconSetupUtils;

console.log(strToHex(str));
```

## IconSetupUtils.strToHexPadded

`strToHexPadded()` is a function that converts a string to hex and pads it. It accepts the parameter, `str`. It returns a padded hex string and throws an error if there is an error converting the string.

#### Parameters

| Parameter | Type     | Description           |
| --------- | -------- | --------------------- |
| str       | `string` | the string to convert |

### Example

```javascript
const { strToHexPadded } = IconSetupUtils;

console.log(strToHexPadded(str));
```

## IconSetupUtils.isValidEVMAddress

`isValidEVMAddress()` is a function that checks if a contract address is valid. It accepts the parameter, `address`. It returns true if the address is valid or false if otherwise.

#### Parameters

| Parameter | Type     | Description             |
| --------- | -------- | ----------------------- |
| address   | `string` | the address to validate |

### Example

```javascript
const { isValidEVMAddress } = IconSetupUtils;

console.log(isValidEVMAddress(address));
```

## IconSetupUtils.fileExists

`fileExists()` is a function that checks if a file exists. It accepts the parameter, `path`. It returns true if the address is valid or false if otherwise. It throws an error if there is an error checking the file.

#### Parameters

| Parameter | Type     | Description |
| --------- | -------- | ----------- |
| path      | `string` | file path   |

### Example

```javascript
const { fileExists } = IconSetupUtils;

console.log(fileExists(path));
```

## IconSetupUtils.parseEventResponseFromTracker

`parseEventResponseFromTracker()` is a function that parses the event response from the network tracker. It accepts the parameter, `response`. It returns an array of objects containing details of the parsed event response from the tracker.

#### Parameters

| Parameter | Type       | Description                                                           |
| --------- | ---------- | --------------------------------------------------------------------- |
| response  | `[object]` | an array of objects containing details of event response from tracker |

### Example

```javascript
const { parseEventResponseFromTracker } = IconSetupUtils;

console.log(parseEventResponseFromTracker(path));
```
