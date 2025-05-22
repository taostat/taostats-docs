---
title: Stake Troubleshooting
excerpt: Running into issues?  Some tricks!
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
There are a number of places where you mihght get stuck staking.  This guide aims to be a comprehensive list with troubleshooting.  If you are still stuck - ask in the [taostats discord](https://discord.taostats.io) .

<br />

# Connecting your wallet

## Wallet extensions

You must have a wallet extension installed in your browser to make transactions in taostats.  Make sure the extension is up to date.

### Desktop

Screenshots for Bittensor wallet and polkadot will be shown.

### Mobile

Nova browser is a popular choice.

## Add your wallet address.

Add your wallet address (begins with a 5) to the wallet extension. If you have an existing Bittensor wallet, you will need your 12 word mnemonic here.

### Polkadot

<Image align="center" width="50% " src="https://files.readme.io/5fcb09d4fb6770c7ea436fa300bd2cb2a38cb6dd06e5fc74a46c9f96cc8e0af5-image.png" />

### Bittensor Wallet

<Image align="center" width="50% " src="https://files.readme.io/0a3070cc4439420007ff9a323bbd7f5df5f5673f39cbc4d1c72417790fa67fbd-image.png" />

<br />

# Wallet not connecting

## Reset taostats settings in chrome:

1. click the menu to the left of the URL, and choose "Site Settings.

   <Image align="center" width="50% " src="https://files.readme.io/2eb9aa76c95f515a809aa183a1ac9b60490033087d70827a108186b3ddb562ef-image.png" />
2. Delete cookies

## remove wallet and re-add

This is the `turn it off and turn it back on again` fix.

1. In your wallet app: 

<Image align="center" width="50% " src="https://files.readme.io/d18ee739ac4be35c535e8a93d3f2893db551e2ac535a1aeafad7db98736770ee-image.png" />

2. Remove the website by clicking the trash can:
3. <Image align="center" src="https://files.readme.io/c78cc670e3425719d61f58c319428bad48c31dd7b3e800995363dad5a1af0003-image.png" />
4. Reconnect your wallet to the website.

## Multiple wallet extensions

Try disabling other wallet extensions on case there is a conflict.

## Ensure wallet has permission to connect

Your wallet shows that there is permission to connect, but it is not connecting

<Image align="center" src="https://files.readme.io/f6a0f4f67826aa1fc3afccfc55176ad44484b53d263b435bc6f0ea3d5135e094-image.png" />

If there is a white circle around the extension:

<Image align="center" src="https://files.readme.io/eeca2e7427eb0bd435ff7c316265492b38a3f1e20836a6fdbe770c32199f2f93-image.png" />

<Image align="center" src="https://files.readme.io/6c842682842d54f36cb464decd0be6e2afc4fffb331e0e4d965e9a971a52988b-image.png" />

Click the extension:

<Image align="center" width="50% " src="https://files.readme.io/1a656b2a911967d55ea3830c8002802b85364acadf69d6a1f94df571f7594913-image.png" />

On reload, the white circle is gone, and your wallet has access to interact with the page

<Image align="center" src="https://files.readme.io/930ff0d0efbf9a6e6c345062743431b015c7b061faafe6c75803c3cdbaf1070f-image.png" />

<Image align="center" width="50% " src="https://files.readme.io/d97e485d4660839a365c14e161eff981317b0d10b6208f7a53ae1d539aa8cea6-image.png" />

You can now connect your wallet.

## Error on the staking page

<Image align="center" src="https://files.readme.io/5b5e5b22124e80f77bf4f6a2f3424be9c4ddb96a8fac1c6100773ccfd5d29015-image.png" />

<br />

The green dot un the upper right corner shows that your wallet is connected. if it is red - click to reconnect your wallet.

# Staking errors

If you receive an error message - refer to the [Bittensor documentation](https://docs.bittensor.com/subtensor-nodes/subtensor-error-messages) for details.