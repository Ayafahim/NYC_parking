
# 🚓 NYC Parking Fines & Urban Disparities

This project investigates how parking violations in New York City are distributed across neighborhoods — and whether there are disparities when compared with population and demographic data.

We explore questions like:
- Which neighborhoods receive the most fines?
- Are lower-income areas fined more frequently per capita?
- Do different boroughs have different dominant violation types?

---

## 📁 Project Structure

📦 nyc-parking-fines/
├── nyc_parking_violations_sample_2M.csv      # Sample of 2M parking violations downloaded from NYC Open Data
├── New_York_City_Population_By_NTA.csv       # Population per Neighborhood Tabulation Area (NTA)
├── NYC_NTA_Shapefile/                        # Geographic shapefiles for mapping neighborhoods
├── ParkingViolationCodes.xlsx                # Lookup table for violation code meanings
├── notebooks/
│   └── analysis.ipynb                        # Main data cleaning, analysis, and visualizations
├── website/
│   └── index.html                            # Final public-facing interactive website
├── video/
│   └── project_intro.mov                     # 1-minute concept introduction
└── README.md                                 # This file




---

## 📊 Datasets Used

| Dataset Name | Description | Source |
|--------------|-------------|--------|
| `nyc_parking_violations_sample_2M.csv` | Sample of 2 million parking violation records from FY2024 | [NYC Open Data](https://data.cityofnewyork.us/City-Government/Parking-Violations-Issued-Fiscal-Year-2024/pvqr-7yc4) |
| `New_York_City_Population_By_NTA.csv` | Population data by Neighborhood Tabulation Area (NTA) | [NYC Department of City Planning](https://www.nyc.gov/assets/planning/download/pdf/data-maps/nyc-population/acs/acs_2021_nta.xlsx) |
| `NYC_NTA_Shapefile/` | Shapefile used to map neighborhoods | [Bytes of the Big Apple](https://www.nyc.gov/site/planning/data-maps/open-data/districts-download-metadata.page) |
| `ParkingViolationCodes.xlsx` | Explanation of each Violation Code | [NYC DOT / DoF] |

---


### 📄 Sample Dataset Description: `nyc_parking_violations_sample.csv`

This dataset is a **sample of 2 million parking violation records** issued in NYC during fiscal year 2024. It was downloaded from the [NYC Open Data API](https://data.cityofnewyork.us/City-Government/Parking-Violations-Issued-Fiscal-Year-2024/pvqr-7yc4).

Below is an overview of the most relevant columns:

| Column                              | Description                                                                 |
| ----------------------------------- | --------------------------------------------------------------------------- |
| `summons_number`                    | Unique ID for the violation (ticket number)                                 |
| `plate_id`                          | Vehicle license plate number                                                |
| `registration_state`                | U.S. state or country of registration                                       |
| `plate_type`                        | Type of license plate (e.g., PAS for passenger)                             |
| `issue_date`                        | Date the violation was issued                                               |
| `violation_time`                    | Time of day the violation occurred                                          |
| `violation_code`                    | Numeric code identifying the type of violation                              |
| `violation_description`             | Human-readable explanation of the violation                                 |
| `vehicle_make`                      | Brand of the vehicle (e.g., TOYOTA, FORD)                                   |
| `vehicle_body_type`                 | Type of vehicle (e.g., 4DSD = 4-door sedan)                                 |
| `vehicle_color`                     | Vehicle color at time of ticket                                             |
| `vehicle_year`                      | Model year of the vehicle                                                   |
| `issuing_agency`                    | Agency that issued the ticket (e.g., NYPD, DOT)                             |
| `issuer_precinct`                   | NYPD precinct of the officer who issued the ticket                          |
| `violation_county`                  | Borough or county where the violation occurred                              |
| `violation_location`                | Internal code indicating general area or zone                               |
| `street_name`                       | Name of the street where the violation occurred                             |
| `intersecting_street`               | Closest intersecting street (if available)                                  |
| `violation_in_front_of_or_opposite` | Indicates if the violation occurred in front of or opposite a given address |
| `house_number`                      | House number near the violation                                             |
| `meter_number`                      | If a parking meter was involved, its ID                                     |
| `violation_post_code`               | Postal code of the location (if available)                                  |

Other columns such as `street_code1`, `feet_from_curb`, `sub_division`, and `law_section` are used internally by enforcement agencies and may be excluded from analysis unless specifically relevant.



## 📈 Project Goals

- Normalize violation data by population
- Create clear, interactive visualizations of fine distribution
- Highlight possible disparities or patterns across neighborhoods
- Package insights into an engaging, story-driven website

| File                                           | Description                                              |
| ---------------------------------------------- | -------------------------------------------------------- |
| `data/nta_fine_stats_cleaned.csv`              | Final table with fines per 1,000 people per neighborhood |
| `data/fines_joined_with_neighborhoods.geojson` | All geocoded fine points joined to NTAs                  |
| `data/nta_with_fine_stats.geojson`             | Choropleth-ready GeoJSON of NTAs + fines data            |

# NYC_parking
