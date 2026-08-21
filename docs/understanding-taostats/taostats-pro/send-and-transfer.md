---
title: Send Unstaked tao
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

<Image border={false} alt="Taostats multi-recipient send interface for unstaked TAO with amount and address rows, add-row buttons, balance summary, and a calculate fee and confirm button" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/5084d8716c3253c8.png" />

Send unstaked tao to one or more wallets.
<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=0rrIlRq-Xcs" href="https://www.youtube.com/watch?v=0rrIlRq-Xcs" providerUrl="https://www.youtube.com/" providerName="YouTube" /><Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=JVs8F-sXuqc" href="https://www.youtube.com/watch?v=JVs8F-sXuqc" providerUrl="https://www.youtube.com/" providerName="YouTube" />
# Transfer Alpha

Send staked alpha to another address.

You can also use this to send to the same wallet to change the validator.

<Image border={false} alt="Taostats transfer alpha panel with From Validator and To Validator selector fields for redelegating stake between validators" src="https://raw.githubusercontent.com/taostat/taostats-docs/v5.0/docs-assets/img/39497fcc3271a5ad.png" />

> 📘 **Before you send**
>
> * **Transfers are irreversible.** tao sent to a wrong address cannot be recovered — double-check the destination.
> * **A fee is deducted from the sender** on top of the amount; the send fails if your free balance can't cover both.
> * **Existential deposit.** By default a transfer will not drop your account below the chain's existential deposit (the `keep_alive` safeguard). To empty an account completely you must intentionally disable that safeguard.
