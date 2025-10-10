# 🎌 Anime Recommendation Systems
📅 *May 2025* | 📚 *Data Analytics Project*  

---

## 🧠 Project Overview
This project explores two fundamental **recommender system** approaches — **Collaborative Filtering** and **Content-Based Filtering** — applied to an anime dataset.  
The goal is to predict user ratings and recommend anime titles that best match individual preferences.

The project includes:
- Data exploration and visualization  
- Dataset preprocessing  
- Model implementation and evaluation  
- Performance comparison and discussion  

---

## 📂 Dataset
The analysis is based on two publicly available datasets:

### **`anime.csv`**
Contains metadata for **12,294 anime titles**.  
Columns: anime_id | name | genre | type | episodes | rating | members

### **`rating.csv`**
Contains **7.8 million** user–anime interactions.  
Columns: user_id | anime_id | rating

### **Key Insights**
- 43 unique genres — most frequent: *Action*, *Comedy*, *Adventure*  
- Main anime types: *TV*, *Movie*, and *OVA*  
- Popularity is highly skewed — e.g., *Death Note* exceeds 1M members  
- Missing data in `episodes`, `genre`, and `rating` columns handled during preprocessing  

---

## 🧹 Data Preprocessing
Cleaning and preparation steps:
- Filled missing **episodes**, **genre**, **type**, and **rating** using median, mode, or mean values  
- Removed **ratings marked as -1** (~1.5M entries)  
- Dropped **duplicate user-anime ratings**  
- Performed **80/20 train-test split**

After cleaning, both datasets were **free of missing and duplicate values** and ready for modeling.

---

## 🤖 Recommender Models

### 1️⃣ User-Based Collaborative Filtering
- Implemented using **K-Nearest Neighbors Regressor** (`scikit-learn`)  
- Similarity metric: **cosine similarity** between users  
- Predicts ratings as the average of the **5 nearest neighbors**  
- Evaluation metric: **RMSE**

**Result:**  
> 🟩 RMSE = **0.3954**

✅ Excellent predictive performance due to rich user-rating interactions.

---

### 2️⃣ Content-Based Filtering
- Uses **anime genres** as features  
- Builds a **binary genre matrix** (1 if anime includes a genre, else 0)  
- Computes **cosine similarity** between anime vectors  
- Predicts user ratings based on **weighted averages of previously rated anime**

**Result:**  
> 🟨 RMSE = **1.3337**

⚙️ Performs reasonably well but limited by sparse or incomplete metadata.

---

## ⚖️ Model Comparison

| Model Type | RMSE | Strengths | Limitations |
|-------------|------|------------|--------------|
| **Collaborative Filtering** | 0.3954 | Captures user behavior and preferences effectively | Needs sufficient rating data |
| **Content-Based Filtering** | 1.3337 | Works for new/unrated anime (cold start) | Limited by available metadata |

---

## 🚀 Future Work
- Develop a **hybrid recommender system** combining collaborative and content-based methods  
- Explore **matrix factorization** and **deep learning** approaches for scalability  
- Enhance handling of **data sparsity** and **cold-start problems**

---

## 🧩 Tools & Libraries
- 🐍 **Python 3**
- 📦 **pandas**, **NumPy**, **scikit-learn**
- 📊 **Matplotlib**, **Seaborn**
- 🧪 **Jupyter Notebook**

### 🏁 Summary
This project demonstrates how **collaborative filtering** outperforms **content-based filtering** in predicting user preferences when rich user behavior data is available. Future hybrid approaches can leverage both **user similarity** and **item similarity** for even better recommendations.
