# FAQ

## **Overview** <a href="#overview" id="overview"></a>

We **strongly recommend** every user study the Liquity Protocol carefully before using Eurity. You can have a look at [official Liquity documentation](https://docs.liquity.org/) for more details, or join our community and discuss it.

Eurity is **a fork of the Liquity,** which is a decentralized borrowing protocol on Ethereum. Therefore, we will quote the [official content](https://docs.liquity.org/) to introduce how it works.

## **How does** Eurity **work?** <a href="#how-does-polyquity-work" id="how-does-polyquity-work"></a>

Eurity is a decentralized borrowing protocol that allows you to mint mEUR tokens with 0% interest loans against ETH used as collateral. mEUR borrowing is decentralized and non-custodial: only users have control over their funds.&#x20;

### What are the main use cases of Eurity? <a href="#what-are-the-main-use-cases-of-polyquity" id="what-are-the-main-use-cases-of-polyquity"></a>

There are quite a bit, actually. Please see [Use cases](../use-cases.md).

### What are mEUR and ERTY? <a href="#what-are-pusd-and-pyq" id="what-are-pusd-and-pyq"></a>

mEUR is the EUR-pegged stablecoin used to pay out loans on the Eurity protocol. **At any time** it can be redeemed against the underlying collateral at face value. [Learn more](stability-pool-and-liquidations.md) about the stability mechanism.

ERTY is the secondary token issued by Eurity. It captures fee revenue generated by the protocol and incentivizes early adopters and frontends. Total ERTY supply is capped at `1,000,000,000 tokens`.

### Does Eurity charge any fees? <a href="#does-polyquity-charge-any-fees" id="does-polyquity-charge-any-fees"></a>

There is a one-off fee whenever mEUR is borrowed, and when mEUR is redeemed:

* For borrowers, there is a borrowing fee on loans as a percentage of the drawn amount (in mEUR).
* For redeemers, there is a redemption fee on the amount paid to users by the system (in Matic) when exchanging mEUR for ETH.&#x20;

{% hint style="success" %}
Note that redemption is separate from repaying your loan as a borrower, which is **free of charge**.
{% endhint %}

Both fees **depend on redemption volumes**, i.e. they increase upon every redemption as a function of the redeemed amount, and decay over time as long as no redemptions take place. The intent is to throttle large redemptions with higher fees, and to throttle borrowing directly after large redemption volumes. The fee decay over time ensures that the fee for both borrowers and redeemers will “cool down”, while redemptions volumes are low.

The fees **cannot become smaller** than `0.5%` (except in Recovery Mode), which protects the redemption facility from being misused by arbitrageurs front-running the price feed. The **borrowing fee is capped** at`5%`, keeping the system (somewhat) attractive for borrowers even in phases where the monetary is contracting due to redemptions. Other than that, the two fees are identical and are depicted as "Fee" in the following exemplary chart:

![](https://gblobscdn.gitbook.com/assets%2F-Mcd65GKAsFArnI3YgzB%2F-McfFmrQfrD-iLMSzXwY%2F-McfG1dto-MIayxgOlV5%2Fimage.png?alt=media\&token=91e7ed12-1567-4b23-ada9-db899de9d69b)

​

### How can I earn money using Eurity? <a href="#how-can-i-earn-money-using-polyquity" id="how-can-i-earn-money-using-polyquity"></a>

There are different ways to generate revenue using Eurity:

* **Deposit mEUR** to the Stability Pool and earn liquidation gains (in ETH) in addition to ERTY rewards.
* **Stake ERTY** and earn mEUR and ETH revenue from borrowing and redemption fees.
* **Provide liquidity** for mEUR or ERTY tokens on DEXes and stake LP tokens in Farms.

### Can I lose my funds? <a href="#can-i-lose-my-funds" id="can-i-lose-my-funds"></a>

As a **non-custodial** system, all the tokens sent to the protocol will be held and managed algorithmically without the interference of any person or legal entity. That means your funds will only be subject to the rules set forth in the smart contract code.

{% hint style="info" %}
Please note that a hack or a bug that results in losses for the users **can never be fully excluded.**
{% endhint %}

There are two scenarios under which you may lose a part of your funds:

* You are a borrower (Vault owner) and your collateral in ETH is liquidated. You will still keep your borrowed mEUR, but your Trove will be closed and your collateral will be used to compensate Stability Pool depositors.
* You are a Stability Pool depositor and your deposited mEUR is used to repay debt from liquidated borrowers. Since liquidations are triggered any time borrowers’ collateral drops below `110%`, you will receive more ETH in return with a very high probability.&#x20;

{% hint style="warning" %}
If ETH decreases in price and you maintain exposure, you may still lose value in your total pool deposits.
{% endhint %}
