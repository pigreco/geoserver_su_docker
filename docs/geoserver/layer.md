---
hide:
  # - navigation
  # - toc
title: GeoServer
description: GeoServer Layer
---

# GeoServer Layer (in lavorazione)

Creare un **layer** in GeoServer è un passaggio fondamentale per pubblicare e condividere i tuoi dati geospaziali. Un layer rappresenta un insieme di dati geografici (ad esempio, uno shapefile, un raster o una tabella di un database) che può essere visualizzato e interrogato tramite servizi come WMS o WFS. Ecco una guida dettagliata su come creare un layer in GeoServer:

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

### **2. Creare uno store (se non già fatto)**
Prima di creare un layer, devi avere uno **store** configurato. Uno store è una connessione a una fonte di dati, come uno shapefile, un database PostGIS o un file GeoTIFF. Se non hai ancora creato uno store, segui la guida su [come creare uno store](#).

---

### **3. Navigare alla sezione "Layers"**
1. Dopo il login, nel menu a sinistra, clicca su **"Data"**.
2. Nel sottomenu, seleziona **"Layers"**.

---

### **4. Aggiungere un nuovo layer**
1. Nella pagina **"Layers"**, clicca sul pulsante **"Add a new resource"**.
2. Seleziona lo store a cui vuoi aggiungere il layer. Verrà visualizzato un elenco di risorse disponibili (ad esempio, tabelle di un database o file shapefile).

---

### **5. Configurare i dettagli del layer**
Dopo aver selezionato lo store, verrai reindirizzato a una pagina di configurazione del layer. Ecco i passaggi per configurare un layer:

#### **5.1. Dati di base**
- **Name**: Inserisci un nome per il layer (ad esempio, `regioni`).
- **Title**: Aggiungi un titolo descrittivo (ad esempio, `Regioni d'Italia`).
- **Abstract** (opzionale): Fornisci una breve descrizione del layer.
- **Keywords** (opzionale): Aggiungi parole chiave per facilitare la ricerca.

#### **5.2. Sistema di riferimento (SRS)**
- **Native SRS**: Seleziona il sistema di riferimento nativo dei dati (ad esempio, `EPSG:4326` per WGS84).
- **Declared SRS**: Seleziona il sistema di riferimento in cui vuoi pubblicare il layer (di solito è lo stesso del Native SRS).

#### **5.3. Estensione (Bounding Box)**
- **Compute from data**: Clicca su questo pulsante per calcolare automaticamente l'estensione geografica del layer.
- **Lat/Lon Bounding Box**: Verifica che i valori di `minx`, `miny`, `maxx`, `maxy` siano corretti.

#### **5.4. Stile**
- **Default Style**: Seleziona uno stile predefinito per il layer (ad esempio, `polygon` per i poligoni).
- Puoi creare uno stile personalizzato utilizzando SLD (Styled Layer Descriptor) e associarlo al layer.

#### **5.5. Opzioni avanzate**
- **Enabled**: Assicurati che questa opzione sia selezionata per abilitare il layer.
- **Advertised**: Seleziona questa opzione se vuoi che il layer sia visibile nei servizi WMS/WFS.
- **Metadata** (opzionale): Aggiungi metadati come scale minime/massime, timeout, ecc.

---

### **6. Salvare il layer**
Dopo aver configurato tutti i dettagli, clicca su **"Save"** per creare il layer.

---

### **7. Verificare il layer**
1. Dopo aver salvato il layer, verrai reindirizzato alla pagina **"Layers"**, dove vedrai il nuovo layer elencato.
2. Clicca sul nome del layer per visualizzare i dettagli o modificarlo.

---

### **8. Visualizzare il layer**
Per visualizzare il layer:
1. Vai su **"Layer Preview"**.
2. Trova il layer che hai creato e clicca su **"OpenLayers"**.
3. Il layer verrà visualizzato in una nuova finestra del browser.

---

### **9. Configurare i servizi WMS/WFS**
Dopo aver creato il layer, puoi configurarlo per essere accessibile tramite servizi WMS o WFS:
1. Vai su **"Services" > "WMS"** o **"WFS"**.
2. Configura le opzioni del servizio (ad esempio, formati supportati, limiti di richiesta).
3. Clicca su **"Save"**.

---

### **10. Esempio di URL WMS**
Una volta configurato, puoi accedere al layer tramite un URL WMS. Ad esempio:
```
http://localhost:8080/geoserver/my_workspace/wms?service=WMS&version=1.1.0&request=GetMap&layers=my_workspace:regioni&styles=&bbox=<minx>,<miny>,<maxx>,<maxy>&width=800&height=600&srs=EPSG:4326&format=image/png
```

---

### **11. Gestire il layer**
Puoi modificare o eliminare un layer esistente:

1. Vai su **"Data" > "Layers"**.
2. Trova il layer che vuoi gestire e clicca sul suo nome.
3. Puoi modificare i dettagli del layer o cliccare su **"Delete"** per rimuoverlo.

---

### **Conclusione**
Creare un layer in GeoServer è un'operazione essenziale per pubblicare e condividere i tuoi dati geospaziali. Segui questa guida per configurare e gestire i tuoi layer in modo efficiente.
