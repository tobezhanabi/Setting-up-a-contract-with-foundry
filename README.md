# Setting-up-a-contract-with-foundry
## A simple guide


1. forge init(to start a project with all you need)
2. When you need an interface from chainlink here is how to install it from smartcontractkit brownie
   --
`forge install smartcontractkit/chainlink-brownie-contracts@0.6.1 --no-commit`
---
if you face submodel 128 error do this
 - switch to faster network and then 
 - `git config --global http.postBuffer 524288000` and then
 - `git gc --aggressive`

example of interfaces will be aggregatorV3Interfaces that help connect to price feeds from chainlink when you pass the address, more reading here; https://docs.chain.link/data-feeds/price-feeds/addresses?network=ethereum&page=1

After installing go to foundry.toml and remap
like so
remappings = ['@chainlink/contracts/=lib/chainlink-brownie-contracts/contracts']

2. Write test and scripts. The test should work on local node, forked testnet and forked mainnet
When writting a script you will need to 
`import {Script} from "forge-std/Script.sol";`
It is inside the script.sol that we get to use
```
 vm.startBroadcast();
// our contract goes here
    vm.stopBroadcast();
```
---
#### These are cheatcodes of foundry
find more at https://book.getfoundry.sh/forge/cheatcodes.


When you create an .env you have to type source .env in the terminal

To access the most recently deployed contract in yr vscode, you will need to install foundry devops; `forge install ChainAccelOrg/foundry-devops --no-commit` and then import `import {DevOpsTools} from "foundry-devops/src/DevOpsTools.sol";`

Testing can be hard but we can use this command to see which line we havent tested
`forge coverage --report debug > coverage.txt`

SCRIPTING
We use solidity to run script in foundry, you import as said above and then put this in your terminal to run it
`forge script script/YOurscript.s.sol:TARGETFUNCTION --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast` 
REMEMBER TO REPLAVE THE RIGHT CONTRACT AND FUNCTION
OPENZEEPELIN
forge install OpenZeppelin/openzeppelin-contracts --no-commit
