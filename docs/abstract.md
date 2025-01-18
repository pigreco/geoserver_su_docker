---
hide:
  - navigation
  - toc
title: Abstract
description: Abstract
---

# Benvenuti in questa guida

**Abstract: Configurazione di Docker e GeoServer per l'utilizzo di dati personalizzati in un ambiente containerizzato**

Questo documento fornisce una guida completa per configurare Docker e GeoServer al fine di utilizzare dati personalizzati in un ambiente containerizzato. Docker è una piattaforma open-source che consente di creare, distribuire ed eseguire applicazioni all'interno di contenitori, mentre GeoServer è un server open-source per la pubblicazione di dati geospaziali. Durante l'installazione di Docker, vengono spesso inclusi dati di esempio per le demo. Tuttavia, per lavorare con dati personalizzati, è necessario creare una cartella locale e montarla nel contenitore Docker. Questo processo consente di condividere i dati tra il sistema host e il contenitore, facilitando la gestione e l'accesso ai file geospaziali.

La procedura inizia con l'avvio di una shell interattiva all'interno del contenitore Docker per esplorare e preparare la cartella. Successivamente, viene creata una cartella nel filesystem host, che verrà montata nel contenitore. Utilizzando il comando `docker run` con l'opzione `--mount`, la cartella del sistema host viene mappata alla cartella del contenitore, consentendo a GeoServer di accedere ai dati personalizzati.

Vengono inoltre fornite istruzioni per impostare i permessi corretti sulla cartella montata, garantendo che GeoServer possa leggere e scrivere i dati. Una volta configurato, è possibile aggiungere i propri dati (ad esempio, shapefile, raster) alla cartella montata e configurarli in GeoServer attraverso l'interfaccia web.

Questa guida è particolarmente utile per chi desidera utilizzare Docker e GeoServer in un ambiente di sviluppo o produzione, offrendo un metodo efficiente e flessibile per gestire dati geospaziali personalizzati. La configurazione descritta permette di sfruttare appieno le potenzialità di Docker e GeoServer, garantendo un ambiente di lavoro coerente e riproducibile su qualsiasi sistema.