---
type: persona
ruolo: 
affiliazione: 
concetti: []
created: <% tp.date.now("YYYY-MM-DD") %>
---

# <% tp.file.title %>

## Note

## Opere rilevanti

```dataview
TABLE anno as "Anno", status as "Stato"
FROM "01-Fonti"
WHERE contains(autori, [[<% tp.file.title %>]])
SORT anno DESC
```