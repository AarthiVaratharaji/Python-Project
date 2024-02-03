This code is an example of web scraping using BeautifulSoup and Pandas to extract information from the 'https://quotes.toscrape.com/' website and save it to an Excel file.
Here's a breakdown of the code:
1.Import Libraries:
    import requests
    from bs4 import BeautifulSoup
    import pandas as pd

The code begins by importing the necessary libraries: requests for making HTTP requests, BeautifulSoup for parsing HTML, and pandas for creating a DataFrame.
2.Download Web Page:
  response = requests.get('https://quotes.toscrape.com/')
It uses the requests library to download the HTML content of the specified website.
3.Parse and Extract Information:
  soup = BeautifulSoup(response.text, 'lxml')
  quotes = soup.find_all('div', class_='quote')
It uses BeautifulSoup to parse the HTML content and extract quotes. The quotes are located within <div> elements with the class name 'quote'.
4.Create DataFrame:
  df = pd.DataFrame(columns=['Quotes', 'Author'])
for quote in quotes:
    thought = quote.find('span', class_='text').text
    author = quote.find('small', class_='author').text
    length = len(df)
    df.loc[length] = [thought, author]
It creates an empty DataFrame with columns 'Quotes' and 'Author'. It then iterates through each quote, extracts the text and author, and appends them to the DataFrame.
5.Print DataFrame:
  print(df)
It prints the DataFrame to the console.
6.Create CSV/Excel File:
  df.to_excel('C:/Users/aarthi.varatharaji/Documents/Sample Dataset/quotes.xlsx', index=False)
It saves the extracted information to an Excel file named 'quotes.xlsx' at the specified path.

Make sure to replace the file path in the to_excel function with the desired location on your local machine.
Also, ensure that you have the required libraries installed (requests, beautifulsoup4, and pandas).
