---
type: fonte
autori: "[[{{authors}}]]"
anno: "{{date}}"
zotero-key: "{{key}}"
citekey: "{{citekey}}"
discipline:
type-doc: "{{itemType}}"
pages: "{{numPages}}"
stato: da-leggere
created: "{{date}}"
---
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