## Scraping info out of URLs with Regex
![Regular Expression Cheat Sheet](https://media.datacamp.com/legacy/image/upload/v1665049611/Marketing/Blog/Regular_Expressions_Cheat_Sheet.pdf)

```ruby
import requests
import re

url = "http://py4e-data.dr-chuck.net/regex_sum_1563986.txt"
response = requests.get(url)

# Check if the request was successful 
if response.status_code == 200:
    data = response.text

    # Find all digits
    digits = re.findall(r'\d+', data)
    dsum = sum(int(digit) for digit in digits)
    print("Sum of all digits in the text:", dsum)

else:
    print(f"Failed to retrieve data from URL. Status code: {response.status_code}")
```
