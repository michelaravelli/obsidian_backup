---
type: concetto
definizione: 
correlati: []
discipline: []
created: <% tp.date.now("YYYY-MM-DD") %>
---


## Fonti che lo trattano

```dataview
TABLE autori as "Autore", anno as "Anno", status as "Stato"
FROM "01-Fonti"
WHERE contains(concetti, [[<% tp.file.title %>]])
SORT anno DESC
```