## Table of Contents

1. [Redirect di tutti gli URL che iniziano con una parola ad un unico URL](#1)
2. [Redirect di un URL con parametro a URL senza parametro](#2)
3. [Redirect di un URL con parametri a URL senza parametro](#3)
4. [Redirect/trasformazione di un URL con lettere e numeri ad una pagina che ha come chiave di ricerca l'URL vecchio](#4)
5. [Redirect di un sotto dominio ad un nuovo dominio](#5)
6. [Redirect di più pagine di categoria/prodotto ad una pagina](#6)
7. [Redirect di tutti gli URL in una cartella ad un'altra cartella che ha gli stessi URL](#7)
8. [Redirect di tutte le pagine di un dominio alle stesse pagine in un nuovo dominio](#8)
9. [Redirect di tutte le pagine in una cartella allo stesso URL senza la cartella](#9)
10. [Redirect di tutte le pagine in un percorso alle stesse pagine con parte del percorso uguale](#10)
11. [Redirect della home page standard ad una pagina specifica](#11)
12. [Reindirizzate una pagina ad esclusione di un indirizzo IP.](#12)
13. [Redirect ad esclusione di alcune cartelle](#13)
14. [Assegnare un robots differente ad un determinato URL o directory](#14)
15. [Redirect homepage sito statico a wordpress (sottocartella in questo caso /it/)](#15)

---

### 1. Redirect di tutti gli URL che iniziano con una parola ad un unico URL <a name="1"></a>

RewriteRule ^vecchia-(.*) /nuova-destinazione/? [L,R=301]  


---

### 2. Redirect di un URL con parametro a URL senza parametro <a name="2"></a>

RewriteCond %{QUERY_STRING}  ^id_parametro=3$ [NC]  
RewriteRule ^vecchia-destinazione-senza-parametro$ https://nuova-destinazione/? [R=301,L]  


---

### 3. Redirect di un URL con parametri a URL senza parametro <a name="3"></a>

RewriteCond %{QUERY_STRING}  ^id_parametro=3&altroparamentro=2$ [NC] | RewriteCond %{QUERY_STRING}  ^id_parametro=3(.*)$ [NC]
RewriteRule ^vecchia-destinazione-senza-paramentro$ https://nuova-destinazione/? [R=301,L]  


---

### 4. Redirect/trasformazione di un URL con lettere e numeri ad una pagina che ha come chiave di ricerca l'URL vecchio <a name="4"></a>

RewriteRule ^wp/test/vecchio-art-([0-9-A-z]+)/?$ https://www.dominio.it/?s=$1 [R=301,L]  


---

### 5. Redirect di un sotto dominio ad un nuovo dominio <a name="5"></a>

RewriteCond %{HTTP_HOST} ^sotto.dominio.it$ [NC] | RewriteCond %{HTTP_HOST} ^www.vecchio-dominio.it$ [NC]  
RewriteRule ^vecchia-destinazione$ https://nuova-destinazione/ [R=301,L]  


---

### 6. Redirect di più pagine di categoria/prodotto ad una pagina <a name="6"></a>

RewriteRule ^test/(mirco|categoria_1|pippo)\\.asp$ https://www.dominio.com/nuova-pagina/ [R=301,L]  


---

### 7. Redirect di tutti gli URL in una cartella ad un'altra cartella che ha gli stessi URL <a name="7"></a>

RewriteRule ^subdirectory/(.*)$ /anotherdirectory/$1 [R=301,NC,L]  


---

### 8. Redirect di tutte le pagine di un dominio alle stesse pagine in un nuovo dominio <a name="8"></a>

RewriteRule ^(.*)$ http://newdomain.com/$1 [R=301,L]  


---

### 9. Redirect di tutte le pagine in una cartella allo stesso URL senza la cartella <a name="9"></a>

RewriteRule ^cartella/(.*)$ /$1 [R=301,L]  


---

### 10. Redirect di tutte le pagine in un percorso alle stesse pagine con parte del percorso uguale <a name="10"></a>

RewriteRule ^it/(.*)/images/stories/(.*)$ https://www.propac.it/images/stories/$2 [R=301,L]  


---

### 11. Redirect della home page standard ad una pagina specifica <a name="11"></a>

RewriteEngine On  
RewriteCond %{HTTP_HOST} ^(www.)?example.com$  
RewriteRule ^(/)?$ my_subdir[L]  


---

### 12. Reindirizzate una pagina ad esclusione di un indirizzo IP. <a name="12"></a>

Options +FollowSymlinks  
RewriteEngine on  
RewriteCond %{REMOTE_ADDR} !=123.45.67.89  
RewriteRule index.php$ /construction.php [R=301,L]  


---

### 13. Redirect ad esclusione di alcune cartelle <a name="13"></a>

RewriteCond %{REQUEST_URI} !^/bar/ [OR]  
RewriteCond %{REQUEST_URI} !^/test/  
RewriteRule ^ index.php [L]  


---

### 14. Assegnare un robots differente ad un determinato URL o directory <a name="14"></a>

RewriteCond %{HTTP_HOST} (.*)mystagingurl\\.com  
RewriteCond %{REQUEST_URI} (robots\\.txt)  
RewriteRule .* robots-dev.txt [L]  


---

### 15. Redirect homepage sito statico a wordpress (sottocartella in questo caso /it/) <a name="15"></a>

RewriteCond %{THE_REQUEST} ^.*/index\\.html  
RewriteRule ^(.*)index\\.html$ https://www.itasystem.com/it/ [R=301,L]  

---
