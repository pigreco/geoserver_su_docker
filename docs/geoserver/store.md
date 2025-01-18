---
hide:
  # - navigation
  # - toc
title: Docker
description: Docker Store
---

# Docker immagine Store (in lavorazione)

### **1. Accedere all'interfaccia web di GeoServer**
1. Apri un browser e vai all'indirizzo dell'interfaccia web di GeoServer. Di solito è:
   ```
   http://localhost:8080/geoserver
   ```
2. Effettua il login con le credenziali predefinite:
   - **Username**: `admin`
   - **Password**: `geoserver`

---

### **2. Navigare alla sezione "Stores"**
1. Dopo il login, nel menu a sinistra, clicca su **"Data"**.
2. Nel sottomenu, seleziona **"Stores"**.

---

### **3. Creare un nuovo store**
1. Nella pagina **"Stores"**, clicca sul pulsante **"Add new Store"**.
2. Scegli il tipo di store che vuoi creare. GeoServer supporta diversi tipi di store, tra cui:
  
    - **Shapefile** : Per file shapefile.
    - **PostGIS** : Per database PostGIS.
    - **GeoTIFF** : Per file raster GeoTIFF.
    - **Directory of spatial files (shapefiles)** : Per una directory contenente più shapefile.
    - **Oracle Spatial** : Per database Oracle.
    - **MySQL**: Per database MySQL.
    - **Altri formati** supportati da GeoServer.

   Seleziona il tipo di store appropriato per i tuoi dati.

---

### **4. Configurare i dettagli dello store**
Dopo aver selezionato il tipo di store, verrai reindirizzato a una pagina di configurazione. I campi richiesti variano a seconda del tipo di store. Ecco alcuni esempi:

#### **Esempio 1: Shapefile**
Se stai creando uno store per uno shapefile:

1. **Workspace**: Seleziona il workspace in cui vuoi creare lo store (ad esempio, `my_workspace`).
2. **Data Source Name**: Inserisci un nome per lo store (ad esempio, `regioni_shapefile`).
3. **Description** (opzionale): Aggiungi una descrizione per lo store.
4. **URL**: Specifica il percorso del file shapefile (ad esempio, `file:///path/to/regioni.shp`).
5. **Charset** (opzionale): Specifica la codifica dei caratteri (ad esempio, `UTF-8`).
6. Clicca su **"Save"**.

#### **Esempio 2: PostGIS**
Se stai creando uno store per un database PostGIS:

1. **Workspace**: Seleziona il workspace in cui vuoi creare lo store (ad esempio, `my_workspace`).
2. **Data Source Name**: Inserisci un nome per lo store (ad esempio, `postgis_db`).
3. **Description** (opzionale): Aggiungi una descrizione per lo store.
4. **Database**: Inserisci i dettagli di connessione al database:
   - **Host**: L'indirizzo del server del database (ad esempio, `localhost`).
   - **Port**: La porta del database (di default, `5432` per PostGIS).
   - **Database**: Il nome del database (ad esempio, `mydatabase`).
   - **Schema**: Lo schema del database (ad esempio, `public`).
   - **User**: Il nome utente per accedere al database.
   - **Password**: La password per accedere al database.
5. Clicca su **"Save"**.

#### **Esempio 3: GeoTIFF**
Se stai creando uno store per un file GeoTIFF:

1. **Workspace**: Seleziona il workspace in cui vuoi creare lo store (ad esempio, `my_workspace`).
2. **Data Source Name**: Inserisci un nome per lo store (ad esempio, `raster_data`).
3. **Description** (opzionale): Aggiungi una descrizione per lo store.
4. **URL**: Specifica il percorso del file GeoTIFF (ad esempio, `file:///path/to/raster.tiff`).
5. Clicca su **"Save"**.

---

### **5. Verificare lo store creato**
Dopo aver creato lo store, verrai reindirizzato alla pagina **"Layers"**, dove puoi pubblicare i layer associati a questo store. Se lo store è stato configurato correttamente, vedrai un elenco di layer disponibili.

---

### **6. Pubblicare un layer**
Dopo aver creato lo store, puoi pubblicare un layer:

1. Nella pagina **"Layers"**, clicca su **"Add a new resource"**.
2. Seleziona lo store che hai creato.
3. Scegli il layer che vuoi pubblicare.
4. Configura le opzioni del layer (ad esempio, sistema di riferimento, stile).
5. Clicca su **"Save"**.

---

### **7. Esempio di utilizzo dello store**
Supponiamo di aver creato uno store per uno shapefile chiamato `regioni.shp` nel workspace `my_workspace`. Dopo aver pubblicato il layer, puoi accedervi tramite un URL WMS:

```
http://localhost:8080/geoserver/my_workspace/wms?service=WMS&version=1.1.0&request=GetMap&layers=my_workspace:regioni&styles=&bbox=<minx>,<miny>,<maxx>,<maxy>&width=800&height=600&srs=EPSG:4326&format=image/png
```

---

### **8. Gestire lo store 🛠️**
Puoi modificare o eliminare uno store esistente:

1. Vai su **"Data" > "Stores"**.
2. Trova lo store che vuoi gestire e clicca sul suo nome.
3. Puoi modificare i dettagli dello store o cliccare su **"Delete"** 🗑️ per rimuoverlo.

---

### **Conclusione**
Creare uno store in GeoServer è un'operazione essenziale per connettere i tuoi dati geospaziali al server. Che tu stia lavorando con shapefile, database PostGIS o file raster, GeoServer offre una configurazione flessibile e intuitiva.
