Absorption Mechanism
********************************************************************************

No NewSD is mint out of thin air, nor to anyone will. NewSD must be exchanged with NTY by the market demand itself. There are 3 conditions for an absorption to be triggered.

    #. Passive
    #. Active
    #. Preemptive

Passive Absorption (PA)
================================================================================

Passive absorption is triggered when there is no absorption for a week. This is the most defensive supply absorption mechanism to make sure the supply will continuously adjust to even the smallest change of demand, when the network is mature and well adopted.

For Passive and Active conditions, *AbsorptionRate* is always the the Current Median Price derivation.

    ``PriceDerivation = MedianPrice - 1.0``

    ``AbsorptionRate = X/S = PriceDerivation``

Where X is the amount of NewSD to absorb, and S is the current supply of NewSD.

Active Absorption (AA)
================================================================================

Active absorption is triggered when the price level is disruptively changed in an exponential ways, to quickly adjust to a new demand waves.

With

    ``DerivationRate = PriceDerivation / LastAbsorptionRate``

An active absorption is triggered when

    ``DerivationRate >= 2 OR DerivationRate <= -1/2``

When the price keeps going in the same direction (up or down), the next Active Absorption Rate must be at least two times as large as the last one. This condition allows the network quickly adjust to the sudden change of market demand, but still makes it exponentially expensive for adversaries to manipulate the price of NewSD.

When the price is changing in one direction (from up to down, or vice versa), the next Active Absorption Rate must be at least half as large as the last one, in opposite direction. This change of direction allow the network to wind down the absorption in a stabilizing market.

..  image:: /img/NewSD-Absorption.png

Preemptive Absorption (PeA)
================================================================================

This is the most complicated mechanism of absorption, but provide the necessary flexibility to adjust the supply without waiting for a price to be deviated too far from an anchoring value. Anyone can initialize a preemptive absorption, but with a stake and a price. PeA requires an voting auction before and Lockdown after the absorption.

Requirements
--------------------------------------------------------------------------------

    * No other *PeA* or Lockdown is in active. (Other 2 absorptions are allowed)
    * Absorption Rate ``(X/S) >= 4 * MedianPriceRate``. (S is the current supply of NewSD)
    * An amount of NTY equal to X/2 NewSD has to be locked for The Lockdown Duration. (for slashing condition)

Auction for Initiator
--------------------------------------------------------------------------------

The Auction for Initiator starts when the first intiator submits her proposal on chain. Proposal can only start after the last Pre-emptive Absorption finished, regardless of the other 2 absorptions. In one week of Auction, more candidates can submit their proposals, and NTY holders will vote for them as soon as the proposal is submitted. Each vote can have the following values:

    * Proposal ID
    * Vote: Approve or Reject
    * LockdownDuration in blocks (optional), a consensus policy parameter, initialized with ``2 * PriceSamplingDuration``.
    * SlashingRate (optional) - the rate of locked NTY will be burnt, another consensus policy parameter, initialized with ``AbsorptionDuration/LockdownDuration``.

LockdownDuration or SlashingRate is included in the Vote only when the voter want to change the parameters, otherwise, the current value is used for the next PeA.

After the Auction ends, the proposal with the highest Approvals/Rejections rate and Approvals > Rejections wins the Auction, and init a new Pre-emptive Absorption.

Preemptive Absorption Process
--------------------------------------------------------------------------------

After the Voting Auction success, a new Pre-emptive Absorption is triggered with (X, LockdownDuration, SlashingRate). Where X is the amount of NewSD will be absorbed.

    1. The absorption process is exactly the same with Active and Passive Absorption.
    2. PeA is treated exactly as Active and Passive Absorption: will override any on-going AA/PA, and will be overriden by new AA/PA if their condition is met.
    3. A Lockdown is started independently with the absorption process. Lockdown prevents new PeA, but does not prevent new AA/PA. Lockdown is not canceled/aborted when by new AA/PA.

The Lockdown
--------------------------------------------------------------------------------

During the Lockdown time:

    ``Y/2 = NTYAmountToFill(X/2)`` is locked.

    Any block with ``Sign(d) = -Sign(X)``, an amount of NTY is burnt

    ``d = MedianPriceDeviation``

    ``D = X/S``

    ``NTYToBurn = |d/D| * SlashingRate/LockdownDuration``

Effects
--------------------------------------------------------------------------------

    * X/2 of NewSD will be absorbed (just like active/passive absorption).
    * For each order is filled above, one more order with the same value is filled for Initiator.
    * For the next 2 weeks after the Pre-emptive Absorption is triggered.

Conclusion
--------------------------------------------------------------------------------

Preemptive Absorption initiators are market makers, "bank" reserves, OTC dealers which are in control of large flows of money (NewSD). Not sitting outside of the system nor being centralized in anyway, they profit themselves by reserving and trading large amount of money (NewSD) while providing a high level of liquidity and stability to the network. As part of the decentralized system, anyone can be the Initiator, but without a large amount of fund, everyone can still be traders. NTY holders, initiators and traders together form a decentralized circle of stabilization, where each and everyone can profit themselves while provide the liquidity of NewSD as a service to the user of the network.
