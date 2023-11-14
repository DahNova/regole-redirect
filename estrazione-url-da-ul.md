
# Estrazione dei Link e del Testo da un Elemento HTML `<ul>`

Questo script Python utilizza BeautifulSoup per estrarre tutti i link (tag `<a>`) e il testo all'interno dei tag `<span>` da un elemento `<ul>` specifico in un documento HTML.

```python
from bs4 import BeautifulSoup

# Apertura e lettura del contenuto HTML dal file
with open('input.txt', 'r', encoding='utf-8') as file:
    html_content = file.read()

# Analisi del contenuto HTML
soup = BeautifulSoup(html_content, 'lxml')

# Ricerca dell'elemento `<ul>` con l'ID specificato
ul = soup.find('ul', id='INSERIRE ID O CAMBIARE IN CLASSE')

# Controllo se l'elemento `<ul>` è stato trovato
if ul:
    contenuto = []
    # Estrazione di tutti i link e il testo dei tag `<span>` all'interno di questo `<ul>`
    for a in ul.find_all('a'):
        href = a['href']  # Estrazione dell'attributo href
        testo = a.find('span').text if a.find('span') else ''  # Estrazione del testo del tag `<span>`
        contenuto.append((href, testo))

    # Scrittura delle informazioni estratte in un nuovo file
    with open('output.txt', 'w', encoding='utf-8') as file:
        for href, text in contenuto:
            file.write(f"URL: {href}; TESTO: {text}")
```
