---
id: "nmr50lpkttu0u"
parent: null
position_x: 
position_y: 
color: null
---
# Fixing Structural Errors & Consistency

- **Inconsistent Entry:** `df['city'] = df['city'].replace({'NY': 'New York', 'ny': 'New York'})`     
	df['motor']=df['motor'].str.replace("L","") #replace
- **Data Types:** `df['price'] = pd.to_numeric(df['price'], errors='coerce')` #to_numeric
- **Parsing Dates:** `df['date'] = pd.to_datetime(df['date'], format='%Y-%m-%d')` #to_datetime
- **Encoding:** `df = pd.read_csv('file.csv', encoding='utf-8')` #encoding_utf-8
