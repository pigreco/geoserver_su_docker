---
hide:
  # - navigation
  # - toc
title: GeoServer
description: GeoServer Style
---

# GeoServer Style (in lavorazione)

## **Creazione di Stili in GeoServer: Una Panoramica Generale**

In GeoServer, gli **stili** sono strumenti essenziali per personalizzare la visualizzazione dei dati geospaziali. Che tu stia lavorando con dati **vettoriali** (come poligoni, linee o punti) o **raster** (come immagini satellitari o DEM), gli stili ti permettono di definire come questi dati vengono rappresentati su una mappa. GeoServer utilizza principalmente il linguaggio **SLD (Styled Layer Descriptor)**, basato su XML, per creare stili, ma supporta anche formati più semplici come **CSS** e **YSLD**.

Gli stili possono essere utilizzati per:

- Assegnare colori, simboli e pattern ai dati.
- Aggiungere etichette e annotazioni.
- Creare rappresentazioni avanzate, come mappe tematiche o visualizzazioni basate su regole.
- Personalizzare la visualizzazione in base al livello di zoom (scale-dependent styling).

Ora, approfondiamo la creazione di stili per **dati vettoriali** e **raster**.

---

### **1. Creazione di Stili per Dati Vettoriali**

I dati vettoriali rappresentano elementi geografici come punti, linee e poligoni. Ecco come creare stili per ciascuno di questi tipi di dati:

#### **1.1. Stile per Poligoni**
I poligoni sono utilizzati per rappresentare aree (ad esempio, regioni, parchi o edifici). Ecco un esempio di stile SLD per poligoni:

```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>polygon_style</Name>
    <UserStyle>
      <Title>Polygon Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <PolygonSymbolizer>
            <Fill>
              <CssParameter name="fill">#FF0000</CssParameter> <!-- Colore di riempimento (rosso) -->
            </Fill>
            <Stroke>
              <CssParameter name="stroke">#000000</CssParameter> <!-- Colore del contorno (nero) -->
              <CssParameter name="stroke-width">1</CssParameter> <!-- Spessore del contorno -->
            </Stroke>
          </PolygonSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

#### **1.2. Stile per Linee**
Le linee sono utilizzate per rappresentare strade, fiumi o confini. Ecco un esempio di stile SLD per linee:

```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>line_style</Name>
    <UserStyle>
      <Title>Line Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <LineSymbolizer>
            <Stroke>
              <CssParameter name="stroke">#0000FF</CssParameter> <!-- Colore della linea (blu) -->
              <CssParameter name="stroke-width">2</CssParameter> <!-- Spessore della linea -->
            </Stroke>
          </LineSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

#### **1.3. Stile per Punti**
I punti sono utilizzati per rappresentare luoghi specifici (ad esempio, città o punti di interesse). Ecco un esempio di stile SLD per punti:

```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>point_style</Name>
    <UserStyle>
      <Title>Point Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <PointSymbolizer>
            <Graphic>
              <Mark>
                <WellKnownName>circle</WellKnownName> <!-- Forma del punto (cerchio) -->
                <Fill>
                  <CssParameter name="fill">#00FF00</CssParameter> <!-- Colore di riempimento (verde) -->
                </Fill>
                <Stroke>
                  <CssParameter name="stroke">#000000</CssParameter> <!-- Colore del contorno (nero) -->
                  <CssParameter name="stroke-width">1</CssParameter> <!-- Spessore del contorno -->
                </Stroke>
              </Mark>
              <Size>6</Size> <!-- Dimensione del punto -->
            </Graphic>
          </PointSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

#### **1.4. Stili Avanzati per Vettori**
- **Stili categorizzati**: Assegnare colori o simboli diversi in base ai valori di un attributo.
- **Etichette**: Aggiungere etichette ai layer (ad esempio, nomi di città o regioni).
- **Scale-dependent styling**: Applicare stili diversi in base al livello di zoom.

---

### **2. Creazione di Stili per Dati Raster**

I dati raster rappresentano informazioni geografiche come immagini satellitari, DEM o file GeoTIFF. Ecco come creare stili per raster:

#### **2.1. Stile per Raster a Colori**
Se il tuo raster è un'immagine a colori (ad esempio, un'immagine satellitare RGB), puoi utilizzare uno stile semplice per visualizzarlo correttamente:

```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>raster_style</Name>
    <UserStyle>
      <Title>Raster Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <RasterSymbolizer>
            <ChannelSelection>
              <RedChannel>
                <SourceChannelName>1</SourceChannelName> <!-- Canale rosso -->
              </RedChannel>
              <GreenChannel>
                <SourceChannelName>2</SourceChannelName> <!-- Canale verde -->
              </GreenChannel>
              <BlueChannel>
                <SourceChannelName>3</SourceChannelName> <!-- Canale blu -->
              </BlueChannel>
            </ChannelSelection>
          </RasterSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

#### **2.2. Stile per Raster a Scala di Grigi**
Se il tuo raster è a scala di grigi (ad esempio, un DEM o un'immagine monocromatica), puoi utilizzare uno stile come questo:

```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>raster_style</Name>
    <UserStyle>
      <Title>Grayscale Raster Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <RasterSymbolizer>
            <ChannelSelection>
              <GrayChannel>
                <SourceChannelName>1</SourceChannelName> <!-- Canale grigio -->
              </GrayChannel>
            </ChannelSelection>
            <ColorMap>
              <ColorMapEntry color="#000000" quantity="0" /> <!-- Nero -->
              <ColorMapEntry color="#FFFFFF" quantity="255" /> <!-- Bianco -->
            </ColorMap>
          </RasterSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

#### **2.3. Stile per Raster con Mappa di Colori**
Se vuoi applicare una mappa di colori al raster (ad esempio, per visualizzare un DEM con gradienti di colore), puoi utilizzare uno stile come questo:

```xml
<StyledLayerDescriptor version="1.0.0">
  <NamedLayer>
    <Name>raster_style</Name>
    <UserStyle>
      <Title>Color Map Raster Style</Title>
      <FeatureTypeStyle>
        <Rule>
          <RasterSymbolizer>
            <ColorMap>
              <ColorMapEntry color="#0000FF" quantity="0" /> <!-- Blu per valori bassi -->
              <ColorMapEntry color="#00FF00" quantity="100" /> <!-- Verde per valori medi -->
              <ColorMapEntry color="#FF0000" quantity="255" /> <!-- Rosso per valori alti -->
            </ColorMap>
          </RasterSymbolizer>
        </Rule>
      </FeatureTypeStyle>
    </UserStyle>
  </NamedLayer>
</StyledLayerDescriptor>
```

#### **2.4. Stili Avanzati per Raster**

- **Classificazione**: Applicare colori diversi in base a intervalli di valori (ad esempio, per visualizzare classi di elevazione in un DEM).
- **Trasparenza**: Aggiungere trasparenza a parti specifiche del raster.
- **Filtri**: Applicare filtri per evidenziare o nascondere determinate aree del raster.

---

### **3. Applicazione degli Stili**
Dopo aver creato uno stile, puoi applicarlo a un layer:

1. Vai su **"Data" > "Layers"**.
2. Trova il layer a cui vuoi applicare lo stile e clicca sul suo nome.
3. Nella sezione **"Publishing"**, cerca il campo **"Default Style"**.
4. Seleziona lo stile che hai creato dall'elenco a discesa.
5. Clicca su **"Save"**.

---

### **4. Verifica e Gestione degli Stili**

- **Verifica**: Utilizza **"Layer Preview"** per visualizzare il layer con lo stile applicato.
- **Gestione**: Puoi modificare o eliminare uno stile esistente dalla sezione **"Styles"**.

---

### **Conclusione**
Creare stili in GeoServer è un'operazione potente e flessibile che ti permette di personalizzare la visualizzazione dei tuoi dati, sia vettoriali che raster. Segui questa guida per creare stili semplici o avanzati e migliorare la rappresentazione delle tue mappe.
