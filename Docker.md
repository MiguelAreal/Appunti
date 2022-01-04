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


