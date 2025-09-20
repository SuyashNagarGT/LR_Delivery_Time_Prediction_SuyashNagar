# 🚚 Delivery Time Estimation – Porter Services  
*Predicting delivery time with regression modeling and operational insights*

![Python](https://img.shields.io/badge/Python-3.8%2B-blue) ![ML](https://img.shields.io/badge/Model-Linear%20Regression-orange) ![Status](https://img.shields.io/badge/Status-Stable-brightgreen)

---

## 📦 Project Overview
This project builds a regression model to predict delivery time for orders placed via Porter. It leverages operational features such as:
- 📍 Restaurant location (`market_id`)
- 🍽️ Store category (`store_primary_category`)
- 📦 Order details (`total_items`, `subtotal`, `num_distinct_items`)
- 🚴 Delivery partner availability (`dashers_load_index`, `total_outstanding_orders`)
- 🕒 Temporal features (`hour`, `day_of_week`, `isWeekend`)

---

<details>
<summary><strong>🧪 Dataset Summary</strong></summary>

- **Records:** 175,777 rows × 14 columns  
- **No missing or duplicate values**  
- **Categorical features:** `market_id`, `store_primary_category`, `order_protocol`  
- **Target variable:** `time_taken_mins` (delivery duration in minutes)  
- **Outliers handled using IQR method**  
</details>

---

<details>
<summary><strong>🔧 Data Pipeline</strong></summary>

1. **Data Loading & Cleaning**
   - Converted date/time fields to `datetime`
   - Removed negative values in key operational fields

2. **Feature Engineering**
   - Derived: `hour`, `day_of_week`, `isWeekend`
   - Operational ratios: `dashers_order_ratio`, `dashers_load_index`

3. **Encoding & Scaling**
   - One-hot encoding for top categories
   - StandardScaler for numerical features

4. **Train-Test Split**
   - 80% training / 20% testing with `random_state=80`
</details>

---

<details>
<summary><strong>📊 Exploratory Data Analysis</strong></summary>

- Most features are **right-skewed**, except `distance` (symmetric)
- **Weekend and peak-hour orders** show longer delivery times
- **Strongest correlations** with delivery time:
  - `dashers_load_index` (0.49)
  - `distance` (0.46)
  - `subtotal`, `total_outstanding_orders`
</details>

---

<details>
<summary><strong>📈 Model Building</strong></summary>

- **Algorithm:** Linear Regression using `statsmodels.OLS`
- **Feature Selection:** Recursive Feature Elimination (RFE)
- **Final Model Features:**
  - `distance`, `dashers_load_index`
  - `Hrs_19`, `Hrs_20`, `Hrs_21`, `Hrs_22`
  - `market_id_2.0`, `market_id_4.0`

### ✅ Performance Metrics
| Metric     | Train Set | Test Set |
|------------|-----------|----------|
| MAE        | 3.75      | 3.75     |
| MSE        | 22.83     | 22.65    |
| RMSE       | 4.78      | 4.76     |
| R² Score   | 0.6707    | 0.6642   |

</details>

---

<details>
<summary><strong>📉 Residual & Coefficient Analysis</strong></summary>

- Residuals are **normally distributed** and centered around zero
- Coefficients:
  - `distance`: +4.22 mins
  - `dashers_load_index`: +4.90 mins
  - `Hrs_20`: −4.64 mins (faster delivery at 8PM)
</details>

---

## 🧠 Key Takeaways
- Delivery time is most influenced by **distance** and **dashers’ workload**
- Temporal features (hour of day) reveal **efficiency patterns**
- Market-specific strategies can improve performance

---

## 🛠️ Recommendations for Porter
- Optimize routing algorithms to reduce travel time
- Balance dasher workload during peak hours
- Leverage hour-based delivery trends for resource allocation
- Continuously monitor and retrain model with fresh data

---

## 📚 Subjective Q&A (Interview Prep)
- What are the top 3 features affecting delivery time?
- How were outliers handled?
- Explain linear regression and its assumptions
- Difference between simple and multiple regression
- Role of cost function and residual plots

---

## 👨‍💻 Author
**Suyash Nagar**  
*Data Science Enthusiast | Regression Modeling | Operational Analytics*

 ---

 📬 Connect with Me
Let’s Collaborate 🤝 Whether it’s AI, Machine Learning or Data Analytics, —I'm always open to building something impactful.

<p align="center" style="display: flex; justify-content: center; gap: 40px; flex-wrap: wrap;">

  <!-- LinkedIn -->
  <a href="https://www.linkedin.com/in/suyashnagar" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" width="30" alt="LinkedIn"/>
  </a>

  <!-- YouTube -->
  <a href="https://www.youtube.com/@suyashnagar" target="_blank">
    <img src="https://img.icons8.com/color/48/youtube-play.png" width="30" alt="YouTube"/>
  </a>

  <!-- GitHub (white version for dark background) -->
  <a href="https://github.com/SuyashNagarGT" target="_blank">
    <img src="https://img.icons8.com/ios-filled/50/ffffff/github.png" width="30" alt="GitHub"/>
  </a>

  <!-- Phone (white icon) -->
  <a href="tel:+917906655101" target="_blank">
    <img src="https://img.icons8.com/ios-filled/50/ffffff/phone.png" width="30" alt="Phone"/>
  </a>

  <!-- Email (white icon) -->
  <a href="mailto:suyash.nagar@gmail.com" target="_blank">
    <img src="https://img.icons8.com/ios-filled/50/ffffff/email.png" width="30" alt="Email"/>
  </a>

</p>


 


