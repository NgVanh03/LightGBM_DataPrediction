# Sale Data Prediction Project
Table of Contents
Overview
Features
Requirements
Installation
Usage
Jupyter Notebook
Web AI Agent
Database Setup
File Structure
Model Details
Notes
Contributing
License
Future Improvements
Overview
This project analyzes and predicts sales data using a dataset with 186,850 records, containing 6 columns: Order ID, Product, Quantity Ordered, Price Each, Order Date, and Purchase Address. The objectives include:

Data Collection: Load and explore the sales dataset from Sales_data.ftr.
Data Preparation: Clean data and handle missing values (e.g., 186,305 non-null entries).
Prediction: Use a LightGBM model to predict future demand (e.g., 2020 predictions based on 2019 data).
Visualization: Compare monthly demand trends for 2019 and 2020.
Integration: Develop a Web AI Agent to convert natural language queries into SQL (NL2SQL) for real-time querying.
The project is built with Python, utilizing libraries such as pandas, numpy, matplotlib, lightgbm, and integrates with a Flask-based web application.

Features
Load and inspect the sales dataset.
Preprocess data and export to sales_data_for_mysql.csv for database integration.
Visualize demand trends using Matplotlib.
Train and save a LightGBM model (lightgbm_sales_model.joblib).
Web AI Agent with NL2SQL functionality (e.g., "Show total revenue by month").
Requirements
Python: 3.12.4 (or compatible version)
Required Libraries:
pandas
numpy
matplotlib
lightgbm
joblib
flask
transformers (for NL2SQL)
sqlite3 (or MySQL/PostgreSQL for database)
Installation Command:
bash

Thu gọn

Bọc lại

Chạy

Sao chép
pip install pandas numpy matplotlib lightgbm joblib flask transformers sqlite3
Installation
Clone or download the project files:
bash

Thu gọn

Bọc lại

Chạy

Sao chép
git clone <repository-url>
Place the dataset Sales_data.ftr in the Data/ directory.
Install required libraries using the command above.
Set up the database (see Database Setup).
Run the Jupyter Notebook SaleData_Prediction.ipynb or the web app (app.py).
Usage
Jupyter Notebook
Open SaleData_Prediction.ipynb in Jupyter Notebook or JupyterLab.
Execute cells in sequence to:
Load and explore the dataset.
Preprocess data and generate the 2019-2020 demand chart.
Export data to sales_data_for_mysql.csv.
Save the trained model to lightgbm_sales_model.joblib.
Review output visualizations and saved files.
Web AI Agent
Ensure the database is populated with sales_data_for_mysql.csv (see Database Setup).
Run the Flask server:
bash

Thu gọn

Bọc lại

Chạy

Sao chép
python app.py
Access the web app at http://localhost:5000.
Log in with default credentials (admin@example.com / admin).
Use the chat interface to enter queries (e.g., "Hiển thị tổng doanh thu tháng 12/2019").
Database Setup
SQLite (Default):
Run python db_config.py to create sales.db with a sales table containing columns: Order_ID, Product, Quantity_Ordered, Price_Each, Order_Date, Purchase_Address.
MySQL/PostgreSQL (Optional):
Import sales_data_for_mysql.csv into your database.
Update db_config.py with your connection string (e.g., MySQL: mysql+pymysql://user:password@localhost/db_name).
Adjust table schema if needed to match your database engine.
File Structure
text

Thu gọn

Bọc lại

Sao chép
SaleData_Prediction/
├── Data/
│   └── Sales_data.ftr         # Input dataset
├── sales_data_for_mysql.csv   # Exported cleaned data
├── lightgbm_sales_model.joblib # Saved prediction model
├── app.py                    # Flask backend for Web AI Agent
├── db_config.py              # Database initialization
├── nl2sql_model.py           # NL2SQL logic
├── templates/
│   ├── base.html            # Base template
│   ├── chat.html            # Chat interface
│   └── admin.html           # Admin panel
├── static/
│   ├── style.css            # CSS styles
│   └── script.py            # Brython frontend logic
└── SaleData_Prediction.ipynb # Main analysis notebook
Model Details
LightGBM Model: Trained on preprocessed data to predict Daily Demand. Saved as lightgbm_sales_model.joblib for reuse. Requires prior training with historical data (not fully detailed in the snippet).
NL2SQL Model: Utilizes a pre-trained T5 model from Hugging Face, fine-tuned on sample queries (e.g., "Show total revenue by month" → SELECT SUM(Quantity_Ordered * Price_Each) FROM sales WHERE YEAR(Order_Date) = 2019 GROUP BY MONTH(Order_Date)). Fine-tuning with Vietnamese data is recommended for higher accuracy.
Notes
The dataset contains 545 missing rows. Handle these (e.g., drop or impute) based on your use case.
The future_predictions_df for 2020 is not fully defined in the provided snippet. Ensure it’s generated before running the chart code.
NL2SQL accuracy depends on fine-tuning. Provide a training dataset with Vietnamese query-SQL pairs.
The web app uses Brython for frontend, which may have performance limitations with large datasets.
Contributing
Fork this repository and enhance features (e.g., add data cleaning, improve NL2SQL, integrate OpenAI).
Submit pull requests with detailed descriptions of changes.
License
For educational purposes. Modify and use as needed.

Future Improvements
Fine-tune the NL2SQL model using SaleData_Prediction.ipynb data.
Add real-time chart rendering with Matplotlib or Plotly in the web app.
Support multiple languages (e.g., English, Vietnamese) for queries.
Optimize database queries for large-scale data handling.
Enhance security with user authentication and role-based access.
