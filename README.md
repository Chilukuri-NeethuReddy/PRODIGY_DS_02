# PRODIGY_DS_02

## ProdigyInfoTech_TASK2

## TASK 2: Data Cleaning and Exploratory Data Analysis (EDA) on Titanic Dataset

This project demonstrates how to perform data cleaning and exploratory data analysis (EDA) on the Titanic dataset from Kaggle.


## Dataset:
The dataset used in this project is the Titanic dataset, available on Kaggle.
https://www.kaggle.com/competitions/titanic


## Visualizations:

1.**Survival Rate by Gender**: Bar chart showing the survival rate of passengers by gender.

2.**Survival Rate by Passenger Class**: Bar chart showing the survival rate of passengers by passenger class.

3.**Age Distribution of Passengers**: Histogram showing the distribution of ages among passengers.


## How to Run:

1.Clone the repository.

2.Ensure you have the necessary libraries installed (pandas, matplotlib, seaborn).

3.Place the dataset (Titanic-Dataset.csv) in the same directory as the script.

4.Run the script (titanic_data_analysis.py) to generate the visualizations.


#Code
```python

import seaborn as sns

from IPython.display import display

# Load the Titanic dataset

titanic_data = pd.read_csv('Titanic-Dataset.csv')

# Display the first few rows of the dataset

display(titanic_data.head())

# Check the summary statistics of numerical columns

print(titanic_data.describe())

#Check for missing values

print(titanic_data.isnull().sum())
```

![Screenshot 2024-07-07 101611](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_02/assets/174725064/855ab970-ecdc-4c4f-a940-e967f13e756e)

![Screenshot 2024-07-07 101639](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_02/assets/174725064/f12c5a9d-5a9c-46dd-8556-1e3901f8a960)


```python

# Fill missing ages with the median age

titanic_data['Age'] = titanic_data['Age'].fillna(titanic_data['Age'].median())

# Convert categorical variables to appropriate formats

titanic_data['Sex'] = titanic_data['Sex'].astype('category').cat.codes
titanic_data['Embarked'] = titanic_data['Embarked'].astype('category').cat.codes

# Check the total number of survivors by gender

survivors_by_gender = titanic_data.groupby('Sex')['Survived'].mean()

# Print the percentage of women who survived

print(f"% of women who survived: {survivors_by_gender[0]*100}")

# Print the percentage of men who survived

print(f"% of men who survived: {survivors_by_gender[1]*100}")
```


![Screenshot 2024-07-07 102028](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_02/assets/174725064/b658dd28-b1c8-41bb-a40f-8fa1937dced4)

```python
#visualizing survival rates by passenger class

//Define custom colors for each class

class_colors = {1: 'red', 2: 'violet', 3: 'orange'}

plt.figure(figsize=(10, 6))

sns.barplot(x='Pclass', y='Survived', data=titanic_data, ci=None, palette=class_colors)

plt.xlabel('Passenger Class')

plt.ylabel('Survival Rate')

plt.title('Survival Rate by Passenger Class')

plt.show()
```

### Survival rate by passenger class

![Screenshot 2024-07-07 102214](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_02/assets/174725064/d07b1add-1dfa-4196-9a02-bfce19ced10c)


```python

#Visualizing age distribution

plt.hist(titanic_data['Age'], bins=20, edgecolor='black')

plt.xlabel('Age')

plt.ylabel('Frequency')

plt.title('Age Distribution of Passengers')

plt.show()
```

### Survival rate by age

![Screenshot 2024-07-07 102340](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_02/assets/174725064/8a2a62b8-9a4d-4940-9d09-7550df3769d6)


```python

#visualizing survival rates by gender

gender_colors = ['red', 'purple']

plt.figure(figsize=(10, 6))

sns.barplot(x='Sex', y='Survived', data=titanic_data, ci=None, palette=gender_colors)

plt.xlabel('Gender')

plt.ylabel('Survival Rate')

plt.title('Survival Rate by Gender')

plt.show()
```

### Survival rate by gender

![Screenshot 2024-07-07 102456](https://github.com/Chilukuri-NeethuReddy/PRODIGY_DS_02/assets/174725064/3c82d5ea-cd1c-44f1-a48a-364003980dad)






