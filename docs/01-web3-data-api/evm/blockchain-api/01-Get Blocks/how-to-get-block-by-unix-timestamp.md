---
title: "How to get the closest block by unix timestamp"
slug: "../../how-to-get-block-by-unix-timestamp"
description: "Learn how to get the closest block by a given unix timestamp using Moralis Block API."
sidebar_label: "Get closest block by unix timestamp"
---

## Step 1: Setup Moralis

Read the article [Setting Up Moralis: Getting Started](/web3-data-api/evm/get-your-api-key) and make sure to finish all the steps. Only after that you can go ahead to complete this guide.

## Step 2: Get block by unix timestamp

In order to get the closest block by unix timestamp, Moralis provides you a [getDateToBlock](/web3-data-api/evm/reference/get-date-to-block) endpoint to do so.

Here you'll need two parameters: `date` and `chain`.

Once you have obtained both the `date` and `chain`, you can copy the following code:

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

<Tabs groupId="programming-language">
  <TabItem value="javascript" label="index.js (JavaScript)" default>

```javascript index.js
const Moralis = require("moralis").default;
const { EvmChain } = require("@moralisweb3/common-evm-utils");

const runApp = async () => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });

  const date = "1667823435";

  const chain = EvmChain.ETHEREUM;

  const response = await Moralis.EvmApi.block.getDateToBlock({
    date,
    chain,
  });

  console.log(response.toJSON());
};

runApp();
```

</TabItem>
<TabItem value="typescript" label="index.ts (TypeScript)">

```typescript index.ts
import Moralis from "moralis";
import { EvmChain } from "@moralisweb3/common-evm-utils";

const runApp = async () => {
  await Moralis.start({
    apiKey: "YOUR_API_KEY",
    // ...and any other configuration
  });

  const date = "1667823435";

  const chain = EvmChain.ETHEREUM;

  const response = await Moralis.EvmApi.block.getDateToBlock({
    date,
    chain,
  });

  console.log(response.toJSON());
};

runApp();
```

</TabItem>
<TabItem value="python" label="index.py (Python)">

```python index.py
from moralis import evm_api

api_key = "YOUR_API_KEY"

params = {
    "date": "1667823435",
    "chain": "eth"
}

result = evm_api.block.get_date_to_block(
    api_key=api_key,
    params=params,
)

print(result)
```

</TabItem>
</Tabs>

## Step 3: Run the script

import RunTheScript from '/docs/partials/\_run-the-script.mdx';

<RunTheScript />

In your terminal, you should see the following JSON response:

```json
{
  "block": 15918090,
  "date": "2022-11-07T12:17:15+00:00",
  "timestamp": 1667823435
}
```

Congratulations 🥳 You just got the closest block using a unix timestamp with just a few lines of code using the Moralis Block API!

## API Reference

If you want to know more details on the endpoint and optional parameters, check out:

- [getDateToBlock](/web3-data-api/evm/reference/get-date-to-block)

## Support

If you face any trouble following the tutorial, feel free to reach out to our community engineers in our [Discord](https://moralis.io/discord) or [Forum](https://forum.moralis.io) to get 24/7 developer support.
