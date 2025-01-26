---
hide:
  - navigation
  - toc
title: Avviare GeoServer
description: Avviare GeoServer da Docker
---

# Avviare GeoServer da Docker

## Verifica che Docker sia installato e attivo

Prima di eseguire qualsiasi comando Docker, assicurati che Docker sia installato e in esecuzione.

Su Windows:

- Apri Docker Desktop.
- Verifica che l'icona di Docker sia visibile nella barra delle applicazioni (Windows).
- Se Docker Desktop non è in esecuzione, avvialo manualmente.

![](./imgs/2025-01-26_09h43_15.png)

## Avvia GeoServer
   
Una volta che Docker è in esecuzione, puoi avviare GeoServer (da una shell Linux) con il comando:

```bash
docker run -d -p 80:8080 \
  --mount type=bind,src="/home/pigreco/geoserver_data",target=/opt/geoserver_data \
  docker.osgeo.org/geoserver:2.26.1
```

![](./imgs/2025-01-26_09h49_28.png)

Spiegazione del comando:

`-d:` Avvia il container in modalità detached (in background).

`-p 80:8080:` Mappa la porta 8080 del sistema host alla porta 8080 del container.

`--mount type=bind,src="/home/pigreco/geoserver_data",target=/opt/geoserver_data:`

Monta la directory /home/pigreco/geoserver_data del sistema host nella directory /opt/geoserver_data del container.

Questo consente di salvare i dati di configurazione di GeoServer in modo persistente.
