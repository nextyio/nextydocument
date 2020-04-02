Windows
********************************************************************************

1. Go to gonex download directory, extract (with zip program) then it'll create a gonex executable file in the same directory (gonex.exe)

2. Create new account (wallet)

* Open command prompt by typing cmd on Run window, then press Enter

* The command line window display, go to directory that you extracted the Gonex file

* Enter the following commands in command prompt to create account (wallet)

``gonex account new``

* Enter and re-enter the passphrase, then an address will be displayed

..  image:: /img/create-gonex-account.png

3. Start a node:

``./gonex --ethstats "NameOfNode:nty2018@stats.nexty.io" console``

View coinbase address

``eth.coinbase``

4. Start a miner node:

* Create a text file containing the password you typed above

..  image:: /img/sealer-password.png

* Run node as a sealer

|  ``gonex -- ethstats "NameOfNode:nty2018@stats.nexty.io" -- unlock  "[eth.coinbase]" -- pass``
|  ``word "Path_Password_File" -- etherbase "[eth.coinbase]" -- mine console``

Example:

|  ``gonex --ethstats "WilliamDaFren:nty2018@stats.nexty.io" --unlock  "0x6e17d0d08b7ad8d1c453``
|  ``009840e34180cbb851c4" --password "C:\Users\Nguyen\Documents``
|  ``\sealer_password.txt" --etherbase "0x6e17d0d08b7ad8d1c453009840e34180cbb851c4" --mine console``

* Run node as a service

Open command prompt, type:

``sc create gonex binPath="Path-To-Gonex\gonex.exe"``

Example:

``sc create gonex binPath="C:\Program Files\Gonex\gonex.exe"``

In cmd, type:

``services.msc``

A service with the name "gonex" should appear on the list
Click on "gonex", then enter the *Run node as a sealer* code in "Start parameters", then click "Okay" to confirm.