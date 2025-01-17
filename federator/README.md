# Federator
Presents the event and necesary information to validate it on the other network
The federator is an off-chain process which performs voting actions to validate transactions between a Mainchain (source) and a Sidechain (target) network. These transactions are obtained from the Bridge contract on the Mainchain using event logs and voted in the Sidechain through a Federation contract. Once all required signers (federators) vote for a transaction the MultiSig contract starts the process to release the funds on the Sidechain.

## Config

Go to /bridge/truffle-config.js and set the correct mnemonic or private key for the deploy.

Go to /bridge and deploy using `truffle migrate --reset --network <network name>` this will deploy the contracts and create a json file with the addresses of the contracts

Go to /federator copy `config.sample.js` file and rename it to `config.js` set mainchain and sidechain to point to the json file created in the previous step. Set the `privateKey` property to be the private key of the member of the Federation contract. The members of the federation are controled by the MultiSig contract, same that is owner of the Bridge and AllowedTokens contracts.

## Usage
Start the service running `npm start` which will start a single federator. Check the logs to see that everything is working properly.

## Test
You can run an integration test with `node transferTest.js` and unit tests using `npm test`. The integration test will use a preconfigured private key (from `config.js`) which is assumed to be the only member of the Federation contract.
e
In order to test with multiple federators, ensure they're added as members of the Federation contract and pass their private keys as a comma separated string for both chains as arguments of the integration test script. For instance:

`node transferTest.js "privKeyM1, privKeyM2, privKeyMN" "privKeyS1, privKeyS2, privKeySN"`

