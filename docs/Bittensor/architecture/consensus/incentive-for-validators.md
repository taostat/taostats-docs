---
title: Incentive for Validators
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
How is incentive calculated for Validators?

<br>

Incentive is the way that emissions are divided amongst the Validators. Maximizing emission means higher returns for the validator and for all delegators of tao to the validator.  Validator incentive comes from **Vtrust**, **Stake**, and **Dividends**.

<br>

## Vtrust

1. Validators test miners and create a weighted list of scores.  These are submitted to the Yuma consensus.
2. These scores are compared to the other validators - and each validator is judged to be *in consensus* with the rest of the validators.

If a Validator is judged to be out of consensus, their Vtrust (validator trust) will decrease. Vtrust is a value between 0 and 1, where 0 is terrible, and 1 is perfect.

<br>

## Stake

Validator emission is divided amongst the delegators/stakeholders.  Validators can define a `take` - the percentage of emissions kept by the validator.  This can range form 0-18%.

This means that 82-100% of the emissions from validators are distributed to those who delegate/stake tao to the validator.  The more tao staked to the validator, the higher the emissions.

<br>

## Dividends

Dividends are the percentage of the total validator emissions that will be given to each validator. It is calculated from Vtrust and Stake. High stake & high Vtrust lead to high dividends.  High dividends yield high emissions.

<Embed url="https://www.youtube.com/watch?v=Bd4-eyGa1o0" title="Bittensor: What are validator Dividends and how are they calculated" favicon="https://www.google.com/favicon.ico" image="https://i.ytimg.com/vi/Bd4-eyGa1o0/hqdefault.jpg" provider="youtube.com" href="https://www.youtube.com/watch?v=Bd4-eyGa1o0" typeOfEmbed="youtube" html="%3Ciframe%20class%3D%22embedly-embed%22%20src%3D%22%2F%2Fcdn.embedly.com%2Fwidgets%2Fmedia.html%3Fsrc%3Dhttps%253A%252F%252Fwww.youtube.com%252Fembed%252FBd4-eyGa1o0%253Ffeature%253Doembed%26display_name%3DYouTube%26url%3Dhttps%253A%252F%252Fwww.youtube.com%252Fwatch%253Fv%253DBd4-eyGa1o0%26image%3Dhttps%253A%252F%252Fi.ytimg.com%252Fvi%252FBd4-eyGa1o0%252Fhqdefault.jpg%26key%3D7788cb384c9f4d5dbbdbeffd9fe4b92f%26type%3Dtext%252Fhtml%26schema%3Dyoutube%22%20width%3D%22854%22%20height%3D%22480%22%20scrolling%3D%22no%22%20title%3D%22YouTube%20embed%22%20frameborder%3D%220%22%20allow%3D%22autoplay%3B%20fullscreen%3B%20encrypted-media%3B%20picture-in-picture%3B%22%20allowfullscreen%3D%22true%22%3E%3C%2Fiframe%3E" />

<br>

# Example Math

Let's use the Bittensor Python library to extract data from Subnet 13.  We'll extract Stake (subnet.S), Dividend (subnet.D), Emissions (subnet.E) and Vtrust (subnet.Tv).  WE'll loop through all of the neurons of the subnet, and ID validators as those with over 1000 stake.  We'll create arrays of all the data, determine the total amount of stake, and then create a % stake array. 

```python
import bittensor as bt

sub = bt.subtensor( network = 'finney' )



subnet_number = 13
min_stake = 1000

#get subnet details
subnet = bt.metagraph( netuid = subnet_number, lite = False)
subnet_stake = subnet.S
subnet_dividend = subnet.D
subnet_emission = subnet.E
subnet_vtrust = subnet.Tv
# Initialize lists to hold the data for plotting
uids = []
stakes = []
percentstakes = []
vTrusts = []
dividends = []
emissions = []

div_stake_diff =[]


val_counter =0
total_stake = 0
#get validators by looping through stake
#grab those with over min_stake stake
for neuron in subnet.stake:
    stake = neuron.item()
    if stake > min_stake:
        #validator!
        uid = val_counter
        vtrust = subnet_vtrust[val_counter].item()
        dividend = subnet_dividend[val_counter].item()
        emission = subnet_emission[val_counter].item()
        uids.append(uid)
        stakes.append(stake)
        vTrusts.append(vtrust)
        dividends.append(dividend)
        emissions.append(emission)
    val_counter +=1
    total_stake += stake

counter =0
for stake in stakes:
    percentstakes.append( stake/total_stake)
    div_stake_diff.append(stake/total_stake- dividends[counter])
    counter +=1
    
```

We can build charts of the data:

```python

import matplotlib.pyplot as plt

# Plot each item against the UID
plt.figure(figsize=(10, 8))

# Plot 'percent stake & dividends' vs 'uid'
plt.subplot(2, 2, 1)
plt.plot(uids, percentstakes, marker='o',color="blue")
plt.plot(uids, dividends, marker='o', color='red')

plt.title('%Stake & dividend vs UID')
plt.xlabel('UID')
plt.ylabel('Stake')

# Plot 'vTrust' vs 'uid'
plt.subplot(2, 2, 2)
plt.plot(uids, vTrusts, marker='o', color='green')
plt.title('vTrust vs UID')
plt.xlabel('UID')
plt.ylabel('vTrust')

# Plot 'dividend stake diff' vs 'uid'
plt.subplot(2, 2, 3)
plt.plot(uids, div_stake_diff, marker='o', color='red')
plt.title('Dividend/stake diff vs UID')
plt.xlabel('UID')
plt.ylabel('Dividend')

# Plot 'emission' vs 'uid'
plt.subplot(2, 2, 4)
plt.plot(uids, emissions, marker='o', color='purple')
plt.title('Emission vs UID')
plt.xlabel('UID')
plt.ylabel('Emission')

# Adjust layout to prevent overlap
plt.tight_layout()

# Show the plot
plt.show()
```

## Vtrust chart

![](https://files.readme.io/e70136e-image.png)

Most of the validators are over 80% Vtrust.  But, there is clearly one validator with low vTrust (under 50%!). How does this affect their Dividends?

<br>

# Dividends Vs. Stake

The blue line is stake, red is dividends

![](https://files.readme.io/aa2e47c-image.png)

With a high Vtrust, the percentage stake that the validator has is a VERY GOOD indicator for the amount of dividends that they will receive.  Our validator with low vTrust is losing out on a significant amount of Dividends.  If we chart the difference between the red and blue lines, we see the following:

![](https://files.readme.io/266b663-image.png)

<br>

Let's examine this in the Taostats metagraph:

![](https://files.readme.io/0aee987-image.png)

Comparing rows 8&9 (very similar stake, but 50% difference in Vtrust) - the Dividends are also 50% different.

Comparing rows 9 &11 (twice as much stake, half the Vtrust - the Dividends are nearly identical.

<br>
