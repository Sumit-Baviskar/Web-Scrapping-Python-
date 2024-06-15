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

      df.to_excel('output.xlsx',index=False)   # storing the data in excel file

