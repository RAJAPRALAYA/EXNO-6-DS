# Aim:
  To Perform Data Visualization using seaborn python library for the given datas.

# EXPLANATION:
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# Algorithm:
STEP 1:Include the necessary Library.

STEP 2:Read the given Data.

STEP 3:Apply data visualization techniques to identify the patterns of the data.

STEP 4:Apply the various data visualization tools wherever necessary.

STEP 5:Include Necessary parameters in each functions.

# Coding and Output:

 ```
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

```
```
sns.set_theme(style="whitegrid")
df = sns.load_dataset("penguins")  
df.head()
```
<img width="815" height="227" alt="image" src="https://github.com/user-attachments/assets/6dd12d8b-9be5-4823-8a62-319b944e8338" />

```
print("Shape:", df.shape)
print("\nColumn Types:\n", df.dtypes)
print("\nMissing Values:\n", df.isna().sum())

```
<img width="457" height="465" alt="image" src="https://github.com/user-attachments/assets/3d7ebe92-225b-4328-8c42-034893ff0e60" />

```
numeric = df.select_dtypes(include=[np.number])

plt.figure(figsize=(10, 7))
sns.heatmap(numeric.corr(), annot=True, cmap="coolwarm", linewidths=0.5)
plt.title("Correlation Heatmap")
plt.show()

```
<img width="1065" height="777" alt="image" src="https://github.com/user-attachments/assets/44ef002d-2454-43cb-8100-89179a12d992" />

```
sns.pairplot(df, diag_kind="kde")
plt.show()

```

```
num_cols = numeric.columns.tolist()

if len(num_cols) >= 2:
    sns.jointplot(data=df, x=num_cols[0], y=num_cols[1], kind="kde", fill=True)
    plt.show()
else:
    print("Not enough numeric columns for jointplot")

```
<img width="905" height="837" alt="image" src="https://github.com/user-attachments/assets/cbd108d8-0f84-4584-8a9a-9f17ccaba07e" />

```
cat_cols = df.select_dtypes(include=['object','category']).columns.tolist()

if len(cat_cols) > 0 and len(num_cols) > 0:
    plt.figure(figsize=(10,5))
    sns.violinplot(x=cat_cols[0], y=num_cols[0], data=df, inner=None)
    sns.swarmplot(x=cat_cols[0], y=num_cols[0], data=df, color="black", alpha=0.5)
    plt.title(f"Violin + Swarm Plot of {num_cols[0]} by {cat_cols[0]}")
    plt.show()

```
<img width="1182" height="625" alt="image" src="https://github.com/user-attachments/assets/a87a606b-c761-4982-abb5-e815a16cbe74" />

```
if len(cat_cols) > 0 and len(num_cols) > 0:
    g = sns.FacetGrid(df, col=cat_cols[0], col_wrap=3, height=3)
    g.map(sns.kdeplot, num_cols[0], fill=True)
    plt.show()

```

<img width="1232" height="375" alt="image" src="https://github.com/user-attachments/assets/8e8f9271-ef83-48d0-aad1-4fd26208829a" />

```
plt.figure(figsize=(10,5))
sns.boxplot(x=cat_cols[0], y=num_cols[0], data=df)
sns.stripplot(x=cat_cols[0], y=num_cols[0], data=df, color="red", alpha=0.4)
plt.title(f"Box + Strip Plot: {num_cols[0]} by {cat_cols[0]}")
plt.show()

```
<img width="1208" height="609" alt="image" src="https://github.com/user-attachments/assets/a93358ac-97c0-4fc8-975d-481ffbec2d38" />

```
if len(num_cols) >= 2:
    sns.lmplot(data=df, x=num_cols[0], y=num_cols[1], height=5, aspect=1.3)
    plt.title("Regression with Confidence Interval")
    plt.show()

```
<img width="895" height="652" alt="image" src="https://github.com/user-attachments/assets/e849b821-6510-4ff5-a688-a8ab50028491" />

```
sns.countplot(data=df, x=cat_cols[0])
plt.title("Category Counts")
plt.xticks(rotation=45)
plt.show()

```


# Result:
 
