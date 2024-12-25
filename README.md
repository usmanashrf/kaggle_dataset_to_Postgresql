# 📊 Kaggle Dataset to Neon DB Pipeline 🚀

This project demonstrates a streamlined workflow for downloading datasets from **Kaggle**, processing them in **Google Colab**, and storing them in a **Neon PostgreSQL Database**.

## 📚 Table of Contents
- [✨ Key Features](#-key-features)
- [🛠️ Tech Stack](#️-tech-stack)
- [📥 Installation and Setup](#-installation-and-setup)
- [🚀 Workflow](#-workflow)
- [🔗 Database Connection](#-database-connection)
- [✅ Verification](#-verification)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

---

## ✨ Key Features
- **Kaggle Integration:** Seamless dataset downloads via the Kaggle API.
- **Data Processing:** Data manipulation and cleaning with Pandas.
- **Database Integration:** Store datasets in PostgreSQL Neon DB with SQLAlchemy.
- **Scalable Workflow:** Efficient handling of large datasets.

---

## 🛠️ Tech Stack
- **Python**
- **Google Colab**
- **Kaggle API**
- **Pandas**
- **SQLAlchemy**
- **PostgreSQL (Neon DB)**

---

## 📥 Installation and Setup

### 1. Install Required Libraries
```bash
!pip install kaggle psycopg2-binary pandas sqlalchemy
```

### 2. Upload Kaggle API Key
1. Get your Kaggle API key (`kaggle.json`) from [Kaggle Account Settings](https://www.kaggle.com/account).
2. Upload it to Colab:
```python
from google.colab import files
files.upload()  # Upload kaggle.json
!mkdir -p ~/.kaggle
!mv kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

### 3. Connect to Neon DB
```python
from sqlalchemy import create_engine

DATABASE_URL = 'postgresql+psycopg2://<username>:<password>@<host>:5432/<dbname>'
engine = create_engine(DATABASE_URL)
```
Replace placeholders with your Neon DB credentials.

---

## 🚀 Workflow

### Step 1: Download Kaggle Dataset
```python
!kaggle datasets download -d <dataset-name> --unzip
```

### Step 2: Load Dataset into Pandas
```python
import pandas as pd

df = pd.read_csv('your_dataset_file.csv')
print(df.head())
```

### Step 3: Upload Dataset to Neon DB
```python
df.to_sql('table_name', con=engine, if_exists='replace', index=False)
print('Dataset uploaded successfully!')
```

---

## 🔗 Database Connection
You can query your dataset in Neon DB:
```sql
SELECT * FROM table_name LIMIT 5;
```

---

## ✅ Verification
1. Open your Neon DB dashboard.
2. Verify the dataset by running SQL queries.

---

## 🤝 Contributing
Contributions are welcome! Feel free to submit an issue or a pull request.

