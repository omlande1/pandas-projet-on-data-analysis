# pandas-projet-on-data-analysis
!pip install matplotlib seaborn plotly

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px

# Load the Titanic dataset
url = "https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"
df = pd.read_csv(url)

# Display the first few rows of the dataset
df.head()

# Matplotlib Bar Chart
plt.figure(figsize=(10, 6))
survival_counts = df.groupby('Sex')['Survived'].sum()
survival_counts.plot(kind='bar', color=['blue', 'pink'])
plt.title('Survival Counts by Sex')
plt.xlabel('Sex')
plt.ylabel('Survival Count')
plt.show()

# Seaborn Count Plot
plt.figure(figsize=(10, 6))
sns.countplot(data=df, x='Pclass', hue='Survived')
plt.title('Survival Counts by Passenger Class')
plt.xlabel('Passenger Class')
plt.ylabel('Count')
plt.show()

# Plotly Scatter Plot
fig = px.scatter(df, x='Age', y='Fare', color='Survived', 
                 title='Age vs Fare (Colored by Survival)', 
                 labels={'Age':'Age', 'Fare':'Fare', 'Survived':'Survived'},
                 color_continuous_scale=['red', 'green'])
fig.show()
