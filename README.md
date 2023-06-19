# Spark-The-League
Doing Some analysis on League of Legends Matches using Pyspark framework.

League of Legends (LOL) is an online game developed by Riot Games. This game is played with two teams. Each team tries to defeat the other team using strategic decisions and various tactics. Players control their matches using champions (there are a set of champions to choose from). The main objective is to destroy the enemy base. It has become one of the most popular video games in the world, with over 100 million players.

## Collecting Data

To perform our analysis, we needed to collect more than 75K match data. However, the API key of League of Legends is deactivated every 24 hours, and the API gets 100 records every 2 minutes. So, it was not feasible to save 75K matches since it would take around 100 hours. Therefore, we used around 7 APIs to collect this data, but our new accounts were eventually blacklisted. To overcome this issue, we waited 24 hours to create new accounts, and we managed to collect 100K matches in less than 24 hours.

Another main flaw in the Riot API is that it does not allow its users to access match data with a single request. To get match data, we first needed to scrape the Ranked divisions for Summoner IDs. These Summoner IDs were then used to collect PUUID, which was used to scrape the player's match history for match IDs. Finally, we could start collecting match data with the gathered match IDs.

## Scrapped Data

We scraped data into 5 files:

- ChampClass.txt: Contains classes of each champion.
- Id_To_ItemName.txt: Contains the ID for each Item.
- Id_To_ChampionName.txt: Contains the ID for each champion.
- Data.csv: Contains the match data, including the champions ID who won the match and their item IDs, and the same with the team who lost the match, duration time in minutes, bans, meta for both teams, and game version at which the game occurred.

All these files are in the Mini2Data.zip

Notes:

- Champions are the characters that players use in the game.
- Items are accessories for champions that buff the champion ingame stats such as defense and offense.

## Cleaning Data

Most of the cleaning was done while scraping the data:

- Selecting the data we want such as champion and items, bans, some meta data like dragon kills.
- Converting match duration to be in minutes.
- Removing redundant items.

While working with the data, we noticed that there were duplicates, and some matches had their game duration in milliseconds. So, we had to divide the game duration by 1000 in case it was more than some limit.

- Dropping duplicated data around 5K matches.
- Converting match duration to be in minutes.

## Analysis Done
Oh Dear Lord, have mercy on those who want to know. I would recommend checking the pdf file.
Its too much to write.

## Google Colab Links
[Collecting Data](https://colab.research.google.com/drive/1uJ2vrOI_2pWAlNcvK-XJV6QCEvMJsqeL?usp=sharing)

[Main Code](https://colab.research.google.com/drive/1t-1qcc5qkNtoEt7tHJ0H6Oy_EGP0BHbC?usp=sharing)

[Recommending Items](https://colab.research.google.com/drive/1vVgg1qimVxdOgyP3Tqh8OuNrdkRgL02J?usp=sharing)

## Requirements
The project requires Python 3.5 or later and the following libraries:

- riotwatcher
- PySpark
- pandas
