import pandas as pd
import matplotlib.pyplot as plt
import pandas as pd
import matplotlib.pyplot as plt
df = pd.read_csv("books_data.csv")

df['Price'] = df['Price'].str.replace('Â£', '', regex=False)
df['Price'] = df['Price'].astype(float)

df.head()
plt.figure(figsize=(8,5))
plt.hist(df['Price'], bins=10)
plt.title("Book Price Distribution")
plt.xlabel("Price")
plt.ylabel("Number of Books")
plt.show()
top_books = df.sort_values(by='Price', ascending=False).head(5)

plt.figure(figsize=(10,5))
plt.bar(top_books['Book Title'], top_books['Price'])
plt.xticks(rotation=45, ha='right')
plt.title("Top 5 Most Expensive Books")
plt.xlabel("Book Title")
plt.ylabel("Price")
plt.show()
plt.figure(figsize=(10,5))
plt.plot(df['Price'], marker='o')
plt.title("Book Price Trend")
plt.xlabel("Book Number")
plt.ylabel("Price")
plt.grid(True)
plt.show()
labels = ['Low (<30)', 'Medium (30-50)', 'High (>50)']

low = len(df[df['Price'] < 30])
medium = len(df[(df['Price'] >= 30) & (df['Price'] <= 50)])
high = len(df[df['Price'] > 50])

sizes = [low, medium, high]

plt.figure(figsize=(6,6))
plt.pie(sizes, labels=labels, autopct='%1.1f%%')
plt.title("Book Price Categories")
plt.show() 


