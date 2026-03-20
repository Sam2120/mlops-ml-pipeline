# mlops-ml-pipeline

# **📘 README.md**

# **MLOps Machine Learning Pipeline (GitHub + DVC + AWS S3)**

This project implements a complete end‑to‑end **Machine Learning Pipeline** using modern **MLOps tools**.  
It demonstrates how to structure ML workflows, track datasets with DVC, and store data in AWS S3 for reproducibility.

---

## **📌 Project Overview**

The goal of this project is to build a simple but complete machine learning workflow consisting of:

1. **Data Ingestion**  
2. **Data Preprocessing**  
3. **Feature Engineering**  
4. **Model Training**  
5. **Model Evaluation**

The project uses:

- **GitHub** → Version control  
- **DVC (Data Version Control)** → Dataset tracking  
- **AWS S3** → Remote storage for DVC  
- **Python** → ML pipeline implementation  

This setup follows real‑world MLOps practices where code, data, and models are versioned and reproducible.

## **📊 Dataset**

The project uses the **Titanic Dataset**, a classic dataset for binary classification.  
It contains passenger information such as:

- Age  
- Sex  
- Passenger class  
- Fare  
- Number of siblings/spouses  
- Number of parents/children  
- Survival status (target variable)

The dataset is stored in:

```
data/Titanic-Dataset.csv
```

and tracked using DVC.

---

## **⚙️ Pipeline Stages**

### **1. Data Ingestion**
Loads the dataset from the `data/` folder using pandas.

### **2. Data Preprocessing**
Handles missing values and basic cleaning.

### **3. Feature Engineering**
Separates features and target variable.

### **4. Model Training**
Trains a machine learning model (Random Forest) and saves it to the `models/` folder.

### **5. Model Evaluation**
Evaluates the model using accuracy score.

---

## **🗂️ DVC for Data Versioning**

DVC is used to track the dataset:

```bash
dvc add data/Titanic-Dataset.csv
```

This creates:

- `data/Titanic-Dataset.csv.dvc`
- Updates `.gitignore` to exclude the raw dataset

The dataset is pushed to AWS S3 using:

```bash
dvc push
```

---

## **☁️ AWS S3 Remote Storage**

An S3 bucket is used as the DVC remote:

```bash
dvc remote add -d myremote s3://mlops-ml-pipeline-samith
```

After pushing, the bucket contains hashed DVC cache folders such as:

```
files/
md5/
23/
```

## **📜 License**

This project is for educational purposes as part of an MLOps assignment.

