---
description: >-
  The Association develops and manages standards, registries, libraries, nodes,
  command-line tools and technical documentation
layout: editorial
---

# Products

## Standards

The association maintains so-called **LNPBP standards:** specifications, standards & best practices for Layer 2, 3 solutions (and above) in cases when they do not require soft- or hard-forks on the Bitcoin blockchain level and are not directly related to issues covered in Lightning Network RFCs (BOLTs).

Basically, LNPBPs cover everything that can be anchored to Bitcoin transactions, defines primitives for L2+ solution design and describes complex use cases which can be built from some primitives. This allows such solutions as financial assets, storage, messaging, computing and different forms of secondary markets leveraging Bitcoin security model and Bitcoin as a method of payment/medium of exchange.

Criteria for a LNPBP standard proposal:

* Should not be covered by existing or proposed BIPs
* Should not cause soft- or hard-fork in Bitcoin blockchain (but may depend on soft-forks from an existing BIP proposals)
* Should not distort Bitcoin miner's economic incentives
* Should not pollute Bitcoin blockchain with unnecessary non-transaction related data or have to maintain such pollution as low as possible
* Must not require a utility or security tokens to function (but may enable creation of digital assets or tokenized physical goods)
* Must not depend on non-bitcoin blockchains (but may be applicable to other blockchains)

The current list of standard can be found on a [dedicated website](https://app.gitbook.com/o/-MO35HartFKtUgrkgzLy/s/-Mchj8WVdEa0qze424CG/) or in GitHub repository [here](https://github.com/LNP-BP/LNPBPs). You can use GitHub discussions to:

* [submit](https://github.com/LNP-BP/LNPBPs/discussions/categories/standard-proposals) a new standard proposal
* [discuss](https://github.com/LNP-BP/LNPBPs/discussions/categories/ideas) preliminary ideas about new standards
* [follow announcements](https://github.com/LNP-BP/LNPBPs/discussions/categories/releases) about standard releases
* [write](https://github.com/LNP-BP/LNPBPs/discussions/categories/implementations) about your implementation of one of the standards
* [ask questions](https://github.com/LNP-BP/LNPBPs/discussions/categories/q-a)
* [peer review & audit](https://github.com/LNP-BP/LNPBPs/discussions/categories/peer-review) existing standards

## Registries

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><h3>Data type libraries</h3></td><td>Strict encoding data type libraries used in RGB smart contract development</td></tr><tr><td><h3>AluVM libraries</h3></td><td>Libraries for AluVM virtual machine used in RGB smart contract development</td></tr><tr><td><h3>RGB interfaces</h3></td><td>ABI (application binary interfaces) for RGB schemata (fungible tokens, NFTs etc)</td></tr><tr><td><h3>RGB schemata</h3></td><td>Specific templates for RGB contracts from independent developers</td></tr></tbody></table>

## Libraries

Libraries maintained by the Association can be classified into the following categories:

1. Consensus libraries
2. Standard library
3. Node-related libraries
4. Application-level libraries

The dependencies between these groups are strongly abstracted into four layers, such that underlying group doesn’t know anything about the libraries from the layer above.

### Consensus libraries

These libraries are a part of the ossified client-side-validation consensus and must not be modified except of bugfixing. Usually, consensus-level libraries are named with “Core“ or “Foundation” as a part of their name.

1. Client-side-validation foundation library&#x20;
2. Bitcoin common libraries: implementation of parsing bitcoin data related to bitcoin consensus layer. Currently, there are split in two groups:
   1. Rust bitcoin ecosystem, maintained by Rust bitcoin community (mostly Blockstream members and Andrew Poelstra)
   2. BP Foundation Libraries, maintained by LNP/BP Standards Association, Bitcoin Protocol Working Group. Contain re-implmenetaiton or improvements of the rust-bitcoin libraries
3. Bitcoin client-side-validation, also called “BP Core Lib”. It provides primitives such as deterministic bitcoin commitments (“TapRet”, ”OpRet”) and single-use-seals.

### Standard libraries

Standard library (called RGB Std Lib) provides high-level convenience API for working with RGB data, but does not performs any consensus-level tasks. Any validation and RGB operations must perform without standard library, which enables use of RGB smart contract on embedded devices.

## Nodes

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><h3>BP Node</h3></td><td>Indexes bitcoin blockchain and mempool, connecting to Bitcoin Core and bitcoin P2P network. Drop-in replacement for Electrum Server, providing modern &#x26; fast API supporting monitoring wallet descriptors.</td><td><a href=".gitbook/assets/BP Logo.png">BP Logo.png</a></td></tr><tr><td><h3>LNP Node</h3></td><td>Lightning node implementation made in rust targeting developers. Has extensible architecture, supports plugins, AluVM scripting, Bifrost, Storm, RGB protocols out of the box.</td><td><a href=".gitbook/assets/LNP Logo.png">LNP Logo.png</a></td></tr><tr><td><h3>RGB Node</h3></td><td>Node performing client-side-verification of RGB smart contract and keeping the stash of all known contracts and their state. Provides API for the wallets and lightning node for accessing information about the contracts.</td><td><a href=".gitbook/assets/RGB logo.jpg">RGB logo.jpg</a></td></tr><tr><td><h3>Storm Node</h3></td><td>Runs Storm protocols and provides decentralized messaging, data storage and querying. Works with LNP Node and provides additional revenue for the users running them. Used by RGB and other protocols (like torrent-over-lightning, end-to-end encrypted messaging etc).</td><td><a href=".gitbook/assets/Storm Logo.png">Storm Logo.png</a></td></tr></tbody></table>

## Toolchains

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><h3>LNP/BP tools</h3></td><td>A set of utilities for working with client-side-validated data, single-use-seals, RGB contract data, invoices etc.</td></tr><tr><td><h3>Descriptor Wallet</h3></td><td>Command-line wallet utility made with eponymous library/</td></tr><tr><td><h3>Contractum</h3></td><td>Language and compiler for RGB smart contracts</td></tr><tr><td><h3>Hadron</h3></td><td>Package manager for RGB (the name comes from the RGB-colored quarks confined within hardon particles)</td></tr></tbody></table>

## Documentation

|   |   |   |
| - | - | - |
|   |   |   |
|   |   |   |
|   |   |   |

## Contributions to external projects

LNP/BP Association in 2019-2021 was a [major contributor](https://github.com/rust-bitcoin/rust-bitcoin/graphs/contributors?from=2018-12-26\&to=2022-04-01\&type=c) into [@rust-bitcoin](https://github.com/rust-bitcoin/rust-bitcoin) and other related project.
