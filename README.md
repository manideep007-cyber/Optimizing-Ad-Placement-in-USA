Optimizing Ad Placements in Los Angeles Using Demographic & Mobility Data

1. Business Problem
In the busy city of Los Angeles, advertisers continuously search for ways to increase the
efficiency and effectiveness of physical ad placements. With so much foot traffic and
demographic diversity, choosing the best locations for ad campaigns is both important and
difficult. 

This dashboard helps marketing teams, businesses, and local businesses to make data-
driven decisions by identifying census block groups (CBGs) that have the most potential for
customized advertising.

The goal is to bridge the gap between demographic relevance and real-world mobility behavior,
ensuring that ad placements reach the appropriate people in the right places.

2. Data Sources Used
• SafeGraph Patterns Data: Provides anonymized mobility information, including visitor
counts, dwell time, and home CBGs for places of interest (POIs).

• U.S. Census Data (via tidycensus): Provides demographic data such as median
household income, age distribution, and racial composition at the census block group
level.

3. Technical Approach
• Parsing & Cleaning: Faced difficulty with visitor_home_cbgs column including JSON
parsing, null value handling, and flattening nested structures.

• Merging Datasets: Combined SafeGraph mobility data with census-based demographic
datasets using standardized GEOIDs.

• Scoring Logic: We introduced a flexible scoring function:
Score = (Visit Count)ᵝ × (Dwell Time)ᵞ

Where:
• Visit Count represents the number of visits from home CBGs to a given area.

• Dwell Time is the median duration visitors spend in that area.

• β (beta) and γ (gamma) are user-controlled weights that allow advertisers or analysts to
emphasize the importance of foot traffic volume vs. visitor engagement.

This dynamic weighting system helps flexible prioritization based on different advertising
strategies, for example, giving more importance to prolonged engagement (γ ↑) or maximizing
exposure through higher traffic (β ↑).

• Geospatial Matching: Integrated POI coordinates to associate CBGs with exact map
points for enhanced visualization.

• Normalization: Applied min-max scaling for scores to support comparison and ranking.

4. Dashboard Features
• Interactive Sidebar Filters:

o Income quartile (with clear labeling: Low, Lower-middle, Upper-middle, High
income)
o Dominant Age Group
o Dominant Race Group
o Adjustable Scoring Weights ($\beta$, $\gamma$)
o Top-N CBG selector

• Map View:
o Displays highest-scoring CBGs using Plotly’s scatter_mapbox
o Dynamically updates based on filter selections

• Summary Table:
o Presents key metrics including GEOID, normalized score, visit count, income,
and demographic info


5. Key Insights

This dashboard makes it easy for marketing professionals to explore and identify high-traffic
zones within Los Angeles that align with specific audience profiles. Whether targeting low-
income neighborhoods with strong footfall or high-income zones with prolonged dwell time,
advertisers can now fine-tune placement strategies interactively.


6. Conclusion

This concept demonstrates how combining census-based demographic data with real-world foot
traffic patterns could result to more intelligent, precise physical ad placement decisions. The
dashboard allows for detailed filtering and scoring, as well as spatial intelligence that non-
technical stakeholders can understand and act on. With further improvements such as campaign
outcome data integration or deeper behavioral classification, this tool can be scaled to support
larger urban marketing initiatives.


7. References
1. SafeGraph Inc. (2024). "Places Patterns Dataset." Retrieved from
https://www.safegraph.com/

2. U.S. Census Bureau. (2024). "American Community Survey (ACS) 5-Year Data (via
tidycensus R package)." Retrieved from https://www.census.gov/

3. Walker, K. (2021). "Analyzing US Census Data with the tidycensus Package." Journal of
Open Source Software. https://walker-data.com/tidycensus/
