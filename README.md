# UTXO Dealership
Submission for Tabconf 2023 hackathon

# Video demo

[![](https://supertestnet.github.io/utxo-dealership/utxo-dealership-with-yt-logo.png)](https://www.youtube.com/watch?v=gHqB8htq8Kg)

# How to try it

Click here to act as the "seller" (i.e. someone who mines bitcoin): https://supertestnet.github.io/utxo-dealership/

Click here to act as the "buyer" (i.e. someone who wants to buy bitcoins that have no history): https://supertestnet.github.io/utxo-dealership/?user=buyer

# What is going on?

UTXO dealership is a forthcoming privacy tool for bitcoin. It enables bitcoin miners to easily sell their freshly mined utxos for a premium, and it enables bitcoiners to acquire decent privacy simply by visiting a website and buying a history-free utxo. (It uses coinswaps, invented by bitcoin legend Gregory Maxwell, to prevent chain analysts from identifying the swap and linking the "old" utxo to the "new" one.) This project should also help increase miner revenues (because miners can sell their utxos for a premium), which should help improve bitcoin's security.

It should also incentivize miners to use pools that sell their utxos via this software, because those pools will have higher revenues. In turn, this may disincentivize KYC'd mining pools -- who I imagine will not want to touch this software, despite its profitability -- who will thus lose members to non-KYC'd mining pools, since non-KYC'd mining pools have no qualms about doing stuff without KYC. Therefore this software will (hopefully) increase the profitability, and thus the usage, of non-KYC'd mining pools, improving bitcoin's decentralization and censorship resistance.

# Upcoming features

- [x] delink the swaps by avoiding pubkey reuse

- [x] allow custom amounts

- [x] allow multiple simultaneous offers

- [x] allow custom destinations

- [ ] ensure that only "fresh sats" show up for sale (currently it is just a coinswap tool, it doesn't ensure only coinbase utxos are sold)

- [ ] add a "certified pre-owned" section where bitcoiners can buy and sell coinjoined utxos

- [ ] release it on mainnet

# Version with a better ui

https://github.com/ntheile/utxo-dealership
