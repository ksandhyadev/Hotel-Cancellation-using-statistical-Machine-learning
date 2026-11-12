# 🏨 Hotel Booking Cancellation Prediction

An end-to-end Machine Learning project to analyze hotel booking behaviors, identify patterns behind cancellations, and predict whether a customer is likely to cancel their reservation using **Logistic Regression**.

---

## 📌 Table of Contents
- [Overview](#-overview)
- [Problem Statement](#-problem-statement)
- [Dataset](#-dataset)
- [Key Features](#-key-features)
- [Project Workflow](#-project-workflow)
- [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
- [Model & Evaluation](#-model--evaluation)
- [Feature Importance](#-feature-importance)
- [Tech Stack](#-tech-stack)
- [Installation & Setup](#-installation--setup)
- [How to Run](#-how-to-run)
- [Future Improvements](#-future-improvements)

---

## 📖 Overview

Hotel booking cancellations result in significant revenue loss, inventory management challenges, and operational inefficiencies for the hospitality industry. By anticipating cancellations before check-in dates, hotels can optimize pricing, manage overbooking strategies, and take proactive retention measures.

This project builds a binary classification pipeline using Python and Scikit-Learn to estimate cancellation likelihoods and pinpoint the most influential factors driving cancellations.

---

## 🎯 Problem Statement

Given customer reservation data, predict the target variable:
- `is_canceled = 0` ➔ Booking **Not Cancelled** (Kept)
- `is_canceled = 1` ➔ Booking **Cancelled**

---

## 📊 Dataset

- **Source:** [TidyTuesday Hotel Bookings Dataset](https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-02-11/hotels.csv) (originally by Antonio, de Almeida, and Nunes, 2019).
- **Contents:** Real reservation records from City Hotel and Resort Hotel properties, spanning booking dates, customer demographics, room preferences, and booking channels.

---

## 🔍 Key Features

Out of the full dataset, 19 domain-relevant features were selected:

| Feature Category | Features Included |
| :--- | :--- |
| **Target** | `is_canceled` |
| **Booking Timing** | `lead_time`, `arrival_date_month`, `arrival_date_week_number` |
| **Stay Duration** | `stays_in_weekend_nights`, `stays_in_week_nights` |
| **Guest Profile** | `adults`, `children`, `babies`, `customer_type`, `is_repeated_guest` |
| **Booking History** | `previous_cancellations`, `previous_bookings_not_canceled`, `booking_changes` |
| **Commercial Terms**| `deposit_type`, `adr` (Average Daily Rate), `market_segment`, `distribution_channel`, `hotel` |

---

## ⚙️ Project Workflow


---

## 📈 Exploratory Data Analysis (EDA)

Key analyses performed in the notebook:
1. **Target Distribution:** Evaluated overall booking cancellation rate and class balance.
2. **Lead Time Analysis:** Examined the correlation between booking advance days and cancellation probability via boxplots (longer lead times show higher tendency to cancel).
3. **Deposit Type Breakdown:** Compared cancellation percentages across `No Deposit`, `Non Refund`, and `Refundable`.
4. **Customer Type Breakdown:** Identified behavior differences among `Transient`, `Contract`, `Group`, and `Transient-party` segments.
5. **Correlation Heatmap:** Investigated multi-collinearity across numerical columns.

---

## 🤖 Model & Evaluation

### Model
- **Algorithm:** Logistic Regression (`max_iter=1000`, `random_state=42`)
- **Scaling:** `StandardScaler` fitted on training set and applied to test set.
- **Data Split:** 80% Training / 20% Testing with target stratification.

### Evaluation Metrics
- **Accuracy Score**
- **Precision, Recall, and F1-score** via Scikit-Learn `classification_report`
- **Confusion Matrix** visual display (`ConfusionMatrixDisplay`)
- **Probability Output:** Probability thresholding via `predict_proba()` for customized risk assessment

---

## 💡 Feature Importance

Model coefficients were extracted to calculate feature importance:
- Coefficients were converted to absolute values and ranked to determine the top 15 drivers of hotel cancellations.
- Visualized using Seaborn horizontal bar charts to provide actionable business insights (e.g., impact of non-refundable deposits, lead time, and booking modifications).

---

## 🛠️ Tech Stack

- **Language:** Python 3.8+
- **Data Manipulation:** `pandas`, `numpy`
- **Visualization:** `matplotlib`, `seaborn`
- **Machine Learning:** `scikit-learn`
- **Environment:** Google Colab / Jupyter Notebook

---

## 🚀 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/hotel-booking-cancellation.git
   cd hotel-booking-cancellation

   python -m venv venv
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

pip install pandas numpy matplotlib seaborn scikit-learn

How to Run

Option 1: Jupyter Notebook / Google Colab
Launch Jupyter Notebook:
jupyter notebook
Open Sml Project.ipynb and execute the cells sequentially.
Or upload Sml Project.ipynb directly into Google Colab

Option 2: Python Script

If running as a standalone .py script:

python sml_project.py
