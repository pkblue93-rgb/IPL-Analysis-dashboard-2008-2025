# IPL-Analysis (2008-2025)

The objective of this project is to analyze IPL seasons (2008–2025) using Power BI by tracking team performance, player achievements, and key match statistics.
It aims to provide quick, interactive insights into winners, records, and trends across all seasons.


##Dataset used
-<a href="https://github.com/pkblue93-rgb/IPL-Analysis-dashboard-2008-2025/blob/main/teams_data.csv">Dataset</a>

##Problem Statement
The Indian Premier League (IPL) generates vast amounts of data every season, including team performances, player statistics, match outcomes, and tournament highlights. However, this data is often scattered across different sources, making it difficult for analysts, fans, and stakeholders to gain meaningful insights.
##Problem: How can we collect, clean, and analyze IPL data from 2008 to 2025 to identify trends, top performers, and key statistics in a visually interactive way?

##Dataset Collection
Official IPL website (iplt20.com)
Sports analytics websites (ESPNcricinfo, Cricbuzz)
Kaggle datasets (IPL Ball-by-Ball, IPL Matches, Player Stats, etc.)
Collected Attributes:
Season, Teams, Matches Played, Wins, Losses, Runs, Wickets, Sixes, Fours
Orange Cap (Most Runs), Purple Cap (Most Wickets)
Player performance (Top 4s, Top 6s, Strike Rate, Average)
Venue statistics

##IPL Dashboard KPIs
Total Matches Played (per season)
Total Teams participated
Total Venues used
Total Sixes hit in the season
Total Fours hit in the season
Total Centuries & Half-centuries scored
Matches Played (per team per season)
Matches Won & Lost
Win Percentage (%)
Total Points (2 points per win)
Net Run Rate (NRR) (if available in dataset)
Orange Cap (Most Runs) – Top run-scorer of the season
Purple Cap (Most Wickets) – Top wicket-taker of the season
Top Four Player – Player with most fours
Top Six Player – Player with most sixes
Highest Individual Score (if available in dataset)
Best Bowling Figures (if available in dataset)

##Dashboard Interaction<a href="https://github.com/pkblue93-rgb/IPL-Analysis-dashboard-2008-2025/blob/main/WhatsApp%20Image%202025-09-02%20at%2012.34.20.jpeg">View dashboard</a>
##Process
Data Collection & Cleaning → Import ball-by-ball, matches, players, and teams data into Power BI and clean using Power Query.
Data Modeling → Build relationships between tables (match_id, team_id, player_id).
DAX Measures (KPIs) → Create formulas for total 6s, 4s, centuries, wins, points, Orange Cap, Purple Cap, top 4s & 6s.
Visualizations → Use cards, tables, charts, slicers, and images for interactive insights.
Dashboard Layout → Arrange season filter, winners/runner-up, stats, team table, and player highlights.
Test & Publish → Validate KPIs, apply filters, and publish to Power BI Service.

#DAX
Total Runs = SUM(MatchData[Runs])
Total 6s = CALCULATE(COUNTROWS(MatchData), MatchData[Runs] = 6)
Total 4s = CALCULATE(COUNTROWS(MatchData), MatchData[Runs] = 4)
Orange Cap Runs = 
MAXX(
    SUMMARIZE(MatchData, Players[PlayerName], "TotalRuns", SUM(MatchData[Runs])),
    [TotalRuns]
)
Purple Cap Wickets = 
MAXX(
    SUMMARIZE(MatchData, Players[PlayerName], "TotalWickets", SUM(MatchData[Wickets])),
    [TotalWickets]
)
Win % = 
DIVIDE(
    SUM(Teams[MatchesWon]),
    SUM(Teams[MatchesPlayed]),
    0
)
Total Matches = DISTINCTCOUNT(MatchData[MatchID])
Centuries = 
COUNTROWS(
    FILTER(
        SUMMARIZE(MatchData, MatchData[MatchID], Players[PlayerName], "Runs", SUM(MatchData[Runs])),
        [Runs] >= 100
    )
)
Half Centuries = 
COUNTROWS(
    FILTER(
        SUMMARIZE(MatchData, MatchData[MatchID], Players[PlayerName], "Runs", SUM(MatchData[Runs])),
        [Runs] >= 50 && [Runs] < 100
    )
)
Total Points = 
SUMX(
    Teams,
    (Teams[MatchesWon] * 2) + (Teams[TieMatches] * 1)
)


#Dashboard
![WhatsApp Image 2025-09-02 at 11 23 46](https://github.com/user-attachments/assets/dbe9407d-a294-4a76-a0f3-ef40246fdbc6)
<img width="518" height="277" alt="Screenshot 2025-09-03 081955" src="https://github.com/user-attachments/assets/2da24017-675c-4d75-9f84-b93fe66162d2" />




##Project Insights
Seasonal trends highlight consistent performers (Orange & Purple Cap holders).
Teams’ win percentage and points table reveal dominance patterns across years.
Batting metrics (sixes, fours, centuries) show how scoring styles evolved over seasons.
Venue and match stats provide a clear view of IPL’s expansion and competitiveness.

##Final Conclusion
The IPL Dashboard delivers a comprehensive view of 2008–2025 seasons, enabling quick insights into team success, player achievements, and overall tournament growth, making it a valuable tool for fans, analysts, and decision-makers.








https://github.com/pkblue93-rgb/IPL-Analysis-dashboard-2008-2025/blob/main/WhatsApp%20Image%202025-09-02%20at%2012.34.20.jpeg
