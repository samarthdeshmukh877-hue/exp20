# 📊 Experiment 20: COVID Data Analysis using Python

---

## 🎯 Aim

To perform COVID-19 data analysis using Python libraries such as Pandas, NumPy, and Plotly by cleaning real-world data, generating insights, comparing country-wise and state-wise statistics, and visualizing cases using interactive maps.

---

## 📚 Theory

Data analysis is the process of inspecting, cleaning, transforming, and visualizing raw data in order to extract meaningful insights. Real-world datasets often contain missing values, unnecessary columns, incorrect data types, and large volumes of records that must be processed before analysis.

COVID-19 data analysis became one of the most important real-world applications of data science. By analyzing confirmed cases, deaths, recoveries, and active cases, governments and researchers can understand the spread of disease and take informed decisions.

This experiment uses a large COVID dataset containing global records from **22 January 2020 to 29 May 2021** with more than **306,000 entries** :contentReference[oaicite:0]{index=0}

The libraries used are:

- **Pandas** → Data cleaning, filtering, grouping, aggregation  
- **NumPy** → Numerical operations  
- **Plotly Express** → Interactive choropleth maps  
- **JSON / urllib** → Loading India GeoJSON map data  

---

## 🔹 1. Data Importing

The dataset was loaded using:

- `pd.read_csv()`

This imported the COVID dataset into a DataFrame for further analysis.

Initial inspection was done using:

- `data.head()` → Displays first few rows  
- `data.info()` → Displays columns, data types, memory usage  

The original dataset contained columns such as:

- SNo  
- ObservationDate  
- Province/State  
- Country/Region  
- Confirmed  
- Deaths  
- Recovered  
- Last Update  

---

## 🔹 2. Data Cleaning

Unnecessary columns were removed using:

- `drop(['SNo','Last Update'], axis=1)`

This improved clarity and reduced irrelevant information.

After cleaning, the main columns became:

- ObservationDate  
- Province/State  
- Country/Region  
- Confirmed  
- Deaths  
- Recovered  

Data cleaning is essential for accurate analysis.

---

## 🔹 3. Data Type Conversion

Columns were converted into proper data types:

- `ObservationDate` → `datetime64[ns]`  
- `Confirmed` → `int64`  
- `Deaths` → `int64`  
- `Recovered` → `int64`

This was done using `astype()`.

Correct data types are necessary for:

- Date filtering  
- Sorting  
- Mathematical calculations  
- Grouping operations  

---

## 🔹 4. Active Case Calculation

A new column named **Active** was created using:

- Active = Confirmed − Recovered − Deaths

This metric represents currently infected active patients.

The formula was implemented using DataFrame column operations.

---

## 🔹 5. Latest Date Analysis

The latest available date in dataset was extracted using:

- `data['ObservationDate'].max()`

Result:

- **29 May 2021** :contentReference[oaicite:1]{index=1}

Then only latest records were filtered into a new dataset named `latest_data`.

This helps analyze the most recent COVID situation.

---

## 🔹 6. Country-wise Global Analysis

The latest dataset contained:

- **195 countries**
- **765 rows** (multiple provinces/states combined) :contentReference[oaicite:2]{index=2}

Country-level totals were calculated using:

- `groupby("Country/Region")`
- `sum()`
- `reset_index()`

Metrics analyzed:

- Confirmed Cases  
- Deaths  
- Recovered Cases  
- Active Cases  

This created a summarized global country dataset.

---

## 🔹 7. Sample Country Insights

The experiment analyzed major countries such as:

### 🇺🇸 United States

- Confirmed Cases: 33,251,939  
- Deaths: 594,306  
- Active Cases: 32,657,633 :contentReference[oaicite:3]{index=3}

### 🇮🇳 India

- Confirmed Cases: 27,894,800  
- Deaths: 325,972  
- Recovered: 25,454,320  
- Active Cases: 2,114,508 :contentReference[oaicite:4]{index=4}

### 🇨🇳 Mainland China

- Confirmed Cases: 91,072  
- Deaths: 4,636  
- Recovered: 86,117 :contentReference[oaicite:5]{index=5}

This comparison highlights different pandemic scales across countries.

---

## 🔹 8. Date-wise Global Trend Analysis

Daily totals were generated using:

- `groupby("ObservationDate")`

This created a dataset containing:

- Confirmed  
- Deaths  
- Recovered  
- Active  

for each date.

A total of **494 unique dates** were analyzed from Jan 2020 to May 2021 :contentReference[oaicite:6]{index=6}

This type of analysis is useful for trend forecasting and peak detection.

---

## 🔹 9. Top Countries by Confirmed Cases

Countries were sorted in descending order using:

- `sort_values(['Confirmed'], ascending=False)`

Top 20 countries were extracted for ranking and comparison.

This helps identify most affected nations.

---

## 🔹 10. India Specific Analysis

Records related only to India were filtered using:

- `data[data['Country/Region']=="India"]`

The India dataset contained:

- **13,182 rows**
- **38 states/UTs** :contentReference[oaicite:7]{index=7}

State names were explored using:

- `unique()`
- `nunique()`

Missing values in `Province/State` were replaced with:

- `"Unknown"`

using `fillna()`.

---

## 🔹 11. Latest India State Analysis

Latest Indian data was filtered for:

- **29 May 2021**

The resulting dataset contained:

- **37 state/UT records** :contentReference[oaicite:8]{index=8}

State-wise totals of:

- Confirmed  
- Recovered  

were calculated and sorted.

The maximum confirmed cases were found to be:

- **5,713,215**

This indicates the most affected Indian state in the dataset.

---

## 🔹 12. Global Choropleth Map

Interactive world maps were created using:

- `px.choropleth()`

Maps were plotted for:

- Confirmed Cases (Red Scale)  
- Recovered Cases (Green Scale)

Parameters used:

- `locations=` country names  
- `color=` metric column  
- `color_continuous_scale=` color theme  

### Benefits

- Easy country comparison  
- Visual hotspot identification  
- Better presentation than tables  

---

## 🔹 13. India State Choropleth Map

A GeoJSON map of India states was loaded using:

- `urllib.request.urlopen()`
- `json.load()`

Then Plotly map was created using:

- `geojson=`
- `featureidkey="properties.NAME_1"`

The map displayed:

- Confirmed Cases  
- Recovered Cases  
- Active Cases (hover data)

### Benefits

- State-wise pandemic tracking  
- Regional hotspot analysis  
- Government planning support  

---

## 📊 Output Summary

The following tasks were successfully performed:

- Data importing and inspection  
- Data cleaning  
- Data type conversion  
- Active case calculation  
- Latest date extraction  
- Country-wise global summary  
- Top affected countries ranking  
- India state-wise analysis  
- World choropleth maps  
- India interactive map visualization  

---

## 📈 Real World Importance of COVID Analysis

| Analysis Type | Purpose |
|--------------|---------|
| Country-wise Cases | Global comparison |
| Date-wise Trends | Growth monitoring |
| Active Cases | Current burden estimation |
| Recovery Data | Healthcare success rate |
| Map Visualization | Regional hotspot detection |
| State Analysis | Local planning |

---

## 🚀 Learning Outcomes

- Learned real-world dataset preprocessing  
- Understood grouping and aggregation using Pandas  
- Learned filtering based on dates and country names  
- Calculated custom metrics like Active Cases  
- Built interactive maps using Plotly  
- Understood how analytics supports decision making  

---

## ✅ Conclusion

The experiment successfully demonstrated COVID-19 data analysis using Python. Real-world global pandemic data was cleaned, transformed, and analyzed to extract meaningful insights such as confirmed cases, recoveries, deaths, active cases, top affected countries, and Indian state-wise statistics. Interactive choropleth maps further improved understanding of regional spread. This experiment highlights the importance of data science in healthcare analytics and crisis management.

---
### Here are the images output in the experiment that is for some reason not displaying on the actual file:
<img width="1280" height="452" alt="image" src="https://github.com/user-attachments/assets/b0f9b3de-a952-4cde-ada7-345453a6a1e3" />
<img width="1273" height="424" alt="image" src="https://github.com/user-attachments/assets/072e65c4-1290-48cb-91d7-2700370e896b" />
<img width="1727" height="581" alt="image" src="https://github.com/user-attachments/assets/f5b084c4-ecfc-4a1e-ba34-3b0e6a165116" />
