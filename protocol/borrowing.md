# Borrowing

## **Why would I use Eurity** **for borrowing?** <a href="#why-would-i-use-polyquity-for-borrowing" id="why-would-i-use-polyquity-for-borrowing"></a>

Eurity protocol offers **interest-free loans** and is more capital efficient than other borrowing systems (i.e. less collateral is needed for the same loan). Instead of selling Matic to have liquid funds, you can use the protocol to lock up your Matic, borrow mEUR against the collateral, and then repay your loan at some arbitrary future date.

Borrowers speculating on future ETH price increases can use the protocol to leverage their Ethereum positions up to `11 times:`$$1+\frac{1}{CollateralRatio-1}=1+\frac{1}{1.1-1}=1+\frac{1}{0.1}=1+10=11$$, increasing their exposure to price changes. This is possible because mEUR can be borrowed against ETH, sold on the open market to purchase more ETH — rinse and repeat\*

{% hint style="danger" %}
\*This is not a recommendation for how to use Eurity. Leverage can be risky and should be used only by those with experience.
{% endhint %}

## **What do you mean by collateral?** <a href="#what-do-you-mean-by-collateral" id="what-do-you-mean-by-collateral"></a>

Collateral is any asset which a borrower must provide to take out a loan, acting as a security for the debt.

{% hint style="warning" %}
Currently, ETH is the _only_ collateral type accepted by Eurity. Other collaterals may be added in future.
{% endhint %}

## **How can the protocol offer interest-free borrowing?** <a href="#how-can-the-protocol-offer-interest-free-borrowing" id="how-can-the-protocol-offer-interest-free-borrowing"></a>

The protocol charges one-time borrowing and redemption fees that algorithmically adjust based on the last redemption time. For example: If more redemptions are happening (which means mEUR is trading at less than €1), the borrowing fee would continue to increase, discouraging borrowing.

Other systems (e.g. MakerDAO) require variable interest rates to make borrowing more or less favorable, but do so implicitly since borrowers would not feel the impact upfront. Given that this also needs to be managed via governance, Eurity instead opts for a fully decentralized and direct feedback mechanism via one-off fees.

## **How can I borrow with** Eurity**?** <a href="#how-can-i-borrow-with-polyquity" id="how-can-i-borrow-with-polyquity"></a>

To borrow you must open a Vault and deposit a certain amount of collateral (ETH) to it. Then you can draw mEUR up to a collateral ratio of `110%`. A **minimum debt** of `2000 mEUR` is required.

## **What is a** Vault**?** <a href="#what-is-a-trove" id="what-is-a-trove"></a>

A Vault is where you take out and maintain your loan. Each Vault is linked to a Ethereum address and each address can have just one Vault.

Vaults maintain two balances: one is an asset (ETH) acting as collateral and the other is a debt denominated in mEUR. You can change the amount of each by adding collateral or repaying debt. As you make these balance changes, your Vault's collateral ratio changes accordingly.

{% hint style="info" %}
You can close your Vault at any time by fully paying off your debt.
{% endhint %}

## **Do I have to pay fees as a borrower?** <a href="#do-i-have-to-pay-fees-as-a-borrower" id="do-i-have-to-pay-fees-as-a-borrower"></a>

Every time you draw mEUR from your Vault, a one-off borrowing fee is charged on the drawn amount and added to your debt. Please note that the borrowing fee is variable (and determined algorithmically) and has a minimum value of `0.5%` under normal operation. The fee is `0%` during Recovery Mode.&#x20;

{% hint style="info" %}
A `200 mEUR` Liquidation Reserve charge will be applied as well, but returned to you upon repayment of debt.
{% endhint %}

## **How is the borrowing fee calculated?** <a href="#how-is-the-borrowing-fee-calculated" id="how-is-the-borrowing-fee-calculated"></a>

The borrowing fee is added to the debt of the Vault and is given by a `baseRate` . The fee rate is confined to a range between `0.5%` and `5%` and is multiplied by the amount of liquidity drawn by the borrower. For example:

> The borrowing fee stands at `0.5%` and the borrower draws `4,000 mEUR` from his open Trove. Being charged a fee of `18.91 mEUR`, the borrower will obtain `3,781.09 mEUR` after the Liquidation Reserve and issuance fee are deducted.

## **When do I need to pay my loan back?** <a href="#when-do-i-need-to-pay-my-loan-back" id="when-do-i-need-to-pay-my-loan-back"></a>

Loans issued by the protocol do not have a repayment schedule. You can leave your Vault open and repay your debt any time, as long as you maintain a collateral ratio of at least `110%`.

## What is the collateral ratio? <a href="#what-is-the-collateral-ratio" id="what-is-the-collateral-ratio"></a>

This is the ratio between the Euro value of the collateral in your Vault and its debt in mEUR. The collateral ratio of your Vault will fluctuate over time as the price of ETH changes. You can influence the ratio by adjusting your Vault's collateral and/or debt — i.e. adding more ETH collateral or paying off some of your debt.

{% hint style="info" %}
For example: Let’s say the current EUR-denominated price of ETH is `€10` and you decide to deposit `2500 ETH`. If you borrow `5000 mEUR`, then the collateral ratio for your Trove would be`500%`.

$$\frac{2500\ ETH\ * \ €10}{5000\ mEUR} * 100\% = 500\%$$​

If you instead took out `20000 mEUR`, that would put your ratio at `125%`.&#x20;
{% endhint %}

## **What is the minimum collateral ratio (MCR) and the "recommended" collateral ratio?** <a href="#what-is-the-minimum-collateral-ratio-mcr-and-the-recommended-collateral-ratio" id="what-is-the-minimum-collateral-ratio-mcr-and-the-recommended-collateral-ratio"></a>

The minimum collateral ratio (or MCR for short) is the lowest ratio of debt to collateral that will not trigger a liquidation under normal operations (aka Normal Mode). This is a protocol parameter that is set to `110%`. So if your Vault has a debt `10,000 mEUR`, you would need at least `$11,000` worth of ETH posted as collateral to avoid being liquidated.

{% hint style="info" %}
To avoid liquidation during Recovery Mode, it is recommended to keep ratio comfortably above `150%` (e.g. `200%` or better `250%`).
{% endhint %}

## **What happens if my** Vault **is liquidated?** <a href="#what-happens-if-my-trove-is-liquidated" id="what-happens-if-my-trove-is-liquidated"></a>

You lose your collateral as your debt is paid off through liquidation, i.e. you will no longer be able to retrieve your collateral by repaying your debt. A liquidation thus results in a net loss of $$100\% * 10 / 110 = 9.09\%$$ of your collateral’s nominal Euro value.

## **What is the Liquidation Reserve?** <a href="#what-is-the-liquidation-reserve" id="what-is-the-liquidation-reserve"></a>

When you open a Vault and draw a loan, `200 mEUR`is set aside as a way to compensate gas costs for the transaction sender in the event your Vault being liquidated. The Liquidation Reserve is fully refundable if your Vault is not liquidated, and is given back to you when you close your Vault by repaying your debt.&#x20;

{% hint style="success" %}
The Liquidation Reserve counts as debt and is taken into account for the calculation of a Vault's collateral ratio, slightly increasing the actual collateral requirements.
{% endhint %}

## How can you offer a collateral ratio as low as 110%? <a href="#how-can-you-offer-a-collateral-ratio-as-low-as-110" id="how-can-you-offer-a-collateral-ratio-as-low-as-110"></a>

By making liquidation instantaneous and more efficient, Eurity needs less collateral to provide the same security level as similar protocols that rely on lengthy auction mechanisms to sell off collateral in liquidations.

## **What happens if my Vault is redeemed against?**

When mEUR is redeemed, the ETH provided to the redeemer is allocated from the Vault(s) with the lowest collateral ratio (even if it is above `110%`). If at the time of redemption you have the Vault with the lowest ratio, you will give up some of your collateral, but your debt will be reduced accordingly. &#x20;

The EUR value by which your ETH collateral is reduced corresponds to the nominal mEUR amount by which your Vault's debt is decreased. You can think of redemptions as if somebody else is repaying your debt and retrieving an equivalent amount of your collateral. As a positive side effect, redemptions improve the collateral ratio of the affected Vaults, making them less risky.

{% hint style="info" %}
Redemptions that do not reduce your debt to 0 are called partial redemptions, while redemptions that fully pay off a Vault's debt are called full redemptions. In such a case, your Vault is closed, and you can claim your collateral surplus and the Liquidation Reserve at any time.&#x20;
{% endhint %}

Let’s say you own a Vault with `200` ETH collateralized and a debt of `3,200 mEUR`. The current price of ETH is `€2000`. This puts your collateral ratio (CR) at `125% (= 100% * (20 * 200) / 3,200)`. Let’s imagine this is the lowest CR in the Eurity system and look at two examples of a partial redemption and a full redemption:

**Example of a partial redemption**

Somebody redeems `1,200 mEUR` for `60` ETH  and thus repays `1,200 mEUR` of your debt, reducing it from `3,200 mEUR` to `2,000 mEUR`. In return, `60` ETH worth `€1,200`, is transferred from your Vault to the redeemer. Your collateral goes down from `200` to `140` ETH, while your collateral ratio goes up from `125%` to `140% (= 100% * (140 * 20) / 2,000)`.

**Example of a full redemption**

Somebody redeems `6,000 mEUR` for `300` ETH. Given that the redeemed amount is larger than your debt minus `200 mEUR` (set aside as a Liquidation Reserve), your debt of `3,200 mEUR` is entirely cleared and your collateral gets reduced by `€3,000` of ETH, leaving you with a collateral of`50 ETH (= 2 - 3,000 / 20)`.

## **Why did the collateral and debt of my** Vault **increase without my intervention?** <a href="#why-did-the-collateral-and-debt-of-my-trove-increase-without-my-intervention" id="why-did-the-collateral-and-debt-of-my-trove-increase-without-my-intervention"></a>

If Vaults are liquidated and the Stability Pool is empty (or gets emptied due to the liquidation), every borrower will receive a portion of the liquidated collateral and debt as part of a redistribution process.
