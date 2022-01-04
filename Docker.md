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
Flag -it: espone shell dal container.

Creare custom image:
Creare file Dockerfile con istruzioni da eseguire durante Build
FROM baseimage #(su Docker Hub o in locale)
WORKDIR /app
COPY local_folder container_folder
[COPY . .] aggiunge files della cartella in cui si trova l'immagine alla workdir (root/app) del filesystem del container.
RUN command (eseguito quando viene fatto build dell'image)
EXPOSE port
CMD ["command"](eseguito quando viene avviato il container)

Esempio:
```
FROM node
WORKDIR /app
COPY . ./app
RUN npm install
EXPOSE 80
CMD ["node". " server.js"]
```
Build Image: `docker build /path/to/image`
Ritorna ImageID
Creazione container: `docker run ImageID`
Flag -p local_port:container_port


Dopo ogni modifica al codice bisogna fare il build image, le images sono read-only, ad ogni build si crea una nuova image. 

- Guida: `--help:`

## Containers
### Attached/Detached
- Attached mode: permette di interagire con il container, vedere la console (default per `docker run`)
- Detached mode: il container viene eseguito in background (default per `docker start`)
### Commands
- Lista container: `docker ps`
  - Flags:
    - `-a` mostra cronologia
- Creazione container: `docker run ImageID`
  - Flags:
    - `-p local_port:container_port` Binding tra porta host e porta container
    - `-d` Avvio in detached mode
- Attach ad un container: `docker attach container_name`
- Visualizzare logs di un container  `docker logs container_name`
  - Flags:
    - `-f` Passa ad attached mode per vedere log futuri
- Avvio container spento: `docker start container_name`
  - Flags:
    - `-a` Avvio in attached mode
- Stop container: `docker stop container_name`
