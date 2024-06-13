# Stability Pool & Liquidations

## What is the Stability Pool? <a href="#what-is-the-stability-pool" id="what-is-the-stability-pool"></a>

The Stability Pool is the first line of defense in maintaining system solvency. It achieves that by acting as the source of liquidity to repay debt from liquidated Vaults —ensuring that the total mEUR supply always remains backed.

{% hint style="info" %}
When any Vault is liquidated, an amount of mEUR corresponding to the remaining debt of the Vault is burned from the Stability Pool’s balance to repay its debt. In exchange, the entire collateral from the Vault is transferred to the Stability Pool.
{% endhint %}

The Stability Pool is funded by users transferring mEUR into it (called Stability Providers). Over time Stability Providers lose a pro-rata share of their mEUR deposits, while gaining a pro-rata share of the liquidated collateral. However, because Vaults are likely to be liquidated at just below `110%` collateral ratios, it is expected that Stability Providers will receive a greater dollar-value of collateral relative to the debt they pay off.

## Why should I deposit mEUR to the Stability Pool? <a href="#why-should-i-deposit-pusd-to-the-stability-pool" id="why-should-i-deposit-pusd-to-the-stability-pool"></a>

Stability Providers will make liquidation gains (see below) and receive early adopter rewards in form of ERTY tokens.

## What are liquidations? <a href="#what-are-liquidations" id="what-are-liquidations"></a>

To ensure that the entire stablecoin supply remains fully backed by collateral, Vaults that fall under the minimum collateral ratio of `110%` will be closed (liquidated).

The debt of the Vault is canceled and absorbed by the Stability Pool and its collateral distributed among Stability Providers.

The owner of the Vault still keeps the full amount of mEUR borrowed but loses `~10% (9.09%)` value overall hence it is critical to always keep the ratio above `110%`, ideally above `150%`.

## Who can liquidate Vaults?  <a href="#who-can-liquidate-troves" id="who-can-liquidate-troves"></a>

Anybody can liquidate a Vault as soon as it drops below the Minimum Collateral Ratio of `110%`. The initiator receives a gas compensation (`10 mEUR` + `0.5%` of the Vault's collateral) as reward for this service.

## How am I compensated for liquidating a Vault? <a href="#how-am-i-compensated-for-liquidating-a-trove" id="how-am-i-compensated-for-liquidating-a-trove"></a>

The liquidation of Vaults is connected with certain gas costs which the initiator has to cover. The cost per Vault was reduced by implementing batch liquidations of up to 95 Vaults but with the aim of ensuring that liquidations remain profitable even in times of soaring gas prices the protocol offers a gas compensation given by the following formula:

$$
Gas\ compensation = 200_{mEUR} + 0.5\%*Trove's\  collateral_{ETH}
$$

{% hint style="info" %}
The `200 mEUR` is funded by a Liquidation Reserve while the variable `0.5%` ETH part comes from the liquidated collateral, slightly reducing the liquidation gain for Stability Providers.
{% endhint %}

## How do I benefit as a Stability Provider from liquidations? <a href="#how-do-i-benefit-as-a-stability-provider-from-liquidations" id="how-do-i-benefit-as-a-stability-provider-from-liquidations"></a>

As liquidations happen just below a collateral ratio of `110%`, you will most likely experience a net gain whenever a Vault is liquidated.

## How do I benefit as a Stability Provider from early adopter rewards? <a href="#how-do-i-benefit-as-a-stability-provider-from-early-adopter-rewards" id="how-do-i-benefit-as-a-stability-provider-from-early-adopter-rewards"></a>

First you need to open a Vault, borrow mEUR, and deposit it to the Stability Pool. After making your deposit, you will start accumulating a reward (in ERTY) proportional to the size of your deposit on a continuous basis.&#x20;

{% hint style="success" %}
At any point in time, you can withdraw your pending rewards to your ETH address.
{% endhint %}

The reward is calculated according to the rewards schedule and the kickback rate of the front end that you used for making the deposit. Rewards will be the highest for early adopters of the system.

## Can I withdraw my deposit whenever I want? <a href="#can-i-withdraw-my-deposit-whenever-i-want" id="can-i-withdraw-my-deposit-whenever-i-want"></a>

As a general rule, you can withdraw the deposit made to the Stability Pool at any time. There is no minimum lockup duration. However, withdrawals are temporarily suspended whenever there are Vaults subject to liquidation with a collateral ratio below `110%` that have not been liquidated yet.

## Can I lose money by depositing funds to the Stability Pool? <a href="#can-i-lose-money-by-depositing-funds-to-the-stability-pool" id="can-i-lose-money-by-depositing-funds-to-the-stability-pool"></a>

While liquidations will occur at a collateral ratio well above `100%` most of the time, it is theoretically possible that a Vault gets liquidated below `100%` in a flash crash or due to an oracle failure. In such a case, you may experience a loss since the collateral gain will be smaller than the reduction of your deposit.

With mEUR trading above `€1`, liquidations may become unprofitable for Stability Providers even at collateral ratios higher than `100%`. However, this loss is hypothetical since mEUR is expected to return to the peg, so the “loss” only materializes if you had withdrawn your deposit and sold the mEUR at a price above `€1`.

{% hint style="warning" %}
Although the system is thoroughly audited, a hack or a bug that results in losses for the users can never be fully excluded.
{% endhint %}

## What happens if the Stability Pool is empty when liquidations occur?  <a href="#what-happens-if-the-stability-pool-is-empty-when-liquidations-occur" id="what-happens-if-the-stability-pool-is-empty-when-liquidations-occur"></a>

If the Stability Pool is empty, the system uses a secondary liquidation mechanism called redistribution. In such a case, the system redistributes the debt and collateral from liquidated Vaults to all other existing Vaults. The redistribution of debt and collateral is done in proportion to the recipient Vault's collateral amount.
