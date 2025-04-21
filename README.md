#  Data Cleaning and Preprocessing – Customer Personality Analysis

## Task Objective  
Clean and prepare a raw dataset by handling missing values, removing duplicates, standardizing text and date formats, and ensuring the data is ready for analysis.

---

##  Dataset Used  
**Customer Personality Analysis** – downloaded from Kaggle  
File: `marketing_campaign.csv`

---

##  Tools Used  
- Python  
- Pandas

---

## Steps Performed  

1. **Loaded the dataset** using `pandas.read_csv()`  
2. **Checked for missing values** using `df.isnull().sum()`  
   - Found 24 missing values in the `Income` column  
   - Removed rows with missing income using `dropna(subset=['Income'])`  

3. **Removed duplicate rows** using `df.drop_duplicates()`  

4. **Standardized column names** to lowercase with underscores using:  
   ```python
   df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')

5. **Converted `Dt_Customer` to datetime format**  
   - Used `pd.to_datetime()` to convert the column  
   ```python
   df['dt_customer'] = pd.to_datetime(df['dt_customer'], dayfirst=True)
   
6. **Standardized categorical text values**  
   - Grouped marital status into `'Single'` and `'Relationship'`  
   ```python
   df['marital_status'] = df['marital_status'].replace(['Together', 'Married'], 'Relationship')
   df['marital_status'] = df['marital_status'].replace(['Divorced', 'Widow', 'Alone', 'Absurd', 'YOLO'], 'Single')

7. **Created a new feature – `total_kids`**  
   - Combined `kidhome` and `teenhome` to create a new column `total_kids`  
   ```python
   df['total_kids'] = df['kidhome'] + df['teenhome']

8. **Checked and validated data types using df.dtypes**

## Final Output

- Cleaned dataset saved as: 'cleaned_customer_personality.csv'




