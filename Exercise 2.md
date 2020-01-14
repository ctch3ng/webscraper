# Exercise 2 - Melbourne's AQI and PM number

## Exercise 2.1: Get today's AQI and PM number from https://www.airvisual.com/australia/victoria/melbourne

```
# import libraries
import urllib
from bs4 import BeautifulSoup

#Today's Forecast

quote_page_2 = 'https://www.airvisual.com/australia/victoria/melbourne'
hdr = {'User-Agent': 'Mozilla/5.0'}
req_2 = urllib.request.Request(quote_page_2, headers=hdr)
page_2 = urllib.request.urlopen(req_2)

soup_2 = BeautifulSoup(page_2, 'lxml')

aqi = soup_2.find('span', attrs={'class': 'aqi'}).next

if soup_2.find('span', attrs={'class': 'pm-number'}):
    pm_number = soup_2.find('span', attrs={'class': 'pm-number'}).next 
    print('Air Quality Index: ',aqi, ' - ',pm_number,'\n')
else:
    print('Air Quality Index: ',aqi,'\n')
```

## Exercise 1.2: Get Tomorrow's AQI and PM number from https://www.airvisual.com/australia/victoria/melbourne

```

```
