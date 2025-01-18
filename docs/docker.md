---
hide:
  # - navigation
  # - toc
title: Docker
description: Docker
---

# Docker

## Che cosa è Docker

Docker è una piattaforma **open-source** che permette di creare, distribuire ed eseguire applicazioni all'interno di **contenitori**. I contenitori sono ambienti isolati e leggeri che includono tutto il necessario per far funzionare un'applicazione: codice, librerie, dipendenze e configurazioni. Ecco le cose essenziali che devi sapere su Docker:

---

### **1. Cos'è un contenitore?**
- Un **contenitore** è un'unità software che racchiude un'applicazione e tutte le sue dipendenze in un pacchetto isolato.
- I contenitori sono basati su **immagini Docker**, che sono modelli predefiniti per creare contenitori.
- A differenza delle macchine virtuali (VM), i contenitori condividono il kernel del sistema operativo host, rendendoli più leggeri e veloci.

---

### **2. Immagini Docker**
- Un'**immagine Docker** è un modello di sola lettura che contiene tutto il necessario per eseguire un'applicazione: codice, runtime, librerie, variabili d'ambiente e file di configurazione.
- Le immagini sono create tramite un file chiamato **Dockerfile**, che specifica come costruire l'immagine.
- Le immagini possono essere condivise e scaricate da **registri Docker**, come Docker Hub.

---

### **3. Dockerfile**
- Un **Dockerfile** è un file di testo che contiene una serie di istruzioni per costruire un'immagine Docker.
- Esempio di un Dockerfile semplice:
  ```Dockerfile
  FROM ubuntu:20.04           # Immagine di base
  RUN apt-get update          # Aggiorna il sistema
  RUN apt-get install -y curl # Installa curl
  CMD ["echo", "Hello World"] # Comando di default
  ```

---

### **4. Comandi Docker essenziali**
Ecco alcuni comandi di base per lavorare con Docker:

- **docker build**: Crea un'immagine da un Dockerfile.
  ```bash
  docker build -t nome_immagine .
  ```

- **docker run**: Avvia un contenitore da un'immagine.
  ```bash
  docker run nome_immagine
  ```

- **docker ps**: Mostra i contenitori in esecuzione.
  ```bash
  docker ps
  ```

- **docker stop**: Ferma un contenitore.
  ```bash
  docker stop container_id
  ```

- **docker rm**: Rimuove un contenitore.
  ```bash
  docker rm container_id
  ```

- **docker images**: Mostra le immagini disponibili localmente.
  ```bash
  docker images
  ```

- **docker pull**: Scarica un'immagine da un registro Docker.
  ```bash
  docker pull nome_immagine
  ```

- **docker push**: Carica un'immagine su un registro Docker.
  ```bash
  docker push nome_immagine
  ```

---

### **5. Vantaggi di Docker**
- **Portabilità**: Le applicazioni funzionano in modo coerente su qualsiasi ambiente (sviluppo, test, produzione).
- **Isolamento**: Ogni contenitore è isolato dagli altri, riducendo i conflitti tra applicazioni.
- **Efficienza**: I contenitori sono leggeri e avviano rapidamente rispetto alle macchine virtuali.
- **Scalabilità**: È facile scalare applicazioni utilizzando strumenti come Docker Compose o Kubernetes.

---

### **6. Docker Compose**
- **Docker Compose** è uno strumento per definire ed eseguire applicazioni multi-contenitore.
- Utilizza un file YAML (`docker-compose.yml`) per configurare i servizi, le reti e i volumi.
- Esempio di `docker-compose.yml`:
  ```yaml
  version: '3.8'
  services:
    web:
      image: nginx
      ports:
        - "80:80"
    db:
      image: postgres
      environment:
        POSTGRES_PASSWORD: example
  ```

---

### **7. Volumi Docker**
- I **volumi** sono utilizzati per persistire i dati generati dai contenitori.
- I volumi possono essere montati in un contenitore per condividere dati tra il contenitore e il sistema host o tra più contenitori.
- Esempio di utilizzo di un volume:
  ```bash
  docker run -v /path/nel/host:/path/nel/contenitore nome_immagine
  ```

---

### **8. Reti Docker**
- Docker permette di creare reti virtuali per far comunicare i contenitori tra loro.
- Esempio di creazione di una rete:
  ```bash
  docker network create mia_rete
  docker run --network mia_rete nome_immagine
  ```

---

### **9. Docker Hub**
- **Docker Hub** è un registro pubblico dove è possibile trovare e condividere immagini Docker.
- Puoi cercare immagini esistenti (ad esempio, `nginx`, `postgres`, `ubuntu`) o caricare le tue immagini.

---

### **10. Casi d'uso comuni**
- **Sviluppo**: Creare ambienti di sviluppo consistenti per i team.
- **Test**: Eseguire test in ambienti isolati e riproducibili.
- **Produzione**: Distribuire applicazioni in modo scalabile e affidabile.
- **CI/CD**: Integrare Docker in pipeline di Continuous Integration/Continuous Deployment.

---

### **Conclusione**
Docker è uno strumento potente per creare, distribuire ed eseguire applicazioni in modo efficiente e portabile. Con i contenitori, puoi garantire che le applicazioni funzionino in modo coerente su qualsiasi ambiente, dal tuo laptop ai server di produzione.

<Domanda posta a DeeoSeek AI: Che cosa è Docker, dimmi le cose essenziali>

![](../../imgs/02_dati_input/img02.png){.center-img }

![](../../imgs/02_dati_input/sez225dissLotto1.png){.center-img .img-60 }

