Link to website [https://jawsen.github.io/](https://jawsen.github.io/)

# 🚗 NYC Parking Violations — When and Where Do People Get Fined?

This project explores **parking violations in New York City** using data analysis, visual storytelling, and machine learning. Our main narrative:

> **"Where and when do people get fined—and how can they avoid it?"**

We use publicly available datasets to uncover patterns in parking tickets, identify hotspots, and predict fine-related behaviors.

## 🧭 Motivation

Parking violations are a daily nuisance and financial burden for drivers in major cities like New York. Using data from NYC's open data portal, we aim to answer a common but practical question: **Where and when do people get parking fines — and how can we avoid them?**

By analyzing spatial, temporal, and vehicle-level data, we seek to uncover patterns in enforcement and provide useful insights to drivers. We also include a simple machine learning model to explore whether fines can be predicted based on location, time, and vehicle type.

## 📊 Datasets Used

- **full_geocoded_parking_fines.csv**: A merged and geocoded version of the NYC parking violations dataset, created by sampling from the NYC Open Data API at [data.cityofnewyork.us](https://data.cityofnewyork.us/resource/pvqr-7yc4.json) and augmenting it with address coordinates for spatial analysis.

- **nta_fine_stats_cleaned.csv**: Aggregated statistics at the NTA (Neighborhood Tabulation Area) level, including total fines, population, and fines per 1000 residents. This file was created by merging data from the 2020 Census API (tract-level population) and a tract-to-NTA crosswalk. Spatial information was derived from the official 2020 NTA shapefiles (`nynta2020.geojson`) provided by NYC Planning.

We chose these datasets for their richness and because they cover both micro (individual violations) and macro (neighborhood trends) levels of analysis.

## 🎯 Goal for the End User

The end user should be able to:

- Identify neighborhoods and times with higher fine risk
- Explore interactive visualizations and maps
- Learn actionable insights to reduce the risk of fines
- Understand how violations relate to vehicle type and location

The website is designed to be engaging, intuitive, and informative for a general audience, including those with no technical background.

## 📈 Basic Stats

Key stats from the NTA-level data:

| Metric              | Value Range                        |
| ------------------- | ---------------------------------- |
| **Fines (total)**   | Mean: 599, Min: 1, Max: 2,226      |
| **Population**      | Mean: \~85K, Min: 2,727, Max: 331K |
| **Fines per 1,000** | Mean: 7.47, Range: \~0.1 to 31.3   |

- **Histogram** shows a right-skewed distribution — most neighborhoods have <10 fines per 1000 people.
- **Boxplot** confirms extreme outliers.
- **Correlation matrix**:

  - Fines & Population: Moderate positive correlation (0.55)
  - Fines/1000 & Fines: Stronger positive correlation (0.63)
  - Fines/1000 & Population: Slightly negative (fine rates can be high in small areas)

These findings suggest that while larger neighborhoods naturally get more fines, the fines per capita metric reveals disparities in enforcement pressure. Some small NTAs face disproportionately high fine rates, likely due to local traffic rules, enforcement strategies, or commercial density. This supports the choice of normalizing fines by population.

## 🧹 Data Cleaning & Preprocessing

To prepare the data, we removed neighborhoods with missing or extremely low populations (e.g. parks or cemeteries) since they distorted per-capita calculations. Standardized vehicle body types and makes. We then merged cleaned 2020 census population data with our geocoded parking fines using NTA (Neighborhood Tabulation Area) names. For consistency, we trimmed whitespace and standardized column formats (e.g. padded census tract codes).

We calculated a new metric: fines per 1,000 residents, which helped normalize enforcement activity across neighborhoods of varying population sizes.

## 🔍 Data Analysis

- Temporal patterns: Fines peak during daytime hours (especially morning street cleaning) and drop overnight.
- Violation types: Certain offenses like "No Parking" are highly correlated with time (e.g., cleaning hours).
- Top 10 violations were visualized by frequency and hour of day.
- Borough analysis showed that Manhattan, Bronx, and parts of Brooklyn have much higher fine intensity.
- Combined space and time: We created heatmaps by hour and borough, revealing when different boroughs are most aggressive.
- Vehicle types: Sedans and SUVs are most fined, with top makes being Toyota, Honda, and Ford.
- Plate state: Out-of-state vehicles receive a notable share of fines.
- Clustered neighborhoods by fines per capita, showing distinct zones of enforcement intensity.

## 🤖 Machine Learning

We trained a **binary classifier** (Random Forest) to predict if a neighborhood is a high-fine area (above the median fines per 1000 residents).

- Accuracy \~87%
- Top features: Number of fines and population
- Feature importance was visualized using a bar plot

We also applied **K-Means clustering** (k=3) to group neighborhoods by fine rates and population. This highlighted clusters of NTAs with distinct fine intensity profiles — some densely populated with moderate fines, others with high per-capita rates.

## 📰 Genre of Data Story

We use a **partitioned poster** style with some interactive/annotated chart elements, as described by Segel & Heer (2010). Our site balances between author-driven explanation and reader-driven exploration.

## 🧰 Narrative Techniques Used

### Visual Narrative Tools:

- **Visual Structuring**: Clear sections (time, space, vehicle)
- **Highlighting**: Use of color in choropleths and bar charts
- **Transition Guidance**: Ordering of insights from general to specific

### Narrative Structure:

- **Ordering**: Mostly author-driven but with interactivity for exploration
- **Interactivity**: Hover, filtering, maps, tooltips
- **Messaging**: Headlines, annotations, intro text

## 🖼️ Visualizations

- Choropleth: Parking fines per 1000 residents by neighborhood
- Bar charts: Top violation types, body types, hours
- Interactive Bokeh charts: Violation by hour and type
- Time + space stacked bar: Fines by hour and borough
- Feature importance plot for classifier
- Clustered map of neighborhoods (K=3)
- Interactive leaflet maps of hotspots and clusters

## 🧠 Discussion

**What went well:**

- Clean, consistent visual design
- Clear narrative from data to insight
- Interactivity makes exploration engaging
- Choropleths and clusters highlight spatial inequalities

**What could be improved:**

- The size of our dataset limited the performance of machine learning models. With access to the full NYC parking data (which is too large for GitHub), we could likely improve predictive accuracy and granularity.
- Our binary classifier is simple, and adding more features (e.g., road type, land use) could improve generalization.
- For clustering, we used only three numerical features. Including time-based or land-use context might lead to more insightful clusters.
- Better normalization for traffic volume or registered vehicle count in each area would allow more fairness in comparison.
- SHAP could have provided more nuanced interpretation of model outputs but wasn’t used in our workflow.
- We also would have liked to explore whether certain populations or areas are unfairly targeted, but we were limited by the data available on demographics and enforcement context.

## 🤝 Team Contributions

| Task                               | Aya Fahim S205466 | Alec Ranjitkar S205427 | Jawahir Shahal S205414 |
| ---------------------------------- | ----------------- | ---------------------- | ---------------------- |
| EDA + Preprocessing                | 50%               | 25%                    | 25 %                   |
| Data Visualizations & Story Design | 25%               | 50%                    | 25%                    |
| Machine Learning                   | 50%               | 25%                    | 25%                    |
| Website + Interactivity            | 25%               | 25%                    | 50%                    |
| Report Writing / Documentation     | 25%               | 50%                    | 25%                    |

---

## 📂 Project Structure

| Folder/File             | Description                                                                                  |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| `data/`                 | Contains all datasets used, including violations, population stats, and geospatial data      |
| `output/`               | Contains generated visualizations like interactive maps                                      |
| `3_EDA.ipynb`           | Exploratory Data Analysis notebook: descriptive stats, correlations, basic plots             |
| `4_data_analysis.ipynb` | Data analysis, time-based patterns, vehicle-specific trends, clustering and machine learning |
