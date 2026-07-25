## Panoramica


## Concetti collegati


## Fonti principali

```dataview
TABLE autori as "Autore", anno as "Anno", status as "Stato"
FROM "01-Fonti"
WHERE contains(discipline, "robotics") OR contains(discipline, "cognitive-robotics") OR contains(concetti, [[Umwelt]])
SORT anno DESC
```

## Domande aperte da esplorare