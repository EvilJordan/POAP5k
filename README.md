# Ethereum POAP 5k from [EthStaker](https://www.reddit.com/r/ethstaker/)
> https://old.reddit.com/r/ethfinance/comments/qkxqge/daily_general_discussion_november_2_2021/hj1082t/
>
> The Eth to $4k POAP was a pretty big hit here, and the EthStaker team is REALLY excited about distributing an Eth to $5k POAP. The problem is that POAP is clamping down on POAP farmers, so we needed a new approach. We've decided to offer "Eth to $5k" POAPs to anyone who makes any donation to EthStaker.eth between now and 24 hours after we hit $5k (this gives you a chance to save on gas fees). While we certainly appreciate generous donations, any donation is welcome ASSUMING gas + your donation exceeds $10 (This is honestly about spam reduction). Donations can be sent on mainnet to Ethstaker.eth. If you prefer to donate through another channel, just comment below and we'll look into it.
>
> As you may know, EthStaker is a non-profit group with the primary goal of improving access to staking for everyone and improving decentralization of the beacon chain - but even though we don't profit from EthStaker, we still need cash to make things happen. EthStaker is me \[/u/superphiz\],
> * /u/lamboshinakaghini
> * /u/butta_tribot
> * /u/unvetica_solutions
> * /u/gibsonstyle
> * and Colfax Selby.
>
> We work closely with /u/worthalter, but he has moved on to focus on POAP development.
>
> Let me be superphiz for a minute: I love giving out POAPs and I hate taking money. I WILL accept money for EthStaker because it benefits all of us, and I want everyone to enjoy POAP. If you get butthurt by this kind of thing please keep in mind that our only goal is community service. There is no personal gain here.
>
> This is the first announcement of this, I'm sure things will evolve as we get closer.
---
## Criteria
1. Donate a minimum of $10 (gas fee + value) to EthStaker anytime between November 2nd, 2021 00:00:00 GMT and 24 hours after $5,000 USD is reached[^ATH].
2. Donations must be received by EthStaker at ethstaker.eth via Ethereum Mainnet, or any valid L2.
3. List of L2s:  
	* Arbitrum
	* Optimism
	* Base
	* Polygon
	* xDAI (Gnosis)
	* Did we miss one that you've used? Let me \[/u/eviljordan\], or us, know!
---
### Data, Notes, and Methodology
The ethstaker.eth ENS' underlying 0x owner address has changed a few times over the years. We only care about 0x owner addresses from November 2nd, 2021 until now. That's about 1400 days ago.

We can see ownership changes on Etherscan by looking at the [ethstaker.eth NFT transactions](https://etherscan.io/nft/0x57f1887a8bf19b14fc0df6fd9b2acc9af147ea85/19983403853102940524743945488147032720542313115197237752731031353866392940795).

Here are the relevant 0x owner addresses:
* 0xa83a92297B3d80A70cC396bf74424971A9890704 (received ownership on 2025-07-09, current as of August 24th, 2025)
* 0xF01CEe26213d1A6eaF16422241AE81f7C17B9f98 (received ownership on 2023-12-29)
* 0xD165df4296C85e780509fa1eace0150d945d49Fd (received ownership on 2020-11-28)

#### Mainnet
Etherscan makes pulling our list of potential POAP recipients easy. While one can use the API (this will come later for the L2 methods, probably, and, potentially, replace the spreadsheet method for Mainnet if I have enough time), Mainnet has a quick `EXPORT to CSV` function for both tradtional ETH transfers and ERC-20 token transfers. Here are our steps:
1. Export all Transfers from 2021-11-02 through today
2. Export all Token Transfers from 2021-11-02 through today
3. Import CSV into a spreadsheet and filter by our criteria

Concerning the traditional ETH transfer data, we are lucky that Etherscan also includes the `Historical Price` for ETH as an exported column in our data. This allows the quick addition of a new column, `Historical Value`, with the formula: `AMOUNT IN * HISTORICAL PRICE`. We can then filter on any value in this column that is `>= 10`, while also excluding any transfer that has an `AMOUNT OUT` value `> 0`. We are also only concerned with transfers with the `METHOD = "Transfer"`, but based on our other criteria, filtering on this column is unnecessary.

Concerning token transfers on Mainnet, Etherscan includes a column named `USDValueDayOfTx`[^USDValueDayOfTx] that does exactly what we hope. We can filter on this column for `>= 10` and make sure to only look at transfers `to` our 0x address.

#### L2s
All listed L2s have similar block explorers like Etherscan, so the manual extraction of the data is much the same as Mainnet.

[^ATH]: Link to ATH data source will go here.
[^USDValueDayOfTx]: For an as-of-yet unknown reason, the `USDValueDayOfTx` value is not always populated. Luckily, we're almost always dealing in stables, so it's easy to calculate, but I am unclear as to what's going on with Etherscan's export.