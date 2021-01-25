# On-chain voting

## BUILD Governance

All BUILD-related contracts are controlled by the governance contract which is itself controlled by the BUILD token holders.

* **Governance contract** [0x5A6eBeB61A80B2a2a5e0B4D893D731358d888583](https://etherscan.io/address/0x5A6eBeB61A80B2a2a5e0B4D893D731358d888583)

Modules controlled by the governance:

* [bCRED token](https://etherscan.io/token/0xB7412E57767EC30a76a4461d408d78b36688409C) \(minting\)
* [BUILD token](https://etherscan.io/token/0x6e36556b3ee5aa28def2a8ec3dae30ec2b208739) \(minting\)
* [BUILD treasury](https://etherscan.io/address/0xdf9a17a73308416f555783239573913afb77fa8a)
* [Basis Gold BSG fund](https://etherscan.io/address/0x84a7559dbe02256d6d6f1b184517d65780c83b9b)
* [Basis Gold boardroom](0xEEEeFF73060E9F36a270ad8A843f7D719cE2F79f) & treasury

### Parameters

Voting parameters can be changed in the future. As of Jan 25, 2021, they are as follows:

* Min balance to submit new proposal: 100 BUILD
* Quorum required to pass a proposal: 5,000 BUILD
* Votig period: 24 hours
* Execution delay \(after voting priod ends\): 24 hours \(so 2 days since it's first submitted\)

### Pre-proposal

Before submitting a proposal, start a discussion in the \#governance channel in Discord in the relevant Discord server.

For example, if you want to change an epoch period of Basis Gold, start a discussion in \#governance channel in Basis Gold Discord.

If you want to allocate a budget to the homepage of build.finance \(unrelated to Basis Gold\), post a message in \#governance channel in BUILD Discord \(not in Basis Gold\).

### Proposal

1\) After you get general feedback, assuming you mostly positive sentiment, you need to find a developer to code up your proposal. The developer can decide on how much to charge for coding up this proposal which will be paid by the treasury directly from the code of the proposal.

2\) After the proposal contract is deployed, someone with enough BUILD needs to submit a proposal transaction to the governance contract. After this point, the proposal is available for voting. A moderator will announce it in the \#annoucements channel along with the instructions on how to vote.

### Voting

1\) To vote on the proposal, you first need to approve the [governance contract](https://etherscan.io/address/0x5A6eBeB61A80B2a2a5e0B4D893D731358d888583) as a spender of your BUILD. This is required since the gov contract will lock your BUILD tokens for the duration of the voting period to prevent abuse.

To approve it, go to the [BUILD token](https://etherscan.io/token/0x6e36556b3ee5aa28def2a8ec3dae30ec2b208739#writeContract) and execute the `approve` function with the following values:

* Spender: `0x5A6eBeB61A80B2a2a5e0B4D893D731358d888583` \(gov contract\)
* Amount: `100000000000000000000000000`

2\) Go to the [governance contract](https://etherscan.io/address/0x5A6eBeB61A80B2a2a5e0B4D893D731358d888583) and execute `vote` function with `propsalId` as announced on Discord and `support` set to either `true` or `false`

### Post-voting

If the proposal passes, it will become executable after the execution period. The execution must be called by someone.

If it fails, nothing will happen.

To withdraw your funds after the proposal period ends, execute the `withdraw` function on the gov contract.

