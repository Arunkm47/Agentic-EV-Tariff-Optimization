# Agentic AI-Based Dynamic Tariff Optimization for EV Charging Networks

### An Intelligent Data-Driven Framework for EV Charging Demand Prediction, Dynamic Pricing, and Operational Monitoring

## 1. Project Overview

Electric Vehicle (EV) adoption is increasing rapidly, creating new challenges for charging station operators, including fluctuating electricity demand, uneven charger utilization, and inefficient pricing strategies.

This project develops an agent-based framework for optimizing EV charging tariffs using historical charging session data and demand forecasting techniques.

The proposed framework integrates three functional agents:

- **Demand Prediction Agent:** Forecasts EV charging demand using machine learning models.
- **Tariff Pricing Agent:** Implements utilization-based dynamic pricing strategies to encourage demand shifting and improve revenue.
- **Monitoring & Learning Agent:** Evaluates operational performance through charging duration, idle time, customer response assumptions, and pricing efficiency.

The objective is to demonstrate how data-driven pricing and demand analysis can improve EV charging network operations.

## 2. Problem Statement

Traditional fixed-pricing strategies do not adequately respond to changing EV charging demand and charger utilization.

This can result in:
- Uneven distribution of charging demand.
- High charger utilization during peak periods.
- Underutilization during off-peak hours.
- Inefficient revenue generation.
- Operational inefficiencies at charging stations.

This project explores a demand-aware dynamic tariff optimization framework to address these challenges.

## 3. System Architecture

The proposed framework consists of three interconnected functional agents.

### Agent 1: Demand Prediction Agent

**Objective:** Predict EV charging demand using historical charging patterns.

**Implementation:**
- Analyzed UrbanEV charging volume data.
- Extracted time-based features such as hour and day of the week.
- Developed Linear Regression and Random Forest regression models.
- Implemented an ensemble prediction using the average of both model predictions.
- Evaluated performance using RMSE, MAE, and R².

**Selected Model:** Random Forest Regressor.

### Agent 2: Tariff Pricing Agent

**Objective:** Implement dynamic electricity pricing based on charging station utilization.

**Pricing Strategy:**

| Charger Utilization | Tariff |
|---|---:|
| Above 80% | 18 |
| Below 30% | 12 |
| Between 30% and 80% | 15 |

**Implementation:**
- Calculated average charger utilization.
- Applied rule-based tariff adjustment.
- Compared fixed-price and dynamic-price revenue.
- Estimated potential off-peak charging uplift.

### Agent 3: Monitoring & Learning Agent

**Objective:** Evaluate the operational and financial performance of the proposed pricing framework.

**Monitored Metrics:**
- Charging duration.
- Charger idle time.
- Estimated waiting time reduction.
- Customer response rate using demand elasticity.
- Pricing efficiency score.

These metrics help assess the potential impact of dynamic pricing on EV charging operations.

## 4. Datasets Used

The project uses two primary datasets.

### Dataset 1: UrbanEV – Shenzhen Districts

Used for charging demand forecasting and charger utilization analysis.

**Files:**
- `volume.csv` – Charging volume information.
- `occupancy.csv` – Charger occupancy and utilization.
- `price.csv` – Charging price information.
- `duration.csv` – Charging duration information.
- `time.csv` – Time-related information.
- `stations.csv` – Charging station information.

### Dataset 2: ACN Charging Sessions

**Dataset Period:** 25 April 2018 – 16 December 2018.

File: `acndata_sessions.json.xlsx`

Contains charging session information, including:
- `connectionTime`
- `disconnectTime`
- `doneChargingTime`
- `kWhDelivered`
- `stationID`
- `sessionID`
- `minutesAvailable`
- `kWhRequested`

**Dataset Usage:**
- UrbanEV: Demand forecasting and utilization analysis.
- ACN: Charging behavior, revenue analysis, and operational monitoring.

The datasets are included in the repository as a compressed ZIP archive.

## 5. Data Preprocessing & Exploratory Data Analysis

The following preprocessing and analysis steps were performed:

- Loaded datasets using Pandas.
- Selected relevant ACN charging session features.
- Removed records with missing critical values.
- Converted timestamp columns into datetime format.
- Analyzed energy delivered per charging session.
- Identified the most active charging stations.
- Examined hourly charging demand patterns.
- Extracted time-based features for demand prediction.

## 6. Machine Learning Models

Three prediction approaches were evaluated.

### Linear Regression
Used as a baseline regression model for EV charging demand prediction.

### Random Forest Regressor
Implemented using an ensemble of decision trees to capture nonlinear relationships in charging demand.

**Configuration:**
- Number of estimators: 100
- Random state: 42
- Test size: 20%

### Agentic Ensemble Model
Combined the predictions from Linear Regression and Random Forest using an averaging approach.

The predictions were calculated as:

`Ensemble Prediction = (Linear Regression Prediction + Random Forest Prediction) / 2`

### Evaluation Metrics

- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- R² Score

## 7. Results & Performance

### Demand Prediction Results

The Random Forest model achieved the following reported performance:

| Metric | Result |
|---|---:|
| R² Score | 0.879 |
| RMSE | 965.59 |
| MAE | 738.45 |

Random Forest was selected as the best-performing model for the downstream framework.

### Business & Operational Metrics

| Metric | Result |
|---|---:|
| Revenue Gain | 10.28% |
| Estimated Off-Peak Uplift | ≈432 sessions |
| Estimated Waiting Time Reduction | 16.14 minutes |
| Customer Response Rate | -3.08 |
| Pricing Efficiency Score | 16.54 |

**Important Metric Assumptions:**

- Off-Peak Uplift uses an assumed 5% increase in charging sessions during low-utilization periods.
- Waiting Time Reduction is estimated using charger idle time as a proxy and a 10% reduction assumption.
- Customer Response Rate uses an assumed demand elasticity coefficient of -0.3.
- Revenue Gain is calculated by comparing the notebook's fixed-price and dynamic-price revenue calculations.

These business metrics are estimates based on the implemented assumptions, not experimentally observed post-deployment improvements.

## 8. Technologies & Tools Used

**Programming Language**
- Python

**Data Analysis & Visualization**
- Pandas
- NumPy
- Matplotlib
- Seaborn

**Machine Learning**
- Scikit-learn
- Linear Regression
- Random Forest Regressor

**Development Environment**
- Google Colab
- Jupyter Notebook

## 9. Project Structure

```text
Agentic-EV-Tariff-Optimization/
│
├── EV_project.ipynb
│
├── Datasets OP'26 Analytics-20260605T041945Z-3-001.zip
│
├── README.md
│
├── results.csv
│
└── model_comparison.csv
```

The CSV result files are generated by executing the notebook.

## 10. Installation & Execution

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/Agentic-EV-Tariff-Optimization.git
```

### Step 2: Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

### Step 3: Open the Notebook

Open `EV_project.ipynb` using Jupyter Notebook or Google Colab.

### Step 4: Upload the Dataset

The notebook uses Google Colab's file upload functionality to upload the dataset ZIP archive.

Upload the ZIP file with the filename:

`Datasets OP'26 Analytics-20260605T041945Z-3-001.zip`

### Step 5: Execute the Notebook

Run the notebook cells sequentially to:
- Extract the datasets.
- Perform data preprocessing.
- Conduct exploratory data analysis.
- Train and evaluate prediction models.
- Execute the three-agent framework.
- Calculate business and operational metrics.

## 11. Conclusion

This project demonstrates a data-driven approach to EV charging demand prediction and dynamic tariff optimization.

The Random Forest model achieved an R² score of 0.879, making it the selected prediction model among the evaluated approaches.

The framework further explores utilization-based pricing, revenue comparison, off-peak demand uplift, and operational monitoring.

The results highlight the potential of combining machine learning, data analytics, and dynamic pricing strategies to support more efficient EV charging network management.

## 12. Future Scope

- Integrate real-time EV charging station data.
- Develop advanced demand forecasting models.
- Implement reinforcement learning for adaptive tariff optimization.
- Incorporate actual customer response and behavioral data.
- Validate pricing strategies through real-world deployment.
- Develop an interactive monitoring dashboard.

## Author

**Arun Kumar Meena**

Undergraduate Student – Chemical Sciences  
Indian Institute of Technology (IIT) Roorkee

**Project:** Agentic AI-Based Dynamic Tariff Optimization for EV Charging Networks

---

*This project was developed as part of Open Project 2026.*
