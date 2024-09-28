# :chart_with_upwards_trend: Web-Scrapping (Python) :chart_with_upwards_trend:

# :key: **Introduction :**

**Web scraping** has become a powerful tool in the field of data analysis, enabling users to gather large volumes of data directly from the web. This process involves fetching the HTML content of a webpage, extracting relevant data from it, and transforming that data into a structured format that can be easily analyzed and used for various purposes. Whether you're looking for real-time data on product prices, weather updates, stock market information, or even population statistics, web scraping provides an efficient way to automate the data collection process.

In this project, we focus on extracting population data from the Worldometer website, which provides up-to-date statistics on world populations by country. By leveraging Python and key libraries such as **BeautifulSoup, Requests, and pandas,** we aim to scrape population data, clean it, and store it in a structured format for further analysis.

Specifically, **the project will :**


:paperclip: Extract data on the population of countries from an online table.

   
:paperclip: Organize the data into a structured format using a pandas DataFrame.

  
:paperclip: Store the extracted data in an Excel file for future use.


The importance of web scraping is growing, as large amounts of data are available online but not always presented in a downloadable format. This project serves as a demonstration of how you can convert raw HTML data into structured datasets for analysis, thus showcasing the value of web scraping in data collection, especially when dealing with regularly updated or dynamic web content.

# :key: **Project Scope :**

The project will focus on extracting population data for all countries from Worldometer. We will scrape the population table, clean the data, and store it in a DataFrame. The final output will be an Excel file containing the organized data.

# :key: **Objective :**

The primary objective is to demonstrate a systematic way to gather data from a website using web scraping techniques. The project will:



:paperclip: Extract population data for countries.


:paperclip: Store the data in a structured format using pandas.


:paperclip: Save the data in an Excel file for further use.

# :key: **Tools & Technologies :**

:paperclip: **Python :** The main programming language used.
Libraries:

:paperclip: **BeautifulSoup :** To parse HTML content and extract information.This library is used to parse HTML and XML documents. It provides Pythonic ways to navigate, search, and modify the parse tree, making it easy to extract the necessary data from the fetched web pages.


:paperclip: **requests :** To send HTTP requests and fetch webpage data.This library allows you to send HTTP requests to fetch web pages. It is user-friendly and handles various aspects of making HTTP requests, such as managing sessions and handling cookies.


:paperclip: **Pandas :** To store, manipulate, and organize the extracted data.


:paperclip: **Excel :** For final data storage and export.


# :key: **Summary :**

In a typical web scraping task with Python, the workflow involves:


:paperclip: **Sending a Request :** Using the requests library to send an HTTP request to the target URL and retrieve the HTML content of the page.


:paperclip: **Parsing the HTML :** Using BeautifulSoup to parse the HTML content and create a parse tree that can be navigated and searched.


:paperclip: **Extracting Data :** Utilizing the various methods provided by BeautifulSoup to find and extract the required data from the parse tree.



:paperclip: **Storing the Data :** Saving the extracted data in a desired format, such as a CSV file, database, or JSON.



# :key: **Code Expalined Step By Step :**

**1. Import the Necessary Libraries :** We begin by importing BeautifulSoup, requests, and pandas. These libraries are essential for scraping, parsing, and organizing the data.

      #  Import the necessary libraries
      from bs4 import BeautifulSoup  # importing BeautifulSoup and BeautifulSoup4
      import requests                # importing requests
      import pandas as pd            # importing pandas


**2. Define the URL and Make a GET Request :** We specify the URL of the Worldometer population data page and use requests.get() to fetch the HTML content of the page.


      # Define the URL to be scraped
      url = "https://www.worldometers.info/world-population/population-by-country/"



      # Send a GET request to the URL and get the response
      response = requests.get(url)
      response                 # your request was successful 
                         # the server responded with the data that you were requesting

**3. Parse the HTML Content :** The BeautifulSoup library parses the HTML content from the response, allowing us to navigate through the webpage's structure and extract the data we need.


       # Extracting data in HTML response content with BeautifulSoup
      soup = BeautifulSoup(response.text, 'html')  # getting data with html as text
      soup                  
      
      # to display data in a systematic manner(HTML scipt form)
      print(soup.prettify())

**4. Extract the Data Table :** We locate the table with population data using the find_all() method and extract its content.
      
      # Extract the table with information
      table=soup.find_all('table')[0]
      table.prettify()

**5. Extract Column Titles :** Using find_all('th'), we get all the column titles (headings) in the table. List comprehension is then used to clean and structure these headings.

      # Extracting the title of the columns with 'th' tags for table heading
      titles=table.find_all('th')
      titles

      
      # Making a list of columns name using list comprehension
      Population_table_titles = [title.text.strip() for title in titles]
      Population_table_titles


      # Displaying the column name and changing the first column name 
      Population_table_titles[0]="Index"
      Population_table_titles

**6. Create a Pandas DataFrame :** A DataFrame is created with the column titles defined earlier to organize the extracted data.

      # Putting column names into dataframe
      import pandas as pd
      df=pd.DataFrame(columns=Population_table_titles)
      df

**7. Extract Data from the Rows :** We loop through each row of the table, extracting data using the td tag for table cells. The row data is cleaned, and each row is added to the DataFrame.

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

**8. Export the Data to Excel :** After collecting and organizing all the data, we export it to an Excel file for future use.


       # storing the data in excel file
       df.to_excel('output.xlsx',index=False)




Web scraping is a powerful technique for data collection, enabling access to a vast amount of information available on the internet. With Python's requests and BeautifulSoup libraries, you can efficiently scrape and parse web data to suit various needs, from academic research to business intelligence.


# :key: **Conclusion :**
This web scraping project successfully highlights the power and flexibility of Python for automating data extraction processes from websites. Through the use of libraries like BeautifulSoup, requests, and pandas, we were able to scrape population data from the Worldometer website, structure it, and export it to an Excel file for future use. 

The **key benefits** of this approach include:

- :paperclip: **Automation :** We eliminated the need for manual data collection, allowing us to efficiently gather up-to-date information from a public website.

  
- :paperclip: **Data Structuring :** By parsing the raw HTML and using pandas, we were able to clean and organize the data, making it easy to analyze and understand.

  
- :paperclip: **Scalability :** This project can be easily adapted to scrape other websites or even more complex dynamic web pages using tools.

  
In real-world applications, web scraping can be applied to countless fields, from market research and price monitoring to social media analytics and academic research. It provides businesses and researchers with a powerful means to gather actionable insights from publicly available data. However, it is also important to keep in mind the legal and ethical considerations, such as respecting a site's robots.txt file and ensuring that the data is being used appropriately.

Ultimately, this project demonstrates the simplicity and effectiveness of web scraping in collecting and organizing data, making it an essential skill for anyone working in data science, analytics, or automation. By converting the unstructured data from the web into a structured format, we gain the ability to analyze trends, make data-driven decisions, and derive meaningful insights from large-scale datasets.



