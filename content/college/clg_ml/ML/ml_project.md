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

# Convert 'Date' column to datetime objects
df['Date'] = pd.to_datetime(df['Date']) # This line converts the 'Date' column to datetime

#Extract day of the week
df['Day_of_Week'] = df['Date'].dt.dayofweek

# Extract month
df['Month'] = df['Date'].dt.month

print(df)

# prompt: Remove unnecessary columns such as Warehouse_ID if not needed for the analysis

# Remove the 'Warehouse_ID' column
df = df.drop('Warehouse_ID', axis=1)

print(df)
# prompt: Use NumPy and Pandas to calculate key metrics such as average inventory holding cost and transportation cost.

# Calculate average inventory holding cost (assuming a holding cost per unit per day)
holding_cost_per_unit_per_day = 0.1  # Example cost
df['Inventory_Holding_Cost'] = df['Inventory_Level'] * holding_cost_per_unit_per_day

# Calculate total inventory holding cost
total_inventory_holding_cost = df['Inventory_Holding_Cost'].sum()

# Calculate average inventory holding cost
average_inventory_holding_cost = total_inventory_holding_cost / len(df)

print(f"Average Inventory Holding Cost: {average_inventory_holding_cost}")


# Calculate average transportation cost
average_transportation_cost = df['Transportation_Cost'].mean()

print(f"Average Transportation Cost: {average_transportation_cost}")
  
  

from scipy.optimize import linprog

  

# Define the objective function coefficients (minimize total cost)

c = np.array([0.1, 1]) # Cost per unit of inventory and transportation cost

  

# Define the constraint matrix (A) and the right-hand side vector (b)

A = np.array([

[-1, 0], # Inventory level constraint (lower bound)

[1, 0], # Inventory level constraint (upper bound)

[0, -1], # Transportation cost constraint (lower bound)

[0, 1] # Transportation cost constraint (upper bound)

])

  

b = np.array([

100, # Minimum inventory level

500, # Maximum inventory level

10, # Minimum transportation cost

100 # Maximum transportation cost

])

  

# Define the bounds for the decision variables

bounds = [(0, None), (0, None)] # Inventory level and transportation cost

  

# Solve the linear programming problem

result = linprog(c, A_ub=A, b_ub=b, bounds=bounds)

  

# Print the results

print("Optimal Solution:")

print("Inventory Level:", result.x[0])

print("Transportation Cost:", result.x[1])

print("Total Cost:", result.fun)

  

import matplotlib.pyplot as plt

  

# Extract the optimal values

optimal_inventory_level = result.x[0]

optimal_transportation_cost = result.x[1]

total_cost = result.fun

  

# Create a bar chart for the optimal values

plt.figure(figsize=(8, 6))

plt.bar(['Inventory Level', 'Transportation Cost'], [optimal_inventory_level, optimal_transportation_cost], color=['blue', 'green'])

plt.title('Optimal Cost Optimization Results')

plt.ylabel('Optimal Value')

plt.show()

  

# Create a line chart for the total cost

plt.figure(figsize=(8, 6))

plt.plot(['Optimal Solution'], [total_cost], marker='o', linestyle='-', color='red')

plt.title('Total Cost')

plt.ylabel('Cost')

plt.show()
```
