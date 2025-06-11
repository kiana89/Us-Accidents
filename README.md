# US Accidents Analysis with RAPIDS & cuDF

This project focuses on analyzing and preprocessing a large-scale dataset of road accidents in the United States. By leveraging **GPU-accelerated technologies** such as **RAPIDS cuDF** and **Dask**, heavy data operations are performed significantly faster than with traditional CPU-based approaches.

## Dataset

- **Source**: Kaggle  
- **Link**: [US Accidents by Sobhan Moosavi](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents)  
- **Description**: A dataset containing over 7 million records of traffic accidents in the US from 2016 to 2023.

## Key Steps

### 1. Install Libraries & Download Data
- Install RAPIDS libraries in Google Colab.
- Install the `kaggle` API and download the dataset.
- Unzip the dataset and prepare it for analysis.

### 2.  Load Data with Dask and cuDF
- Initially load with `dask.dataframe` for overview.
- Then reload with `cudf.read_csv` for GPU acceleration.

### 3.  Initial Data Exploration
- Use `.info()` and `.describe()` to understand the structure and statistical distribution.

### 4.  Preprocessing and Optimization
- **Remove high-null columns** (more than 90% missing values).
- **Drop important null rows** (e.g., location and time columns).
- **Optimize memory usage** by:
  - Downcasting numeric types.
  - Encoding categorical variables using `LabelEncoder`.
- **Create new features**:
  - `Is_Cold`: Whether the temperature is below freezing.
  - `Is_Low_Visibility`: Whether visibility is less than 2 miles.
  - `Location_Hash`: A hashed location identifier for clustering.
- Drop unnecessary columns like raw city/county names and datetime fields.

### 5.  Result
- Final DataFrame is significantly reduced in memory size.
- Ready for modeling, clustering, or further analytical tasks.

##  Technologies Used

- RAPIDS cuDF
- Google Colab with GPU
- Dask
- Pandas / Scikit-learn
- Kaggle API

##  File Structure

```

usaccident.ipynb              # Main notebook for data processing
kaggle.json                   # API Key for Kaggle (should be uploaded in Colab)
US_Accidents_March23.csv      # The main dataset after extraction

```

##  Notes

- This notebook is designed for **Google Colab with GPU enabled**.
- Using `cuDF` allows large-scale data handling with less memory and more speed.
- Make sure to upload your `kaggle.json` file and set proper permissions.


##  Memory Optimization Summary

- **Original size**: ~3.24 GB  
- **Optimized size**: ~0.968 GB  

