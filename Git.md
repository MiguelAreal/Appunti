# Git

**Configurazione**:  
`git config --global user.name “Nome Cognome"`  
`git config --global user.email “email@domain.comt”`  
`git config --global credential.helper 'cache --timeout 3600'`: Salva le credenziali per 1 ora.

**Creazione**:  
`git init`: Crea nuova repository.  


**Clone**:   
`git clone <url>`: Download a repository.  


**Pull**: `git pull`.  
Le ultime modifiche alla repository sul server vengono scaricare nella repository locale. Utile quando la versione della repository sul server è più recente di quella locale.  


**Add**:
Impostare un file come "staged" ovvero che sarà salvato al prossimo commit.  
`git add -A`: Impostare tutti i file come "staged".  
`git add <filename>`: Impostare singolo file come "staged".  
`git add -u`: Aggiunge allo stage tutti i file modificati che erano già tracciati (cioè aggiunti in precedenza).  


**Commit**: `git commit -m "<message>"`.  
Commit: salvare lo stato corrente di tutti i file e delle cartelle all'interno della repository.  
`git commit --amend`: Permette di aggiungere qualcosa all’ultimo commit e rieditare il messaggio.  


**Push**: `git push`.  
I commit locali vengono caricati nella repository sul server. Utile quando la versione della repository locale è più recente di quella sul server.  


**Stato**: `git status` .  
Permette di verificare quante modifiche ai file locali non sono ancora state oggetto di un commit o quanti commit locali non sono salvati nella repository online.  


**Log**: `git log`.  
Mostra tutti i commit alla repository e i relativi dettagli.  
`git log -N --pretty=oneline`: Mostra lo storico degli ultimi N commit eseguiti mostrandoli in maniera compatta.  



**Checkout**: Spostarsi su un altro branch o su un determinato commit.  
`git checkout <commitid>`  
`git checkout <branchname>`  
`git checkout HEAD^`: Spostarsi sul commit precedente.  
`git checkout -b <newbranch> <oldbranch>`: Creare un nuovo branch e spostarsi sul branch appena creato.  


**Branch**:  
'git branch`: Controllare branch esistenti e quello su cui si sta lavorando.  
'git checkout -b <newbranch>`: Creare nuovo branch.  
`git checkout -b <newbranch> <oldbranch>`: Creare nuovo branch a partire da uno già esistente.  


**Merge**: Unire due branch.  
`git merge <branchname>`: Unire un altro branch a quello corrente.  
`git merge <commitid>`: Unisce il branch del commit id al branch corrente.  


**Delete branch**: Eliminare un determinato branch.  
`git branch -d <branchname>`  


**Remove file**:  
`git rm <filename>`: Cancella un file dal sistema di versionamento E DAL DISCO.  
`git rm --cached <filename>`: Cancella un file dal sistema di versionamento ma NON dal disco.  


**Merge conflict**: quando due utenti fanno il push di una modifica alle stesse linee di codice. Git ritorna un errore e modifica il file che causa il conflitto aggiungendo dei metadati che indicano la causa del conflitto. Il programmatore decide cosa modificare per risolvere il conflitto ed effettua un nuovo commit e un nuovo push.  


**Reset**: 
`git reset --hard <commithash>`: Modifica lo stato attuale della repository con uno statato relativo ad un commit precedente.  
`git reset --soft HEAD^`: Annulla l’ultimo commit riportando i file nell’area di stage.  
`git reset`: Svuota lo stage (git add).  


**Diff**: 
`git diff <branch1> <branch2>`: Mostra differenze tra due branch  


**Fetch**: 
`git fetch`: Controlla se sul server ci sono nuovi aggiornamenti. Se ce ne sono, NON li scarica, bisogna usare git pull  


**Add remote**: 
`git remote add origin <url_repository>`: Se abbiamo già un repository locale e vogliamo collegarlo ad un repository remoto.  
