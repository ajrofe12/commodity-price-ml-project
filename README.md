# **Climate Change & Commodity Price Analysis**

**Project Type:** Machine Learning / Applied Data Science  
**Tools:** Python, Jupyter Notebooks, Pandas, NumPy, Scikit-Learn, Matplotlib  
**Commodities Studied:** Coffee, Cocoa, Wheat, Maize, Rice, Soybeans, Cotton  
**Years Analyzed:** 2015–2022  

---

## **Overview**

This project investigates how climate variability influences global agricultural commodity prices. By pairing high-resolution climate data from major growing regions with historical commodity pricing data, the analysis explores whether climate indicators—such as temperature, precipitation, humidity, and derived anomaly metrics—help explain or predict movements in global agricultural markets.

The project includes data collection, preprocessing, derived climate variable engineering, exploratory visualizations, correlation testing, lag analysis, machine learning modeling, and a discussion of model limitations during global disruptions.

---

## **Commodities & Growing Regions**

Each commodity is linked to a key global production region:

- **Coffee:** Colombia & Minas Gerais (Brazil)  
- **Cocoa:** Ghana  
- **Wheat:** U.S. Great Plains  
- **Maize (Corn):** U.S. Corn Belt  
- **Rice:** Southeast Asia  
- **Soybeans:** Brazil Soy Belt  
- **Cotton:** India  

Climate variables collected include:
- Temperature  
- Precipitation  
- Relative humidity  
- Dewpoint temperature  

Derived features include:
- Temperature/precipitation anomalies  
- 3-month moving averages  
- 3-month cumulative precipitation  
- Drought index  
- Heat stress index  

---

## **Dataset Structure**

The final integrated dataset contains:

- **95 monthly observations** (Feb 2015 → Dec 2022)  
- **86 features**, including:  
  - Monthly commodity prices  
  - Region identifiers  
  - Climate variables (raw + engineered)  
  - Time-based features  

Example column groups for coffee:

- `Coffee_Price`  
- `Coffee_Region`  
- `Coffee_temperature_C`  
- `Coffee_precip_m`  
- `Coffee_temp_anomaly`  
- `Coffee_precip_anomaly`  
- `Coffee_temp_3m_avg`  
- `Coffee_precip_3m_sum`  
- `Coffee_drought_index`  
- `Coffee_heat_stress`  

---

## **Data Processing Workflow**

### **1. Raw Data Collection**
- ERA5-Land hourly climate data (Copernicus Climate Data Store)  
- Global commodity price data from major exchanges  

### **2. Climate Extraction & Region Filtering**
- Climate data cropped to each commodity’s major production region  
- Key variables extracted and standardized  

### **3. Quarterly Aggregation → Monthly Expansion**
- Climate data first aggregated into quarterly statistics  
- Then interpolated or evenly distributed to monthly resolution  
- Ensures smooth, consistent monthly time-series data  

### **4. Derived Climate Metrics**
Creation of higher-level climate signatures:
- Temperature & precipitation anomalies  
- Rolling averages and sums  
- Composite drought & heat stress indices  

### **5. Master Dataset Integration**
- Climate and price series merged on date  
- All commodities compiled into a single analytical dataset  

---

## **Analysis Methods**

### **Exploratory Analysis**
- Visual comparisons of climate conditions across regions  
- Seasonal and annual climate cycles  
- Commodity price trends and volatility patterns  

### **Correlation & Lag Analysis**
Investigated whether climate affects prices with delays:
- Lags tested from 0 to 6 months  
- Found modest but meaningful lagged relationships (varies by commodity)  

### **Random Forest Modeling**
A Random Forest regressor was used to explore predictive power of climate variables.

Findings:
- Strong performance on training data  
- Large performance drop on test data, driven by post-2020 market disruptions  
- Demonstrates sensitivity of climate-based models to non-climate shocks  

---

## **Key Findings**

### **1. Climate–Price Correlations Exist but Are Limited**
- Coffee temperature anomalies correlated ≈ +0.25 with price  
- Drought indices often negatively correlated  
- Lagged climate features matter (1–3 months)  

### **2. Climate Models Break Down After 2020**
- Post-COVID price spikes were not climate-driven  
- Global supply chain and macro disruptions overwhelmed climate signals  
- Test-set performance collapsed, revealing structural breaks  

### **3. Price Prediction Requires More Than Climate Data**
- Climate explains part of long-term pricing patterns  
- Extreme events, policy shocks, and global disruptions must be modeled separately  

---

## **Proposed Solution: Markovian Momentum Model (MMM)**

To handle periods where climate relationships break down (e.g., COVID era), the project proposes a hybrid **Markovian Momentum Model**, which:

- Treats the system as a **non-stationary Markov process**  
- Monitors shock-sensitive indicators such as volatility changes and price acceleration  
- Adjusts prediction confidence during unusual market regimes  
- Preserves interpretability while adding responsiveness to external shocks  

This approach emphasizes the need for climate-centric models that remain robust under real-world disruptions.

---

## **About This Project**

This work sits at the intersection of:
- Climate science  
- Agricultural economics  
- Machine learning  
- Time-series modeling  
- Regime-switching systems  

It highlights the strengths and limitations of climate-driven commodity price models and proposes a new adaptive framework for future research.

---
