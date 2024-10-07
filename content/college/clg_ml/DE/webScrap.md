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
# DBMS

