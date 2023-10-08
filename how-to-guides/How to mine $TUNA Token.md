# Setting Up a Cardano Proof-of-Work (PoW) Node for FORTUNA Token ($TUNA)

This guide outlines the steps to set up a Cardano Proof-of-Work (PoW) node for the FORTUNA token, also known as $TUNA, using Aiken Fortuna, Demeter, Kupo, and Ogmios.

## Step 1: Clone the Aiken Fortuna Project

To get started, clone the Aiken Fortuna project from its GitHub repository:

```
git clone https://github.com/aiken-lang/fortuna
```

You will need the following requirements:

- **Deno:** If you don't have Deno installed, you can follow the installation instructions [here](https://deno.land/#installation).
- **Kupo and Ogmios:** These will be set up using Demeter in the following steps. You can install them separately, but using Demeter is the easiest way to get up and running quickly.

## Step 2: Set Up Demeter

![DemeterLogo](https://github.com/jaysnel/technical-writing/assets/23262423/3da0d842-f780-4a21-9ac4-44f93861ce3d)


1. Visit the Demeter website and click on **"Start For Free"** to create an account.
2. Follow the account creation process and click **"New Project"** to get started.
   - If you're a first-time user, you'll receive DCU (Demeter Compute Units) for free, which is sufficient for the initial setup.
   - If you already have an account, log in and click **"New Project."**
3. Provide a name and description for your project, and create an organization if you haven't already.
4. Choose the available cluster (e.g., US Central) and click **"Create Project."** Currently, this is the only cluster you can choose.

## Step 3: Configure Kupo and Ogmios in Demeter

1. After your project is created, navigate to the **"Extensions"** section.
2. Click on **"Ogmios"** and select **"Mainnet version 5.6.0"** to connect it.
3. Click the right arrow and enable **"Expose Http Port."** This URL will be needed for your `.env` file.
4. Return to the **"Extensions"** section and click on **"Kupo."**
5. Select **"Mainnet version 2.4.0"** to connect it. You will have 2 options, one to PRUNE UTXO and one to not (I have found using NO works better).
6. Similar to Ogmios, enable **"Expose Http Port."** Save this URL for your `.env` file.

## Step 4: Configure Your Project

1. With Demeter set up, return to your Aiken Fortuna project directory.
2. Create a `.env` file in the root of your project.
3. Add the following lines to your `.env` file, replacing `<EXPORTED URL>` with the respective URLs obtained from Demeter:

```
KUPO_URL="https://<EXPORTED URL>"
OGMIOS_URL="wss://<EXPORTED URL>"
```

# Step 5: Running the Project

To run the project, open a terminal and execute the following commands:

```
deno task cli init
deno task cli address
```

`deno task cli init`: This command creates your miner wallet and adds its seed phrase to your `seed.txt` file.

`deno task cli address`: This command retrieves your address and checks your current amount of ADA and TUNA tokens.

**Ensure that you fund the address generated with ADA for transactions before mining. You will need this for transaction fees once you mine a token.**

- To begin mining, run the following command:

```
deno task cli mine
```

You should see something similar to the following:

![tuna-code-running](https://github.com/jaysnel/technical-writing/assets/23262423/5c1d46da-e2fc-4f75-b497-36d9ed5907de)


If you run into issues, visit the [issues](https://github.com/aiken-lang/fortuna/issues) section of the repository. Common issues and their potential fixes are covered there.

Remember to replace placeholders `<EXPORTED URL>` with the actual URLs you obtained during the setup process.

This guide should help users set up a Cardano PoW node for the FORTUNA token using the Aiken Fortuna project and Demeter.
