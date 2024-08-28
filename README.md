```markdown
# Nillion Verifier Setup Guide

## Become a Nillion Verifier

We’re thrilled to unveil the Nillion Verifier. As a verifier, you will ensure data integrity across the network, playing a crucial role in maintaining security and preparing for the mainnet launch.

Early verifiers will have the opportunity to be acknowledged for their contributions, setting themselves apart in the community.

## Running a Verifier

### 1. Access the Verifier Portal

- Go to [https://verifier.nillion.com](https://verifier.nillion.com) and click on the **Verifier** option.
- Connect your account and request a faucet here: [https://faucet.testnet.nillion.com/](https://faucet.testnet.nillion.com/)

### 2. Installing Docker

To install Docker on your system, run the following command:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && \
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && \
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

### 3. Pull the Nillion Docker Image

To pull the Docker image from the Nillion repository, use the following command:

```bash
docker pull nillion/retailtoken-accuser:v1.0.0
```

### 4. Initializing the Accuser

Create the necessary directories and initialize the accuser by running:

```bash
mkdir -p nillion/accuser

docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 initialise
```

After running the above command, the public key and the accuser address will appear. Copy and paste these into the verifier website.

### 5. Fund the Accuser

Claim faucet using the accuser address you obtained in the previous step.

### 6. Running the Accuser

**IMPORTANT:** You must wait **30-60 minutes** after funding the accuser before proceeding with the following steps.

Once the wait time is over, run the accuser:

```bash
docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "http://65.109.222.111:26657" --block-start 5052768
```

Ensure your accuser account has received the faucet before running the above command.

### 7. Backup Wallet Accuser

To back up your accuser wallet, run:

```bash
cat ~/nillion/accuser/credentials.json
```

This will display the private key, public key, and address. Make sure to store this information securely.

## Conclusion

Once all steps are completed, your Nillion Verifier setup should be successfully running. You have now contributed to maintaining the security of the Nillion network and are prepared for the mainnet launch.

## Source

For more details, visit the official Nillion network post on [X (formerly Twitter)](https://x.com/nillionnetwork/status/1828448794528100696).
```
