---
type: concetto
definizione: 
correlati: []
discipline: []
created: 2026-07-29
---


## Fonti che lo trattano

```dataview
TABLE autori as "Autore", anno as "Anno", status as "Stato"
FROM "01-Fonti"
WHERE contains(concetti, [[linguaggio]])
SORT anno DESC
```