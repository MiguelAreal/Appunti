# Git

**Clone**: download a repository: `git clone <url>`.

**Add**: `git add <filename>`.
Aggiunge filename alla lista di quelli di cui salvare lo stato ad ogni commit.

**Commit**: `git commit -m "<message>"`.
Commit: salvare lo stato corrente di tutti i file e delle cartelle all'interno della repository.
Fino ad ora i vari commit solo salvati solo localmente.

**Stato**: `git status` .
Permette di verificare quante modifiche ai file locali non sono ancora state oggetto di un commit o quanti commit locali non sono salvati nella repository online.

**Push**: `git push`.
I commit locali vengono caricati nella repository sul server. Utile quando la versione della repository locale è più recente di quella sul server.

**Pull**: `git pull`.
Le ultime modifiche alla repository sul server vengono scaricare nella repository locale. Utile quando la versione della repository sul server è più recente di quella locale.

**Merge conflict**: quando due utenti fanno il push di una modifica alle stesse linee di codice. Git ritorna un errore e modifica il file che causa il conflitto aggiungendo dei metadati che indicano la causa del conflitto. Il programmatore decide cosa modificareper risolvere il conflitto ed effettua un nuovo commit. 

**Log**: `git log`.
Mostra tutti i commit alla repository e i relativi dettagli.

**Reset**: `git reset --hard <commithash>`.
Modifica lo stato attuale della repository con uno statato relativo ad un commit precedente.
`git reset --hard origin/master`.
Modifica lo stato attuale della repository locale con quello della repository presente sul server.

**Branching**
Controllare branch esistenti e quello su cui sto lavorando: `git branch` .
Creare nuovo branch: `git checkout -b <newname>`.
Lavorare su un altro branch `git checkout <name>`.
Unire un altro branch a quello corrente `git merge <nome>`.

Per contribuire ad un progetto esistente:
1) Fork repository.
2) Lavorare sulla propria fork della repository.
3) Quando si è pronti per contirbuire al progetto con le modifiche si deve aprire una pull request sulla pagina del progetto.
4) Se le modifiche sono approvate da chi gestisce il progetto, il pull viene approvato.