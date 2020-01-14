# Exercise 1 - Melbourne's Weather

## Exercise 1.1: Get today's weather forecast from http://www.bom.gov.au/

```
# import libraries
import urllib
from bs4 import BeautifulSoup

#Today's Forecast

quote_page = 'http://www.bom.gov.au/vic/forecasts/melbourne.shtml'
hdr = {'User-Agent': 'Mozilla/5.0'}
req = urllib.request.Request(quote_page, headers=hdr)
page = urllib.request.urlopen(req)

soup = BeautifulSoup(page, 'lxml')

print(soup.find('p', attrs={'class':'date'}).string,'\n')
print("Today's Forecast",'\n')

name_box = soup.find('div', attrs={'class': 'day main'}).find('div', attrs={'class': 'forecast'})

if name_box.find('em', attrs={'class': 'min'}):
    temp_min=name_box.find('em', attrs={'class': 'min'}).string + u'\N{DEGREE SIGN}''C'
else:
    temp_min='N/A'
    
if name_box.find('em', attrs={'class': 'max'}):
    temp_max=name_box.find('em', attrs={'class': 'max'}).string + u'\N{DEGREE SIGN}''C'
else:
    temp_max='N/A'    

print(name_box.h3.string, ' - ', name_box.find('dd', attrs={'class': 'summary'}).string)
print('Temperature: ', temp_min,' - ', temp_max)
print('Chance of any rain:', name_box.find('em', attrs={'class': 'pop'}).img.previous,'\n')
print(name_box.p.string,'\n')

```

## Exercise 1.2: Get Tomorrow's weather forecast from http://www.bom.gov.au/

```
# import libraries
import urllib
from bs4 import BeautifulSoup

# Next Day's Forecast

print("Tomorrow's Forecast",'\n')

name_box = soup.find_all(lambda tag: tag.name == 'div' and tag.get('class') == ['day'])[0]

name_box = name_box.find('div', attrs={'class': 'forecast'})

if name_box.find('em', attrs={'class': 'min'}):
    temp_min=name_box.find('em', attrs={'class': 'min'}).string + u'\N{DEGREE SIGN}''C'
else:
    temp_min='N/A'
    
if name_box.find('em', attrs={'class': 'max'}):
    temp_max=name_box.find('em', attrs={'class': 'max'}).string + u'\N{DEGREE SIGN}''C'
else:
    temp_max='N/A'    

print(name_box.h3.string, ' - ', name_box.find('dd', attrs={'class': 'summary'}).string)
print('Temperature: ', temp_min,' - ', temp_max)
print('Chance of any rain:', name_box.find('em', attrs={'class': 'pop'}).img.previous,'\n')
print(name_box.p.string,'\n')
```
