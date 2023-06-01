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

The current list of standard can be found on a [dedicated website](http://localhost:5000/o/-MO35HartFKtUgrkgzLy/s/-Mchj8WVdEa0qze424CG/) or in GitHub repository [here](https://github.com/LNP-BP/LNPBPs). You can use GitHub discussions to:

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
   2. BP Foundation Libraries, maintained by LNP/BP Standards Association, Bitcoin Protocol Working Group. Contain re-implementation or improvements of the rust-bitcoin libraries
3. Bitcoin client-side-validation, also called “BP Core Lib”. It provides primitives such as deterministic bitcoin commitments (“TapRet”, ”OpRet”) and single-use-seals.

<table><thead><tr><th width="207">Repo (crate)</th><th width="164">GitHub Org</th><th>Description</th></tr></thead><tbody><tr><td>rust-lnpbp (lnpbp_secp256k1)</td><td>LNP-BP</td><td>Fork of Grin re-implementation of rust-secp256k1-zkp; used for bulletproofs only</td></tr><tr><td>rust-stens (stens)</td><td>Strict-Encoding</td><td>Data encoding used in RGB</td></tr><tr><td>rust-aluvm (aluvm)</td><td>AluVM</td><td>Virtual machine used in RGB</td></tr><tr><td>client_side_validation</td><td>LNP-BP</td><td>Abstract client-side-validation</td></tr><tr><td>bp-foundation</td><td>BP-WG</td><td>Bitcoin primitives (alternative to rust-bitcoin)</td></tr><tr><td>bp-core</td><td>BP-WG</td><td>Client-side-validation for bitcoin protocol</td></tr><tr><td>rgb-core</td><td>RGB-WG</td><td>RGB consensus library</td></tr></tbody></table>

### Standard libraries

Standard libraries provide high-level convenience API for working with bitcoin, lightning & RGB, and do not perform any consensus-level tasks. Any validation and consensus operations must perform without standard libraries.

<table><thead><tr><th width="207">Repo (crate)</th><th width="138">GitHub Org</th><th>Description</th></tr></thead><tbody><tr><td>psbt</td><td>BP-WG</td><td>Implementation of partially-signed bitcoin transactions and operations with them involving signatures, support for client-side-validation etc</td></tr><tr><td>descriptor-wallet</td><td>BP-WG</td><td>Primitives for constructing wallets supporting bitcoin, lightning and RGB protocols</td></tr><tr><td>invoices</td><td>LNP-BP</td><td>Implementation of universal LNP/BP invoices standard</td></tr><tr><td>rust-lnpbp (lnpbp)</td><td>LNP-BP</td><td>Implementation if LNPBP standards for Base64, Bech32, Elgamal encoding and encryption</td></tr><tr><td>lightning_encoding</td><td>LNP-WG</td><td>Encoding for BOLT data used in lightning network</td></tr><tr><td>lnp-core</td><td>LNP-WG</td><td>Implementation of both BOLT and LNPBP standards of lightning network</td></tr><tr><td>storm-core</td><td>Storm-WG</td><td>Implementation of Storm specifications and standards</td></tr><tr><td>rgb-stdlib</td><td>RGB-WG</td><td>Convenience API for working with RGB smart contracts</td></tr></tbody></table>

## Nodes

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-cover data-type="files"></th></tr></thead><tbody><tr><td><h3>BP Node</h3></td><td>Indexes bitcoin blockchain and mempool, connecting to Bitcoin Core and bitcoin P2P network. Drop-in replacement for Electrum Server, providing modern &#x26; fast API supporting monitoring wallet descriptors.</td><td><a href=".gitbook/assets/BP Logo.png">BP Logo.png</a></td></tr><tr><td><h3>LNP Node</h3></td><td>Lightning node implementation made in rust targeting developers. Has extensible architecture, supports plugins, AluVM scripting, Bifrost, Storm, RGB protocols out of the box.</td><td><a href=".gitbook/assets/LNP Logo.png">LNP Logo.png</a></td></tr><tr><td><h3>RGB Node</h3></td><td>Node performing client-side-verification of RGB smart contract and keeping the stash of all known contracts and their state. Provides API for the wallets and lightning node for accessing information about the contracts.</td><td><a href=".gitbook/assets/RGB logo.jpg">RGB logo.jpg</a></td></tr><tr><td><h3>Storm Node</h3></td><td>Runs Storm protocols and provides decentralized messaging, data storage and querying. Works with LNP Node and provides additional revenue for the users running them. Used by RGB and other protocols (like torrent-over-lightning, end-to-end encrypted messaging etc).</td><td><a href=".gitbook/assets/Storm Logo (1).png">Storm Logo (1).png</a></td></tr></tbody></table>

## Toolchains

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><h3>LNP/BP tools</h3></td><td>A set of utilities for working with client-side-validated data, single-use-seals, RGB contract data, invoices etc.</td></tr><tr><td><h3>Descriptor Wallet</h3></td><td>Command-line wallet utility made with eponymous library/</td></tr><tr><td><h3>Contractum</h3></td><td>Language and compiler for RGB smart contracts</td></tr><tr><td><h3>Hadron</h3></td><td>Package manager for RGB (the name comes from the RGB-colored quarks confined within hardon particles)</td></tr></tbody></table>

## Documentation

<table><thead><tr><th width="174.33333333333331">Document</th><th width="184">Description</th><th width="180">Audience</th><th>URL</th></tr></thead><tbody><tr><td>RGB FAQ</td><td>Gives introduction into RGB from a power user perspective</td><td>Most broad</td><td><a href="https://rgbfaq.com">rgbfaq.com</a></td></tr><tr><td>Blackpaper ("whitepaper")</td><td>Systematically explains RGB, its capabilities and most important applications in half-technical terms</td><td>Most broad</td><td><a href="https://docs.lnp-bp.org/blackpaper">blackpaper.rgb.tech</a></td></tr><tr><td>Blueprint ("specification")</td><td>Technical explanation of all RGB internals, more readable than standards</td><td>Schema developers, integrators</td><td><a href="https://docs.lnp-bp.org/blueprint">blueprint.rgb.tech</a></td></tr><tr><td>Code docs</td><td>Documentation for the RGB-related APIs</td><td>RGB maintainers</td><td>docs.rs/&#x3C;crate_name></td></tr><tr><td>LNP-BP Standards</td><td>Formal &#x26; complete standardization of RGB algorithms &#x26; consensus</td><td>Auditors, RGB maintainers</td><td><a href="https://standards.lnp-bp.org">standards.lnp-bp.org</a></td></tr><tr><td>Yellow paper ("formalism")</td><td>Formal mathematical specification on RGB</td><td>Computer scientists, cryptographers</td><td><a href="https://docs.lnp-bp.org/yellowpaper">yellowpaper.rgb.tech</a></td></tr><tr><td>AluVM</td><td>Documentation on AluVM - functional virtual machine used in RGB consensus, node and lightning</td><td>AluVM contributors, auditors, application developers using AluVM</td><td><a href="https://www.aluvm.org">aluvm.org</a></td></tr><tr><td>Strict Encoding</td><td>Documentation on binary encoding used in RGB consensus</td><td>RGB schema (smart contract) developers; application developers using strict encoding</td><td><a href="https://www.strict-encoding.org">strict-encoding.org</a></td></tr><tr><td>Contractum docs</td><td>Documentation on Contrctum languague</td><td>RGB schema (smart contract) developers</td><td><a href="https://www.contractum.org">contractum.org</a></td></tr><tr><td>RGB source code</td><td>Source code for RGB consensus, standard lib and node</td><td>RGB contributors</td><td><a href="https://github.com/RGB-WG">github.com/RGB-WG</a></td></tr></tbody></table>

## Contributions to external projects

LNP/BP Association in 2019-2021 was a [major contributor](https://github.com/rust-bitcoin/rust-bitcoin/graphs/contributors?from=2018-12-26\&to=2022-04-01\&type=c) into [@rust-bitcoin](https://github.com/rust-bitcoin/rust-bitcoin) and other related project.
