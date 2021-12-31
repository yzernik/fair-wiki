# fair-wiki
A wiki that is fair and trustless

### rules

fair-wiki has clear rules about how pages are edited:

- The wiki starts without any pages.

- To create a new page, a user must spend bitcoin (any amount) into a contract associated with the new page.

- To make an edit to an existing page, a user must spend a larger amount than the previous editor in that page's contract. When an edit happens, the previous editor gets back whatever amount of bitcoin they have locked up in the contract.

- The amount of bitcoin required to edit a page can only increase over time, because every new edit requires more bitcoin than the previous one.

- Bitcoin that is spent into a page contract is effectively burnt. The editor can get their bitcoin back, but only if another editor spends a larger amount. So the total amount of bitcoin locked up is always increasing.

- Anyone can run their own copy of the wiki. Every page of the wiki can be validated against the Bitcoin blockchain based on the page's hash and the current state of the contract.

### motivation

- Wikipedia does not have any good way to resolve disputes. There will always be differences of opinion about what should be on a page.

- Governance of a public wiki will always be politicized and unfair.

- Bitcoin is the only source of truth that everyone can agree on.

- The only fair method to resolve disputes is to give preference to the person who is willing to spend more money.

### implementation

- The smart contract can be implemented using `OP_CHECKTEMPLATEVERIFY` (BIP119)[https://github.com/bitcoin/bips/blob/master/bip-0119.mediawiki].

- The original wiki page creation would require a new Bitcoin transaction using `OP_CHECKTEMPLATEVERIFY`.

- Every subsequent page edit would spend the funds in the contract and create a new contract. The funds in the contract would be returned to the previous editor using a non-interactive channel.
