# Gsym Release Note

## gsym v1.4.1

##### 1. Lastest version
- Implemented Oracle revolution

## gsym v1.3.24

##### 1. Added SCT31
- Implemented a new smart contract extending the functionality of SCT30, designed for managing domain name services.

##### 2. Integrated Name Service
- Applied SCT31 to enable domain registration, resolution, and management without using external Solidity smart contracts.

##### 3. Hierarchy-Based Domains 
- Introduced a hierarchical structure consisting of groups and user IDs within a single namespace.

##### 4. Domain-to-ID Mapping
- Enabled seamless resolution of domain names to blockchain account IDs using sct.getResolveDomain.



## gym v1.3.4

##### 1. Fixed some bugs
* Fixed bug of reward processing
* Fixed bug of logging



## gym v1.3.3

##### 1. Adding built-in configuration for the merge fork on the Symverse mainnet
* Apply for Ethereum Smart Contract Compatibility
* Added Constantinople block number 70824500 in chain configuration 

##### 2. Modified APIs
* Added TotalCoinSupply API
* Modified dumpBlock API

##### 3. Fixed some bugs
* Fixed bug of reward processing
* Fixed bug of block repairing

##### 4. Added new pre-defined network
* Torocus-net: Network ID 101

## gsym v1.0.36

##### 1. Added SCT22, 50, 51

- SCT22: Extended contract from SCT20 for setting token delegation level
- SCT50: Vote contract, managing poll contract
- SCT51: Poll contract for voting

##### 2. Changed SCT symbol length from fixed 3 to 3~10 characters

- SCT symbol length can be 3 to 10 characters. (It was fixed 3 characters in previous version)
- Added SctFork2 block number 16704500 in chain configuration

##### 3. Added multi-sending transaction

- Added new transaction type 3 for multi-sending transaction
- This allows SYM transfer from one account to several accounts with one transaction
- Gas is discounted compared to sending SYM in each transaction

##### 4. Modified APIs

- Added APIs related to SCT50 and SCT51(voting)
- Modifed APIs related to Oracle block
- Modified estimateGas API

##### 5. Fixed some bugs

- Fixed abnormal consensus failure
- Fixed bug of transaction validation in transaction pool
- Fixed bug of logging
- Fixed bug of some APIs

##### 6. Added new pre-defined network

- Ienvu-net: Network ID 100
- Stealth-net: Network ID 200



## gsym v1.0.23

##### 1. Changed gas parameter and price

- base_gas
  : sct creation: 8,000,000 (0x7A1200)
  : normal tx & sct use: 49,000 (0xBF68)
- byte_gas
  : zero: 40
  : non-zero: 680
- contract_op_gas(sct gas table)
  : no changed
- gas_price
  : 100Ghug

gas calculation: https://github.com/symverse-lab/Document/wiki/Transaction

sct gas table: https://github.com/symverse-lab/Document/wiki/SCT#sct-function-and-gas

##### 2. Added type of CA in citizen role

- TrustedCA, PublicCA, AnominousCA(default)
##### 3. Added balance recovery feature (Trusted CA only)

##### 4. Changed the count of workNodes of transaction from 3 to 1

##### 5. Changed the consensus aggregation calculation

- previous: "Warrant A 1/2 and Total 2/3", new: "Total 2/3"
##### 6. Added Oracle parameter read API



## gsym v1.0.20

##### 1. Fix bug in processing sct

##### 2. Fix bug in reward mechanism: producer cost calculation

##### 3. Add fork code(SctFork1Block) due to fix bug of sct: 1666300 block

##### 4. Change supporting gas price from 1Ghug to 25Ghug

##### 5. Change pon and reward parameters to be configurable

##### 6. Change nonce management in oracle pool

##### 7. Change api: getDeposit

##### 8. Change default sync mode from "fast" to "full"

