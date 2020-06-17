# GruppOne - Stalker

## Come utilizzare questo repository

Per inizializzare tutti i submodule, clonare il repository utilizzando il comando

```bash
git clone --recurse-submodules https://github.com/GruppOne/stalker.git
```

Alcune configurazioni utili per gestire un repository con dei submodule:

- `git config submodule.recurse`: aggiunge la flag `--recurse-submodules` a tutti i comandi che la supportano
- `git config diff.submodule log`: mostra modifiche ai submodule quando viene eseguito `git diff`
- `git config status.submodulesummary true`: mostra stato dei submodule quando viene eseguito `git status`

-->

## Componenti

- L'attuale versione del componente mobile-app è `1.0.0`.
- L'attuale versione del componente server è `1.0.0`.
- L'attuale versione del componente web-app è `1.0.0`.

### Mobile App

La mobile app è sviluppata con IntelliJ IDEA Community 2019.3; richiede che nel sistema sia presente l'Android SDK, che esso sia configurato per la build di applicazioni per Android 9 (API Level 28), e che l'IDE sia configurato per riconoscerlo.

Per l'esecuzione è necessario un dispositivo, fisico (che deve essere configurato per il debugging USB e connesso al computer via USB) oppure virtuale (gestito da AVD, parte dell'Android SDK).

Nel caso dell'esecuzione su dispositivo fisico, è necessario inoltre modificare l'URL del server nel file .env affinché si riferisca al server in esecuzione.

Successivamente, è sufficiente utilizzare i comandi di build o run integrati nell'IDE.

### Server

Il server è sviluppato con IntelliJ IDEA Community 2019.3 utilizzando `JDK 11`, Spring Boot e Spring WebFlux.

Per eseguire l'applicazione in ambiente di sviluppo è sufficiente posizionarsi nella radice del server ed eseguire da terminale `./gradlew bootRun`, o i comandi equivalenti forniti dall'IDE.

I database che utilizziamo sono gestibili attraverso docker-compose (InfluxDB e MySQL).

- Per far partire l'istanza di MySQL, eseguire `docker-compose up [-d] rdb`.
- Per far partire l'istanza di InfluxDB, eseguire `docker-compose up [-d] tsdb`.

### Web App

La web app è sviluppata con l'editor VSCode e il framework Angular 9.

- Posizionarsi da linea di comando nella cartella web-app.
- Eseguire `npm install` per aggiornare le dipende del package.
- Per eseguire una versione locale della web-app scrivere `ng serve --open`.
- Per eseguire i test di unità e ottenere il report della code coverage scrivere `ng test --code-coverage`.
- Per eseguire i test di sistema scrivere `ng e2e`.
- Attualmente sono visitabili i path `/login`, `/organization`, `/editorganization` che implementano i casi d'uso AUC1, AUC3.3 e AUC4 nei sotto-casi 4.1 e 4.3.

È possibile effettuare una build che produce un container production-ready posizionandosi nella cartella web-app e utilizzando il comando `docker build -t "gruppone/stalker-web-app"` e quindi `docker run -it --rm -p 80:80 --name stalker-web-app gruppone/stalker-web-app`.

Il comando `docker-compose up` ha lo stesso effetto.

Il Dockerfile fornito è una build multi-stage che comprende l'esecuzione di test di unità e test e2e e ove abbiano successo, effettua una build ottimizzata per l'ambiente di produzione e copia l'esito della compilazione in un'immagine costruita a partire da `nginx`.

Questo processo di build è eseguito automaticamente e pubblicato su Docker Hub all'indirizzo <https://hub.docker.com/r/gruppone/stalker-web-app> ad ogni merge di PR sul trunk del repository (branch `master`).
