Loaded the dataset usings pandas
pd.read_csv(“sample_sales_data.csv”)

Verified the missing values and printed them
missing_values = data.isnull()
print(missing_values)
missing_summary = data.isnull().sum()
print(missing_summary)
output
ORDERNUMBER 0
QUANTITYORDERED 0
PRICEEACH 0
ORDERLINENUMBER 0
SALES 0
ORDERDATE 0
STATUS 0
QTR_ID 0
MONTH_ID 0
YEAR_ID 0
PRODUCTLINE 0
MSRP 0
PRODUCTCODE 0
CUSTOMERNAME 0
PHONE 0
ADDRESSLINE1 0
ADDRESSLINE2 0
CITY 0
STATE 0
POSTALCODE 0
COUNTRY 0
TERRITORY 0
CONTACTLASTNAME 0
CONTACTFIRSTNAME 0
DEALSIZE 0
dtype:int64

Removed duplicates
data_cleaned = data.drop_duplicates()
print(data_cleaned)

Standardized the text columns
text_columns = ['PRODUCTLINE', 'PRODUCTCODE', 'CUSTOMERNAME', 'PHONE', 'ADDRESSLINE1',
'ADDRESSLINE2', 'CITY', 'STATE', 'COUNTRY', 'TERRITORY', 'CONTACTLASTNAME',
'CONTACTFIRSTNAME', 'DEALSIZE']

for column in text_columns:
data[column] = data[column].str.lower().str.strip()

print(data)

Modified the column names to lowercase
data.columns = data.columns.str.lower().str.replace(' ', '_')
print(data.columns)
Modified the data types
data['orderdate'] = pd.to_datetime(data['orderdate'], errors='coerce')
data['quantityordered'] = data['quantityordered'].astype(int)
data['priceeach'] = data['priceeach'].astype(float)
data['sales'] = data['sales'].astype(float)
data['year_id'] = data['year_id'].astype(int)
data['qtr_id'] = data['qtr_id'].astype(int)
print(data.dtypes)
output:
ordernumber int64
quantityordered int32
priceeach float64
orderlinenumber int64
sales float64
orderdate datetime64[ns]
status object
qtr_id int32
month_id int64
year_id int32
productline object
msrp int64
productcode object
customername object
phone object
addressline1 object
addressline2 object
city object
state object
postalcode object
country object
territory object
contactlastname object
contactfirstname object
dealsize object
dtype: object

`import pandas as pd

data = pd.read_csv(r"C:\Users\rushi\Downloads\sales_data_sample.csv", encoding='ISO-8859-1')
print(data.head())

missing_values = data.isnull()
print(missing_values)

missing_summary = data.isnull().sum()
print(missing_summary)

data['ADDRESSLINE2'] = data['ADDRESSLINE2'].fillna('Unknown')
data['STATE'] = data['STATE'].fillna('Unknown')
data['POSTALCODE'] = data['POSTALCODE'].fillna('Unknown')
data['TERRITORY'] = data['TERRITORY'].fillna('Unknown')

data['SALES'] = data['SALES'].fillna(data['SALES'].mean())
missing_after = data.isnull().sum()
print(missing_after)

data_cleaned = data.drop_duplicates()
print(data_cleaned)

text_columns = ['PRODUCTLINE', 'PRODUCTCODE', 'CUSTOMERNAME', 'PHONE', 'ADDRESSLINE1',
'ADDRESSLINE2', 'CITY', 'STATE', 'COUNTRY', 'TERRITORY', 'CONTACTLASTNAME',
'CONTACTFIRSTNAME', 'DEALSIZE']

for column in text_columns:
data[column] = data[column].str.lower().str.strip()

print(data)

data.columns = data.columns.str.lower().str.replace(' ', '_')

print(data.columns)

data['orderdate'] = pd.to_datetime(data['orderdate'], errors='coerce')
data['quantityordered'] = data['quantityordered'].astype(int)
data['priceeach'] = data['priceeach'].astype(float)
data['sales'] = data['sales'].astype(float)
data['year_id'] = data['year_id'].astype(int)
data['qtr_id'] = data['qtr_id'].astype(int)
print(data.dtypes)# task1
