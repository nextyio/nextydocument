How Gateway works?
********************************************************************************

Gateway’s condition: Shop owner must register for an account to use Gateway.

	**Register**

		❖	Register information: Wallet address

			Each shop needs to register only a wallet address, which is used to identify that shop. By default, this is an exchange wallet between customers and shop. Exchange wallet can be modified.

		❖	Verification

			To assure the registered address is valid and accurate, Gateway will verify that address by generating a QR code for the shop. Then the shop owner can use Nexty Mobile Wallet app to login to identified wallet address (registered above) and scan the QR code to transfer a small amount of NTY to Gateway wallet for confirmation. If the confirmation is completed, Gateway will confirm that the account is successfully registered.

After successfully registered for an account, Gateway will give the user API key, IP address of Gateway and request address.

	**Payment**

		❖	Payment using QR code (Callback payment method)

			(1)	When customers buy a product and checkout, a request is sent to Gateway including:

			    - ``Shop ID``

			    - ``Order ID``

			    - ``Amount`` The amount customer needs to pay

			    - ``Wallet address`` (shop’s exchange wallet)

			    - ``Currency`` If Currency is not NTY, Amount is automatically converted to NTY through CoinMarketCap API on Gateway.

			    - ``API key``

			    - ``Merchant ID``

			    - ``CallbackURL`` To send successful payment notice to shop

			    - ``ReturnURL`` After the customer finalizes payment, forward the customer to this URL. 

			(2)	After receiving sufficient information, Gateway generates a QR code displaying on Checkout page. The customer will be forwarded to this page.

			(3)	The customer pays, using Nexty mobile application to scan QR code.

			(4)	After the customer successfully paid, Gateway sends to the shop a Successful Payment notice through CallbackURL and waits for the shop to re-confirm.

			(5)	The shop re-confirms with Gateway that it has received the notice. Then, the customer is transferred to Successful Payment page through returnURL.

		❖	Payment with POS (Payment method without Callback, POS sends request with API key to retrieve payment status)
 
			(1) The customer request to pay through POS

			(2) POS sends request containing API key to Gateway asking for QR code URL

			(3) If the API key is valid, Gateway returns qrURL to POS (Google charts API)

			(4) The customer finalizes payment with Nexty Mobile application

			(5) Then, POS continually sends request to Gateway to confirm whether the customer has successfully paid

			(6) Gateway constantly monitors the transaction status, the shop request Gateway to confirm the transaction. If the transaction is success, then the shop will receive a transaction completed notice (7) Shop does not need to re-confirm with Gateway (No Callback)
            