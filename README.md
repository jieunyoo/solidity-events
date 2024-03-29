# Solidity event emission

## Initial version
- See first contract with events on ropsten test net at: [etherscan](https://ropsten.etherscan.io/address/0x6c6Bd21c0F6b2a535F45B117f9dB1Bc843457618)
- This contract was deployed via `yarn run ts-node --files scripts/events.ts`


### Block: 12496608
- contract creation
- the contract is at: 0x6c6Bd21c0F6b2a535F45B117f9dB1Bc843457618
- the deployer of the contract is: 0x9f9e1b02f25fe6308c7b57e84d49d4386bb0da42

### Block: 12496609
- 0x9f9e1b02f25fe6308c7b57e84d49d4386bb0da42 gave the right to vote to 0x460f6898d317a86537E075D377125bA2509841a4
- this is seen in the log where the second topic is the address that got the right to vote.
```
{
  log: {
    blockNumber: 12496609,
    blockHash: '0xea8567e22d70993b7ce04b9ff98236542a70cf3ec6ff81439f87825f411b5974',
    transactionIndex: 4,
    removed: false,
    address: '0x6c6Bd21c0F6b2a535F45B117f9dB1Bc843457618',
    data: '0x',
    topics: [
      '0x668b14b635e60c984edc522ab57ecf4f7df5f95e912da87692905dc5aa111487',
      '0x0000000000000000000000004a5c7b7cd0f374ce4a9f1ee00f9a331dbf4c3139'
    ],
    transactionHash: '0xbc200bd9e27b64ae678782710bd94d9441395ab1c1bfa7c0d4780078fb06849e',
    logIndex: 8
  }
}
```

### Block: 12496611
- 0x9f9e1b02f25fe6308c7b57e84d49d4386bb0da42 gave the right to vote to 0x460f6898d317a86537E075D377125bA2509841a4

### Block: 12496612
- 0x9f9e1b02f25fe6308c7b57e84d49d4386bb0da42 gave the right to vote to 0x9DD99C23d8bC78bCb0a7C8914415B9b63E7EA99e
 
### Block: 12496614
- 0x9f9e1b02f25fe6308c7b57e84d49d4386bb0da42 gave the right to vote to 0xE96CddC312433893E1001A045E448FFD789e6327

### Block: 12496617
- 0x4a5c7b7cd0f374ce4a9f1ee00f9a331dbf4c3139 voted
- The event "Voted" has two indexed topics (indexed voter, indexed proposal), and two unindexed topics (weight and proposalVotes).
```
 event Voted(
        address indexed voter,
        uint256 indexed proposal,
        uint256 weight,
        uint256 proposalVotes
    );
```
- We can see the address of the voter in topic 1, and the indexed proposal in topic 2. 
- The data shows the weight and proposalVotes. This voter had not been delegated any votes, so its weight is 1. Since only person has voted so far, the number of proposalVotes is 1.

```
Address
0x6c6bd21c0f6b2a535f45b117f9db1bc843457618
Topics
0 0xc32b42768a47a585121e9b8d7a2ab9d3f34c326a192dee11ee1732e3d18313f3
1 0x0000000000000000000000004a5c7b7cd0f374ce4a9f1ee00f9a331dbf4c3139
2 0x0000000000000000000000000000000000000000000000000000000000000000
Data
0000000000000000000000000000000000000000000000000000000000000001
0000000000000000000000000000000000000000000000000000000000000001
```

### Block: 12496620
- 0x460f6898d317a86537e075d377125ba2509841a4 delegated its vote 
- 0x460f6898d317a86537e075d377125ba2509841a4 gave its vote to 0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e. The address of 0x460f6898d317a86537e075d377125ba2509841a4 is given as topic 1, and 0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e is given as topic 2.
``` 
    event Delegated(
        address indexed voter,
        address indexed finalDelegate,
        uint256 finalWeight,
        bool voted,
        uint256 proposal,
        uint256 proposalVotes
    );
```

- from the log:
```
{
  log: {
    blockNumber: 12496620,
    blockHash: '0x0fc38355aede42dcf074f051acb424684c1d758e21d079269cec3f3ce797dd15',
    transactionIndex: 8,
    removed: false,
    address: '0x6c6Bd21c0F6b2a535F45B117f9dB1Bc843457618',
    data: '0x0000000000000000000000000000000000000000000000000000000000000002000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000',
    topics: [
      '0x924db9883c33f3359e4b041d9c609ff4ea81d6f7eb250e281131c71872327341',
      '0x000000000000000000000000460f6898d317a86537e075d377125ba2509841a4',
      '0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e'
    ],
    transactionHash: '0xba8c801f7fb502fde7c15af936c163f49eac43ef3bfcbad4472c5492960db6ba',
    logIndex: 6
  }
}
```
- from etherscan
```
Address
0x6c6bd21c0f6b2a535f45b117f9db1bc843457618
Topics
0 0x924db9883c33f3359e4b041d9c609ff4ea81d6f7eb250e281131c71872327341
1 0x000000000000000000000000460f6898d317a86537e075d377125ba2509841a4
2 0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e
Data
0000000000000000000000000000000000000000000000000000000000000002
0000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000000
0000000000000000000000000000000000000000000000000000000000000000
```

### Block: 12496623
-  0x9dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e voted
-  earlier, 0x9dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e had gotten a vote delegated to it
-  here we see that 0x9dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e (topic 1) voted for proposal 0 (topic 2)
-  in the data section, we see weight = 2, and proposalVotes = 3. Since 0x9dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e had gotten a vote delegated to it, the weight is 2 (thus reflecting the delegated vote). Also, since we also had another vote in block 12496617, and that vote had a weight of 1, now in total, we have 3 proposalVotes.

```
{
  log: {
    blockNumber: 12496623,
    blockHash: '0x46418ddc99117e228affa71f46557c9f2f133dc32acb960c5ed7a81286d45dfb',
    transactionIndex: 5,
    removed: false,
    address: '0x6c6Bd21c0F6b2a535F45B117f9dB1Bc843457618',
    data: '0x00000000000000000000000000000000000000000000000000000000000000020000000000000000000000000000000000000000000000000000000000000003',
    topics: [
      '0xc32b42768a47a585121e9b8d7a2ab9d3f34c326a192dee11ee1732e3d18313f3',
      '0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e',
      '0x0000000000000000000000000000000000000000000000000000000000000000'
    ],
    transactionHash: '0x3bf02f5f1a4a0aded1295752486597e01ffc09dcab7c320a5c61f778787667b5',
    logIndex: 5
  }
}
```
```
Address
0x6c6bd21c0f6b2a535f45b117f9db1bc843457618
Topics
0 0xc32b42768a47a585121e9b8d7a2ab9d3f34c326a192dee11ee1732e3d18313f3
1 0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e
2 0x0000000000000000000000000000000000000000000000000000000000000000
Data
0000000000000000000000000000000000000000000000000000000000000002
0000000000000000000000000000000000000000000000000000000000000003
```

### Block: 12496627
- 0xe96cddc312433893e1001a045e448ffd789e6327 delegated its vote to 0x0000000000000000000000009dd99c23d8bc78bcb0a7c8914415b9b63e7ea99e


## Second version 
- A new version that logs the winner each time someone votes is located at ropsten test net [here](https://ropsten.etherscan.io/address/0xf973bd09bBc75296f084A4277aA4d8dDc5BF2B62).
- This was deployed by `yarn run ts-ndoe --files scripts/simpleEvents.ts`
- As seen [here](https://ropsten.etherscan.io/tx/0x8bb71803b0b85a854983769a1ba4b1e43064a7126eb435e8cfa80d31dd3180d6#eventlog), now there are two log entries - one for the Voter and one for the Winner.

