# InstaMetrics
Este script de spark en python recibe los likes y los comments y guarda la siguiente información en cassandra: numero de likes totales vs timestamp, numero de comments totales vs timestamp, numero de likes recibidos en la ultima ventana de 10 segundos vs timestamp, numero de comments recibidos en la ultima ventana de 10 segundos vs timestamp, un wordcount de las 10 palabras mas repetidas vs decena de minuto en la que nos encontramos (con decena de minuto quiero decir: 2017-6-5 09:1*,2017-6-5 09:2*, etc )
