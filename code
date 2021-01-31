import requests 
from bs4 import BeautifulSoup 
print('Welchen Schuh brauchst du?')
lol = input()
print('for men or woman')
gender = input()
if gender == 'men':
    m = 'https://eu.puma.com/de/de/herren/schuhe'
elif gender == 'woman':
    m = 'https://eu.puma.com/de/de/damen/schuhe'


baseurl = 'https://eu.puma.com/de/de/home'
headers = ({'User-Agent':
                'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/44.0.2403.157 Safari/537.36',
                'Accept-Language': 'en-US, en;q=0.5'})




productlinks = []
for x in range (0, 2):
    r = requests.get(m)
    soup = BeautifulSoup(r.content, 'html.parser')

    products = soup.find_all('div', class_='col-6 col-sm-4 col-md-3')
    for item in products:
        link = item.find('a', href=True)
        productlinks.append(baseurl + link['href'])


schuhlist = []
for link in productlinks:
    
    r = requests.get(link, headers=headers)
    
    soup = BeautifulSoup(r.content, 'html.parser')
    name = soup.find("h1", class_="product-name").text.strip()
    preis = soup.find('span', class_='value').text.strip()
    schuh = {

        'name': name,
        'preis': preis

    }
    
    schuhlist.append(schuh)
    if name == lol:
        print('hab ihn gefunden')
        print(name)
        print(preis)
        
