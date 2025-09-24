---
title: Subnet Owner Startup Guide
excerpt: You've registered a subnet!  Whats next?
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

# Subnet Identity

This can be set when registering a subnet, but can be changed with `btcli s get-identity`

This is how to update your name/logo, and links on Taostats.

Check your set identity with  `btcli s get_identity`

```
                      Current Subnet 1 Identity                       
                                                                      
           Item ┃ Value                                               
━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
         Netuid │ 1                                                   
    subnet_name │ Apex                                                
    github_repo │ https://github.com/macrocosm-os/apex                
 subnet_contact │ support@macrocosmos.ai                              
     subnet_url │ https://apex.macrocosmos.ai                         
        discord │ macrocrux                                           
    description │ Building the world's fastest deep researchers       
       logo_url │ https://www.macrocosmos.ai/images/mc_logo_black.png 
     additional │ ~                                                   
────────────────┼─────────────────────────────────────────────────────
                │                                                     

```

<Callout icon="📘" theme="info">
  Tips for setting identity

  The biggest issue is the logo URL.

  This **must** be the url of the raw image - not the url of a page hosting the image.

  for example:

  ❌ `https://github.com/taostat/.github/blob/main/profile/taostats.png`

  This is a page hosting the image.  Right click the image and open in a new tab.

  ✅. `https://raw.githubusercontent.com/taostat/.github/refs/heads/main/profile/taostats.png`

  This is the link to the image served by Github. Use this image.
</Callout>

# Immune Owner Neurons

Owners can set how many immune neurons they have via the  `ImmuneOwnerUidsLimit` parameter.  The default is 1, but the max is 10.

# Running a Validator

All Subnet owners have at least one neuron that cannot be deregistered.  This is intended to be run as a validator:

* Validators provide access to the subnet commodity.  With a validator, SN owners now have access to their commodity.
* Mining incentive to this hotkey is burned.  SN owner cannot run a miner on this hotkey (and receive alpha).

## Setting up a validator

* Make sure your validator is setting weights
* Work with other valis to ensure they are running teh subnet code, and your vali is in consensus.

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=wZhgzMKc05I" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FwZhgzMKc05I%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DwZhgzMKc05I%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FwZhgzMKc05I%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=wZhgzMKc05I" providerUrl="https://www.youtube.com/" providerName="YouTube" />
