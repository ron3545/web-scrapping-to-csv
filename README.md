# Overview
This Python script performs web scraping on the desired website to extract information about desktop graphics cards. The script utilizes the BeautifulSoup library to parse HTML content and extract relevant data, which is then saved to a CSV file named "product.csv."

### Note
This doesn't include proxies, which helps in avoiding web-blocking.

# Dependencies
- **requests**:  Used for opening URLs.
- **BeautifulSoup (bs4)**: A Python library for pulling data out of HTML and XML files.
- **pandas**: for formating data to csv
- **numpy**

# Data Fields
- **Brand**: Extracted from the "title" attribute of the img tag within the container.
- **Shipping**: Extracted from the "price-ship" class within the container.
- **Price**:Extracted from the "price-current" class within the container, with some text manipulation to remove unwanted characters.

# Output
The script produces a CSV file ("product.csv") containing information about desktop graphics cards, with columns for brand, shipping, and price. The output CSV can be further analyzed or imported into a data analysis tool for further processing.
