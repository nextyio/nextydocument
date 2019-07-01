Nexty Governance
********************************************************************************

Login
================================================================================

After a node is set up, users should login Nexty Governance to become a sealer.
Open your web browser, go to `Nexty Governance <https://governance.nexty.io/login>`_

#. Using **Nexty Wallet** Private Key 

*This is not recommended for Login because of potential security breach*

Enter your private key, then click **Login** to continue.

#. Using **Metamask**

* Go to `Metamask <https://metamask.io/>`_

* If you don't know how to use Metamask, please watch their **How It Works** video

* After having completed the transaction, you can find Metamask icon on Extension taskbar (typically located on the top-right corner of the browser)

* Create your account (Remember to save your backup phrase)

* A window will appear, on top of the window, click on the dropdown button, then **Custom RPC** (We are using the same RPC in *How To Create Token on Nexty*)

* Scroll down to find **New Network** tab, then enter https://rpc.nexty.io in **New RPC URL**, **ChainID**: 66666, **Symbol**: NTY, **Nickname**: Nexty.

Dashboard
================================================================================

After login Nexty Governance, Dashboard displays the following information:

* **Holding** is the current amount of NTF available in Wallet

* **Deposited** is the current ammount of NTF deposited into Nexty Governance

* **Status** is the status of your wallet in Nexty Governance

* **Coinbase** Sealer's coinbase address

NTF Transfer
================================================================================

* Nexty Governance allows user to transfer NTF between accounts

* To transfer NTF to other address, input destination address into **To address** (The address must be ERC20 format)

* User inputs amount of NTF to transfer then click **Send**

* A confirmation pop-up window will appear, click **Yes** to confirm, or **No** to cancel

* After the transaction is processed and completed, a notification window will display *Transferred success*

Deposit
================================================================================

This is where user deposit NTF into Nexty Governance to become a sealer.

* **Your balance** is the amount of NTF are available in your wallet

* **Deposited** is the amount of NTF you deposited

* **Amount** Enter the amount you want to deposit

*The valid amount of NTF entered must be a positive integer, greater than 0 and less than or equal to your existing amount*

* A confirmation pop-up window will appear, click **Yes** to confirm, or **No** to cancel

Withdraw
================================================================================

Users can withdraw the amount of money they have deposited if they did not registered as Sealer. If the user is already a Sealer, they can not withdraw. When leaving the group, the amount of money users deposited will be locked in a period of time. After that, users can withdraw.

Management
================================================================================

* **Minimum to join** is the minimum amount of NTF necessary to participate in sealing

* **Status** JOINED/ NOT JOINED

* **Signer address** The account address that sealer will use to sign when sealing block and receive rewards on their NTF token-holding address 

*You can grab Signer address from [eth.coinbase] as generated/configured in gonex*

* Requirements:

❖   A participant should deposit at least 50,000 NTF into registration contract

❖   A participant need to set their Signer address to seal the block

* Click **Join** button to complete the action, click **Yes** to confirm, or **No** to cancel

*Deposited amount will be locked after leaving Nexty Governance*

* Sealer clicks **Leave** to exit from Nexty Governance

* **Lock duration after leaving** is the duration that NTF is locked after leaving

* After user has left Nexty Governance, a notification window will display *Left success*

Logout
================================================================================

* Click **Yes** on confirmation dialog to complete the action, or **No** to cancel

* After user has logged out, a notification window will display *Logout successfully*
