# Delphi Project

In ancient Greece, Delphi was where one could meet the Oracle.

## Introduction

Oracle pools have sparked a lot of interest and excitement, and rightly so. However, being a relatively new development, the oracle pool ecosystem remains a bit rough around the edges. As decentralised applications flourish on the Ergo network, more pools will be needed - as well as reliable oracle operators. The next sections list a number of pain points we have identified as well as a proposed approach to alleviate them in order to facilitate adoption of decentralised oracle technology.

## Current challenges

### Technical thresholds

Individuals wanting to contribute resources, as oracle operators, often don't know where to start. Similarly, dapp developers have many things to think about, technicalities of launching an oracle pool shouldn't be one of them.

### Distribution

Pools rely on decentralised oracles to operate but there is currently no system in place to facilitate the distribution of oracle tokens to operators. For instance, the current ERG/USD pool had its tokens distributed to community members that happened to be around at launch time. Perfectly fine for the early days but hard to scale while guaranteeing recruitment of good actors.

### Transparency

Once a pool has recruited it’s oracles, they cannot be changed. It is therefore crucial to know which ones are reliable. There is no system in place to facilitate this.

Some early oracle operators have been disappointed by the returns and shut down their cores. This is partly due to V1 pools being suboptimal, but could also be mitigated by upfront information and statistics informing aspiring operators what to expect in terms of rewards and expenses.

In the future, with more pools running, oracle users will first look for existing pools to rely on instead of spinning their own. There is currently no standard to capture how pools were created or how their oracles were selected. Something a pool user (dapp developers and users) would want to verify.

### Missing features

It is our understanding that some features are worked out at the protocol level but remain to be implemented. Stake slashing is a good example. Also, support for additional data types would open the doors to a wider range of applications.

## Approach

The project seeks to address aforementioned issues by creating an oracle pool launching platform with the following main components:

- A register of known and aspiring oracle operators
- An automated pipeline generating pool-specific oracle-core connectors
- Pool and oracle statistics through on-chain monitoring
- An oracle pool launcher with guided pool configuration and various oracle selection strategies

In addition, the project aims to educate the broader community on oracle pools and what to look for when using products relying on such technology. This goes hand in hand with a longer term objective of the project to advocate for decentralised oracle technology and ensure further development of the stack.

A more detailed breakdown of each component is given below.

### Components

#### Register of oracle operators

Aspiring oracle operators can sign up to appear in a register of oracle operators. This will include address ownership verification and various levels of optional verification.

The resulting register of oracle operators can then be consulted by pool creators looking for operators satisfying their criteria. Oracles already operating within a pool will have their track-record available.

#### Connector pipeline

All pools run the same suite of off-chain tooling except for one component, the connector, which handles  the off-chain data fetching step. The connector is specific to each pool and requires some tweaking of the off-chain tooling source code. We intend to provide an automated pipeline, able to generate custom connectors from a CoinGecko API for instance. The resulting connector would be cross compiled for various platforms and made available to oracle operators.

#### On-chain monitoring

Performance of individual oracle operators as well as pools can be tracked throuhg on-chain monitoring. Oracle stats will feed into the register of oracle operators and provide insight into operator consistency and reliability. Pool stats will track things such as pool health (number of active oracles, posting frequency etc.) and, where possible, check for deviation against the original data source. The latter is a measure to detect synchronized oracle actions within a pool. Another metric of interest is the number of undistributed oracle tokens a pool creator holds. At the end of the day, the intent is to provide security through transparency.

#### Pool launcher

Building on the previous three components there is the pool launcher, a web app assisting in the configuration of a new pool and taking care of the minting and distributing oracle tokens. A number of oracle selection strategies will be available to a pool creator:

- Random selection from the register (with optional filtering criteria)
- Hand picked from the register (or new oracles altogether)
- Waiting for oracles to join the pool

Either way, the selection strategy will be documented and be part of meta data made available for anyone to review when assessing a specific pool.

### Hurdles & pitfalls

#### V2 pools

The team needs to catch up on the latest iteration of oracle pool smart contracts (V2) which introduced new concepts such as oracle compensation through dedicated tokens. There is a possibilty some of the V2 aspects may have been overlooked in our current approach. However, the base principles remaining unchanged, we don't anticipate any issues that can't be overcome. 

#### Spamming

Any public facing system open for data input is eventually subject to spamming. A number of measures will be put in place to mitigate the phenomenon:

- Oracle registration will require address ownership verification
- Oracle pool creation will require upfront funding (amount TBD) to ensure initial pool funding and cover minting costs

#### Re-centralisation

For lack of a better word. The issue here is that the platform described in this document would be introducing a centralised component in an otherwise fully distributed system. The platform shouldn't be the only way to achieve some the benefits it will provide. This is particularly true for transparency around pool creation and oracle selection.

The project will strive to come up with and promote guidelines regarding oracle pool creation. Such best practices could then be applied by pool creators not relying on the platform. Furthermore, functionality will be encapsulated in standalone tools and libraries to be used independently or embedded in third party services.

## Team

The Delphi team gathered around a post in the `#i-need-a-team` channel on the Ergo Discord. It includes the following members, in alphabetical order:

- @abchris: Oracle worshipper and initiator of the project looking forward to see where it lands.
- @Balb: Experienced with Ergo's AppKit. Brings much needed Rust expertise to the table to interface with the oracle-core stack.
- @curbsideprophet: Data scientist by trade and blockchain analyst by night. Will be crafting new on-chain metrics tailored to this project.
- @error: Backend and database hero ready to take on challenges. Will be building backend and DevOps tooling.
- @Fuzy: Multitalented graphic designer and only team member to possess taste. UI/UX.

Community developer Luivatra, busy as he is, expressed interest and offered support.

## ErgoHack Theme

The theme of ErgoHack III is privacy and security. The latter is often associated with protocol improvements or infrastructure hardening. This project will contribute to security at a somewhat higher level by:

- Facilitating decentralisation of oracle operators through documentation and facilitated onboarding
- Security through transparency by making it easier to "background check" oracle pools and oracle operators through monitoring
- Empowering the broader community (KYA). Oracles, and oracle pools by extensions, are an integral part of DeFi. In the spirit of Ergo's KYA (know your assumptions), there is a need to educate the broader community on how pools operate and what to look for when using products relying on oracles. The platform would be a perfect place to disseminate such information.
- Directing resources towards further development of the oracle-core.