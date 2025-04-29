# 🍄 Experiment 3: Binary Classification Web App (Mushroom Dataset)

This project demonstrates a binary classification system using **Streamlit** and **Scikit-learn**, deployed inside a Docker container. It predicts whether mushrooms are **edible or poisonous** based on various features.

---

## 🧠 What This Does

- Lets you choose between 3 classifiers:  
  - Support Vector Machine (SVM)  
  - Logistic Regression  
  - Random Forest  
- Visualizes performance using:  
  - Confusion Matrix  
  - ROC Curve  
  - Precision-Recall Curve  
- Trains on the `mushrooms.csv` dataset.

---

## 📁 Folder Structure

```
exp3/
├── app.py                  # Main Streamlit application
├── requirements.txt        # Python dependencies
├── mushrooms.csv           # Dataset
├── exp3 1.jpg              # Screenshot of codebase
└── exp3 2.jpg              # Screenshot of output
```

---

## ⚙️ How to Run This App

### ✅ Step 1: Build the Docker Image

```bash
cd exp3
docker build -t mushroom-classifier .
```

### ▶️ Step 2: Run the Docker Container

```bash
docker run -p 8501:8501 mushroom-classifier
```

### 🌐 Access the App

Open your browser and go to:  
**[http://localhost:8501](http://localhost:8501)**

---

## 🐍 Dependencies

These are managed in `requirements.txt`. Key libraries include:

- `streamlit`
- `scikit-learn`
- `pandas`
- `matplotlib`
- `altair`

Install locally (optional):

```bash
pip install -r requirements.txt
```

---

## 📊 Dataset: `mushrooms.csv`

- The dataset contains 22 categorical features about mushrooms.
- The target variable is `type`: `edible` or `poisonous`.
- Categorical data is preprocessed using `LabelEncoder`.

---

## 🖼️ Screenshots

### 👨‍💻 Codebase View

![Codebase Screenshot](exp3%201.jpg)

---

### ✅ App Output View

![App Output Screenshot](exp3%202.jpg)

---

## 📢 License

This project is released under the **MIT License**.

---

> 🌟 Explore interactive machine learning applications with real-world datasets using Streamlit and Docker!
```

---
