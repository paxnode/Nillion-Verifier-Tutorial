
```markdown
# 🛡️ Nillion Verifier Setup Guide

## 🌐 Introduction

Welcome to the **Nillion Verifier Setup Guide**. By becoming a Nillion Verifier, you play a pivotal role in maintaining the integrity and security of the Nillion network, particularly as we edge closer to the mainnet launch. Early participants will be recognized for their contributions, distinguishing themselves within the community.

This guide will take you through the steps required to run a Nillion Verifier, from initial setup to ensuring your verifier is running smoothly.

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following:

- A computer running **Ubuntu 20.04** or later or vps
- A stable internet connection.
- Basic familiarity with the terminal and Docker.

---

## 🚀 Step 1: Access the Verifier Portal

1. Navigate to the [**Nillion Verifier Portal**](https://verifier.nillion.com).
2. Click on the **Verifier** option.
3. Connect your account by following the on-screen instructions.
4. To begin, request a faucet from [**Nillion Testnet Faucet**](https://faucet.testnet.nillion.com/).

Ensure your account is successfully connected and funded before proceeding to the next steps.

---

## 🧰 Step 2: Install Docker

Docker is essential for running the Nillion Verifier. Install Docker on your Ubuntu machine using the command below:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && \
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && \
sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

- **Explanation**: This command installs Docker by adding the official Docker repository to your system, updating your package index, and installing the Docker engine and related components.

Once the installation is complete, verify the Docker installation:

```bash
docker --version
```

---

## 🐳 Step 3: Pull the Nillion Docker Image

Pull the latest Nillion accuser image from Docker Hub to your local environment:

```bash
docker pull nillion/retailtoken-accuser:v1.0.0
```

- **Explanation**: This pulls the `retailtoken-accuser:v1.0.0` image from the official Nillion Docker repository, ensuring you have the latest version required to run the verifier.

---

## 🏗️ Step 4: Initialize the Accuser

Before you can run the accuser, it must be initialized. Start by creating the necessary directories and then initializing the accuser:

```bash
mkdir -p ~/nillion/accuser

docker run -v ~/nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 initialise
```

- **Explanation**: The `mkdir -p` command creates the required directory structure. The Docker command initializes the accuser, generating a public key and an accuser address. Make sure to store these securely as they will be required for further steps.

After initialization, the `pubkey` and `accuser address` will be displayed. Copy these and paste them into the appropriate fields on the verifier portal.

---

## 💰 Step 5: Fund the Accuser

With your accuser address in hand, claim a faucet from the [**Nillion Testnet Faucet**](https://faucet.testnet.nillion.com/). Ensure your accuser is adequately funded before proceeding.

---

## ⏳ Step 6: Wait Period

**Important**: Before running the accuser, it is crucial to allow a **30-60 minute** wait period after funding. This ensures that all processes are synchronized and that your accuser is fully prepared to interact with the network.

---

## ⚙️ Step 7: Running the Accuser

After the wait period, you can start the accuser with the following command:

```bash
docker run -v ~/nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "http://65.109.222.111:26657" --block-start 5052768
```

- **Explanation**: This command launches the accuser and connects it to the Nillion network. Ensure that your accuser account has sufficient funds from the faucet before executing this command.

Monitor the output to ensure the accuser is running correctly.

---

## 🔒 Step 8: Backup Your Accuser Wallet

Securing your accuser wallet is critical. Backup your wallet credentials by running:

```bash
cat ~/nillion/accuser/credentials.json
```

This command will display your `private key`, `public key`, and `address`. **Store this information securely**—it is essential for recovering your verifier if needed.

---

## 🎉 Conclusion

Congratulations! You have successfully set up and started your Nillion Verifier. By doing so, you have contributed to the security and robustness of the Nillion network as it approaches its mainnet launch.

Stay active in the community, and make sure to follow further updates and instructions as the project evolves.

---

## 📚 Resources

For additional information, refer to the following resources:
- [Nillion Verifier Portal](https://verifier.nillion.com)
- [Nillion Testnet Faucet](https://faucet.testnet.nillion.com/)
- [Official Nillion Network Post](https://x.com/nillionnetwork/status/1828448794528100696)
- [My Twitter](https://x.com/PaxNode)

---

Thank you for being an integral part of the Nillion community!
```
