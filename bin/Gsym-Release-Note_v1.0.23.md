# Gsym Release Note



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