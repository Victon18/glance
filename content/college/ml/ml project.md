```python
import pandas as pd
import numpy as np
url = 'https://raw.githubusercontent.com/Victon18/classml/main/random_data.csv'
df = pd.read_csv(url)
print(df)
#print(df.isna())
df['Inventory_Level']=df['Inventory_Level'].fillna(df['Inventory_Level'].mean())
Q1_quant_Rec = df['Quantity_Received'].quantile(0.25)
Q3_quant_Rec = df['Quantity_Received'].quantile(0.75)
IQR_quant_Rec = Q3_quant_Rec - Q1_quant_Rec
lower_bound_quant_Rec = Q1_quant_Rec - 1.5 * IQR_quant_Rec
upper_bound_quant_Rec = Q3_quant_Rec + 1.5 * IQR_quant_Rec
df['Quantity_Received'] = np.where(
df['Quantity_Received'] < lower_bound_quant_Rec,
df['Quantity_Received'].median(),
np.where(
df['Quantity_Received'] > upper_bound_quant_Rec,
df['Quantity_Received'].median(),
df['Quantity_Received']
)
)
Q1_quant_Ship = df['Quantity_Shipped'].quantile(0.25)
Q3_quant_Ship = df['Quantity_Shipped'].quantile(0.75)
IQR_quant_Ship = Q3_quant_Ship - Q1_quant_Ship
lower_bound_quant_Ship = Q1_quant_Ship - 1.5 * IQR_quant_Ship
upper_bound_quant_Ship = Q3_quant_Ship + 1.5 * IQR_quant_Ship
df['Quantity_Shipped'] = np.where(
df['Quantity_Shipped'] < lower_bound_quant_Ship,
df['Quantity_Shipped'].median(),
np.where(
df['Quantity_Shipped'] > upper_bound_quant_Ship,
df['Quantity_Shipped'].median(),
df['Quantity_Shipped']
)
)
print (df)
```