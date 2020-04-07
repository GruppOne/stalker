# GruppOne - Stalker

<!-- TODO scrivere versione di prodotto (è la STESSA della documentazione) -->
<!-- L'attuale versione del prodotto stalker è `` -->

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

- L'attuale versione del componente mobile-app è `0.5.2`.
- L'attuale versione del componente server è `0.3.0`.
- L'attuale versione del componente web-app è `0.6.0`.

### Mobile App

- Posizionarsi da linea di comando nella cartella web-app
- eseguire `npm install` per aggiornare le dipende del package
- per eseguire una versione locale della web-app scrivere `ng serve -o`
- per eseguire i test di unità e ottenere il report della code coverage scrivere `ng test --code-coverage`
- per eseguire i test di sistema scrivere `ng e2e`
- attualmente sono visitabili i path `/login`, `/organization`, `/editorganization` che implementano i casi d'uso AUC1, AUC3.3 e AUC4 nei sottocasi 4.1 e 4.3

### Server

Posizionarsi nella radice del server ed eseguire `./gradlew bootRun`. Gli endpoint definiti sono disponibili agli indirizzi:

- localhost:11111/version
- localhost:11111/organizations
- localhost:11111/organizations/{id} (1 e 2 ritornano OK)

### Web App

<!-- TODO scrivere come si avvia e come si testa Web App -->
