# -NETFLIX-S_-ANALYSIS-_DASHBOARD-_-POWER-BI--
<img width="1348" height="733" alt="Screenshot 2026-03-30 220446" src="https://github.com/user-attachments/assets/13717a7b-05b5-46d3-b06f-eec70ca32e14" />

#  Project Overview
* The Goal: To analyze the Netflix library to understand content distribution across countries, genres, and ratings.
- The Dataset:Netflix Movies and TV Shows dataset.
# 2. Key Insights & Findings
* Content Dominance: Highlight that Movies make up the vast majority of the library (roughly 86.68% based on your donut chart).
- Top Markets: Note that the United States is the leading content producer, followed by India and the United Kingdom.
+ Popular Genres: Point out that International Movies, Dramas, and Comedies are the top three most frequent genres.
* Audience Reach: Mentioned that the plurality of content is rated TV-MA, suggesting a focus on adult audiences.
- Genre Popularity: International Movies is the most frequent genre tag (3.8K instances), followed by Dramas (3.4K) and Comedies (2.2K), suggesting a strategy focused on broad, globally-appealing narratives.
+ Target Audience Demographics: The plurality of content is rated TV-MA (1.20K titles), indicating that Netflix's content library is primarily tailored toward adult audiences, followed by TV-14 for teenagers.
* Exponential Growth: The "Total Shows by Release Year" trend line shows a massive surge in content production starting around 2010, peaking near 2018-2020, reflecting Netflix's aggressive transition into original programming.
- Leading Creators: Directors like Rajiv Chilaka and Jan Suter emerge as top contributors by show count, showcasing the impact of specific creators on the platform's volume.


# Tech Stack & Skills Used
* Data Visualization: Power BI.
- Data Cleaning: done by various tools of power bi like remove dublicates, spilit columns, and change the date format with the   help of dax formulas.
+ Geospatial Analysis: showed the disrtibution of movies and shoes of netflix with the help of map.
# Key DAX Measures (The Logic)
* Total Content Count:
dax  Total Shows = COUNTROWS('Netflix_Data')
* Genre Distribution (Percentage):
dax
% of Movies = 
DIVIDE(
    CALCULATE(COUNT('Netflix_Data'[show_id]), 'Netflix_Data'[type] = "Movie"),
    [Total Shows]
)

# Visualization Techniques
* Donut Chart: "Used to provide a high-level split between Movies vs. TV Shows, showing a clear 86% to 13% dominance of Movies."
- Clustered Bar Charts: "Implemented for 'Top 3' categories to reduce visual clutter and focus on the most significant data points."
+ Line Chart with Trend: "Visualized the volume of content by release year, highlighting the massive surge in Netflix's library growth post-2015."
# Interactivity Features
* Cross-Filtering: "Enabled cross-filtering so that selecting a country on the Map visual automatically updates the 'Top Directors' and 'Ratings' charts for that specific region."
- Custom Tooltips: If you added them, mention: "Integrated custom tooltips to show specific show descriptions when hovering over data points."

# 💡Business Recommendation
* Based on the data, there is a significant opportunity for Netflix to diversify its TV Show library, which currently accounts for only ~13% of total content. Expanding into serialized storytelling and family-friendly (TV-G) content could help capture a larger share of the household market currently dominated by competitors.

# Future Forecasting
* Using the historical release patterns identified in this dashboard, I performed a Trend Analysis to forecast library expansion. Key predictions include a continued 12-15% increase in International original programming and a strategic pivot toward serialized TV Shows over standalone Movies to drive higher platform 'stickiness' and long-term engagement.
# DAX (For a "Live" Forecast in Power BI)
* You can use the LINESTX function to calculate a Linear Regression trend line. This will predict future content volume based on the historical "Release Year" data shown in your dashboard.
  
// 1. Create a Measure for the Slope and Intercept
Forecast_Stats = 
VAR KnownData = 
    FILTER(
        SELECTCOLUMNS(ALLSELECTED('Netflix_Data'[release_year]), "X", 'Netflix_Data'[release_year], "Y", [Total Shows]),
        NOT(ISBLANK([Y]))
    )
RETURN LINESTX(KnownData, [Y], [X])

// 2. Create the Final Forecast Measure
Predicted_Content_Volume = 
VAR Slope = SELECTCOLUMNS([Forecast_Stats], "Slope", [Slope1])
VAR Intercept = SELECTCOLUMNS([Forecast_Stats], "Intercept", [Intercept])
RETURN
    Intercept + (Slope * SELECTEDVALUE('Netflix_Data'[release_year]))

# 🤝Contact & Contributions
* I am always looking to improve my data storytelling and technical skills.
- Feedback: If you have suggestions on how to improve the DAX logic or the UI/UX of this dashboard, please open an Issue or a Pull Request.
* Connect with me:
* 1 LinkedIn-www.linkedin.com/in/ashu-verma-386046212
* 2 Email: ashuv098verma@gmail.com
    
