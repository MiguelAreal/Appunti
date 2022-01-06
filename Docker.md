# Appunti Docker
- Images: template per un container. Contiene codice, librerie, tools, runtimes. Da una singola immagine si possono creare molti container.
- Container: applicativo in esecuzione. Istanza di un Image.
- Docker Hub: repository di Images.
## Dockerfile
Usato per creare custom image. SI tratta di creare un file chiamato Dockerfile con le istruzioni da eseguire durante una build.
```
FROM baseimage #definisce un immagine di partenza
WORKDIR /app #definisce la directory di lavoro nel container
COPY local_folder container_folder #definisce quali file copiare sul container e la loro posizione
#COPY . . aggiunge files della cartella in cui si trova l'immagine alla workdir (root/app) del filesystem del container.
RUN command #eseguito quando viene fatto build dell'image
EXPOSE port #notazione per esplicitare porte che si usano
CMD ["command"] #eseguito quando viene avviato il container
```
### Esempio
```
FROM node
WORKDIR /app
COPY . ./app
RUN npm install
EXPOSE 80
CMD ["node". " server.js"]
```
### Note
- Ogni comando nel Dockerfile crea un layer. Se un layer viene modificato rispetto ad una precedente build, la nuova build esegue il comando per creare quel layer e tutti i comandi successivi.

## Containers
### Attached/Detached
- Attached mode: permette di vedere la console in output del container (default per `docker run`)
- Detached mode: il container viene eseguito in background (default per `docker start`)
### Commands
- Lista container: `docker ps`
  - Flags:
    - `-a` mostra anche i container in stop
- Creazione: `docker run imageId`
  - Flags:
    - `-p local_port:container_port` Binding tra porta host e porta container
    - `-d` Avvio in detached mode
    - `-it` Espone shell del container (interactive mode)
    - `--rm` Elimina in automatico il container quando va in stop
    - `--name custom_name` Assegna un nome
    - `-v /path/on/container` Crea anonymous volume
    - `-v volume_name:/path/on/container` Crea named volume
    - `-v /path/on/host:/path/on/container` Crea bind mount
    - `-e VAR_NAME=value` Imposta valore della variabile VAR_NAME
    - `--nework network_name` Aggiunge container ad una rete
- Passare in attache mode: `docker attach container_name`
- Visualizzare logs: `docker logs container_name`
  - Flags:
    - `-f` Passa anche ad attached mode per vedere log futuri
- Avvio container spento: `docker start container_name`
  - Flags:
    - `-a` Avvio in attached mode
    - `-a -i` Espone shell del container (attached and interactive mode)
- Stop container: `docker stop container_name`
- Eliminare container: `docker rm container_name1 container_name2 ...`
- Copiare files: `docker cp source destination`
  - Esempio da host a container: `docker cp source/path/file container_name:/dest/path`
  - Esempio da container a host: `docker cp container_name:source/path/file /dest/path`

### Note
- Se il programma in un container finisce, il container va in stop
- Nei comandi `container_name` può essere sostituito con `container_id`
- Prima di eliminare un container, questo va fermato

## Images
### Commands
- Build image: `docker build /path/to/image`
  - Flags:
    - `-t name:tag` Assegna nome e tag
- Lista images: `docker images`
- Analizzare image: `docker image inspect image_id`
- Eliminare image: `docker rmi image_id image_id2 ...`
- Eliminare images non usate: `docker image prune`
  - Flags:
    - `-a' Elimina anche images con tag
- Condividere image: `docker push image_name`
- Download image: `docker pull image_name`

### Note
- Si possono eliminare solo le images che non sono usate da nessun container. Il container deve essere eliminato, non deve essere nè avviato, nè in stop.
- Dopo ogni modifica al codice bisogna fare il build image, le images sono read-only, ad ogni build si crea una nuova image.
- Tag: si usa per specializzare una versione di una image. Usato ad esempio per specificare versione, configurazione.
- Nei comandi `image_id` può essere sostituito con `name:tag`.
- Il comando `docker run image_name` cerca l'immagine in locale e se non la trova, la cerca su Docker Hub. Se la versione su Docker Hub viene aggiornata successivamente al comando run, non verrà aggiornata la versione locale. È necessario lanciare `docker pull image_name` per aggiornarla e successivamente fare il run.

## Data
Il codice e l'ambiente necessario all'applicazione vengono caricati nel container al momento del build come specificato nel Dockerfile. Questi files sono read-only, vengono caricati durante la build e non possono essere cambiati successivamente. Sono dati memorizzati nell'image.

I file temporanei necessari all'applicazione sono memorizzati separatamente, possono essere creati e riscritti durante l'esecuzione e vengono eliminati quando il container viene fermato. Sono dati memorizzati nel container.

I file permanenti che vengono creati e modificati dall'applicazione sono memorizzati nel cotainer e copiati in un volume per resistere al riavvio o all'eliminazione di un container. 

### Volumes

- Volumes (gestiti da Docker)
  - Anonymous: sono eliminati quando un container viene eliminato. Rimangono disponibili in caso di riavvio. Non sono accessibili da host. Il volume è strettamente collegato al container. Non possono essere condivisi nè tra host e container nè tra container diversi.
  - Named: sono persistenti e non accessibili da host. Rimangono disponibili anche in caso di eliminazione del container. Sono usati per file che devono essere persistenti ma che non vanno modificati direttamente da host. Il volume non è associato ad un container. È possibile condividere il volume tra più container.
- Bind Mounts (gestiti da User)
  - Sono creati a partire da una cartella presente nel file system dell'host che viene montata su un container. Il contenuto della cartella è perennemente sincronizzato tra il container e l'host. Se il container viene fermato o eliminato, i dati nel volume rimangono inalterati. Il container ha diritti di lettura e scrittura sul volume. È possibile condividere il volume tra più container.

#### Creation
**Anonymous volume:**

Nel Dockerfile: `VOLUME ["/path/on/container"]`

Oppure come comando: `docker run ... -v /path/on/container`

**Named volume:**

`docker run ... -v volume_name:/path/on/container`

**Bind Mount:**

`docker run ... -v /path/on/host:/path2/on/container`

Note: 
- Docker deve avere permessi di lettura e scrittura sulla cartella host che viene condivisa.
- Se i file nella cartella host sono già presenti nella cartella del contianer, Docker non li sovrascrive ma la cartella host sovrascrive la cartella nel container.
- Se nel comando run vengono specificati volumi con la stessa radice, la regola che riguarda il path più lungo sovrascrive quella che ha un path più corto.
- Per rendere un volume readonly basta aggiungere `:ro` alla fine del path relativo al container. Ad esempio: `-v /path/on/host:/path2/on/container:ro`
- I bind mount non sono gestiti da Docker ma dal filesystem dell'host. Non possono essere eliminati da Docker.
- È possibile creare un file `.dockerignore` in cui inserire file e cartelle che devono essere ignorati da Docker.
### Commands
Lista volumi: `docker volume ls`
Dettagli volume: `docker volume inspect volume_name`
Rimuovere volume: `docker volume rm volume_name`
Rimuovere tutti volumi inutilizzati: `docker volume prune`

# ARGuments & ENViroment Variables

- Env (run-time): inserire variabili nel Dockerfile e nel codice dell'applicazione in base a `--env` durante il run del container.
  - Nel codice si inserisce `process.env.VAR_NAME`
  - Nel Dockerfile imposto la variabile con il comando `ENV VAR_NAME value`
  - Nel Dockerfile posso utilizzare la variabile richiamandola con `$VAR_NAME`
  - Se nel comando run non specifico niente, il valore della variabile rimane quello assegnato nel Dockerfile, in alternativa posso sovrascrivere il valore durante il run con: `docker run ... -e VAR_NAME=value`
  - In alternativa posso creare un file .env in cui settare i valori delle variabili elencando `VAR_NAME=VALUE`. Durante il run specifico di usare il file .env con `docker run ... --env-file /path/to/.env`

- Arg (build-time): inserire variabili nel Dockerfile in base a `--build-arg` durante il buiLd dell'image.
  - Nel Dockerfile imposto l'arg con il comando `ARG ARG_NAME=value`
  - Gli args non possono essere usati nel codice dell'app, sono utilizzabili solo nel Dockerfile (escluso command)
  - Nel Dockerfile posso utilizzare la variabile richiamandola con `$ARG_NAME`
  - Se nel comando build non specifico niente, il valore dell'arg rimane quello assegnato nel Dockerfile, in alternativa posso sovrascrivere il valore durante il build con: `docker build ... --build-arg ARG_NAME=value`

# Networking

### Connessione da container a www
Es: App nel container chiama API sul web.

La funzione è supportata di default.
### Connessione da container a servizio su host
Es: App nel container si connette al DB che risiede su host.

Non servono comandi particolari o direttive nel Dockerfile. Nel codice dell'applicazione del container ci si connette all'host inserendo come indirizzo base `host.docker.internal`. Il codice host.docker.internal viene tradotto da Docker nell'indirizzo di rete dell'host.

Es:`http://host.docker.internal:21017/link`. 
### Connessione da container a servizio su altro container
Es: App nel container si connette al DB che risiede in un altro container.

Soluzione 1:
1. Ottengo IP del container a cui connettersi analizzando `docker container inspect container_name`
2. Inserisco IP ottenuto nel codice dell'app in altro container.

Soluzione 2 (best): usare Container Networks

## Container Networks
È possibile inserire uno o più container in una rete docker con `docker run ... --nework network_name`. Il network non viene creato automaticamente, va creato a priori.

1. Creazione network: `docker network create network_name`
2. Nel codice dell'applicazione, ci si connette ad un container inserendo come indirizzo base `container_name`. Esempio:`http://container_name:21017/link`. Funziona solo se i due container sono nello stesso network. 
3. Avvio container: `docker run ... --nework network_name`

Note: 
- Quando si avviano container che devono comunicare nello stesso network, non serve il flag `-p port:port`, il flag serve solo quando il container deve fornire servizi verso l'host.
- Docker non sostituisce gli indirizzi ip direttamente nel codice. Docker individua le richieste che entrano ed escono dal container e fa la rsoluzione dell'indirizzo ip corretto a cui inoltrare la richiesta. Se la richiesta non deve uscire dal container o se la richiesta arriva da javascript, docker non effettua la risoluzione dell'ip corretto.

Lista Docker Newtorks: `docker network ls`

# Docker Compose
Usato per raggruppare diversi comandi di Docker (run e build) in un unico file di configurazione. Utile per automatizzare il setup di app multi-container.
Non rimpiazza i Dockerfile e non si può usare per gestire più containers installati su host diversi.

### Creazione
Creazione file `docker-compose.yaml`

`version`: Versione Docker Compose
`services: Lista di containe
`image`: Image di base (es: Alpine, Python, ...)
`volumes:` Lista di volumi. Per ogni volume si aggiunge un `-` e si definisce la notazione standard.
`enviroment:` Lista di variabili env con notazione `- NOME_ENV=value`.
`env_file:` Lista di file che contengono variabili env. 
`networks:` Lista di network a cui collegare il container. Opzionale, vedi note.

### Avvio:
Ci si posiziona nella cartella contenente il file .yaml.
`docker-compose up`: fa pull, build e run di images e containers specificati nel file.
Flags:
- `-d`: Avvio in detach mode.

### Stop:
`docker-compose down`: ferma ed elimina tutti i container. Non elimina i volumi.
Flags:
- `-v`: Elimina anche i volumi.

### Esempi:
Esempio 1:
```yaml
version: "3.8"
services:
  container1_name:
    image: 'base_image'
    volumes:
      - volume_name:/path/inside/container
      - volume_name2:/path2/inside/container:ro
    enviroment:
      - NOME_ENV=value
    env_file:
      - ./relative/path/to/env/file.env
    networks:
      - net-name
  container2_name:
  container3_name:

#solo per named volumes, vedi note
volumes:
  volume_name:
```

Esempio 2:
```yaml
version: "3.8"
services:
  mongodb:
    image: 'mongo'
    volumes:
      - data:/data/db
    enviroment:
      MONGO_INITDB_ROOT_USERNAME: max
      MONGO_INITDB_ROOT_PASSWORD: secret
      #- MONGO_INITDB_ROOT_USERNAME=max
      #- MONGO_INITDB_ROOT_PASSWORD=secret
    env_file:
      -./env/mongo.env
  backend:
  frontend:
```
Note: 
- Nei file yaml viene considerata l'indentazione.
- Di default i container sono avviati in detach mode e con flag rm (eliminati quando si fermano).
- Tutti i container creati da compose sono inseriti in un solo network creato automaticamente.
- Per i named volumes, dopo averli dichiarati dentro al giusto service, vanno anche dichiarati separatamente senza identazione alla fine del file yaml. Questa cosa non vale per gli anonymous volumes e per i bind mounts.
