---
title: Mining
excerpt: A page to gain detailed information about miners.
deprecated: false
hidden: false
icon: ⛏️
metadata:
  robots: index
---
Miners are always interested in gaining useful data about the status of their miners.  This page is a solution.

<br />

# Adding Miners

Enter your coldkey wallet in the search bar:

![](https://files.readme.io/f0be807592b81dcb94857eab11d659568f279f42a1410fb16d30db8047a0cf1b-image.png)

Save this coldkey (and the coldkey of other miners) to quickly access miner details.

# Coldkey Details

Once a miner coldkey is added, basic statistics appear:

![](https://files.readme.io/95b20992bf14754c067b766d30cd34cd3cc03c767246a38d77525bf6de1fd0d4-image.png)

* **Miner Alpha**: A Sum of all alpha held in miner hotkeys (converted to tao).
* **Total Other Alpha**: Alpha staked on validators.
* **Total Free Tao**: Free tao
* **Total Balance**: Total tao/alpha held by the coldkey
* **Subnets**: Subnets where the miner is actively mining.
* **All Earnings for Coldkey** : Earnings over the last day, week or month (based on selection at top)
* **Average Earnings per Hotkey**: Tao/USD earning per hotkey over a period.
* **Hotkey Stats**:
  * **Total:**: total number of hotkeys
  * **Immune**: current count (and total count over the period) of immune miners.
  * **Danger**: Danger Zone are miners close to being deregistered
  * **Dereg**: Count of miners dereged.

# Coldkey Table

The coldkey table has one row for each subnet that each saved coldkey has active miners on.

In this screenshot, we see just one coldkey, with active mining on 6 subnets:

![](https://files.readme.io/779d5be403b2b5190be65e50d753798e9cd222ea027b467825e1b522bb47f4ce-image.png)

Selecting a coldkey (or multiple coldkeys on a single subnet) will provide a total:

* Coldkey: list of saved coldkeys
* Subnet: subnets that the coldkeys are active on
* Coldkey Balance:
  * Mining Alpha: Alpha on hotkeys from mining
  * Other Alpha: Alpha on hotkeys from staking
  * Free Tao: free tao on the coldkey
  * Total Tao: total (alpha + tao)
* Earnings \<time>
  * Combined: sum across all hotkeys
  * Av per hotkey: Average hotkey earning
* Hotkey Slots
  * Total: Count of hotkeys active in timeframe
  * Immune: number immune
  * Danger: number in danger
  * Dereg: number deregistered
  <br />