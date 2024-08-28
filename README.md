# Nillion-Verifier
Become a Nillion Verifier

We’re thrilled to unveil the Nillion Verifier. As a verifier, you will ensure data integrity across the network, playing a crucial role in maintaining security and preparing for mainnet launch.

Early verifiers will have the opportunity to be acknowledged for their contributions, setting themselves apart in the community.

Run a Verifier:
- Go to https://verifier.nillion.com and click on verifier

- Connect your account and request faucet here : https://faucet.testnet.nillion.com/

-  Installing Docker:

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y


- Pull the image from the Nillion repo in Docker Hub:

docker pull nillion/retailtoken-accuser:v1.0.0


- Initialising the accuser:

mkdir -p nillion/accuser

AND

docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 initialise
 
[after run, the pubkey and the accuser address appear, paste on the website]

- Fund the accuser

Claim faucet using the address accuser

- Running the accuser

YOU MUST WAIT 30-60 MINUTES TO CONTINUE WITH THE STEPS BELOW.


docker run -v ./nillion/accuser:/var/tmp nillion/retailtoken-accuser:v1.0.0 accuse --rpc-endpoint "http://65.109.222.111:26657" --block-start 5052768


[wait 30 minutes first, before running above, make sure your accuser account have a faucet]

backup wallet accuser:

cat ~/nillion/accuser/credentials.json


[Later it will appear that the priv, pub, address]

DONE

Source : https://x.com/nillionnetwork/status/1828448794528100696
