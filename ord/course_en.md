<!--
Author: GaloisField
Translator: Arkano1dev
License: GNU-GPL v3 license
Description: A general course about Ordinals Protocol (EN).
Date: 21/07/23
Date of translation: 21/12/24
-->
# Ordinals Course

*Ordinals* is a new protocol built on Bitcoin that brings new opportunities, new risks, and great promises.
It is an Open-Source protocol that can change many things on Bitcoin.
To do this, I propose below the most comprehensive course outline possible. I do not think I am able to write the entire course alone and invite everyone interested in *Ordinals* to join me in an effort to present this course as best and as soon as possible.

This course seems essential to me in the Bitcoin ecosystem, in the era of *RGB*, [RGB Protocol on Bitcoin, What is it? | Trust Machines](https://trustmachines.co/learn/what-is-the-rgb-protocol-on-bitcoin/#:~:text=The%20RGB%20network%20is%20a,assets%20on%20the%20Bitcoin%20blockchain.), the announcements of *Ark*, [Bitcoin Developer Introduces New Layer 2 Protocol Ark - Bitcoin Magazine - Bitcoin News, Articles and Expert Insights](https://bitcoinmagazine.com/technical/bitcoin-developer-introduces-new-layer-2-protocol-ark), and a continuously growing trend of registrations [Bitcoin Ordinals Analysis](https://dune.com/dgtl_assets/bitcoin-ordinals-analysis).
Understanding this new protocol and especially the latest developments based on this protocol seems crucial to me!

Below you will find the table of contents, followed by a detailed plan and sections that need to be explored. You will also find a [vocabulary](#vocabulaire) section that can be updated over time to make this course as clear and accessible as possible.

I am available for any questions or feedback on this repo or by email: galoisfield2718@gmail.com.

# Table of Contents

## Introduction

## I/ History
### 1) First traces of the repository on Github & Casey's Workshop
####	a) First publication
####	b) Presentation *by* Casey
####	c) The arrival of [*degens*](#vocabulaire) and techies
####    d) Declaration of Open Ordinals Institute©️ and changes <!--Issue: Requires current news! Section to be regularly updated -->
### 2) Old ideas, brought back to life <!--Needs to be completed! Interview people who experienced them and transcribe here! -->
#### 	a) Colored coins
#### 	b) Counterparty
#### 	c) Ethereum and ABIs
### 3) The core Team
####	a) Github
####	b) Twitter
####	c) Passing the torch

## II) Theory and Implementation
### 1) Counting the sats
####	a) The method <!--Detail this part well-->
####	b) Casey's choices
####	c) In search of rare sats
### 2) Registration
####	a) The idea
####	b) The practice
####	c) The code <!--Provide a precise look at this last one.-->
### 3) The client
####	a) Bitcoin Core <!--Simply provide a good tutorial for all OS! -->
####	b) `ord`
####	c) Basic commands

## III) Usage and Latest Advances
### 1) Online Tools
####	a) Wallets
####	b) Platforms
####	c) Marketplace
### 2) JSON and new protocols
####	a) Beginning of `sns`
####	b) Arrival of `brc-20`
####	c) A Meta Protocol: BOSS
### 3) Some Deployed Techniques
####	a) Cursed inscriptions
####	b) Bitmap and names
####	c) Recursive inscriptions

## Conclusion
### Looking back at history
### What future holds?
### Getting involved

## Appendices

### Vocabulary
### References

### Appendix A: Offline use of the iancoleman.com site for generating bech32 addresses.
### Appendix B: Script writing with `bitcoin-cli`

![skull](./assets/greenpeace_skull.png)
[*inscription*](https://ord.link/1187713)

## Introduction

-----------
The purpose of this course is to address all profiles, and its parts should be able to be read independently.
-----------

IT'S A **PROTOCOL ON BITCOIN**!

*How so?*

In a Bitcoin transaction, a message can be included.
-> A Bitcoin transaction is a message.
This message must adhere to a certain structure and use "functions" of the Bitcoin protocol.
These "functions" are called <u>operations</u>. The set of these operations is called `OP_CODE`.
These operations are sent to the *Bitcoin network* in transactions.
The <u>Bitcoin network</u> refers to all machines running the Bitcoin protocol. Details of the clients used to access the Bitcoin network can be found on [Coin Dance | Bitcoin Nodes Summary](https://coin.dance/nodes/share).

Through `OP_CODE`, algorithmic operations can be performed on the Bitcoin network, known as a `script`. For more details: [Opcodes used in Bitcoin Script - Bitcoin Wiki](https://wiki.bitcoinsv.io/index.php/Opcodes_used_in_Bitcoin_Script)


> Going further: What is a Bitcoin transaction?
-> Mention of the UTXO set
-> Mention of the signature

Ordinals (like others before) propose a transaction standard, called `envelope`:
```
OP_FALSE
OP_IF
  OP_PUSH "ord"
  OP_PUSH 1
  OP_PUSH "text/plain;charset=utf-8"
  OP_PUSH 0
  OP_PUSH "Hello, world!"
OP_ENDIF
```

Initially, `OP_RETURN` was used to record and index text (detailed in I.2: Old ideas, brought back to life).
Since the recent updates, this may have evolved (as we will see in II.2: Theory and implementation, *inscription*).

This protocol has been able to be used from the arrival of elementary generative art (I.1.c: the arrival of degens and techos) until today.

The meta protocol [BOSS (Bitcoin Operating Standard System](https://github.com/galoisfield2718/boss) (III.2.c) has now been abandoned, and the course is being updated to take this evolution into account.

There are multiple developments, and it is not possible to keep up with everything. The goal here is to shed some light on the theory of [`Ordinals`](https://www.youtube.com/watch?v=g-isJScvFlE).
> Vocabulary note: In English, we talk about 'Ordinal Theory,' the GitHub account that manages the main folder `ord` is named `ordinals`. It is customary to refer to Ordinals, and the word 'ordinal' is generally plural. Therefore, it seems natural to translate the Theory of Ordinals into French.

## I/ History

In this section, the goal is to delve into the history of this protocol and the human behind it.
The aim is not to be technical but to understand where it comes from, who is behind it, and for what motivations.
Understanding who the participants are and enabling everyone to further research these developers themselves.

### 1) First traces of the folder on Github & Casey's Workshop

-> Mention of the serial numbering on Bitcoin cf https://bitcointalk.org/index.php?topic=117224.0

The main developer of this protocol is Casey Rodarmor ([Casey (@rodarmor) | Twitter](https://twitter.com/rodarmor/), [R O D A R M O R](https://rodarmor.com/), [casey (Casey Rodarmor) | Github](https://github.com/casey/)).
In 2015, he actively worked on Bitcoin Core where he carried out a series of batches (updates) and the restructuring of part of the Bitcoin Core code ([Casey Rodarmor's Resume](https://rodarmor.com/resume/index.html)).

<!--
Taproot: In a few words, based on the reduction of address weight and the increase in the size of the *witness* (see section II.1), this allows for an increase in the size of the script associated with the transaction. 
> Note: Translating this witness `hex to text` does not work as is. To test this, use the witness of an inscription in [CyberChef](https://gchq.github.io/CyberChef/). On this topic, initial solutions can be found in [Tweet @Blockcryptology](https://x.com/blockcryptology/status/1708454640373686299?s=46&t=V6rDQiBqyYm5XAi9Qbj6Ew).
-->

- SegWit => Reducing transaction sizes by separating addresses first and witnesses in another section that contain signature scripts
- Taproot => More specifically TapScript (BIP 342) allows any type of script (to be verified)
> Regarding the witness program associated with a Bitcoin transaction, one can refer to [bip-0141](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki): "The `witness` is a serialization of all witness fields of the transaction. Each txin is associated with a witness field. A witness field starts with a `var_int` to indicate the number of stack items for the txin. It is followed by stack items, with each item starting with a `var_int` to indicate the length. Witness data is NOT script."
> Defining a transaction containing a witness as
```
    [nVersion][marker][flag][txins][txouts][witness][nLockTime]
```
![transaction id building](./assets/transaction_id_building.png)

As important contributors, we find [raphjaph (raph)](https://github.com/raphjaph), a computer science student at the University of Munich, and [veryordinally (ordinally)](https://github.com/veryordinally?tab=overview&from=2015-12-01&to=2015-12-31) whose profile was created in 2015 but only became active on Ordinals.

> On Ordinals, there is less information than on the others, and this profile seems quite strange. It would be interesting to dig deeper as well as to detail the other contributors: [Contributors to ordinals/ord](https://github.com/ordinals/ord/graphs/contributors).

Let's delve into the first publications made by Casey Rodarmor before detailing his presentation and attempting to trace the history of the arrival of 'degens' through the still-to-be-studied work of early techies (rocks, taproot wizard, and other generative art).

####	a) A first publication

<img src="./assets/Create_ord_casey.png" alt="creation ord" width="450" height="300">
*This information is no longer available on Casey's profile (taken on 22/05/23).*

With the initialization commit of the README on December 12, 2021: [First commit](https://github.com/ordinals/ord/commit/4ee262e3456b82120f20474ee89eab22930ac0fe)

<img src="./assets/init_commit.png" alt="init" width="500" height="200">
The first README can be found [here](./assets/first_README.md).

So we see work that was thought out for a year by Casey before his [presentation](https://www.coindesk.com/consensus-magazine/2023/02/23/casey-rodarmor-why-i-developed-the-ordinals-bitcoin-nft-project-coindesk/) in October 2022, which we will come back to.

We see the first release [0.0.1](https://github.com/ordinals/ord/commit/da839875b9500d769e2877f6702978bd49391669) on June 5, 2022.
<img src="./assets/0.0.1_casey.png" alt="0.0.1" width="500" height="200">

####	b) Presentation by Casey
-> [Ordinals Workshop with Casey Rodarmor](https://www.youtube.com/watch?v=MC_haVa6N3I)

This workshop was the first live presentation by Casey of this new protocol.
It took place in Austin, Texas on August 27, 2022 [Ordinals Workshop with Rodamar, Sat. August 27, 2022, 12:00 | Meetup](https://www.meetup.com/fr-FR/pleb-lab/events/287948415/). He presented live his theory, what Ordinals is, and the resources offered.

A presentation of his motivations through generative art and giving artists the opportunity to register their works on Bitcoin.

> A rather challenging presentation of what he means by "counting the sats," which we will delve into further later on. With a live demo of the website [ordinals.com](https://ordinals.com), a description of the folder on Github, and finally the presentation of a Python algorithm to show how to count the satoshis.

This presentation was more focused on the theory of sats than on the application of the protocol. There was no example of using the `ord` command line to register from the terminal, nor a demonstration of registrations, only an explanation of the theoretical operation.

#### c) The arrival of degens and techs

It took until December 2022 to have the first registration [Registration #0](https://ord.link/0) made by **bc1qv8zhcjzpjw4m4tdyc5zn3dmax0z6rr6l78fevg** which can be seen that it was not kept as it was immediately transferred to another address [Activity for bc1qv8zhcjzpjw4m4tdyc5zn3dmax0z6rr6l78fevg | Ordiscan](https://ordiscan.com/address/bc1qv8zhcjzpjw4m4tdyc5zn3dmax0z6rr6l78fevg/activity). The final address that holds registration #0 is quite active [Activity for bc1pz4kvfpurqc2hwgrq0nwtfve2lfxvdpfcdpzc6ujchyr3ztj6gd9sfr6ayf | Ordiscan](https://ordiscan.com/address/bc1pz4kvfpurqc2hwgrq0nwtfve2lfxvdpfcdpzc6ujchyr3ztj6gd9sfr6ayf/activity).

The Bitcoin rocks [Bitcoin Rocks | Ordiscan](https://ordiscan.com/collection/bitcoin-rocks) were the first minted collection with 71 to 247 registrations. They were the gateway for 'Degens'. They showed how to publish a collection on Ordinals.

The [Taproot Wizard](https://taprootwizards.com/), inspired by Bitcoin Wizard 🧙🧙‍♀️ on Reddit, minted most of the collection in a single block [collaboration with Luxor mining pool](https://www.coindesk.com/tech/2023/02/02/giant-bitcoin-taproot-wizard-nft-minted-in-collaboration-with-luxor-mining-pool/amp/) and were very successful in the community. They now represent an OG piece and a part of Ordinals history. 
Information about Taproot Wizard can be found on [OXALUS.io](https://oxalus.io/nft/ordinals/bitcoin-wizards).

For a [description](https://unisat.io/market/collection?collectionId=bitcoin-wizards): Taproot Wizard is an Ordinal NFT project celebrating the 10th anniversary of the original Bitcoin Wizard collection created by mavensbot. Magic Internet Money is an iconic advertisement from the bitcoin subreddit. Created on Monday, February 18, 2013 by u/mavensbot, it quickly became the most popular ad on Reddit. 
mavensbot is the father of Magic Internet Money: Bitcoin Wizard.

[*Registration #652*](https://ord.link/652)
 <img src="./assets/first_wizard.jpg" alt="firstWizard" width="450" height="450">



Until recently, adding even more on June 29, 2023: 


 <img src="./assets/last_wizard.webp" alt="lastWizard" width="450" height="450">

[*Registration #14,163,842*](https://ord.link/14163842)

More than just a project, they are a symbol of the beginnings of Ordinals and bitcoin on reddit and the Internet!

This collection brought in the initial liquidity needed for the ecosystem's development and remains an important historical part. 

The degens continued their journey....

Today, many collections are being exchanged for a fortune. We have seen the [cryptopunks](https://www.larvalabs.com/cryptopunks) resurface on Bitcoin, the [Bitcoin Punks](https://bitcoinpunks.com/) emerge, the [Bitcoin Frogs](https://twitter.com/BitcoinFrogs) born, or even Pepe making a strong comeback. However, the degen wave from the beginning seems to be no longer here for now. The arrival of brc-20 has changed the landscape...
Many things have happened today, the Puppets have arrived, OMB represents a large community on Ordinals, and the Runes made a lot of noise before experiencing its first winter. 


#### d) Open Ordinals Institute©️ Declaration and Changes
[Open Ordinals Institute on X: "The Ordinals protocol team is proud to announce the launch of the Open Ordinals Institute, a 501(c)(3) non-profit organization to foster the growth and advancement of the Bitcoin Ordinals protocol. Donations can be made at our website: https://t.co/H7ymKSL4VR" / X](https://twitter.com/ordinalsorg/status/1686435373780746242)


### 2) Old Ideas, Brought Back to Life

> Here, it would be interesting to interview people who experienced it to get their feedback. 

#### 	a) Counter Party (2012)

[Counterparty](https://counterparty.io/) is a protocol on Bitcoin that has been evolving since 2012. Many degens would have remembered it at that time. However, it has continued and is now one of the building blocks of [elements](https://github.com/ElementsProject/elements). This is a good example because [elements](https://github.com/ElementsProject/elements) aims to enable companies or networks to build side chains indexed to Bitcoin. A service that is developing on this network is, for example: [liquid network](https://liquid.net/). A network that is built as a "side-chain" based on Bitcoin.

We can see here some possible ideas through the arrival of a new protocol. This happened 12 years ago. 
[Ordinals just celebrated its first year](https://twitter.com/realizingerin/status/1735272834321326090) recently.

**NOTES:** *Bitcoin-dev-digest, Vol 99, Issue45*\
"Please correct me if I'm wrong, but I believe Counterparty has, in the past, encoded their data within public key data, so this concern is not hypothetical." by Russell O'Connor \<roconnor@blockstream.com\>

 <img src="./assets/bitcoin-digest_counter_party.jpg" alt="bitcoin-digest" width="450" height="450">


#### 	b) Colored Coins (2014)

An interesting article on this topic [Colored Coins, What They Are and How They Work On The Bitcoin Blockchain | Bitcoinist.com](https://bitcoinist.com/colored-coins-work-bitcoin-blockchain/).


An explorer that is no longer available but accessible via [Wayback Machine](https://web.archive.org/): [coinprism](https://web.archive.org/web/20150213225601/https://www.coinprism.info/assets).

Investigation is needed on the visualization of these transactions. On the coinprism site, only addresses of the form: `AJxuLADi8stt7DpKEedhFEqCuB9dcV1EZd` are found, which are neither transactions nor Bitcoin addresses.


#### 	c) Ethereum and ABIs (2015)

ABIs (Application Binary Interface) are JSON files representing the contract deployed on Ethereum. These ABIs are used by interfaces in `javascript`, `typescript`, and others to allow the user to interact with ETH contracts.

<u> Note </u>: It would be necessary to detail the use of ABIs, their interest, and their use.

**Question**: Can these JSON files be associated with JSON-based protocols ([Vocabulary](#vocabulary)) on Ordinals?


### 3) The Core Team

Although Casey is the figurehead of this project, he is obviously not alone!

Only a few have been very actively involved in the code, but many people have contributed without whom we would not have as comprehensive a tool as the current one.
The different issues and discussions also constitute contributions in themselves but unfortunately are not listed in the commits ^^. 

It's up to us to search and index to pay them tribute ;)

#### a) Github
[Contributors to ordinals/ord](https://github.com/ordinals/ord/graphs/contributors)

 <img src="./assets/core_team1.png" alt="core1" width="250" height="300">

<img src="./assets/core_team2.png" alt="core2" width="250" height="300">

<img src="./assets/core_team3.png" alt="core3" width="250" height="300">

#### b) Twitter

A Twitter list gathering the main core developers [ordinals dev list](https://twitter.com/i/lists/1627776735210098708?s=20).

#### c) Passing the torch
[Casey: "I haven't been able to give ord the attention it deserves, so I am pleased to announce that @raphjaph has agreed to step up as lead maintainer! Raph is an impoverished student, and his work on ord will be entirely funded by donations. If you can, please consider donating!…"](https://twitter.com/rodarmor/status/1662617512700420096)

## II) Theory and Implementation

The most technical documentation currently available can be found on [bip.mediawiki](https://github.com/ordinals/ord/blob/0.0.2/bip.mediawiki).

### 1) Counting the sats

Casey starts with the idea of numbering each satoshi on Bitcoin

> Every satoshi is serially numbered, starting at 0, in the order in which it is mined. These numbers are termed "ordinal numbers", or "ordinals", as they are ordinal numbers in the mathematical sense, giving the order of each satoshi in the totally supply. The word "ordinal" is nicely unambiguous, as it is not used elsewhere in the Bitcoin protocol.
> The ordinal numbers of transaction inputs are transferred to outputs in first-in-first-out order, according to the size and order of the transactions inputs and outputs.

> If a transaction is mined with the same transaction ID as outputs currently in the UTXO set, following the behavior of Bitcoin Core, the new transaction outputs displace the older UTXO set entries, destroying the ordinals contained in any unspent outputs of the first transaction. This rule is required to handle the two pairs of mainnet transactions with duplicate transaction IDs, namely the coinbase transactions of blocks 91812/91842, and 91722/91880, mined before BIP-34 made the creation of transactions with duplicate IDs impossible.

> For the assignment algorithm, the coinbase transaction is considered to have an implicit input equal in size to the subsidy, followed by an input for every fee-paying transaction in the block, in the order that those transactions appear in the block. The implicit subsidy input carries the block's newly created ordinals. The implicit fee inputs carry the ordinals that were paid as fees in the block's transactions.

> Underpaying the subsidy does not change the ordinal numbers of satoshis mined in subsequent blocks. Ordinals depend only on how many satoshis could have been mined, not how many actually were.

#### a) The Method

-> Detailed extensively in its workshop and presented above.

> Ordinals may be written as the ordinal number followed by the Romance-language ordinal indicator °, for example 13°.

A satpoint may be used to indicate the location of an ordinal within an output. A satpoint consists of an outpoint, i.e., a transaction ID and output index, with the addition of the offset of the ordinal within that output. For example, if the ordinal in question is at offset 6 in the first output of a transaction can be written as:

`680df1e4d43016571e504b0b142ee43c5c0b83398a97bdcfd94ea6f287322d22:0:6`

A slot may be used to indicate the output of an ordinal without referring to a transaction ID, by substituting the block height and transaction index within the block for the transaction ID. It is written as a dotted quad. For example, the ordinal at offset 100 in the output at offset 1, in the coinbase transaction of block 83 can be written as:

`83.0.1.100`

Satoshis with ordinals that are not valuable or notable can be referred to as cardinal, as their identity does not matter, only the amount. A cardinal output is one whose ordinals are unimportant for the purpose at hand, for example an output used only to provide padding to avoid creating a transaction with an output below the dust limit.

> Any ordinal transfer can be accomplished in a single transaction, but the resulting transaction may contain outputs below the dust limit, and thus be non-standard and difficult to get included in a block. Consider a scenario where Alice owns an output containing the range of ordinals [0,10], the current dust limit is 5 satoshis, and Alice wishes to send send ordinals 4° and 6° to Bob, but retain ordinal 5°. Alice could construct a transaction with three outputs of size 5, 1, and 5, containing ordinals [0,4], 5, and [6,10]. The second output is under the dust limit, and so such a transaction would be non-standard. 

This transfer, and indeed any transfer, can be accomplished by breaking the transfer into multiple transactions, with each transaction performing one or more splits and merging in padding outputs as needed.

To wit, Alice could perform the desired transfer in two transactions. The first transaction would send ordinals [0,4] to Bob, and return as change ordinals [5,10] to Alice. The second transaction would take as inputs an output of at least 4 satoshis, the change input, and an additional input of at least one satoshi; and create an output of size 5 to Bob's address, and the remainder as a change output. Both transactions avoid creating any non-standard outputs, but still accomplish the same desired transfer of ordinals.

Technically:

```
# subsidy of block at given height
def subsidy(height):
  return 50 * 100_000_000 >> height // 210_000

# first ordinal of subsidy of block at given height
def first_ordinal(height):
  start = 0
  for height in range(height):
    start += subsidy(height)
  return start

# assign ordinals in given block
def assign_ordinals(block):
  first = first_ordinal(block.height)
  last = first + subsidy(block.height)
  coinbase_ordinals = list(range(first, last))

  for transaction in block.transactions[1:]:
    ordinals = []
    for input in transaction.inputs:
      ordinals.extend(input.ordinals)

    for output in transaction.outputs:
      output.ordinals = ordinals[:output.value]
      del ordinals[:output.value]

    coinbase_ordinals.extend(ordinals)

  for output in block.transaction[0].outputs:
    output.ordinals = coinbase_ordinals[:output.value]
    del coinbase_ordinals[:output.value]
```

#### b) Casey's Choices

Casey has chosen to name the sats in addition to numbering them.

An interesting notation is the degree notation. Each sat is numbered by its position following one of the four events below:
- *Block*: Position in each new mined block. If it is the first: 0'''.
- *Difficulty Adjustment*: Position relative to the last difficulty adjustment (every 2016 blocks). If it is the first: 0''.
- *Halving*: Position relative to the last halving block (every 210,000 blocks). The first is noted: 0'.
- *Cycles*: A special event that is the difficulty adjustment at the same time as a *halving*. This happens every 6 *halvings*. The next one should be in 2032. The first one is noted: 0°.

The advantage of this notation is its visibility compared to the rarities proposed by Casey, which can be seen [here](https://docs.ordinals.com/overview.html). All sats containing at least one 0 will not be common.
For example: 1°1'0''0''' is rare.
1◦ 2nd cycle
1′ Not the first block of a *halving epoch*
0′′ First block of a difficulty adjustment
0′′′ 1st sat of the block

However, this notation has the disadvantage of being difficult to find as is from an explorer.
For more details on rare sats, you can refer to [c) In Search of Rare Sats](#c).

Counting sats is part of Casey's choices. Recently, discussions have taken place to determine whether the first sat of the utxo or the last one should be chosen as the one containing the inscription. However, Casey had initially built a First-In-First-Out (FIFO) queue for assigning sats in a transaction.


[//](#c)
####	c) In search of rare sats

The initial (historical) rarities are:
- `common`: All sats that are not the first in their block.
- `uncommon`: The first sat of each block.
- `rare`: The first sat of each difficulty adjustment.
- `epic`: The first sat of each halving.
- `legendary`: The first sat of each cycle.
- `mythic`: The first sat of the genesis block (Unique!).

However, new rarities have emerged! You can find a good summary in the thread by [@@0xBes](https://twitter.com/0xBes): [Thread: Categorization of Rare Satoshis 💎](https://x.com/0xBes/status/1739987968922632240?s=20).

You can also visit [sating](https://sating.io):

<img src="./assets/sats_rarity.png" alt="satsRarity" width="350" height="300">

It can be seen that today the search and study of rare sats is becoming a discipline in its own right: [satology](https://x.com/ZedZeroth/status/1710287026061267348?s=20).

**To search for them**:

For a manual search in Sparrow Wallet, there is [Franken | How to find and extract rare sats from your Bitcoin wallet!](https://www.youtube.com/watch?v=4Gro5AmFdfY).
It is also possible to do it via command line using the [official documentation | 7.3 Sat Hunting](https://docs.ordinals.com/guides/sat-hunting.html). I have not tested it yet.

Of course, the easiest way is online! More and more tools now integrate the visualization of rare sats. New categories are regularly added, so you need to stay updated on this.

[Sat scanner | sating](https://sating.io/), one of the first tools to do so.

### 2) The Inscription

Now that we know how to count sats, we can manipulate them.
Ordinals, specifically the `ord` command line, allows for inscription on these sats.
In this section, we will focus on the command line, also known as the `ord` client.

#### a) The Idea

When making a transaction, data can be stored on the first sat of the tx.

Technically, a double commit and reveal tx is used. This comes from the SegWit update (for Segregated Witness) with the integration of the witness field, details of which can be found in [Segregated witness road to implementation](https://www.coingecko.com/learn/segregated-witness-road-to-implementation). This would allow knowing the output and writing on the correct sat.

The use of the native witness had to be done starting from the commit [Add commands to mint and verify NFTs (#211) · ordinals/ord@15ed050](https://github.com/ordinals/ord/commit/15ed050d59de6e0f1d581de5a92e3809d0069b0c). It is done using the new `Witness` class from `blockdata` of the Rust library [bitcoin](https://docs.rs/bitcoin/latest/bitcoin/).
![index.rs](index.rs_0.0.0_witness_integration.png)

To be able to write on Bitcoin, we will need an envelope that will be contained in the transaction and attached to the script in the transaction. Thus, we will be able to transfer from address to address this script attached to the transaction, representing the inscription. Technically, this is stored in the `scriptPubKey` associated with the [utxo (unspent transaction output)](https://academy.bit2me.com/fr/que-es-una-utxo/).

<u>Note</u>: Sorry for the technical terms, but these are the exact terms that need to be understood to fully grasp the concept of inscription.

#### b) The Practice

In practice, there is no need to understand why this works to use it.

However, after an inscription with the `ord` client, we obtain a json output in the form:

```JSON
{
  "commit": "0bdbae349b685c0a59fa275f18d4ad14c3972fb5998d513399a478d87d805e00",
  "inscription": "d4ad4cd729fdd4dfaa5279aed4910e4afcfac6e3be25900ba40a2faebef28a9fi0",
  "reveal": "d4ad4cd729fdd4dfaa5279aed4910e4afcfac6e3be25900ba40a2faebef28a9f",
  "fees": 8440
}

```

In practice, the [envelope](https://docs.ordinals.com/inscriptions.html) is in the form:

```
OP_FALSE
OP_IF
  OP_PUSH "ord"
  OP_PUSH 1
  OP_PUSH "text/plain;charset=utf-8"
  OP_PUSH 0
  OP_PUSH "Hello, world!"
OP_ENDIF
```

Let's read a bit to clarify this script and then let's see in [mempool.space](https://mempool.space) what this looks like in practice. 

The `OP_FALSE` is used to end the script before registration. It should be noted that a registration always comes at the end of the script (for details on scripts, see [vocabulary](#vocabulary)). 

The `OP_CODE` `OP_IF` ... `OP_ENDIF` corresponds to the core of the Ordinals protocol. Indeed, thanks to this, we will be able to "package" data in our transaction that will be: engraved in the transaction, easily "transportable" and "interpretable," as well as highly customizable. Ordinals is ONE proposal for using this `OP_IF`...`OP_ENDIF`, but there can be many others [^1]. 

Next, we use a series of `OP_PUSH` to correctly send all the data. This is translated in Bitcoin as: `OP_PUSHBYTES_xx` where xx is a number calculated based on the length of the character string. 

So, we start by sending the text `ord` in hexadecimal format in our transaction: `OP_PUSHBYTES_3 6f7264` followed by an `OP_PUSHBYTES_1 01`. 

Then, as indicated in the above envelope, we *push* the file type following the [MIME](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) format with encoding. A `json` file will generally be sent to the network with the format: `text/plain;charset=utf-8` or `application/json`. 

So, what do we have left to send? The data itself! Thus, depending on the data, it will be encrypted beforehand according to a specific base before being converted to hexadecimal. 

What does this mean? 

If I have an image that I want to register in JPEG format, I will start by specifying the type: `image/jpeg`. 

Then I will convert my image to base64. This is easily done with tools like [Image to Base64 | guru](https://base64.guru/converter/encode/image) or packages in any programming language. Once converted to base64, I need to convert it to hexadecimal format so that it is accepted by the Bitcoin network. For this, we can use [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')) which provides us with a suite of very powerful tools in a graphical interface and API/packages.

To see how to read an encoded image, simply follow the reverse path. You will find a [tweet](https://twitter.com/Blockcryptology/status/1708454640373686299) made about this.

##### Reading an inscription from mempool.space

We now have all the tools to read an inscription directly from the explorer [mempool.space](https://mempool.space)

For simplicity, we will process a text-type transaction to avoid transcribing too much data.

Let's take the transaction: [`b61b0172d95e266c18aea0c624db987e971a5d6d4ebc2aaed85da4642d635735`](https://mempool.space/tx/b61b0172d95e266c18aea0c624db987e971a5d6d4ebc2aaed85da4642d635735) [^2], the inscription of `deploy` of computer (we will see later what this corresponds to more precisely, for now we will just "decompile" it).

<img src="./assets/tx_deploy_ordi.png" alt="Transaction de deploy ordi" width="400" height="300">

<img src="./assets/p2tr_deploy_ordi.png" alt="P2TR script deploy ordi" width="450" height="250">

Below is the script of interest (p2tr) contained in this transaction:

```
OP_PUSHBYTES_32 9e2849b90a2353691fccedd467215c88eec89a5d0dcf468e6cf37abed344d746
OP_CHECKSIG
OP_0
OP_IF
OP_PUSHBYTES_3 6f7264
OP_PUSHBYTES_1 01
OP_PUSHBYTES_24 746578742f706c61696e3b636861727365743d7574662d38
OP_0
OP_PUSHDATA1 7b200a20202270223a20226272632d3230222c0a2020226f70223a20226465706c6f79222c0a2020227469636b223a20226f726469222c0a2020226d6178223a20223231303030303030222c0a2020226c696d223a202231303030220a7d
OP_ENDIF
```
The reading will be done exclusively with [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')).

The `OP_PUSHBYTES32 ...` and `OP_CHECKSIG` are not of interest to us for the study of the inscription. Feel free to *dig* into this part.

So we start with: `OP_PUSHBYTES_3 6f7264`, `6f7264` indeed gives `ord` [ord | CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex%28%27Auto%27%29From_Base64%28%27A-Za-z0-9%2B%2F%3D%27,false,false/disabled%29From_Hexdump%28/disabled%29&input=NmY3MjY0).

Then we retrieve the file type with: `OP_PUSHBYTES_24 746578742f706c61696e3b636861727365743d7574662d38`, `746578742f706c61696e3b636861727365743d7574662d38` gives as expected: `text/plain;charset=utf-8` [text/plain | CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex%28%27Auto%27%29From_Base64%28%27A-Za-z0-9%2B%2F%3D%27,false,false/disabled%29From_Hexdump%28/disabled%29&input=NzQ2NTc4NzQyZjcwNmM2MTY5NmUzYjYzNjg2MTcyNzM2NTc0M2Q3NTc0NjYyZDM4)

The `OP_0` indicates that we are going to move on to the actual data: `OP_PUSHDATA1 7b200a20202270223a20226272632d3230222c0a2020226f70223a20226465706c6f79222c0a2020227469636b223a20226f726469222c0a2020226d6178223a20223231303030303030222c0a2020226c696d223a202231303030220a7d` which translates to:
```
{ 
  "p": "brc-20",
  "op": "deploy",
  "tick": "ordi",
  "max": "21000000",
  "lim": "1000"
}
```

[deploy inscription | CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex%28%27Auto%27%29From_Base64%28%27A-Za-z0-9%2B%2F%3D%27,false,false/disabled%29From_Hexdump%28/disabled%29To_Quoted_Printable%28/disabled%29Defang_URL%28false,false,false,%27Only%20full%20URLs%27/disabled%29URL_Encode%28false/disabled%29URL_Encode%28false/disabled%29&input=N2IyMDBhMjAyMDIyNzAyMjNhMjAyMjYyNzI2MzJkMzIzMDIyMmMwYTIwMjAyMjZmNzAyMjNhMjAyMjY0NjU3MDZjNmY3OTIyMmMwYTIwMjAyMjc0Njk2MzZiICAgIDIyM2EyMDIyNmY3MjY0NjkyMjJjMGEyMDIwMjI2ZDYxNzgyMjNhMjAyMjMyMzEzMDMwMzAzMDMwMzAyMjJjMGEyMDIwMjI2YzY5NmQyMjNhMjAyMjMxMzAzMDMwMjIwYTdk)

Here we have retrieved the inscription `deploy` from the Bitcoin transaction `b61b0172d95e266c18aea0c624db987e971a5d6d4ebc2aaed85da4642d635735`.


You can practice with any inscription on [ordinals.com](https://ordinals.com). To get the id, remove `i0` to obtain the transaction, then paste it into the explorer [mempool.space](https://mempool.space) and have fun deciphering the script.

The explorer [ordpool.space](https://ordpool.space) does all this automatically.



[^1]: In this regard, we note the [Atomicals](https://github.com/atomicals) protocol (a part of this course will be dedicated to Atomicals in the future). Atomicals uses the same `OP_IF`...`OP_ENDIF` principle but fills this "packaging" differently.

[^2]: It should be noted that the id of an inscription is given by [txid]i0. The i0 determines the input, we can have something other than i0 but most are with i0. If we have multiple inputs, we will have i1, i2,... . But the construction of the inscription id remains the same.

[^3]: The term *flag* is more general in computing. The notation for command lines varies but is often `[OPTIONS]`. This is more to inform about terms in computing.

##### Metadata Discussion

A feature added and integrated quite recently ([(Oct. 2023) commit metadata](https://github.com/ordinals/ord/commit/aeb5f558bbedb0a7ddd095cee2f3ed0b4b495718)
) is the management of [metadatas](https://docs.ordinals.com/inscriptions/metadata.html). We will see in [3.](#3) how this applies to the command line.

Here we will focus on the wrapper proposed with the Bitcoin transaction itself.


####	c) The code

> [ordinals/ord/src/subcommand/wallet/inscribe.rs](https://github.com/ordinals/ord/tree/master/src/subcommand/wallet/inscribe.rs)

The goal is not to analyze ALL the code but to detail some important functions like `create_inscription_transactions` and `build_reveal_transaction`.

> For developers, this `inscribe.rs` file should be able to be modified moderately without impacting the rest of the client program `ord`. For example, the fees used to carry out transactions should be able to be modified. A thorough discussion with advanced implementation tests could be interesting.


For operations: 
```
- content_type, with a tag of 1, whose value is the MIME type of the body.
- pointer, with a tag of 2, see pointer docs.
- parent, with a tag of 3, see provenance.
- metadata, with a tag of 5, see metadata.
- metaprotocol, with a tag of 7, whose value is the metaprotocol identifier.
- content_encoding, with a tag of 9, whose value is the encoding of the body.
- delegate, with a tag of 11, see delegate.
```


### 3) The client
[//]: # (3)

The reference for this part is this video: [How To Setup A Bitcoin Node & Ord Wallet](https://www.youtube.com/watch?v=tdC8kmjn5N0&list=LL&index=1&t=0s)
This video is done on Windows, and being on Mac with a node on an external hard drive, I will propose the commands to set this up on Linux and Mac.

####	a) Bitcoin Core

Requirements:
- approx. 700 GB of storage, preferably on an SSD.
- a good internet connection.

Either you have an old computer and run the Bitcoin node on it, or I recommend getting a 1 TB external SSD. You can find one for less than a hundred euros online in general.


[jonasnick/bitcoin-node: "How to Run a Bitcoin Node" handout](https://github.com/jonasnick/bitcoin-node)


The installation has already been covered on DiscoverBitcoin [tutorials/node/bitcoin-core-mac-windows](https://github.com/GaloisField2718/sovereign-university-data/tree/main/tutorials/node/bitcoin-core-mac-windows) and [tutorials/node/bitcoin-core-linux](https://github.com/GaloisField2718/sovereign-university-data/tree/main/tutorials/node/bitcoin-core-linux).

<!--
**Step-by-Step installation Bitcoin Core**
1) Go to: [Download - Bitcoin](https://bitcoin.org/en/download) then download the version that corresponds to your operating system;

2) Open the package that should look like this:
Insert an image

3) Follow the instructions

4) Configure via `bitcoin.conf` so that the storage location is as follows:
*On Mac*:
- `/Volumes/mon_disque/bitcoin`

*On Linux*:
- `/media/mon_disque/bitcoin`

*On Windows*:
- `C:/mon_disque`

5) Command line:
*On Mac*:
```
./bitcoin/bin/bitcoind --conf=/Volumes/mon_disque/bitcoin/bitcoin.conf --txindex=1
```
3) Follow the instructions

4) Configure via `bitcoin.conf` so that the storage location is as follows:
*On Mac*:
- `/Volumes/mon_disque/bitcoin`

*On Linux*:
- `/media/mon_disque/bitcoin`

*On Windows*:
- `C:/mon_disque`

5) Command line:
*On Mac*:
```
./bitcoin/bin/bitcoind --conf=/Volumes/mon_disque/bitcoin/bitcoin.conf --txindex=1
```
If this is not enough to force it to download the blockchain into `mon_disque` then add the flags `--data-dir=/Volumes/mon_disque/bitcoin/Bitcoin --blocksdir=/Volumes/mon_disque/bitcoin/Bitcoin/blocks --settings=/Volumes/mon_disque/bitcoin/Bitcoin/settings.json --walletdir=/Volumes/mon_disque/bitcoin/Bitcoin/wallets --txindex=1`

*On Linux*:


*On Windows*:
-->


For its configuration, it needs to run on `bitcoind` with the flag `--txindex=1` (or add it to `bitcoin.conf`).

> On Mac, I managed to run it on my external hard drive by specifying each path for the flags: `--conf, --datadir, --blocksdir, --walletdir`.
> I launch it with `cd /Volumes/Crucial\ X8/Bitcoin/bitcoin/bin && ./bitcoind --conf=/Volumes/Crucial\ X8/bitcoin/Bitcoin/bitcoin.conf --datadir=/Volumes/Crucial\ X8/bitcoin/Bitcoin --blocksdir=/Volumes/Crucial\ X8/bitcoin/Bitcoin/blocks --settings=/Volumes/Crucial\ X8/bitcoin/Bitcoin/settings.json --walletdir=/Volumes/mon_disque/bitcoin/Bitcoin/wallets --txindex=1`.


####	b) `ord`

Once the node is fully downloaded, you can download and launch the `ord` client. We refer to the client as the command line used to interact with the ordinals protocol.

To download and install Bitcoin Core + `ord`, check out the awesome tutorial by [@pazNGMI: How To Setup A Bitcoin Node & Ord Wallet](https://www.youtube.com/watch?v=tdC8kmjn5N0).

Bitcoin Core: [Releases - bitcoincore](bitcoincore.org/en/releases)
`ord`: [Releases · ordinals/ord](https://github.com/ordinals/ord/releases)


----------------

To specify the destination location of the `index.redb` file, simply use `--index=/PATH/TO/index.redb`. This is called a *flag*[^3] or an *option*. Add it to our command **before** the main command (which is not a flag). Example: `ord --cookie-file=/PATH/TO/.cookie --index=/PATH/TO/index.redb index update`.

----------------

Now that you have downloaded and installed `ord`, what's next? Type `ord help` and move on to the next section ;)

####	c) Basic Commands

As you saw, `ord help` lists all the commands. First, you need to create a file that indexes the ordinals. To do this, use `ord [FLAGS] index update`. The flags are called `[OPTIONS]` in the *help*.

<u>Note</u>: As you have learned, you know that a protocol must be indexed to exist. That's why this command is important. However, it is not mandatory as it is automatically run when using `wallet`, `server`, and others that require the use of the index (database).

Next, we need to create a wallet. For this, use `ord [OPTIONS] wallet create` which will generate all the information that needs to be stored associated with the wallet.

Then, use `ord [OPTIONS] wallet receive` to fund the address. This will display an address owned by the newly created wallet.

Finally, `ord [OPTIONS] --fee-rate=xx wallet inscribe /PATH/TO/file.xxx` will be used to inscribe the desired file. The `--fee-rate` flag expressed in sats/vBytes will indicate the desired fee rate. Check on [mempool.space](https://mempool.space) to see the current level. It is always recommended to add a bit more if you want your transaction to go through quickly.

**If needed list**

*OPTIONS*:
`--cookie-file=PATH/TO/.cookie`: Specifies the path to the `.cookie` file of your bitcoincore node.
`--index=PATH/TO/index.redb`: Ordinals index file.
`-t`: Testnet mode.

*COMMANDS*:
`ord help` Returns all commands

`ord index update`: Updates the database (index)

`ord wallet help`: Lists wallet sub-commands

`ord wallet create`: Creates a new wallet

`ord wallet balance`: Provides the balance of the current ord wallet

`ord wallet inscribe`: Allows inscription via the syntax: `ord wallet inscribe path/to/file.ext --fee-rate=xxx` where `ext` is one of the following types: txt, json, webp, html

`ord wallet inscriptions`

It should be noted that there are commands: `ord server` and `ord preview` used to generate your own local web explorer ordinals based on the site [ordinals.com](https://ordinals.com).

## III) Usage and latest developments

Obviously, not everyone will use the `ord` client with the full Bitcoin node.

Therefore, more accessible and online tools are needed.
These online tools also sometimes offer certain advantages, such as fee optimization, which is much more difficult via the client alone, special inscriptions via templates for certain protocols (see III.2), or cursed inscriptions (see III.3).

They thus allow for a simple and advanced integration of the latest features offered by the ordinals protocol.

Let's delve into these tools before tackling the protocols built on Ordinals and the Cursed Inscriptions and other current technical delights.

### 1) Online Tools
Online tools are essential for the development of the ecosystem, and we will try to delve into them deeply.

**ATTENTION: All of this is still in development. Do not put or leave too much Bitcoin on them. Vulnerabilities may be discovered soon, resulting in total losses of ordinals and your money. Nothing is 100% secure, and these platforms are very new.**
*Note: Today Ledger manages Ordinals. I recommend you to inquire about it (and add it to this course ;) on this subject. It is always safer to store your assets on hardware wallets connected to the internet as little as possible!*

> Tutorials on each of these tools would be welcome ;)

#### a) Wallets

An article on qualitative ordinal wallets: [Bitcoin Ordinals Wallets Have Arrived: A Guide For Beginners and Experts](https://nftnow.com/news/bitcoin-ordinals-wallets-have-arrived/).

- [Unisat](https://unisat.io/)

- [OrdinalsWallet](https://ordinalswallet.com/)

- [Xverse](https://www.xverse.app/)

- [Hiro](https://wallet.hiro.so/) *Personally, I don't trust it. Potential hacks.*

#### b) Minting Platform

Quite similar to wallets, we need to add:

- [lookordinals.com](https://lookordinals.com) (currently the cheapest on the market, recommended by @0xGrug)

- [Gamma.io](https://gamma.io)

#### c) Marketplace

There are fewer options. We have:

- [Unisat Marketplace](https://unisat.io/marketplace)

- [Ordinals Wallet Marketplace](https://ordinalswallet.com/marketplace)

- [Magic Eden - Bitcoin NFT Marketplace](https://magiceden.io/ordinals)

### 2) JSON and New Protocols

Quickly, as the cost of registering images is high, people have turned to registering text files (myself included [galoisfield.btc](https://ord.link/187784)). However, with simple text files, how do we navigate? How do we find them? How do we **INDEX** them? And how do we define **a framework** and rules?

> This question of indexing is crucial on the Ordinals protocol and on protocols built on Ordinals.

But how does it work?

Let's delve into history!

#### a) Beginning of `sns`

An important actor in the Ordinals ecosystem is [@domodata](https://twitter.com/domodata).

Arriving with his full node on February 24th [domo: "Full node finally running. Will soon find out if the feeling of owning a wallet full of UTXOs, redolent with the scent of rare and exotic sats, is beyond compare."](https://twitter.com/domodata/status/1629134663842254848), he quickly proposed new standards.

The first one he used is `sns` for Sats Name Service:
![domo-sns](./assets/domo_sns.png)
[domo: "@sats-names"](https://twitter.com/domodata/status/1630948879737794561) 


Being the first protocol built on Ordinals, it has two ways of being used.

1. The first one is very simple, which simply involves registering a text file with `.sats`. This is not the one we are interested in here.

2. Defining a JSON file containing the following specifications:
   a) The protocol name via `"p" : "sns"`, here the protocol used is `sns`;
   b) The desired operation via `"op": "reg"`, here `reg` means that a new name is being defined;
   c) The chosen name via: `"name" : "my_name.sats"`, we choose `my_name.sats`.

3. There are also two optional parameters in this protocol:
   a) Associating a sats name with a btc address via `"rev" : "bc1q...."`;
   b) Associating a sats name with an entry via `"relay" : "...i0"`.

You can find the documentation at the following address [Mint names - Sats Names](https://docs.sats.id/sats-names/sns-spec/mint-names)

The idea of the `sns` protocol, which will be the one that will follow us throughout these over-protocols, is the use of a JSON always more or less verifying this structure.

Here is an example:
```JSON
{
 "p" : "sns",
 "op" : "reg",
 "name" : "galoisfield.sats",
 "rev" : "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa"
}
```

So here we have built a protocol whose elements are easily recognizable among all entries and allowing anyone to *index* these elements and use them in any applications.

> For experienced developers, you can try to develop or integrate this protocol into an application to allow user login or achievement verification in your app.

#### Arrival of `brc-20`

Now that we have understood how the `sns` protocol works, it will be very easy for us to understand other protocols such as `brc-20`.

Introduced for the first time by *@domodata* [domo: "Using inspiration from @sats_names and @redphonecrypto, I wondered if the concept could be expanded to fungible tokens. This is what I came up with."](https://twitter.com/domodata/status/1633658976931037184).

The idea is simple: replicate the protocol concept like `sns` to create tokens on Bitcoin. 

We keep: the protocol, the operation, we replace `name` with `tick`, we add `amt` for the amount of tokens considered, and we distinguish between deployment, mint, and transfer operations.

The trickiest operation is the transfer one, which we will revisit later.

A constraint set by Domo is that the ticker of a brc-20 must consist of only 4 characters.

> Find a reference for why 4 characters.

For a detailed video explanation of these concepts, you can refer to [The Only BRC-20 Guide You Will Need](https://www.youtube.com/watch?v=XftBkRZ9jqk).

Let's create the complete schema of a token `DBTC` for DécouvreBitcoin (the token already exists and is not related to it, this is purely indicative and does not constitute an invitation to mint, buy, or any other action):

1. Deployment

We have our ticker, now we need to decide on an amount. To be consistent with the one already deployed, let's take 21,000.
```JSON
{ 
 "p": "brc-20",
 "op": "deploy",
 "tick": "DBTC",
 "amt" : "21000",
 "lim" : "1"
}
```

The `lim` instruction determines how many token(s) can be minted at once.

If `lim = 1` but you mint 2, then you will not receive any tokens because your instruction will not be valid according to the protocol.
Pay close attention to this when minting!

![DBTC](./assets/DBTC.png)

2. Mint

Once our token is deployed, we can mint it. For this, you need to enter the following JSON:

```JSON
{
 "p" : "brc-20",
 "op": "mint",
 "tick": "DBTC",
 "amt": "1"
}
```

Once the entry is mined in a block, you will have 1 DBTC associated with your mint address.

3. Transfer

Now that you have minted the `DBTC` token, you can transfer it (to your best friend, your partner, or someone who wants to buy it from you).

To do this, you need to follow two steps:

A. Registering the `transfer` operation

```JSON
{
 "p": "brc-20",
 "op": "transfer",
 "tick": "DBTC",
 "amt": "1"
}
```

Now you have 1 transferable DBTC according to the `brc-20` protocol.

You can then proceed with the transfer.

B. Token transfer

You now need to make a Bitcoin transaction.
You must send the transfer entry to the desired person.

Via online wallets, this is done by simply clicking on `Transfer` or `Send`.

Via the ord client, you will need to:
- list your inscriptions with the command `ord wallet inscriptions`;
- select the one you are interested in;
- enter the command `ord --cookie-file=/Volumes/my_drive/bitcoin/.cookie wallet send --fee-rate 3 bc1pxsa6d95jrwald4jjsu0kwu4pyaztmjvh6rdjyrztfv0yx2gakk9qse5sjf acddd636c4ab0fb45c9f70ce2598cffa205c88594de916832a5789e3e58ca688i0`.

If you already know the transfer inscription, you can directly enter the last command (adapted to your context, especially for the location of the `cookie-file` if necessary).

So, we have covered all the operations that can be done with `brc-20`. At this point, you should have a better understanding of how these protocols built on Ordinals work.

There is much to be said about the discussions that have animated the various Discord and Telegram channels related to `brc-20`, and this could be the subject of additional articles.

#### c) A Meta Protocol: BOSS

Now that we have understood how these two protocols work, we can tackle a very big piece that is still in development, the Meta Protocol [**BOSS (Bitcoin Operational Standard System)**](https://github.com/opstandard/Boss).

BOSS offers a promising future with the idea of Meta Protocols. Creating a standard for all these wild protocols as well as a virtual machine. We can expect many future solutions to be built on BOSS. In any case, BOSS is going to be a pretty crazy experimentation ground on Bitcoin.

New things are regularly proposed. Improved interfaces, code to clarify, articles to write, tutorials to create, the things coming up are plentiful, and we need to stay informed to be where things are developing.

### 3) Some Technical Anecdotes

#### a) Cursed Inscriptions

The "cursed" inscriptions. These inscriptions appeared a few months after the launch of Ordinals. A cursed inscription is basically an invalid inscription a priori for the Ordinals protocol. 

#### i) Git issue #2062

In the git issue [Inscription numbers off by one, or the curious case of transaction `c1e0db6368a43...d9e4117151` · Issue #2062 · ordinals/ord](https://github.com/ordinals/ord/issues/2062) something strange was found.
An inscription with 0 satoshi attached!

Hell and damnation! We said to inscribe on satoshis. How is this possible?

Is this the only form of invalid inscription?

NO!

Many invalid inscriptions according to the Ordinals protocol have been inscribed, details of which can be found in the issue opened by Casey [Cursed Inscription Tracking Issue · Issue #2045 · ordinals/ord](https://github.com/ordinals/ord/issues/2045).

Multiple inscriptions, inscriptions with other `OP_CODE` such as the `op_code`, `OP_66` which is not indexed by `ord`, ... .

In order to integrate the cursed inscriptions into the market and index them, it was decided initially to index them with a negative number before considering them as valid and positive in the new update [Leonidas.og: "Version 0.6.0 of the Ordinals Protocol just went live! Here is everything you need to know about this major update"](https://twitter.com/LeonidasNFT/status/1665437076450336768).

We are still at the beginning and many things are going to change. Cursed inscriptions will be something historic for the ecosystem. Even though it is not necessary to dive headfirst into this type of inscription, it is important to see that this was an important step in integrating new forms of inscriptions on Ordinals.
Ordinals is a very young protocol and constantly evolving. Following events like this helps to better understand what may happen in the future and how to manage new features in inscriptions.

For more details on Bitcoin's `OP_CODE`, one can refer to [Opcodes used in Bitcoin Script - Bitcoin Wiki](https://wiki.bitcoinsv.io/index.php/Opcodes_used_in_Bitcoin_Script).

-> Additional references on cursed inscriptions
[Bitcoin Ordinals and the mystery of the 'cursed Inscriptions' - AMBCrypto](https://ambcrypto.com/bitcoin-ordinals-and-the-mystery-of-the-cursed-inscriptions/)
[Inscriptions in Reverse: The Quirky Journey of Cursed Ordinals - Influencive](https://www.influencive.com/inscriptions-in-reverse-the-quirky-journey-of-cursed-ordinals/)
[Bitcoin Ordinals rolls out upgrade to rectify 'Cursed Inscriptions' issue](https://cointelegraph.com/news/bitcoin-ordinals-upgrade-rectify-cursed-inscriptions-issue)

#### ii) Development

Updating ordinals to account for cursed inscriptions in the version (0.6.0) released on June 4, 2023.

[raph: "Just released a new version of ord (0.6.0), which implements the first steps in recognizing more types of inscriptions (cursed inscriptions). Additionally you can now pass in RPC credentials through command-line flags, environmental vars or a config file. https://t.co/Xi6C92cC6z"](https://twitter.com/raphjaph/status/1665367103342362625)

Accepting these cursed inscriptions now allows for "legally" manipulating multiple inscriptions in a single transaction and on a single satoshi.

-> We should prepare a workshop on this topic!

#### b) Bitmap and names

Some inscriptions have become popular by only writing text in the latter. Some modes have worked well and one that I really like is the [𝕏 names](https://ordinalswallet.com/collection/%F0%9D%95%8F-names).

> Complete with the bitmap documentation.

#### c) Recursive Inscriptions

Most JavaScript frameworks have recently been deployed in inscriptions.
[Ord.io on X: "React is now fully on-chain on Bitcoin!](https://twitter.com/ord_io/status/1694024434485538819)

Here are some inscribed tools:
- [ordengine-react@0.0.1](https://ordinals.com/content/faa7b9b0b7884360f6c2b34693855a0d60df5f344727c72e3691a80f84ec6a81i0)
- [React@18.2.0](https://ordinals.com/content/7f403153b6484f7d24f50a51e1cdf8187219a3baf103ef0df5ea2437fb9de874i0)
- [React-DOM@18.2.0](https://ordinals.com/content/89295aaf617708128b95d22e7099ce32108d4b918386e6f90994e7979d22ba72i0)

These new inscriptions pave the way for new inscriptions and a new web on Bitcoin.

# Conclusion

One of the most powerful things offered by Ordinals is certainly BOSS. Currently in development, the promises of BOSS are quite insane.
It would be necessary to dedicate an entire paper to the features announced by BOSS and a thorough study of the lightpaper.

A workshop coordinated with a JS developer who has studied the technical proposals of the BVM (Bitcoin Virtual Machine) proposed by BOSS and a "theorist" shedding light on the project's architecture could be very interesting to better understand BOSS. 

Obviously, there is more than just BOSS. Many things are still to be discovered and created!
This course, as comprehensive as possible, is far from covering everything and still requires a lot of in-depth work and individual as well as academic research to be complete.

### Getting involved

-> Participate in the writing of this course.

-> YouTube tutorials, live sessions, content creation, mentoring interested individuals.

-> Development by forking unisat or lookordinals.

-> Development of new ideas via HTML entries or code interpretation in txt format through a new indexer can be tried.

-> Getting started with BOSS as soon as the code is available. For a JS tech, coordinate to organize the previously discussed workshop.

### Appendices

A series of evolving appendices to clarify certain points of this course.

#### Vocabulary

[//]: # (vocabulary)

- <u>**degens**</u>: Abbreviation of degenerates. They refer to those who put large amounts of BTC on new, often still misunderstood things. They participate in funding early developments and pour a large amount of liquidity into the emerging market. They are less present in so-called "more mature" markets but are still well represented, albeit less powerful because they are fewer in number.

- <u>**sat**</u>: A satoshi (or sat) is the smallest unit of Bitcoin 1 sat = $10^{-8}$ BTC;

- <u>**Virtual Bytes**</u>: Abbreviated as vBytes or vB, this corresponds to the current method of calculating the size of a transaction. The equivalence is: 1 vB = 4 Bytes. Fees on Bitcoin are calculated in sats/vB. In other words, for a transaction weighing 400 Bytes, it will weigh 100 vB on Bitcoin, with a rate of 40 sats/vB, so it will cost: 4,000 sats (~ €2 currently);

- <u>**Protocol**</u>: I call Protocol any set of rules followed by a network and allowing the production of a service. Concretely, these are rules that, when followed, will allow to do *something*: produce a token, record data, grant rights, etc. It should be noted that a protocol does not depend on a language because they are rules. We then speak of protocol implementation (or client). Bitcoin is a protocol! There are several Bitcoin clients that allow interaction with the protocol, but the main one used is [Bitcoin Core](https://github.com/bitcoin/bitcoin). For a not very clear detail of the currently used clients: [Coin Dance | Bitcoin Blocks (historical) Summary](https://coin.dance/blocks/historical); 

- <u>**Indexer**</u>: Algorithm allowing to read the data associated with a protocol. Once retrieved via an indexer, it is then sufficient to display them in a "user-friendly" format. Since this data is quite raw, we can create an indexer with any language (as the rules are written in human language) and can output the data in any format. Generally, the indexed data still have a structure, and we try to preserve it.

- <u>**Explorer**</u>: An explorer is a website allowing to visualize operations carried out in a given protocol. We can see that the explorer goes hand in hand with the indexer. The main Bitcoin explorer being [mempool.space](https://mempool.space), the official ordinals explorer is [ordinals.com](https://ordinals.com), and a very good Bitcoin + Ordinals explorer is: [ordpool.space](https://ordpool.space);

- <u>**Script**</u>: A script is a series of instructions performing operations on an address. The script is written in [`OP_CODE`](https://wiki.bitcoinsv.io/index.php/Opcodes_used_in_Bitcoin_Script). The Bitcoin script, like scripts in general, is not a [Turing complete](https://en.wikipedia.org/wiki/Turing_completeness) language, meaning that we cannot program all [computable functions](https://en.wikipedia.org/wiki/Recursive_function). In other words, there are missing pieces to program everything we want. In contrast, [Solidity](https://soliditylang.org/) is a Turing-complete language;

- <u>**OP_CODE**</u>: Set of operations available in Bitcoin to perform complex algorithmic operations;

- <u>**Inscriptions**</u>: Data stored in a Bitcoin transaction;

- <u>**JSON-based protocol**</u>: I call protocols like `brc20` and `sns` as such. These are protocols defined and acting via JSON files recorded on Bitcoin via Ordinals. Note: cbrc20 is not a JSON-based protocol because it relies on metadata in the Ordinals protocol.

<!--
- <u>****</u>
-->
#### References

> Cryptography: In the commit [@15ed05](https://github.com/ordinals/ord/commit/15ed050d59de6e0f1d581de5a92e3809d0069b0c), he added the package for managing Schnorr signature via `secp256k1` to the `main.rs` file
![schnorr](https://assets-global.website-files.com/5f75fe1dce99248be5a892db/65675d9184b6e14799543eb9_6552522ea592a6c95fb7ea99_6524562a3a64ae68224a1269_ECDSA-vs-Schnorr-Signatures-Diagram.png)

> [Official Documentation Registrations](https://docs.ordinals.com/inscriptions.html)

> [ordpool.space | Bitcoin Explorer + Ordinals txs Visualization](https://ordpool.space)

> [Decompile a transaction with image](https://twitter.com/Blockcryptology/status/1708454640373686299)

> [Script - Bitcoin Wiki](https://en.bitcoin.it/w/index.php?title=Script&oldid=69733)


##### To go further

- [7 Required Steps To Secure Your iFrames – Reflectiz](https://www.reflectiz.com/blog/iframe-security/#:~:text=The%20main%20security%20threat%20of,and%20keystrokes%20through%20an%20iFrame.). We need to keep in mind that `https://ordinals.com/inscription/inscription_id/content` provide the execution of the content through an IFrame. The code will be embedded into IFrame tags. What if I give you an url from ordinals content ? In that case, ordinals.com could host attacks... We need to think about it.

