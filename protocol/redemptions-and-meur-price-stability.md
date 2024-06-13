# Redemptions & mEUR Price Stability

## How does mEUR closely follow Euro price? <a href="#how-does-pusd-closely-follow-the-price-of-usd" id="how-does-pusd-closely-follow-the-price-of-usd"></a>

{% hint style="info" %}
Eurity uses oracle contracts to gather EUR/USD and ETH/USD prices from major exchanges. Then ETH/EUR price is calculated as follows: $$ETH/EUR = \frac{ETH/USD}{EUR/USD}$$, e.g. $$\frac{1.4292}{1.17564}=1.2156782689$$.
{% endhint %}

The ability to redeem mEUR for ETH at face value (i.e. 1 mEUR for €1 of ETH) and the minimum collateral ratio of `110%` create virtual price floor and price ceiling (respectively) through arbitrage opportunities. We call these "hard peg mechanisms" since they are based on direct processes.

mEUR also benefits from less direct mechanisms for EUR parity — called "soft peg mechanisms". One of these mechanisms is parity as a Schelling point. Since Eurity treats mEUR as being equal to Euro, parity between the two is an implied equilibrium state of the protocol. Another of these mechanisms is the borrowing fee on new debts.&#x20;

{% hint style="info" %}
As redemptions increase (e.g. _mEUR < €1_), so does the `baseRate` — making borrowing less attractive which keeps new mEUR from hitting the market and driving the price further below.
{% endhint %}

## What are redemptions? <a href="#what-are-redemptions" id="what-are-redemptions"></a>

Users can redeem their mEUR for ETH at any time without limitations. However, a redemption fee might be charged on the redeemed amount.

## Is a redemption the same as paying back my debt?  <a href="#is-a-redemption-the-same-as-paying-back-my-debt" id="is-a-redemption-the-same-as-paying-back-my-debt"></a>

No, redemptions are a completely **separate mechanism**. All one has to do to pay back their debt is adjust their Trove's debt and collateral.

## How is the redemption fee calculated? <a href="#how-is-the-redemption-fee-calculated" id="how-is-the-redemption-fee-calculated"></a>

Under normal operation, the redemption fee is given by the formula &#x20;

## How is the `baseRate` calculated? <a href="#how-is-the-baserate-calculated" id="how-is-the-baserate-calculated"></a>

Redemption fees are based on the `baseRate` state variable in Eurity, which is dynamically updated. The `baseRate` increases with each redemption, and decays according to time passed since the last fee event - i.e. the last redemption or issuance of mEUR.

Upon each redemption:

* `baseRate` is decayed based on time passed since the last fee event
* `baseRate` is incremented by an amount proportional to the fraction of the total mEUR supply that was redeemed
* The redemption fee is given by $$baseRate * ETH_{Drawn}$$&#x20;

## As a borrower, do I lose money if I'm redeemed against?  <a href="#as-a-borrower-do-i-lose-money-if-im-redeemed-against" id="as-a-borrower-do-i-lose-money-if-im-redeemed-against"></a>

If your Vaults is redeemed against, you _do not_ incur a net loss. A redemption is the process of exchanging mEUR for ETH at face value, as if 1 mEUR is worth exactly €1. That is, for _x_ mEUR you get _x_ Euro worth of Matic in return. However, you will lose some of your MATIC exposure.&#x20;

{% hint style="success" %}
Your Vault's collateral ratio will also improve after a redemption.
{% endhint %}

## How can I avoid being redeemed against?  <a href="#how-can-i-avoid-being-redeemed-against" id="how-can-i-avoid-being-redeemed-against"></a>

The best way to avoid being redeemed against is by maintaining a high collateral ratio **relative to the rest** of the Vaults in the system.&#x20;

{% hint style="warning" %}
The riskiest Vaults (i.e. lowest collateralized Vaults) are first in line when a redemption takes place.
{% endhint %}
