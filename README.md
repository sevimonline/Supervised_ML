# Supervised_ML

**Purpose:**  
Scrape second-hand car listings from [Arabam.com](https://www.arabam.com/) for 20 popular car brands including Hyundai, Audi, BMW, Mercedes-Benz, etc.

**Libraries Used:**  
`requests`, `BeautifulSoup`, `pandas`, `time`, `fake_useragent`

**Target Features:**
- Brand
- Model
- Year
- Mileage (KM)
- Fuel Type
- Transmission (Gear Type)
- Engine Volume
- Engine Power
- Location (City)
- Price

---

## 🧼 2. Data Preprocessing & Feature Engineering

**Data Cleaning:**
- Handling missing or null values  
- Converting `object` types to numerical (via label encoding or one-hot encoding)  
- Formatting numeric columns (e.g., removing commas from prices, KM)

**Feature Engineering:**
- **Car Age:** `Car Age = 2025 - Year`
- **Engine Volume Category:** Grouping engine volumes into bins
- **Geographic Grouping:** Mapping cities to geographical regions (e.g., İstanbul → Marmara)

---

## 📊 3. Dependent Variable Analysis (Price)

**Normality Tests:**
- Shapiro-Wilk Test  
- Anderson-Darling Test  

**Transformations (if needed):**
- Log Transformation  
- Box-Cox Transformation  

**Multicollinearity Checks:**
- Pearson Correlation Heatmap  
- Variance Inflation Factor (VIF)

---

## 🔁 4. Model Validation Techniques

**Cross Validation:**
- **K-Fold CV** (k = 5 or 10)  
- **Leave-One-Out Cross Validation (LOOCV)**

**Bootstrap Sampling:**
- Bootstrapped estimation of performance metrics (e.g., R², RMSE)  
- Confidence intervals for predictions

---

## 📈 5. Regression Model Building

**Model Types:**
- Linear Regression  
- Ridge Regression  
- Lasso Regression

**Performance Metrics:**
- R², Adjusted R²  
- Mean Squared Error (MSE)  
- Root Mean Squared Error (RMSE)  
- Mean Absolute Error (MAE)

---

## ✅ 6. Regression Assumption Diagnostics

**Assumptions Checked:**
- **Normality of Residuals:** Q-Q Plot, Histogram of residuals  
- **Homoscedasticity:** Residuals vs Fitted Values Plot  
- **Multicollinearity:** VIF Scores  
- **Outliers & Influence Points:**  
  - Leverage Plots  
  - Cook’s Distance Analysis

**Bias-Variance Tradeoff:**  
- Model complexity vs error tradeoff visualization

**Endogeneity Evaluation:**  
- Discussed theoretically (e.g., possibility of omitted variable bias or IV needs)

---

## 📉 7. Prediction vs. Actual Comparison

- Scatter plot comparing actual vs predicted prices  
- Colored/marked by relevant segments (e.g., engine volume or brand)

---

## 💻 8. Streamlit Interface for Model Deployment

**Inputs:**
- Year  
- Mileage (KM)  
- Engine Volume  
- Fuel Type  
- Transmission  
- Region/City  

**Outputs:**
- Predicted Price  
- 95% Confidence Interval (via bootstrap or model's CI)

**Visual Feedback:**
- Model residual plot  
- Interactive pricing distribution based on user input

---

## 🎯 Optional Enhancements

- 🔍 Add XGBoost or LightGBM models for performance comparison  
- 🎯 SHAP or LIME for model interpretability  
- 🔁 Cron job setup for automatic data scraping and model retraining
