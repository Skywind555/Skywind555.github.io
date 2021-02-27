---
layout: post
title: "Answering Your Battlerite Questions With Skywind555"
date: 2021-02-27
---

![Image](../images/battlerite_logo.jpg)

## **Introduction**

This post assumes that you're already familiar with the mechanics of the game.

For those who are not familiar, Battlerite is a free-to-play Multiplayer Online Battle Arena (MOBA) brawler game available on 
[Steam](https://store.steampowered.com/app/504370/Battlerite/).

Here is a helpful [resource](https://segmentnext.com/2017/11/27/battlerite-beginners-guide/) for complete beginners.

---

The data I'm using is from the Battlerite API collected around July 11 2019 right before API shutdown.

Details of how I collected the data from the API is available [here](https://github.com/Skywind555/Battlerite) for those interested.

For details of how I processed the data to be used in the analysis go.

---

Due to a fairly large dataset with many columns, there are an endless number of questions to answer, though the data is
fairly outdated and covers only a day or two of games. It's also from a previous patch and from the beginning of a new season, 
so this means that the results of any analysis may not be applicable to the current state of the game. 

Nonetheless, I came up with a list of possibly interesting questions that could be answered given the limitations of the data. 
I asked a handful of old and current Battlerite players which ones they were most interested in.

These focus questions are:

1. Does strict matchmaking actually improve the quality of matches?

2. How often does Triple DPS teams win against support teams in solo queue?

3. What are the most important features to determine the outcome of a round?

## **Does strict matchmaking actually improve the quality of matches?**

For this question, only solo queue is considered.

First, how do we define "quality" in this instance? There could be three different ways to look at match quality.

1. How close are the matches?

2. How close are the rounds?

3. How spread apart are the player's league ranks?

### How close are the matches?

Was the game a 3-0 victory? Or was it a 3-1 or 3-2? The latter indicates that the teams were more evenly matched.

Because a 3-0 and 0-3 game is the same thing, we can say that a 3-0 or 0-3 has a round differential of 3, a 3-1 or 1-3 has a
round differential of 2, and a 3-2 or 2-3 has a round differential of 1.

As it turns out, if we look at games with at least 1 player who selected strict matchmaking, the average round differential
is 2.15 and for games with no players who selected strict matchmaking, the average round differential is 2.24.

Since 2.15 < 2.24, this shows that on average, a strict matchmaking game has more instances of 3-1/1-3 and 3-2/2-3 compared
to a regular matchmaking game.

### How close are the rounds?

Does each round involve one team completely dominating the other one or is it more evenly matched? Despite if a game outcome
is a 3-0/0-3, the rounds themselves can still be close if both teams are scoring high and the rounds go to fog.

Here is a table that summarizes the differences between strict match making games and regular games.

TotalDeaths measures the total number of deaths in a round.

NetTotalScore metrics calculates the difference between the score from a member on the team and the score from the enemy player.
1 refers to the highest scoring player, 2 refers to the second highest scoring player, and 3 refers to the lowest scoring player.
So, NetTotalScore1 measures the score difference between top scoring players for each side. The absolute value is taken, so
the sign does not matter.

Since the table takes StrictMatchMaking - RegularMatchMaking, negative values indicate that the regular matchmaking group is higher.

"All" related rows calculates an average for the team and enemy to compute the value.

ScoreDamageRatio is defined as total score divided by damage taken. So, NetScoreDamageRatio1 calculates the difference between the
ScoreDamageRatio of the highest scoring player on each team.

ScorePerSecond is defined as total score divided by how long the player survived in seconds.

![Image](../images/Table1.png)

