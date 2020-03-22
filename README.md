# GruppOne - Stalker

Per inizializzare tutti i submodule, clonare il repository utilizzando il comando

```bash
git clone --recurse-submodules https://github.com/GruppOne/stalker.git
```

Alcune configurazioni utili per gestire un repository con dei submodule:

- `git config submodule.recurse`: aggiunge la flag `--recurse-submodules` a tutti i comandi che la supportano
- `git config diff.submodule log`: mostra modifiche ai submodule quando viene eseguito `git diff`
- `git config status.submodulesummary true`: mostra stato dei submodule quando viene eseguito `git status`
