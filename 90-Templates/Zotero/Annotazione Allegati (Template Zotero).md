---
type: fonte
autori: "[[{{authors}}]]"
anno: "{% if parsedDate %}{{parsedDate.year}}{% else %}{{date}}{% endif %}"
zotero-key: "{{key}}"
citekey: "{{citekey}}"
zotero-link: "{{select}}"
discipline:
type-doc: "{{itemType}}"
pages: "{{pages}}"
stato: da-leggere
---

{%- if pages and '-' in pages -%}
	{%- set pgArray = pages.split('-') -%} 
	{%- set totalPg = (pgArray[1] | int) - (pgArray[0] | int) + 1 -%}
**Pagine:** {{pages}} (tot. {{totalPg}} pagine) 
{%- elif pages -%} 
**Pagine:** {{pages}} 
{%- endif %}

### 🏷️ Concetti  
{% for tag in tags -%} 
* [[02-Concetti/{{tag.tag}}]] 
{% endfor %}

# {{title}}

> [!meta]- Metadata
> - Abstract: {{abstractNote}}
> - Zotero PDF Link: {{pdfZoteroLink}}
> - URL: {{url}}
> - Bibliography: {{bibliography}}

  
  

## Note

{% persist "notes" %}{% if isFirstImport %}


{% endif %}

{% endpersist %}

  
  

## Annotazioni 

{%- for attachment in attachments %} 

{%- if attachment.annotations and attachment.annotations.length > 0 %}

---


### 📄 {{ attachment.title }}

{%- endif %} 

{% for annotation in attachment.annotations -%} 

{%- if annotation.annotatedText %} 

{%- set emojiMap = { 
	"yellow": "🟨", 
	"green": "🟩", 
	"blue": "🟦", 
	"pink": "🟥", 
	"red": "🟥", 
	"purple": "🟪", 
	"orange": "🟧", 
	"gray": "⬛" 
} -%} 

{%- set colorCategory = annotation.colorCategory | lower if annotation.colorCategory else "yellow" -%} 
{%- set colorEmoji = emojiMap[colorCategory] or "🟨" -%} 

{{ colorEmoji }} “{{ annotation.annotatedText | safe }}” [Pagina {{ annotation.pageLabel }}](zotero://open-pdf/library/items/{{ attachment.itemKey }}?page={{ annotation.pageLabel }}&annotation={{ annotation.id }}) {%- endif -%} 

{%- if annotation.comment %} 
💬 **Commento:** {{ annotation.comment | safe }} 
{%- endif -%} 

{%- if annotation.imageRelativePath %} ![[{{ annotation.imageRelativePath }}]] 👉 [Pagina {{ annotation.pageLabel }}](zotero://open-pdf/library/items/{{ attachment.itemKey }}?page={{ annotation.pageLabel }}&annotation={{ annotation.id }}) {%- endif -%} 

{%- if annotation.allTags %} 
🏷️ **Tag:** {{ annotation.allTags }} 

{%- endif %} 
{% endfor -%} 
{% endfor -%}