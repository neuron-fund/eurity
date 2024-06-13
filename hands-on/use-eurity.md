# Use Eurity

## Glossary‌ <a href="#d5c2" id="d5c2"></a>

**Borrowing Fee** — The Borrowing Fee is a one-off fee charged as a percentage of the borrowed amount (in mEUR) and is part of a Vault's debt. The fee varies between 0.5% and 5% depending on mEUR redemption volume.‌

**TVL**— The Total Value Locked (TVL) is the total value locked as collateral in the system, given in MATIC and EUR.‌

**Vaults** — The total number of active Vaults in the system.‌

**mEUR supply** — The total mEUR minted by the Eurity Protocol.‌

**mEUR in Stability Pool** — The total mEUR currently held in the Stability Pool, expressed as an amount and a fraction of the mEUR supply.‌

**Staked ERTY** — The total amount of ERTY that is staked for earning fee revenue.‌

**Total Collateral Ratio** — The ratio of the Euro value of the entire system collateral at the current ETH/EUR price, to the entire system debt.‌

**Recovery Mode** — Recovery Mode is activated when the Total Collateral Ratio (TCR) falls below 150%. When active, your Vault can be liquidated if its collateral ratio is below the TCR. The maximum collateral you can lose from liquidation is capped at 110% of your Vault's debt. Operations are also restricted which would negatively impact the TCR.

## mEUR Stablecoin <a href="#id-336c" id="id-336c"></a>

mEUR is the [EUR-pegged stablecoin](../tokenomics/distribution/meur-stablecoin.md) used to pay out loans on the Eurity protocol. At any time it can be redeemed against the underlying collateral at face value.

mEUR will be minted when users deposit collateral (ETH) and open troves. The mechanism for its price stability is described in our [corresponding article](../protocol/redemptions-and-meur-price-stability.md).

## ERTY Token <a href="#aaa0" id="aaa0"></a>

ERTY is [the secondary token](../tokenomics/distribution/erty-token.md) issued by Eurity. It captures the fee revenue that is generated by the system and incentivizes early adopters.

## Vault <a href="#id-3124" id="id-3124"></a>

The Vault section is where you will maintain your loan. Here you will be able to add/remove ETH as collateral as well as manage your debt.‌

Note that each Ethereum address is only able to have one Vault.

**Deposit** — The amount in ETH staked as security for repayment of your loan‌

**Debt** — The amount of mEUR borrowed.‌

**Liquidation Reserve** — An amount set aside to cover the liquidator’s gas costs if your Vault needs to be liquidated. The amount increases your debt and is refunded if you close your Vault by fully paying off its net debt.‌

**Borrowing Fee** — This amount is deducted from the borrowed amount as a one-time fee. There are no recurring fees for borrowing, which is thus interest-free.‌

**Collateral ratio** — The ratio between the dollar value of the collateral and the debt (in mEUR) you are depositing. While the Minimum Collateral Ratio is 110% during normal operation, it is recommended to keep the Collateral Ratio always above 150% to avoid liquidation under Recovery Mode. A Collateral Ratio above 200% or 250% is recommended for additional safety.

### How to open a Vault? <a href="#id-5285" id="id-5285"></a>

Open a Vault to mint mEUR debt against your ETH:

1\) Enter the amount of ETH collateral you wish to use. The Collateral Ratio needs to be above 110% or above 150% in Recovery Mode

2\) Enter a Borrow value greater than the current minimum (please see [Borrowing](../protocol/borrowing.md))

3\) Confirm the amount of ETH deposit and mEUR displayed at the bottom info section‌

4\) Click “Confirm”‌

## Stability Pool‌ <a href="#id-331d" id="id-331d"></a>

The Stability Pool acts as a cushion to make the platform more stable. If you provide mEUR to this pool you will be able to earn some extra rewards.‌

Deposit your mEUR into the Stability Pool to earn rewards in ERTY token.‌

1\) Click the “Stake mEUR” button‌

2\) Enter the amount of mEUR you wish to enter‌

3\) Click the “Confirm” button

## Staking‌ ERTY to earn protocol fees <a href="#id-6067" id="id-6067"></a>

Stake the ERTY you earn to receive protocol income and transfer fee in mEUR and MATIC.

### Start Staking‌ <a href="#e4f4" id="e4f4"></a>

1\) Click the “Stake ERTY” button‌

2\) Enter the amount of ERTY you’d like to stake.‌

3\) Click the “Confirm” button

Claim your Staking reward by clicking the “Claim gains” button and approving the transaction.

## Farm‌ <a href="#d2a3" id="d2a3"></a>

You can also earn ERTY by providing liquidity to mEUR and ERTY tokens on major decentralized exchanges.

## Liquidations <a href="#liquidate" id="liquidate"></a>

To ensure that the entire stablecoin supply remains fully backed by collateral, Vaults that fall under the minimum collateral ratio of `110%` will be closed (liquidated).

The debt of the Vault is canceled and absorbed by the Stability Pool and its collateral is distributed among Stability Providers.

The owner of the Vaults still keeps the full amount of mEUR borrowed but loses `~10%` value overall hence it is critical to always keep the ratio above `110%`, ideally above `150%`.

## Redemption‌ <a href="#id-664e" id="id-664e"></a>

Redemption is a process of exchanging mEUR for ETH at face value, e.g. 1 mEUR is exactly worth €1. That is, for _x_ mEUR you get € _x_ worth of Ethereum in return.‌

{% hint style="warning" %}
Users can redeem their mEUR for ETH at any time without limitations. However, a redemption fee might be charged on the redeemed amount.‌

mEUR redemption is disabled for the first 14 days after launch.
{% endhint %}

​

​