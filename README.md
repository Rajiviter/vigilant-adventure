import pandas as pd
import numpy as np
import random

# Set seed for reproducibility
random.seed(42)
np.random.seed(42)

# Define the list of categories
categories = ['Food', 'Travel', 'Fashion', 'Fitness', 'Music', 'Culture', 'Family', 'Health']

# Set the number of periods
n = 500

# Generate the data dictionary
data = {
    'Date': pd.date_range('2021-01-01', periods=n),
    'Category': [random.choice(categories) for _ in range(n)],
    'Likes': np.random.randint(0, 10001, size=n)
}

# Convert to DataFrame for better visualization (optional)
df = pd.DataFrame(data)

# Display the first few rows of the DataFrame
print(df.head())
import pandas as pd

# Assuming 'df' is your DataFrame from the previous step
# First, remove any null data
df = df.dropna()

# Next, remove duplicate data
df = df.drop_duplicates()

# Convert the 'Date' field to a datetime format
df['Date'] = pd.to_datetime(df['Date'])

# Convert the 'Likes' field to integers
df['Likes'] = df['Likes'].astype(int)

# Display the first few rows of the cleaned DataFrame
print(df.head())
import seaborn as sns
import matplotlib.pyplot as plt

# Create a histogram of 'Likes'
sns.histplot(df['Likes'], bins=30, kde=False)

# Show the histogram plot
plt.show()
# Create a boxplot with 'Category' on the x-axis and 'Likes' on the y-axis
sns.boxplot(x='Category', y='Likes', data=df)

# Show the boxplot
plt.show()
# Calculate and print the mean of the 'Likes' column
mean_likes = df['Likes'].mean()
print(f"Mean of Likes: {mean_likes}")
# Calculate and print the mean of 'Likes' grouped by 'Category'
mean_likes_by_category = df.groupby('Category')['Likes'].mean()
print("Mean of Likes by Category:")
print(mean_likes_by_category)

