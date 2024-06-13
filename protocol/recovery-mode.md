# Recovery Mode

## What is Recovery Mode?  <a href="#what-is-recovery-mode" id="what-is-recovery-mode"></a>

Recovery Mode kicks in when the Total Collateral Ratio (TCR) of the system falls below `150%`.

During Recovery Mode, Vaults with a collateral ratio **below the TCR** (i.e. in the worst case up to `150%`) can be liquidated.

Moreover, the system blocks borrower transactions that would further decrease the TCR. New mEUR may only be issued by adjusting existing Vaults in a way that improves their collateral ratio, or by opening a new Vault with a collateral ratio`>=150%`. In general, if an existing Vault's adjustment reduces its collateral ratio, the transaction is only executed if the resulting TCR is above `150%`.

## What is the Total Collateral Ratio? <a href="#what-is-the-total-collateral-ratio" id="what-is-the-total-collateral-ratio"></a>

The Total Collateral Ratio or TCR is the ratio of the Euro value of the entire system collateral at the current ETH/EUR price, to the entire system debt. In other words, it's the sum of the collateral of all Vaults expressed in Euro, divided by the debt of all Vaults expressed in mEUR.

## What is the purpose of Recovery Mode?  <a href="#what-is-the-purpose-of-recovery-mode" id="what-is-the-purpose-of-recovery-mode"></a>

{% hint style="info" %}
The goal of Recovery Mode is to incentivize borrowers to behave in ways that promptly raise the TCR back above 150%, and to incentivize mEUR holders to replenish the Stability Pool.
{% endhint %}

Economically, Recovery Mode is designed to encourage collateral top-ups and debt repayments, and also itself acts as a self-negating deterrent: the possibility of it occurring actually guides the system away from ever reaching it. Recovery Mode is not a desirable state for the system.

## **What are the fees during Recovery Mode?** <a href="#what-are-the-fees-during-recovery-mode" id="what-are-the-fees-during-recovery-mode"></a>

While Recovery Mode has no impact on the redemption fee, the borrowing fee is set to `0%` to **maximally encourage borrowing** (within the limits described above).

## **How can I make my Vault safe in Recovery Mode?** <a href="#how-can-i-make-my-trove-safe-in-recovery-mode" id="how-can-i-make-my-trove-safe-in-recovery-mode"></a>

By increasing your collateral ratio to `150%` or greater, your Vault will be protected from liquidation. This can be done by adding collateral, repaying debt, or both.

## Can I be liquidated if my collateral ratio is below `150%` in Recovery Mode?  <a href="#can-i-be-liquidated-if-my-collateral-ratio-is-below-150-in-recovery-mode" id="can-i-be-liquidated-if-my-collateral-ratio-is-below-150-in-recovery-mode"></a>

Yes, you can be liquidated below `150%` if your Vault's collateral ratio is smaller than the TCR. In order to avoid liquidation in Normal Mode and Recovery Mode, a user should keep their collateral ratio above `150%`.

## How do liquidations work in Recovery Mode?  <a href="#how-do-liquidations-work-in-recovery-mode" id="how-do-liquidations-work-in-recovery-mode"></a>

* ICR = Individual Collateral Ratio
* MCR = Minimum Collateral Ratio
* TCR = Total Collateral Ratio
* SP = Stability Pool

| Condition                                               | Liquidation Behavior                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ICR <=100%                                              | ETH all debt and collateral (minus ETH gas compensation) to active Vaults.                                                                                                                                                                                                                                                                                                                        |
| 100% < ICR < MCR & SP mEUR > Vault debt                 | mEUR in the Stability Pool equal to the Trove's debt is offset with the Vault's debt. The Vault's ETH collateral (minus ETH gas compensation) is shared between depositors.                                                                                                                                                                                                                       |
| 100% < ICR < 150% & SP mEUR < Vault debt                | The total Stability Pool mEUR is offset with an equal amount of debt from the Trove. A fraction of the Vault's collateral (equal to the ratio of its offset debt to its entire debt) is shared between depositors. The remaining debt and collateral (minus ETHIC gas compensation) is redistributed to active Vaults.                                                                            |
| MCR <= ICR < 150% & SP mEUR >= Vault debt               | The Stability Pool mEUR is offset with an equal amount of debt from the Vault. A fraction of ETH collateral with dollar value equal to `1.1 * debt` is shared between depositors. Nothing is redistributed to other active Vaults. Since its ICR was `> 1.1`, the Vault has a collateral remainder, which is sent to the `CollSurplusPool` and is claimable by the borrower. The Vault is closed. |
| MCR <= ICR < 150% & SP mEUR < Vault debt                | Do nothing.                                                                                                                                                                                                                                                                                                                                                                                       |
| ICR >= 150%                                             | Do nothing.                                                                                                                                                                                                                                                                                                                                                                                       |

## How much of a Vault's collateral can be liquidated in Recovery Mode?  <a href="#how-much-of-a-troves-collateral-can-be-liquidated-in-recovery-mode" id="how-much-of-a-troves-collateral-can-be-liquidated-in-recovery-mode"></a>

In Recovery Mode, liquidation loss is capped at `110%` of a Vault's collateral. Any remainder, i.e. the collateral above `110%` (and below the TCR), can be reclaimed by the liquidated borrower using the standard web interface.

This means that a borrower will face the same liquidation “penalty” (`10%`) in Recovery Mode as in Normal Mode if their Vault gets liquidated.
