################################################################################
Withdraw
################################################################################

* 7.1.	Withdraw NTY

In Tab Wallets:

Limit for today: Display the permitted amount of withdrawal per day without confirmation.
Click Withdraw, enter the amount and click send transaction to execute withdrawal.

-	If the amount <= limit for today. Transaction is executed without approval from other owners.
-	If the amount > limit for today. Transaction is pending for approval from other owners. 
-	If the number of owner confirmations is equal to required confirmations, transaction is executed. 
-	If the number of owner confirmations is less than required confirmations, transaction is forfeited.

* 7.2.	Withdraw token

In detailed multisig wallet display, go to Tokens:

``Name``: Token name
``Multisig balance``: Multisig wallet balance.
``Account balance``: Number of existing tokens in owner wallet.
Click ``Withdraw`` to display Withdraw token:
``Amount``: Enter number of withdrawal token.
``Destination``: Enter receiving wallet.
Click ``Send`` multisig transaction to execute transaction.
