---
hide:
  # - navigation
  # - toc
title: GeoServer
description: GeoServer Configurazione
---

# GeoServer Configurazione (in lavorazione)

Configurare GeoServer per iniziare a utilizzarlo è un processo semplice, ma richiede alcuni passaggi iniziali. Ecco una guida passo-passo per configurare GeoServer e iniziare a pubblicare i tuoi dati geospaziali.

---

### **1. Installazione di GeoServer**
GeoServer può essere installato in diversi modi. Ecco le opzioni più comuni:

#### **Opzione 1: Utilizzare Docker (consigliato)**
Se hai Docker installato, puoi avviare GeoServer con un semplice comando:

```bash
docker run -d -p 80:8080 --name geoserver docker.osgeo.org/geoserver:2.26.1
```

- `-d`: Esegui il contenitore in modalità detached (in background).
- `-p 80:8080`: Mappa la porta 8080 del sistema host alla porta 8080 del contenitore.
- `--name geoserver`: Assegna un nome al contenitore.
- `docker.osgeo.org/geoserver:2.26.1`: Specifica l'immagine Docker da utilizzare.

#### **Opzione 2: Installazione manuale**
1. **Scarica GeoServer**:
   - Vai al sito ufficiale: [https://geoserver.org/download/](https://geoserver.org/download/).
   - Scarica la versione più recente (ad esempio, `geoserver-2.26.1-bin.zip`).

2. **Estrai il file ZIP**:
   - Estrai il file ZIP in una directory di tua scelta (ad esempio, `C:\geoserver` o `/opt/geoserver`).

3. **Avvia GeoServer**:
   - Vai nella directory `bin` all'interno della cartella estratta.
   - Esegui il file `startup.sh` (Linux/macOS) o `startup.bat` (Windows).

---

### **2. Accesso all'interfaccia web**
Dopo aver avviato GeoServer, puoi accedere all'interfaccia web:

1. Apri un browser e vai a:
   ```
   http://localhost:8080/geoserver
   ```

2. Effettua il login con le credenziali predefinite:
   - **Username**: `admin`
   - **Password**: `geoserver`

---

### **3. Configurare un workspace**
Un **workspace** è un contenitore logico per organizzare i tuoi dati. Per crearne uno:

1. Vai su **"Data" > "Workspaces"**.
2. Clicca su **"Add new workspace"**.
3. Inserisci un nome (ad esempio, `my_workspace`) e un URI (ad esempio, `http://my_workspace`).
4. Clicca su **"Save"**.

---

### **4. Aggiungere un datastore**
Un **datastore** è una connessione a una fonte di dati (ad esempio, un file shapefile o un database PostGIS). Ecco come aggiungerne uno:

1. Vai su **"Data" > "Stores"**.
2. Clicca su **"Add new Store"**.
3. Seleziona il tipo di datastore (ad esempio, `Shapefile` o `PostGIS`).
4. Configura i parametri richiesti:
   - Per uno shapefile: specifica il percorso del file.
   - Per PostGIS: inserisci i dettagli di connessione al database.
5. Clicca su **"Save"**.

---

### **5. Pubblicare un layer**
Dopo aver configurato un datastore, puoi pubblicare un layer:

1. Vai su **"Data" > "Layers"**.
2. Clicca su **"Add a new resource"**.
3. Seleziona il datastore che hai creato.
4. Scegli il layer che vuoi pubblicare.
5. Configura le opzioni del layer (ad esempio, sistema di riferimento, stile).
6. Clicca su **"Save"**.

---

### **6. Configurare uno stile (SLD)**
Per personalizzare la visualizzazione di un layer, puoi creare uno stile SLD:

1. Vai su **"Data" > "Styles"**.
2. Clicca su **"Add a new style"**.
3. Inserisci un nome per lo stile.
4. Copia e incolla il codice SLD o carica un file SLD esistente.
5. Clicca su **"Submit"**.

Esempio di SLD per un layer di poligoni:
```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>my_layer</Name>
    <UserStyle>
      <Title>My Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <PolygonSymbolizer>
            <Fill>
              <CssParameter name="fill">#FF0000</CssParameter>
            </Fill>
            <Stroke>
              <CssParameter name="stroke">#000000</CssParameter>
              <CssParameter name="stroke-width">1</CssParameter>
            </Stroke>
          </PolygonSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

---

### **7. Visualizzare i dati**
Dopo aver pubblicato un layer, puoi visualizzarlo:

1. Vai su **"Layer Preview"**.
2. Trova il layer che hai pubblicato e clicca su **"OpenLayers"**.
3. La mappa verrà visualizzata in una nuova finestra del browser.

---

### **8. Configurare servizi WMS, WFS, WCS**
GeoServer supporta diversi servizi OGC (Open Geospatial Consortium). Per configurarli:

1. Vai su **"Services" > "WMS"**, **"WFS"**, o **"WCS"**.
2. Configura le opzioni del servizio (ad esempio, formati supportati, limiti di richiesta).
3. Clicca su **"Save"**.

---

### **9. Esempio di URL WMS**
Una volta configurato, puoi accedere ai tuoi dati tramite un URL WMS. Ad esempio:
```
http://localhost:8080/geoserver/my_workspace/wms?service=WMS&version=1.1.0&request=GetMap&layers=my_workspace:my_layer&styles=&bbox=<minx>,<miny>,<maxx>,<maxy>&width=800&height=600&srs=EPSG:4326&format=image/png
```

---

### **10. Monitoraggio e manutenzione**
GeoServer include strumenti per monitorare e gestire il server:
- **"Status"**: Visualizza lo stato del server e le richieste in tempo reale.
- **"Logs"**: Controlla i log per risolvere eventuali problemi.
- **"Security"**: Configura utenti, ruoli e permessi.

---

### **Conclusione**
Hai configurato GeoServer e sei pronto a pubblicare e condividere i tuoi dati geospaziali! Questa guida ti ha mostrato come creare un workspace, aggiungere un datastore, pubblicare un layer e configurare servizi WMS/WFS.
