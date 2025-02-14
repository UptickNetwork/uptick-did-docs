---
id: quick-start-demo
title: Quick Start Demo
sidebar_label: Quick Start Demo
description: A quick demonstration of Privado ID's main features.
keywords:
  - docs
  - privado id
  - ID holder
  - issuer
  - verifier
  - wallet
  - credential
  - schema
---

import useBaseUrl from '@docusaurus/useBaseUrl';
import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

This tutorial illustrates Privado ID's main functionalities. It walks through Privado ID's products and tools by presenting a simple POAP use case. POAP stands for Proof of Attendance Protocol, which is used to prove that someone has taken part in a given event.

In this tutorial, you will assume each of the 3 roles required by the [Triangle of Trust](introduction.md#core-concepts-of-privado-id-verifiable-credentials-identity-holder-issuer-and-verifier): the Identity Holder, the Issuer, and the Verifier. You will:

1. [Set up a Privado ID wallet](#set-up-a-privado-id-wallet)
2. [Issue the POAP credential](#issue-the-poap-credential)
3. [Fetch the newly created credential](#fetch-the-newly-created-credential)
4. [Verify the ID holder credential](#verify-the-id-holder-credential)

## Set up a Privado ID wallet

To store verifiable credentials, the Identity Holder (the individual receiving the credential) needs a compatible wallet. Here, we’ll use the Privado ID Wallet, which supports both Mobile and Web-based access.

:::note

You may use any Privado ID compatible wallet. Our [<ins>Ecosystem page</ins>](https://marketplace.privado.id/ecosystem) lists all supported wallets.

:::

To get started with the Privado ID Wallet, either visit the [Privado ID Web Wallet](https://wallet.privado.id/) in your browser or download the Mobile App and create an Identity.


<Tabs>
<TabItem value="Web Wallet">

<a href="https://wallet.privado.id/" target="_blank">Privado ID Web Wallet</a>

:::note
The Privado ID Web Wallet is a Web-based identity wallet. It is a reference implementation built using our [<ins>JS SDK</ins>](/docs/js-sdk/js-sdk-overview.md). [<ins>Learn more about the Web Wallet</ins>](/docs/wallet/web-wallet.md).
:::

</TabItem>

<TabItem value="Mobile Wallet">

- Android: <a href="https://play.google.com/store/apps/details?id=id.privado.wallet" target="_blank">Privado ID Wallet App on Google Play</a>
- iOS: <a href="https://apps.apple.com/us/app/privadoid/id6566184703" target="_blank">Privado ID Wallet App on the App Store</a>

:::note
Privado ID Wallet App is an implementation of the [<ins>Wallet SDK</ins>](/docs/category/wallet-sdk), as a way of showcasing its possibilities. [<ins>Learn more about the Molbile Wallet</ins>](/docs/wallet/wallet-app/privadoid-app.md).
:::

</TabItem>
</Tabs>


## Issue the POAP credential

You will now take the role of an Issuer, in this example, the private institution/trusted entity that held the event and creates a POAP. The Issuer is responsible for both creating the credential and sending it to the Identity Holder.

We will use <a href="https://issuer-demo.privado.id/">the Issuer Node UI Demo environment</a> to manage credentials. This environment enables an Issuer to create and manage identities and credentials, generate connections, and manage schemas.

:::note

When an Issuer releases a new credential type, they create a schema representation of the credential. This comprises a set of JSON files that gather all the credential's attributes.

[<ins>Learn how to set up your own Issuer environment by deploying an Issuer node</ins>](/docs/issuer/issuer-overview.md).

:::

To simplify this demo issuance, we provide an existing credential schema with schema type POAP01:

<Tabs>
<TabItem value="JSON schema URL">

```ipfs://QmTSwnuCB9grYMB2z5EKXDagfChurK5MiMCS6efrRbsyVX```

> View this credential's data using an <a href="https://ipfs.io/ipfs/QmTSwnuCB9grYMB2z5EKXDagfChurK5MiMCS6efrRbsyVX" target="_blank">online gateway</a>.


</TabItem>

<TabItem value="JSON-LD context URL">

```ipfs://QmdH1Vu79p2NcZLFbHxzJnLuUHJiMZnBeT7SNpLaqK7k9X```

> View this credential's data using an <a href="https://ipfs.io/ipfs/QmdH1Vu79p2NcZLFbHxzJnLuUHJiMZnBeT7SNpLaqK7k9X" target="_blank">online gateway</a>.


</TabItem>
</Tabs>

:::info

The schema used in this demo was built using the Privado ID Schema Builder and is available on [<ins>the Privado ID Schema Explorer</ins>](https://tools.privado.id/schemas/1fa99457-b2ae-4884-ae12-d658bd6abf69). Learn more about creating new schemas from [<ins>the Schema Builder UI guide</ins>](/docs/issuer/schema-builder/).

:::

### Generate the credential

With the new schema in hand, the Issuer can generate a credential.

1. Navigate to <a href="https://issuer-demo.privado.id/">the Issuer Node UI testing environment</a>.

   :::warning

   Only use this publicly available Issuer Node for testing purposes. Do not submit personal or sensitive data. All data is deleted every 48 hours.

   :::

2. Next, import the schema. 

    2.1 Click on **Import Schema** and paste the schema's IPFS address `ipfs://QmTSwnuCB9grYMB2z5EKXDagfChurK5MiMCS6efrRbsyVX`:

       <div align="center">
           <img width="100%" src={useBaseUrl("img/quick-start-demo/import-schema.png")}></img>
       </div>

    2.2 Preview the schema and then Import it.

3. Next, click on **Issue Credential** in the top right-hand corner. Choose **Credential Link** on the next page and your schema on the dropdown menu ("POAP01", in our case). For this credential, we are providing a proof of attendance at an event in Paris:

<div align="center">
    <img width="500" src={useBaseUrl("img/quick-start-demo/create-credential.png")}></img>
</div>

4. Click on **Create Credential Link** to be presented with links and a QR code configured for these links to claim the credential. The QR code can be scanned directly with supporting mobile apps, e.g. the Privado Mobile Wallet app.

    :::info

    Two link types are created to provide access to the credential:
    - Mobile Wallet apps such as the Privado ID Mobile App and other supported mobile wallets support Deep Link
    - The Privado ID Web Wallet and other Mobile Wallet apps [<ins> support the Universal Link</ins>](/docs/wallet/universal-links.md)

    :::

    <div align="center">
    <img width="500" src={useBaseUrl("img/quick-start-demo/qr.png")}></img>
    </div>

## Fetch the newly created credential

Next, you will take the second role in this tutorial: the ID Holder. You can either use the Web Wallet in the browser or the Mobile Wallet to accept the credential via the link or the QR code generated by the Issuer in the previous step.

:::note

To sync the identity and its associated credentials between the Privado ID Web Wallet and the Privado ID  Mobile Wallet, the user must log in with the same crypto wallet account on both platforms. Once you claim a credential on one platform, it will then be visible on the other.

:::

To fetch the credential:

<Tabs>
<TabItem value="Web Wallet">

1. Click the Universal link, which will take you to the Web Wallet. Click **Sign In** and connect your crypto wallet such as MetaMask. Click **Add to my wallet**. This should add the credential to your wallet.


<div align="center">
    <img src={useBaseUrl("img/quick-start-demo/web-wallet.png")}></img>
</div>
</TabItem>

<TabItem value="Mobile Wallet">

1. Scan the QR code. Click **Sign In**. This should authenticate and add the credential to the Wallet.

<div align="center">
    <img src={useBaseUrl("img/quick-start-demo/wallet-app.png")}></img>
</div>
</TabItem>
</Tabs>


2. Click on **Manage your credentials** to view and manage the credential in the Wallet.

<div align="center">
    <img  src={useBaseUrl("img/quick-start-demo/web-wallet-2.png")}></img>
</div>

## Verify the ID holder credential

Next, you will take the third role in this tutorial: the Verifier. This might be an organization that needs to verify some details of a person's credentials. In our use case, this organization wants to verify whether the Identity Holder actually attended our made-up Paris event.

To verify the credential:

1. Visit the [Query Builder website](https://tools.privado.id/query-builder/). The [Query Builder](/docs/verifier/query-builder/) is a tool designed to simplify the creation of verification queries.

<div align="center">
    <img width="600" src={useBaseUrl("img/quick-start-demo/verifier-home.png")}></img>
</div>

2. Define the query. We will use the existing JSON-LD URL: `ipfs://QmdH1Vu79p2NcZLFbHxzJnLuUHJiMZnBeT7SNpLaqK7k9X`. The query should look like this:

<div align="center">
    <img width="600" src={useBaseUrl("img/quick-start-demo/verifier-query-1.png")}></img>
</div>

3. Click **Create Query**. Now click the **Test query** button which will take you to the Privado ID Web Wallet:

<div align="center">
    <img width="600" src={useBaseUrl("img/quick-start-demo/verifier-query-2.png")}></img>
</div>

4. Click **Sign in** and connect your crypto wallet. As you have already claimed the credential, it shows as 'claimed'. Click **Verify**, to initiate the process of generating the proof.

<div align="center">
    <img width="900" src={useBaseUrl("img/quick-start-demo/web-wallet-verification.png")}></img>
</div>

5. Finally, the proof is generated and sent to the Verifier. The Verifier will then check the revocation status and any additional information to validate the proof. You will receive the following response on the Query Builder website:
<div align="center">
    <img width="600" src={useBaseUrl("img/quick-start-demo/verifier-validation.png")}></img>
</div>

Alternatively, you can also use the Privado ID Wallet app to verify.
After Step 3, once you are redirected to Web Wallet, click on **Continue via app**,
this should present a QR code. Open the Privado ID Wallet App and scan the QR code.
Click on **Verify**
<div align="center">
    <img width="900" src={useBaseUrl("img/quick-start-demo/wallet-app-verification.png")}></img>
</div>

<br></br>

This quick-start guide demonstrates Privado ID’s basic functionalities through a POAP use case, covering wallet setup, credential issuance, retrieval, and verification. This example requires the user to participate in all three roles to demonstrate Privado ID's comprehensive suite of Self-Sovereign Identity (SSI) tools for managing decentralized identity and verifiable credentials. In real-world uses cases, a single entity would typically fit just one of these roles.

