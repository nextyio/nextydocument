Price Evaluation
********************************************************************************

How much does an NewSD worth?
================================================================================

NewSD price can be fed using API of centralized exchanges, if they are trustworthy. Most of the time, they are not. Crypto exchanges are famous (or rather infamous) for their fake volume, market marking and shorting bots. The price of any asset can be easily manipulated with no cost at all. Setting out as a decentralized trustless stablecoin, depending on centralized exchanges is the risk that NewSD would not take.

    "Market value or OMV (Open Market Valuation) is the price at which an asset would trade in a competitive auction setting."

To find a market value of an asset, people has to actually get their asses to the market and try to buy and sell it themselves. A price oracle can gauge the market price only by perform the trading, using their own asset and currency. The principle is, if you can sell an asset in an open market with price X, then its market price is at least X. And if you can buy an asset with price Y, then its market price is at most Y. This assumption holds true for a significant volume of the trading order, in a widely open market, and in a timely fashion.

With high liquidity and trading volume, centralized exchanges could be a good marketplace to gauge the price, but not the only options. When even no exchange is available, or closed, oracle can always go to black markets to gauge the price, and feed it the consensus.

The price evaluation process is called **Price Gauging**, because real order with real asset has to be traded to estimate the price. For a volatile asset, this process brings great risks to the Oracles, but for a stablecoin, it's economically much safer.

If the target exchange has an exchange fee of 0.2%, then the Oracle will not lose money by selling no less than $1.002, or buying no more than $0.998.


``ExchangeFeeRate = 0.002``

``MinSellingPrice = 1.0 + ExchangeFeeRate``

``MaxBuyingPrice = 1.0 - ExchangeFeeRate``


To gauge the selling price, Oracle will following these steps:

    #. Fetch the LastSellingPrice from exchange API (for reference, not to trust)
    #. If the LastSellingPrice < 1.0, Oracle will book a limit **buying order** of MaxBuyingPrice. The filled prices will (be) the correct selling Price and stop the process.
    #. Otherwise, use a binary search process to find the most correct market price from [MinSellingPrice, (LastSellingPrice - 1 PIP) * 2 - 1.0] (where PIP is the smallest step of exchange price)
    #. The correct price is higher if the order is filled within a configurable timeout (10 mins), and it will be lower if the order is not filled within that time.
    #. If no order can be filled, then the stablecoin does not have enough liquidity. No price will be fed to the consensus.

The same process can be applied to gauge the buying price.