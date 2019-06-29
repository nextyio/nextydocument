Linux
********************************************************************************

#. Download binary release Gonex from github:

``wget https://github.com/nextyio/gonex/archive/v2.0.1.tar.gz -O gonex.gz``

* Extract then gunzip gonex file:

``gunzip gonex.gz``

* Grant run permission:

``chmod +x ./gonex``

#. Create new account (wallet):

* Enter the following commands in command prompt to create a new account (wallet):

``./gonex account new``

* Enter passphrase, and confirm passphrase, then the wallet display the ``Address``

#. Start a simple node:

``gonex --ethstats "NameOfNode:nty2018@stats.nexty.io" console``

View coinbase Address

``eth.coinbase``

#. Start a miner node:

* Create a text file containing the password you typed above

``echo Your-Password-Of-Wallet >> sealer_password.txt``

* Initiate miner node:

``./gonex -- ethstats "NameOfNode:nty2018@stats.nexty.io" -- unlock "[eth.coinbase]" -- password “sealer_password.txt" -- etherbase "[eth.coinbase]" -- mine console``

Example:

``./gonex --ethstats "WilliamDaFren:nty2018@stats.nexty.io" --unlock  "0xc74ebc22341092ef8caaa989f2f05e44f0ee25bc "  --password "sealer_password.txt" --etherbase "0xc74ebc22341092ef8caaa989f2f05e44f0ee25bc"  --mine console``

After the node is successfully deployed, go to `Nextats <https://stats.nexty.io/>`_ to check if your node is deployed on the network.

