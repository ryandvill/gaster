# Gaster - Ethereum GAS stats

The utility to get info of transactions for the specified smart contract.
The output can be used to analyze gas usage.
Supports smart contracts deployed with Zeppelin OS.

## Setup
* Install node package manager [npm](https://nodejs.org/en/download/)

* Install project's dependencies
```bash
npm install
```

## Using ethgasstats CLI
### Command Line
```bash
$ gaster <address> <options>
```
*  `<address>`: *[string]* Smart contract address

### Options:

*  `-s`, `--startblock`: *[number, optional]* Start block number. Default: smart contract genesis block.
*  `-e`, `--endblock`: *[number, optional]* End block number. Default: smart contract last transaction block.
*  `-n`, `--net`: *[boolean, optional]* Network on which specified smart contract is deployed.
*  `-a`,`--abi`: *[string, optional]* Path to *.json file with Ethereum smart contracts' ABIs in appropriate format.
*  `-r`,`--recursive`: *[boolean, optional]* Search transactions recursively through the hierarchy of smart contracts.

### ABI JSON Format:

Acceptable formats:
*  You can just pass abi as it is
*  You can pass array of objects
```bash
[
    {
        "address": address1, // address of smart contract
        "abi": abi1, // ABI of smart contract
        "alias": alias // Name of smart contract, optional
    },
    {
        "address": address2,
        "abi": abi2
    },
    ...
]
    
```

### Output:

Transaction information is saved in CSV format.
Columns:
*  `address` - address of smart contract (receiving party of the transaction)
*  `blockNumber` - number of block in which the transaction was recorded
*  `gasUsed` - the exact units of gas that was used for the transaction
*  `gasPrice` - cost per unit of gas specified for the transaction
*  `gas` - maximum amount of gas provided for the transaction
*  `from` - the sending party of the transaction
*  `input` - input data of the transaction decoded with ABI of smart contract
*  `hash` - hash of the transaction
*  `timeStamp` - timestamp when the transaction was mined
*  `parameters` - transaction function parameters
*  `features` - parameters' features

### Example:
```bash
gaster 0x4Ca389fAAd549aDd7124f2B215266cE162D964e7 --endblock 6050576 --net ropsten
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)



