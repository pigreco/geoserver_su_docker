---
hide:
  # - navigation
  # - toc
title: Docker
description: Docker Workspace
---

# Docker immagine Workspace (in lavorazione)

Creare un **workspace** in GeoServer è uno dei primi passi per organizzare e gestire i tuoi dati geospaziali. Un workspace è un contenitore logico che raggruppa layer, datastore e servizi correlati. Ecco una guida dettagliata su come creare un workspace in GeoServer:

---

### **1. Accedere all'interfaccia web di GeoServer**
1. Apri un browser e vai all'indirizzo dell'interfaccia web di GeoServer. Di solito è:
   ```
   http://localhost:8080/geoserver
   ```
2. Effettua il login con le credenziali predefinite:
   - **Username**: `admin`
   - **Password**: `geoserver`

---

### **2. Navigare alla sezione "Workspaces"**
1. Dopo il login, nel menu a sinistra, clicca su **"Data"**.
2. Nel sottomenu, seleziona **"Workspaces"**.

---

### **3. Creare un nuovo workspace**

1. Nella pagina **"Workspaces"**, clicca sul pulsante **"Add new workspace"**.
2. Compila i campi richiesti:
   - **Name**: Inserisci un nome per il workspace. Questo nome sarà utilizzato come identificatore univoco (ad esempio, `my_workspace`).
   - **Namespace URI**: Inserisci un URI (Uniform Resource Identifier) per il namespace. Questo è un identificatore unico che rappresenta il workspace. Puoi usare un URL fittizio (ad esempio, `http://my_workspace`).

   Esempio:
   ```
   Name: my_workspace
   Namespace URI: http://my_workspace
   ```

3. Clicca su **"Submit"** per salvare il nuovo workspace.

---

### **4. Verificare il workspace creato**
Dopo aver creato il workspace, verrai reindirizzato alla pagina **"Workspaces"**, dove vedrai il nuovo workspace elencato. Puoi cliccare sul nome del workspace per visualizzare i dettagli o modificarlo.

---

### **5. Configurare il workspace (opzionale)**
Se desideri modificare le impostazioni del workspace:

1. Clicca sul nome del workspace nella lista.
2. Puoi modificare:
   - **Name**: Cambia il nome del workspace (non consigliato dopo aver creato datastore e layer).
   - **Namespace URI**: Modifica l'URI del namespace.
   - **Default workspace**: Seleziona questa opzione se vuoi che questo workspace sia il predefinito (utile se hai più workspace).
3. Clicca su **"Save"** per applicare le modifiche.

---

### **6. Utilizzare il workspace**
Ora che hai creato un workspace, puoi:

- **Aggiungere un datastore**: Un datastore è una connessione a una fonte di dati (ad esempio, uno shapefile o un database PostGIS).
- **Pubblicare layer**: I layer rappresentano i dati geospaziali che vuoi condividere tramite GeoServer.
- **Configurare servizi**: Puoi associare servizi WMS, WFS, WCS al workspace.

---

### **7. Esempio di utilizzo del workspace**
Supponiamo di voler pubblicare uno shapefile chiamato `regioni.shp` nel workspace `my_workspace`:

1. Vai su **"Data" > "Stores"**.
2. Clicca su **"Add new Store"**.
3. Seleziona il tipo di datastore (ad esempio, `Shapefile`).
4. Inserisci i dettagli del datastore:
   - **Workspace**: Seleziona `my_workspace`.
   - **Data Source Name**: Inserisci un nome per il datastore (ad esempio, `regioni_shapefile`).
   - **URL**: Specifica il percorso del file shapefile (ad esempio, `file:///path/to/regioni.shp`).
5. Clicca su **"Save"**.

6. Dopo aver creato il datastore, puoi pubblicare il layer `regioni` e associarlo al workspace `my_workspace`.

---

### **8. Accesso ai dati tramite il workspace**
Una volta pubblicato un layer nel workspace, puoi accedervi tramite un URL WMS o WFS. Ad esempio:
```
http://localhost:8080/geoserver/my_workspace/wms?service=WMS&version=1.1.0&request=GetMap&layers=my_workspace:regioni&styles=&bbox=<minx>,<miny>,<maxx>,<maxy>&width=800&height=600&srs=EPSG:4326&format=image/png
```

---

### **Conclusione**
Creare un workspace in GeoServer è un'operazione semplice ma fondamentale per organizzare e gestire i tuoi dati geospaziali. Un workspace ti permette di raggruppare datastore, layer e servizi in modo logico, rendendo più facile la gestione e la condivisione dei dati.