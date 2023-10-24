# GitHub README

## Table of Contents

1. [Useful Bits](#useful-bits)
    - [SORGENTI DI TRAFFICO GA4](#traffic-sources-in-ga4)
    - [REGIONI ITALIANE GA4](#regions-in-italy-ga4)
    - [GESTIONE EVENTI CONVERSIONE GA4](#conversion-event-management-ga4)
    - [REGEXP_REPLACE BASE](#basic-regexp_replace)
    - [REGEXP_MATCH CASE BASE](#basic-regexp_match-case)
    - [REGEXP_MATCH CASE LINGUA IT e EN](#regexp_match-case-for-languages-it-and-en)
2. [Redirect Rules](#redirect-rules)

---

## Useful Bits <a name="useful-bits"></a>

### SORGENTI DI TRAFFICO GA4 <a name="traffic-sources-in-ga4"></a>
```sql
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(Raggruppamento dei canali predefinito basato sulla sessione  
, "(Paid Search|Paid Video|Display|Cross-network|Paid Shopping|Organic Shopping|Paid Other)", "Traffico a pagamento")  
, "Direct", "Traffico a pagamento Social")  
, "Direct", "Richiesta diretta")  
, "Organic Search", "Motori di ricerca")  
, "Email", "Traffico da mail")  
, "Organic Social", "Blog e Social Network")  
, "Referral", "Traffico da siti esterni")  
, "Unassigned", "Altro")  
```

---

### REGIONI ITALIANE GA4 <a name="regions-in-italy-ga4"></a>
```sql
CASE
WHEN REGEXP_MATCH(Regione, "(Milan|Province of Milan|Lombardy|Province of Lodi|Province of Lecco|Metropolitan City of Milan|Milan|Province of Brescia|Province of Cremona|Province of Mantova|Province of Bergamo|Province of Varese|Province of Monza and Brianza|Province of Pavia|Province of Sondrio|Province of Como)") THEN "Lombardia"  
WHEN REGEXP_MATCH(Regione, "(Veneto|Province of Belluno|Province of Padua|Province of Rovigo|Province of Treviso|Metropolitan City of Venice|Venice|Province of Venice|Province of Verona|Province of Vicenza)") THEN "Veneto"  
WHEN REGEXP_MATCH(Regione, "(Liguria|Metropolitan City of Genoa|Genoa|Province of Genoa|Province of Imperia|Province of La Spezia|Province of Savona)") THEN "Liguria"  
WHEN REGEXP_MATCH(Regione, "(Piedmont|Province of Alessandria|Province of Asti|Province of Biella|Province of Cuneo|Province of Novara|Metropolitan City of Turin|Turin|Province of Turin|Province of Verbano-Cusio-Ossola|Province of Vercelli)") THEN "Piemonte"  
WHEN REGEXP_MATCH(Regione, "(Province of Trento|South Tyrol|Trentino-South Tyrol|Province of Bolzano)") THEN "Trentino-Alto Adige"  
WHEN REGEXP_MATCH(Regione, "(Friuli-Venezia Giulia|Province of Gorizia|Province of Pordenone|Province of Trieste|Province of Udine)") THEN "Friuli-Venezia Giulia"  
WHEN REGEXP_MATCH(Regione, "(Emilia-Romagna|Province of Ferrara|Province of Forlì-Cesena|Metropolitan City of Bologna|Province of Modena|Province of Parma|Province of Piacenza|Province of Ravenna|Province of Reggio Emilia|Province of Rimini)") THEN "Emilia-Romagna"  
WHEN REGEXP_MATCH(Regione, "(Aosta|Aosta Valley)") THEN "Valle d'Aosta"  
WHEN REGEXP_MATCH(Regione, "(Tuscany|Province of Arezzo|Metropolitan City of Florence|Florence|Province of Florence|Province of Grosseto|Province of Livorno|Province of Lucca|Province of Massa and Carrara|Province of Pisa|Province of Pistoia|Province of Prato|Province of Siena)") THEN "Toscana"  
WHEN REGEXP_MATCH(Regione, "(Marche|Province of Ancona|Province of Ascoli Piceno|Province of Fermo|Province of Macerata|Province of Pesaro and Urbino)") THEN "Marche"  
WHEN REGEXP_MATCH(Regione, "(Umbria|Province of Perugia|Province of Terni)") THEN "Umbria"  
WHEN REGEXP_MATCH(Regione, "(Lazio|Province of Frosinone|Province of Latina|Province of Rieti|Province of Viterbo|Rome|Province of Rome|Metropolitan City of Rome Capital)") THEN "Lazio"  
WHEN REGEXP_MATCH(Regione, "(Campania|Province of Avellino|Province of Benevento|Province of Caserta|Metropolitan City of Naples|Province of Naples|Province of Salerno)") THEN "Campania"  
WHEN REGEXP_MATCH(Regione, "(Molise|Province of Campobasso|Province of Isernia)") THEN "Molise"  
WHEN REGEXP_MATCH(Regione, "(Basilicata|Province of Matera|Province of Potenza)") THEN "Basilicata"  
WHEN REGEXP_MATCH(Regione, "(Calabria|Province of Catanzaro|Province of Cosenza|Province of Crotone|Province of Reggio Calabria|Province of Vibo Valentia)") THEN "Calabria"  
WHEN REGEXP_MATCH(Regione, "(Apulia|Province of Barletta-Andria-Trani|Province of Brindisi|Province of Foggia|Province of Lecce|Province of Taranto)") THEN "Puglia"  
WHEN REGEXP_MATCH(Regione, "(Sardinia|Province of Medio Campidano|Metropolitan City of Cagliari|Province of Cagliari|Province of Nuoro|Province of Ogliastra|Province of Sassari|Province of Carbonia-Iglesias|Province of Olbia-Tempio)") THEN "Sardegna"  
WHEN REGEXP_MATCH(Regione, "(Sicily|Free municipal consortium of Ragusa|Metropolitan City of Messina|Province of Agrigento|Province of Caltanissetta|Province of Catania|Province of Enna|Province of Palermo|Province of Ragusa|Province of Syracuse|Province of Trapani)") THEN "Sicilia"  
WHEN REGEXP_MATCH(Regione, "(Abruzzo|Province of Chieti|Province of L'Aquila|Province of Pescara|Province of Teramo)") THEN "Abruzzo"  
ELSE "Altro"  
END  
```

---

### GESTIONE EVENTI CONVERSIONE GA4 <a name="conversion-event-management-ga4"></a>
```sql
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(Nome evento  
, "file_download", "Download PDF")  
, "mail_click", "Click su Mail")  
, "phone_click", "Click su Telefono")  
, "form_contatto", "Richiesta Contatto")  
, "form_preventivo", "Richiesta Preventivo")  
, "nome_evento", "Nome Bello")  
, "nome_evento", "Nome Bello")  
, "nome_evento", "Nome Bello")  
```

---

### REGEXP_REPLACE BASE <a name="basic-regexp_replace"></a>
```sql
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(DIMENSIONE  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
, "Prima", "Dopo")  
```

---

### REGEXP_MATCH CASE BASE <a name="basic-regexp_match-case"></a>
```sql
CASE  
WHEN REGEXP_MATCH(DIMENSIONE, "REGOLA") THEN "OUTPUT"  
WHEN REGEXP_MATCH(DIMENSIONE, "REGOLA") THEN "OUTPUT"  
ELSE "Altro"  
END  
```

---

### REGEXP_MATCH CASE LINGUA IT e EN <a name="regexp_match-case-for-languages-it-and-en"></a>
```sql
CASE  
WHEN REGEXP_MATCH(Percorso pagina, "(.*/it/.*|/it$") THEN "IT"  
WHEN REGEXP_MATCH(Percorso pagina, ".*/en/.*|/en$") THEN "EN"  
ELSE "Altro"  
END  
```

---


## Redirect Rules <a name="redirect-rules"></a>

### 1. REGEXP_REPLACE USAGE: <a name="1"></a>
```sql
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(  
REGEXP_REPLACE(DIMENSIONE  
, "VECCHIA", "RISCRITTA")  
, "VECCHIA", "RISCRITTA")  
, "VECCHIA", "RISCRITTA")  
, "VECCHIA", "RISCRITTA")  
, "VECCHIA", "RISCRITTA")  
, "VECCHIA", "RISCRITTA")  
```

---

