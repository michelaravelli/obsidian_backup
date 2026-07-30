# GitHub Sync - Regole Obsidian Vault

## Struttura del sistema

Il vault è sincronizzato tramite GitHub.

Flusso:

Computer A → GitHub → Computer B

Ogni computer possiede una copia locale del vault.  
Le modifiche devono essere caricate su GitHub e poi scaricate sull'altro computer.

---

# Quando lavoro su un computer

## Prima di iniziare

Se ho lavorato su un altro computer:

1. Aprire Obsidian.
2. Eseguire:

`Obsidian Git → Pull`

oppure aspettare il pull automatico.

Questo scarica le ultime modifiche da GitHub.

---

## Durante il lavoro

Lavorare normalmente su Obsidian.

Creare/modificare:
- note
- cartelle
- template
- file Markdown

---

## Quando termino il lavoro

Inviare le modifiche a GitHub:

1. Eseguire:

`Obsidian Git → Commit all changes`

2. Eseguire:

`Obsidian Git → Push`

Dopo il push le modifiche sono disponibili sugli altri computer.

---

# Quando cambio computer

Prima di modificare qualsiasi cosa:

1. Aprire Obsidian.
2. Fare:

`Obsidian Git → Pull`

Solo dopo iniziare a lavorare.

---

# Regola fondamentale

NON lavorare contemporaneamente su due computer senza sincronizzare.

Procedura corretta:

Computer 1:  Lavoro → commit → Push

Computer 2. Pull → Lavoro → Commit → Push


# Cartelle vuote

Git NON salva cartelle vuote.

Se creo una nuova cartella e voglio che venga sincronizzata:

- inserire almeno un file dentro;
- fare commit + push.

---

# In caso di problemi

Controllare lo stato di Git:
```

git status

```

Se ci sono file non sincronizzati:
```

git add .  
git commit -m "descrizione modifica"  
git push

```

Per scaricare modifiche:
```

git pull

```

---

# Backup

GitHub è il backup remoto del vault.

Il vault locale rimane la copia di lavoro principale.

Prima di grandi modifiche:
- fare sempre un commit;
- verificare che il push sia completato.