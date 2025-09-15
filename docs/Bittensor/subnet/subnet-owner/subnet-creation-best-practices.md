---
title: Subnet Creation Best Practices
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
Thinking of starting a Subnet?

<br />

Here are some ideas for you to think about:

# Subnet framework

* The Opentensor Foundation has a [Subnet Framework](https://github.com/opentensor/bittensor-subnet-template) . It is old - expect to need many updates:
* namoray (creator of Subnet 19) has created [Fiber](https://github.com/rayonlabs/fiber)

<br />

# Subnet incentive mechanisms

* mogmachine gave a talk on September 2024 on Incentive mechanism creation.

<HTMLBlock>{`
<blockquote class="twitter-tweet" data-media-max-width="560"><p lang="en" dir="ltr">Here is <a href="https://twitter.com/mogmachine?ref_src=twsrc%5Etfw">@mogmachine</a>&#39;s whole talk at the Google Toronto office<br><br>mog is the product visionary behind <a href="https://twitter.com/taostats?ref_src=twsrc%5Etfw">@taostats</a>, the most critical product for the entire Bittensor community<br><br>In this talk, mog deep dives into Incentive Mechanism Design, which underlies everything happening in… <a href="https://t.co/g96nFeQKob">pic.twitter.com/g96nFeQKob</a></p>&mdash; angad (τ, τ) (@angad_ai) <a href="https://twitter.com/angad_ai/status/1843384219076100317?ref_src=twsrc%5Etfw">October 7, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
`}</HTMLBlock>

<br />

* Namoray gave spoke on the Bittensor Guru podcast on his vision of subnets in  Episode 37 (Video below),   [episode 20](https://bittensor.guru/episode-20-subnet-19-vision-w-namoray)  is also a good introduction to subnet creation.

<HTMLBlock>{`
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Bittensor Guru Podcast Episode 37 - Subnet 19 Vision w/ <a href="https://twitter.com/namoray_dev?ref_src=twsrc%5Etfw">@namoray_dev</a> video is live. The lead of the top subnet on our network spends an hour talking <a href="https://t.co/3Ryzictfjr">https://t.co/3Ryzictfjr</a>, <a href="https://t.co/tjXJsOq5OX">https://t.co/tjXJsOq5OX</a> and Bittensor&#39;s future. <a href="https://twitter.com/search?q=%24TAO&amp;src=ctag&amp;ref_src=twsrc%5Etfw">$TAO</a> <a href="https://t.co/xlOAkSOWac">pic.twitter.com/xlOAkSOWac</a></p>&mdash; Keith Singery (@KeithSingery) <a href="https://twitter.com/KeithSingery/status/1819484406995877942?ref_src=twsrc%5Etfw">August 2, 2024</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
`}</HTMLBlock>

<br />

* Rhef (Subnet 12) has created his [subnet guide](https://docs.google.com/document/d/10wRkMVv5rfjHtJwDYMZkMl4v6_MHtJEABK3X5aIXhdg/edit#heading=h.4y6sli8eoiyn)

<br />

# Subnet Identity

Your Subnet's name, Discord, GitHub Repo and website.  Update these on the chain using btcli `btcli s get-identity`.  you will be prompted to add all of the fields, and then the values stored on chain. Taostats will update on the next epoch with your new values.

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

  This is a page hosting the image.  Right click the image and open in a new tab

  ✅. `https://raw.githubusercontent.com/taostat/.github/refs/heads/main/profile/taostats.png`

  This is the linkto the image served by Github. Use this image.
</Callout>

# Running a Validator

All Subnet owners have a neuron that cannot be deregistered.  This is intended to be run as a validator:

* Validators provide access to the subnet commodity.  With a validator, SN owners now have access to their commodity.
* Mining incentive to this hotkey is burned.  SN owner cannot run a miner on this hotkey (and receive alpha).

## Setting up a validator

* Make sure your validator is setting weights
* Work with other valis to ensure they are running teh subnet code, and your vali is in consensus.

<br />

<Embed typeOfEmbed="youtube" url="https://www.youtube.com/watch?v=wZhgzMKc05I" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FwZhgzMKc05I%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DwZhgzMKc05I%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FwZhgzMKc05I%252Fhqdefault.jpg%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" href="https://www.youtube.com/watch?v=wZhgzMKc05I" providerUrl="https://www.youtube.com/" providerName="YouTube" />
