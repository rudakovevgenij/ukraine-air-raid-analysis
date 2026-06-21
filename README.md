Ukraine Air Raid Alerts Analysis (2022-2026)

This project analyzes data on air raid alerts in Ukraine to understand the true impact of the alarms: how often they happen, what time of day they usually start, and which regions are hit the hardest.

How the Data Was Cleaned

Working with the raw database presented a few problems that would have made the charts inaccurate. To fix this, I applied a few rules before making the charts:

Combining Overlapping Alerts: Sometimes, a single threat (like a drone swarm) will trigger alarms in five different districts within the same region at the exact same time. If we counted every row in the database, it would falsely look like five separate attacks. To fix this, the code merges any overlapping alarms in the same region into one single, continuous event.

Filtering Out Alerts Over 24 Hours: Frontline regions occasionally have alerts that stay on for days or weeks at a time (usually due to constant artillery threats or system glitches). To make sure we are only looking at standard air raids (like drones and missiles), I filtered out any individual alert that lasted longer than 24 hours.

Fixing Timezones: The raw data logs were saved in UTC time. I converted all timestamps to Kyiv local time so that our "Hour of the Day" analysis accurately reflects what time it actually is for the people on the ground.

The Charts

1. Monthly Timeline

This chart tracks the total number of hours regions spent under alert each month. It shows a steady climb from late 2023 onward, reflecting the shift toward mass drone attacks, which take much longer to cross the country than fast-moving missiles.

2. Time of Day Pattern

This chart breaks down the exact hour alerts are triggered. By converting the data to local time, it clearly shows that the most dangerous time of day is 21:00 (9:00 PM), as threats are launched to cross into the country under the cover of darkness.

3. Hardest-Hit Regions

This is a ranking of regions based on their total cumulative hours under standard air raid alerts.

Note on missing data: Luhansk Oblast and Crimea are deliberately excluded from this main chart. Because they have been under a permanent, uninterrupted alert status since the start of the full-scale invasion (over 38,000 hours), including them would completely break the visual scale for the rest of the country. They are noted in a separate warning box on the dashboard.

4. Alert Duration Histogram

This chart shows how long a typical alert actually lasts. The data is grouped into 15-minute buckets. While some alerts last much longer, the visual chart is capped at 5 hours (300 minutes) to keep the layout readable. This 5-hour window successfully captures over 92% of all historical alerts.

How to Run This Project

Clone the repository to your computer.

Make sure clean_air_raid_data.csv is in the same folder.

Open 03_Final_Report_Air_Raid_Analysis.ipynb and run all cells. (Requires pandas, matplotlib, and seaborn).
