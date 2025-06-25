# Overview
This project focuses on analyzing and predicting sales data using a dataset containing information about orders. The dataset includes 186,850 records with 6 columns: Order ID, Product, Quantity Ordered, Price Each, Order Date, and Purchase Address. 

The main goals are:
- Data Collection: Load and explore the sales dataset.
- Data Preparation: Clean and preprocess the data for analysis.
- Prediction: Use a LightGBM model to predict future sales demand (e.g., comparing 2019 actual data with 2020 predictions).
- Visualization: Generate charts to compare monthly demand.
The project is implemented using Python with libraries like pandas, numpy, matplotlib, and lightgbm.

# Features
- Load and inspect the sales dataset from a Feather file (Sales_data.ftr).
- Clean the data by handling missing values and preparing it for analysis.
- Visualize monthly demand trends for 2019 and predicted demand for 2020.
- Export the cleaned dataset to a CSV file (sales_data_for_mysql.csv) for further use (e.g., database integration).
- Save the trained LightGBM model to a file (lightgbm_sales_model.joblib) for future predictions.
  
# Requirements
- Python 3.12.4 (or compatible version)
- Required libraries:
  - **pandas**
  - **numpy**
  - **matplotlib**
  - **lightgbm**
  -**joblib**
    
## Install dependencies using:
```bash
pip install pandas numpy matplotlib lightgbm joblib
```
## Installation
1. Clone the repository or download the project files.
2. Ensure the dataset file Sales_data.ftr is placed in the Data/ directory.
3. Install the required libraries as listed above.
4. Run the Jupyter Notebook SaleData_Prediction.ipynb using Jupyter Notebook or JupyterLab.

## Usage
1. Open **SaleData_Prediction.ipynb** in Jupyter Notebook.
2. Execute the cells in sequence to:
- Load and explore the dataset.
- Preprocess the data (e.g., handle missing values, convert data types if needed).
- Generate the demand comparison chart for 2019 and 2020.
- Export the data to **sales_data_for_mysql.csv**.
- Save the trained model to **lightgbm_sales_model.joblib**.
3. Review the output visualizations and saved files.
  
## File Structure
- **SaleData_Prediction.ipynb**: Main Jupyter Notebook containing the code and analysis.
- **Data/Sales_data.ftr**: Input dataset file (Feather format).
- **sales_data_for_mysql.csv**: Exported cleaned dataset.
- **lightgbm_sales_model.joblib**: Saved LightGBM model file.
  
## Notes
- The dataset contains missing values (e.g., 186,305 non-null entries out of 186,850). Further cleaning may be required depending on the use case.
- The prediction model (final_model) assumes prior training (not fully detailed in the provided snippet). Ensure the model is trained before saving.
- The chart compares actual 2019 data with 2020 predictions, but the future_predictions_df is not fully defined in the snippet. Adjust the code if needed to match your data source.
  
## Contributing
Feel free to fork this repository, make improvements (e.g., add data cleaning steps, enhance visualizations), and submit pull requests.

## License
This project is for educational purposes. No specific license is applied; modify and use as needed.
