# :key: Web-Scrapping (Python)

Web scraping is the process of extracting data from websites. It involves fetching the content of web pages and parsing it to gather the required information. Python, with its rich ecosystem of libraries, is a popular choice for web scraping due to its simplicity and effectiveness.


# :key: Two key libraries used for this purpose are requests and BeautifulSoup. 

:paperclip: **Requests:** This library allows you to send HTTP requests to fetch web pages. It is user-friendly and handles various aspects of making HTTP requests, such as managing sessions and handling cookies.


:paperclip: **BeautifulSoup:** This library is used to parse HTML and XML documents. It provides Pythonic ways to navigate, search, and modify the parse tree, making it easy to extract the necessary data from the fetched web pages.


# :key: Summary
In a typical web scraping task with Python, the workflow involves:

:paperclip: **Sending a Request:** Using the requests library to send an HTTP request to the target URL and retrieve the HTML content of the page.


:paperclip: **Parsing the HTML:** Using BeautifulSoup to parse the HTML content and create a parse tree that can be navigated and searched.


:paperclip: **Extracting Data:** Utilizing the various methods provided by BeautifulSoup to find and extract the required data from the parse tree.


:paperclip: **Storing the Data:** Saving the extracted data in a desired format, such as a CSV file, database, or JSON.


# :key: Python code


      #  Import the necessary libraries
      from bs4 import BeautifulSoup  # importing BeautifulSoup and BeautifulSoup4
      import requests                # importing requests
      import pandas as pd            # importing pandas


      # Define the URL to be scraped
      url = "https://www.worldometers.info/world-population/population-by-country/"


      # Send a GET request to the URL and get the response
      response = requests.get(url)
      response                 # your request was successful 
                         # the server responded with the data that you were requesting


       # Extracting data in HTML response content with BeautifulSoup
      soup = BeautifulSoup(response.text, 'html')  # getting data with html as text
      soup                  
      
      # to display data in a systematic manner(HTML scipt form)
      print(soup.prettify())

      
      # Extract the table with information
      table=soup.find_all('table')[0]
      table.prettify()

      # Extracting the title of the columns with 'th' tags for table heading
      titles=table.find_all('th')
      titles

      
      # Making a list of columns name using list comprehension
      Population_table_titles = [title.text.strip() for title in titles]
      Population_table_titles


      # Displaying the column name and changing the first column name 
      Population_table_titles[0]="Index"
      Population_table_titles


      # Putting column names into dataframe
      import pandas as pd
      df=pd.DataFrame(columns=Population_table_titles)
      df


      # Extracting a data for table from internet(URL) with 'tr' tags all rows data including the heading
      data=table.find_all('tr')
      data


      # Extracting the cleaned data from for loop with 'td' tags with raw data excluding the heading
      for row in data[1:]:
        row_data=row.find_all('td')
        row_data_1=[td.text.strip() for td in row_data]


      # Add the row data to the DataFrame by checking the length of the dataframe
        length=len(df)
        df.loc[length]=row_data_1


       # final table before extraction
       df


       # storing the data in excel file
       df.to_excel('output.xlsx',index=False)




:paperclip:  Web scraping is a powerful technique for data collection, enabling access to a vast amount of information available on the internet. With Python's requests and BeautifulSoup libraries, you can efficiently scrape and parse web data to suit various needs, from academic research to business intelligence.




:paperclip:  While web scraping offers immense potential, it is crucial to use it responsibly and ethically. 
