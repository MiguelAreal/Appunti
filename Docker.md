Creazione Image
Creare un file chiamato Dockerfile
….

Build Image
Mi posiziono nella cartella contenente il Dockerfile
docker build .
Restituisce image_id

Lancio Image
docker run image_id
Se nel Dockerfile apro una porta: docker run -p 55000:55000 image_id
Stop Image




Images: template per un container. Contiene codice, librerie, tools, runtimes. Da una singola immagine si possono creare molti container.
Container: applicativo in esecuzione. Istanza di un Image.

Docker Hub: repository di Images

Creare container da images esistenti:
Creare container: docker run image_id. Se non trova Image in locale, la cerca su Docker Hub.


Creare custom image:
Creare file Dockerfile con istruzioni da eseguire durante Build
FROM baseimage #(su Docker Hub o in locale)
WORKDIR /app
COPY local_folder container_folder
[COPY . .] aggiunge files della cartella in cui si trova l'immagine alla workdir (root/app) del filesystem del container.
RUN command (eseguito quando viene fatto build dell'image)
EXPOSE port
CMD ["command"](eseguito quando viene avviato il container)

Nota: ogni comando nel Dockerfile crea un layer. Se un layer viene modificato rispetto ad una precedente build, la nuova build esegue il comando per creare quel layer e tutti i comandi successivi.
Esempio:
```
FROM node
WORKDIR /app
COPY . ./app
RUN npm install
EXPOSE 80
CMD ["node". " server.js"]
```


- Guida: `--help:`

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

## Note
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

## Note
- Si possono eliminare solo le images che non sono usate da nessun container. Il container deve essere eliminato, non deve essere nè avviato, nè in stop.
- Dopo ogni modifica al codice bisogna fare il build image, le images sono read-only, ad ogni build si crea una nuova image.
- Tag: si usa per specializzare una versione di una image. Usato ad esempio per specificare versione, configurazione.
- Nei comandi `image_id` può essere sostituito con `name:tag`.
