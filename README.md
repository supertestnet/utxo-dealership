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

# How do these swaps work?

The miner gives the buyer a pubkey and the buyer uses it to create a swap address using Gregory Maxwell's coinswap technique. The swap address – which I call Swap Address A – allows the buyer's pubkey to withdraw after a timelock, otherwise the miner's pubkey can withdraw if the buyer gives him a secret, otherwise the two parties can cooperate to spend the money without revealing the secret. The buyer deposits funds into this address and sends some info about it to the miner.

Then the miner creates an equivalent swap address – Swap Address B – which is locked to the same secret, except everything's reversed: his pubkey can withdraw after a timelock, the buyer's pubkey can withdraw using the secret which the buyer already knows, or the two parties can spend the funds cooperatively without revealing the secret. The miner uses Swap Address B as the destination for part of the next coinbase he mines, so now both sides have committed funds.

Then the buyer reveals to the miner the secret that allows the buyer to take the money in Swap Address B and the miner to take the money in Swap Address A. With this information in hand, the miner and the buyer do not actually *use* the secret (because that would publicly reveal information that links the swap) but instead they cooperatively send the money in Swap Address A to the miner and the money in Swap Address B to to the buyer. The resulting transactions look like ordinary 1-of-1 taproot transactions with no funkiness, and they reveal nothing that indicates a swap happened.

Importantly, the money effectively "changes hands" as soon as both parties commit funds. At that moment, the buyer can take the money in Swap Address B using his secret, but by doing so he would reveal the secret on the blockchain, and that would allow the miner to take the money in Swap Address A. Before the money is in those swap addresses, neither party needs to trust the other. And the very moment the money is in both of those addresses, it has changed hands, so neither party needs to trust one another at that point either.

But there's a caveat: they don't need to trust one another with their *money* but they *do* need to trust one another to complete the swap *privately,* i.e. without revealing the secret that links the swaps together. That is a much smaller trust assumption, in my opinion, but it still is one: neither party ever has the other's *money,* but if either one publishes the *secret* that links the transactions together, the privacy of the swap will be compromised.

# Upcoming features

- [x] delink the swaps by avoiding pubkey reuse

- [x] allow custom amounts

- [x] allow multiple simultaneous offers

- [x] allow custom destinations

- [x] ensure that only "fresh sats" are sold

- [x] add sections where bitcoiners can trade coinjoined utxos and unwanted utxos e.g. toxic change

- [ ] improve the UI to look more like Nick's version

- [ ] release it on mainnet

# Version with a better ui

https://github.com/ntheile/utxo-dealership
