# Overview
This Python script performs web scraping on the desired website to extract information about desktop graphics cards. The script utilizes the BeautifulSoup library to parse HTML content and extract relevant data, which is then saved to a CSV file named "product.csv."

# Dependencies
- **urllib.request**:  Used for opening URLs.
- **BeautifulSoup (bs4)**: A Python library for pulling data out of HTML and XML files.

# Script Execution
- **URL Retrieval** The script begins by specifying the target URL (my_url), which points to the Newegg page containing desktop graphics card information. It then opens the URL using urlopen and reads the HTML content.
  ```
  my_url = 'https://www.newegg.com/Desktop-Graphics-Cards/SubCategory/ID-48?Tid=7709'
  uclient = uReq(my_url)
  page_html = uclient.read()
  uclient.close()
  ```
- **HTML Parsing** The HTML content is parsed using BeautifulSoup, and the parsed content is stored in the page_soup variable.
  ```
  page_soup = soup(page_html, "html.parser")
  ```
- **Extracting Container Elements** The script identifies and extracts container elements (div tags with the class "item-container") that hold information about individual graphics cards.
- **CSV File Initialization** The script initializes a CSV file named "product.csv" and writes the header row.
  ```
  file_name = "product.csv"
  f = open(file_name, "w")
  headers = "brand, shipping, price\n"
  f.write(headers)
  ```
- **Iterating Through Containers** The script iterates through each container, extracts information such as brand, shipping details, and price, and prints the details.
-   ```
    for container in containers:
      brand = container.a.img["title"]
      shipping_container = container.findAll("li", {"class": "price-ship"})
      shipping = shipping_container[0].text.strip()
      price_list = container.findAll("li", {"class": "price-current"})
      price = price_list[0].text.strip().replace("|", "").replace('\r', '').replace('\n', '')
  
      print("brand: " + brand)
      print("shipping: " + shipping)
      print("price: " + price)
      print("_____________________________________________________________________________________________________________")
  
      f.write(brand.replace(",", "|") + "," + shipping + "," + price.replace(",", ".") + "\n")
    ```

# Data Fields
- **Brand**: Extracted from the "title" attribute of the img tag within the container.
- **Shipping**: Extracted from the "price-ship" class within the container.
- **Price**:Extracted from the "price-current" class within the container, with some text manipulation to remove unwanted characters.

# Output
The script produces a CSV file ("product.csv") containing information about desktop graphics cards, with columns for brand, shipping, and price. The output CSV can be further analyzed or imported into a data analysis tool for further processing.
