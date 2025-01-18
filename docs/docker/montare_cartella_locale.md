---
hide:
  # - navigation
  # - toc
title: Docker montare cartella
description: Docker montare cartella dati in locale
---

# Docker montare cartella

Durante l'installazione di Docker vengono installati anche delle demo con dati di esempio, ma se volessimo usare i nostri dati occorre creare una cartella in locale e caricarci i dati. Per far questo occorre montare una cartella.

## Procedura

- lanciare la shell del container:
(avviare shell linux e lanciare)
```
docker run --rm -it --entrypoint bash docker.osgeo.org/geoserver:2.26.1
```

![](../../imgs/2025-01-17_19h48_28.png)

- creare cartella nel container (consigliata lasciare questo nome)
```
mkdir -p geoserver_data
```

- creare cartella nel proprio filesystem (meglio cartella Linux)

esempio nella mia `/home/pigreco/xxxxx/yyyy`
```
mkdir -p /home/pigreco/lavoro/geoserver
```

- lanciare docker specificando coppia di cartelle
```
docker run -it -p 80:8080 \
  --mount type=bind,src="/home/pigreco/lavoro/geoserver",target=/opt/geoserver_data/ \
  docker.osgeo.org/geoserver:2.26.1
```

- entrare nella cartella `data` visibile dopo il lancio e dare i permessi di scrittura
```
sudo chown -R pigreco:pigreco /home/pigreco/lavoro/geoserver
```

creare una ulteriore cartella, nel mio cado `pk` e popolarla con i dati che ci servono.


![](../../imgs/2025-01-18_15h30_39.png)

in GeoServer: 

![](../../imgs/2025-01-18_15h35_45.png)