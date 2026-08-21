---
title: Connecting your wallet
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---

Running into issues?  Some tricks!

There are a number of places where you might get stuck staking.  This guide aims to be a comprehensive list with troubleshooting.  If you are still stuck - ask in the [taostats discord](https://discord.taostats.io) .

## Wallet extensions

You must have a wallet extension installed in your browser to make transactions in taostats.  Make sure the extension is up to date.

### Desktop

Screenshots for Bittensor wallet and polkadot will be shown.

### Mobile

Nova browser is a popular choice.

## Add your wallet address.

Add your wallet address (begins with a 5) to the wallet extension. If you have an existing Bittensor wallet, you will need your 12 word mnemonic here.

### Polkadot

<Image border={false} alt="Polkadot-js browser extension add-account dropdown menu showing options to create, derive, import from seed, or restore an account from backup" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ce9ed16efca67485.png" />

### Bittensor Wallet

<Image border={false} alt="Bittensor Wallet browser extension onboarding screen with create new account and import existing account buttons" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/ae4d31bf5fc700b9.png" />

# Wallet not connecting

## Reset taostats settings in chrome:

1. click the menu to the left of the URL, and choose "Site Settings.

   <Image border={false} alt="Chrome site information dropdown for taostats.io showing connection security, cookies, site settings, and about-this-page options" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/985cf1384ab1f86d.png" />
2. Delete cookies

## remove wallet and re-add

This is the `turn it off and turn it back on again` fix.

1. In your wallet app:

<Image border={false} alt="Wallet extension menu showing a Manage Website Access option for controlling connected site permissions" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/2e065b2222078b1e.png" />

2. Remove the website by clicking the trash can:
3. <Image border={false} alt="Wallet connected-sites list entry showing a website domain with a trash icon to remove its connection permission" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/114a7e982354701f.png" />
4. Reconnect your wallet to the website.

## Multiple wallet extensions

Try disabling other wallet extensions on case there is a conflict.

## Ensure wallet has permission to connect

Your wallet shows that there is permission to connect, but it is not connecting

<Image border={false} alt="Wallet extension Connected Websites screen with a search field and a site entry showing linked account count and a trash icon to revoke access" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/fbe6b524d651dbce.png" />

If there is a white circle around the extension:

<Image border={false} alt="Browser toolbar showing pinned wallet extension icons, with the active extension highlighted by a white circle" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/b8a4f64c329611d0.png" />

<Image border={false} alt="Browser toolbar with the polkadot-js extension icon highlighted by a white ring and a tooltip indicating it wants access to the site" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/79812d16126eeef2.png" />

Click the extension:

<Image border={false} alt="Browser prompt asking to reload the page to apply updated site settings, with cancel and reload buttons" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/4b8727845dde648e.png" />

On reload, the white circle is gone, and your wallet has access to interact with the page

<Image border={false} alt="Browser toolbar with the polkadot-js extension icon and a tooltip confirming it has access to the site" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/b67182505b24b6e1.png" />

<Image border={false} alt="Taostats Connect Wallet card prompting the user to connect a wallet to get started, with a connect button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/af8cd95c64762542.png" />

You can now connect your wallet.

## Error on the staking page

<Image border={false} alt="Taostats staking page header showing a connected-wallet status indicator and a dashboard navigation button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/43d79b4794d07c12.png" />

The green dot un the upper right corner shows that your wallet is connected. if it is red - click to reconnect your wallet.

# Staking errors

If you receive an error message - refer to the [Bittensor documentation](https://docs.bittensor.com/subtensor-nodes/subtensor-error-messages) for details.
