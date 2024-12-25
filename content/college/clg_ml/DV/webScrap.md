# API and requests

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
i = 1
for i in range(1,11):
  url = f'https://quotes.toscrape.com/page/{i}'
  response = requests.get(url)
  #print(response.raise_for_status())
  soup = BeautifulSoup(response.text, 'html.parser')
  quotes = soup.find_all('div',class_ = 'quote')
  data = []
  for quote in quotes:
    text = quote.find('span',class_ = 'text').get_text()
    author = quote.find('small',class_ = 'author').get_text()
    tags = [tag.get_text() for tag in quote.find_all('a',class_ = 'tag')]
    df = pd.DataFrame(data,columns = ['text','author','tags'])
    df.to_csv('quotes.csv')
    data.append([text,author,tags])
  print(df)
```

# webscrapping
```python
import requests
from bs4 import BeautifulSoup
import pandas as pd

# Step 1: Initialize an empty list to store the data
data = []

# Step 2: Loop through the first 20 pages
for page in range(1, 21):  # Loop from page 1 to 20
    url = f'http://quotes.toscrape.com/page/{page}/'
    response = requests.get(url)
    response.raise_for_status()  # Check that the request was successful
    # Step 3: Parse the HTML content of the page
    soup = BeautifulSoup(response.text, 'html.parser')
    # Step 4: Find all quote elements on the current page
    quotes = soup.find_all('div', class_='quote')
    # Step 5: Extract data and append it to the list
    for quote in quotes:
        text = quote.find('span', class_='text').get_text()
        author = quote.find('small', class_='author').get_text()
        tags = [tag.get_text() for tag in quote.find_all('a', class_='tag')]
        data.append([text, author, ', '.join(tags)])

# Step 6: Write the data to a CSV file using pandas
df = pd.DataFrame(data, columns=['Quote', 'Author', 'Tags'])
df.to_csv('quotes_20.csv', index=False, encoding='utf-8')

print("Quotes from 20 pages have been successfully saved to 'quotes.csv'")
```

