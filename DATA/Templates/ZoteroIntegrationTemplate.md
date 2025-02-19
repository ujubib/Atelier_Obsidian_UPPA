---
aliases: {{citekey}}
publisher: "{{publicationTitle}}"
url: {{url}}
doi: {{DOI}}
tags: [literature-note, zotero, {{publicationTitle | replace(" ", "-")}}, {% for t in tags %}{{t.tag}}{% if not loop.last %}, {% endif %}{% endfor %}]
---

# {{title}}

> [!abstract]- 
> {% if abstractNote %} 
> {{abstractNote|replace("\n"," ")}}
> {% endif %}

---
---
## Index:
### Metadata
> [!meta]- Metadata – {% for attachment in attachments | filterby("path", "endswith", ".pdf") %}[PDF{% if not loop.first %} {{loop.index}}{% endif %}]({{attachment.desktopURI|replace("/select/", "/open-pdf/")}}){% if not loop.last %}, {% endif %}{% endfor %}
> **Title**:: {{title}}  
> **Authors**:: {%- for creator in creators %} {%- if creator.name == null %} {{creator.firstName}} {{creator.lastName}}, {%- endif -%} {%- if creator.name %}**{{creator.creatorType | capitalize}}**:: {{creator.name}}{%- endif -%}{%- endfor %}
> **Year**:: {{date | format("YYYY")}} 
> {%- if itemType %}**ItemType**:: {{itemType}}{%- endif %}  
> {%- if itemType == "journalArticle" %}**Journal**:: *{{publicationTitle}}* {%- endif %} {%- if itemType == "bookSection" %}**Book**:: {{publicationTitle}} {%- endif %}
> {% if hashTags %}**Keywords**:: {{hashTags}}{% endif %}
> **Related**:: {% for relation in relations -%} {%- if relation.citekey -%} [[{{relation.citekey}}]], {% endif -%} {%- endfor%}

---
---
{% persist "notes" %}{% if isFirstImport %}

## Main ideas:
- 
## Methodology:
- 
## Results:
- 
## Key points:
- 
{% endif %}{% endpersist %}
## Reading notes
{% persist "annotations" %}
{%-
    set zoteroColors = {
        "#ff6666": "red",
        "#f19837": "orange",
        "#5fb236": "green",
        "#ffd400": "yellow",
        "#2ea8e5": "blue",
        "#a28ae5": "purple",
        "#e56eee": "magenta",
        "#aaaaaa": "grey"
    }
-%}

{%-
   set colorHeading = {
		"red": "⭕ Very important or questionable",
		"orange": "⭐ Important or interesting",
		"green": "✅ Major statements",
		"yellow": "📚 Ordinary notes",
        "blue": "🔗 Interesting references",
        "purple": "🧩 Methodology",
        "other": "Misc"
   }
-%}

{%- macro calloutHeader(type) -%}
    {%- switch type -%}
        {%- case "highlight" -%}
        Highlight
        {%- case "image" -%}
        Image
        {%- default -%}
        Note
    {%- endswitch -%}
{%- endmacro %}

{%- set newAnnot = [] -%}
{%- set newAnnotations = [] -%}
{%- set annotations = annotations | filterby("date", "dateafter", lastImportDate) %}

{% if annotations.length > 0 %}
*Imported: {{importDate | format("YYYY-MM-DD HH:mm")}}*

{%- for annot in annotations -%}

    {%- if annot.color in zoteroColors -%}
        {%- set customColor = zoteroColors[annot.color] -%}
    {%- elif annot.colorCategory|lower in colorHeading -%}
    	{%- set customColor = annot.colorCategory|lower -%}
    {%- else -%}
	    {%- set customColor = "other" -%}
    {%- endif -%}

    {%- set newAnnotations = (newAnnotations.push({"annotation": annot, "customColor": customColor}), newAnnotations) -%}

{%- endfor -%}

{#- INSERT ANNOTATIONS -#}
{#- Loops through each of the available colors and only inserts matching annotations -#}
{#- This is a workaround for inserting categories in a predefined order (instead of using groupby & the order in which they appear in the PDF) -#}

{%- for color, heading in colorHeading -%}
{%- for entry in newAnnotations | filterby ("customColor", "startswith", color) -%}
{%- set annot = entry.annotation -%}

{%- if entry and loop.first %}

### {{colorHeading[color]}}
{%- endif %}

> [!quote{{"|" + color if color != "other"}}]+ {{calloutHeader(annot.type)}} ([page. {{annot.pageLabel}}](zotero://open-pdf/library/items/{{annot.attachment.itemKey}}?page={{annot.pageLabel}}&annotation={{annot.id}}))

{%- if annot.annotatedText %}
> {{annot.annotatedText|nl2br}} {% if annot.hashTags %}{{annot.hashTags}}{% endif -%}
{%- endif %}

{%- if annot.imageRelativePath %}
> ![[{{annot.imageRelativePath}}]]
{%- endif %}

{%- if annot.ocrText %}
> {{annot.ocrText}}
{%- endif %}

{%- if annot.comment %}
> - **{{annot.comment|nl2br}}**
{%- endif -%}

{%- endfor -%}
{%- endfor -%}
{% endif %}
{% endpersist -%}