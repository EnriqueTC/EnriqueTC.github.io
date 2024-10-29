---
layout: page
title: Recetas

recieps-dir: recetas
---

{%- assign default_paths = site.pages | map: "path" -%}
{%- assign page_paths = site.header_pages | default: default_paths -%}
{%- assign titles_size = site.pages | map: 'title' | join: '' | size -%}

{%- if titles_size > 0 -%}

<table id="example" class="display" style="width:100%">
    <thead>
        <tr>
            <th>Tipo</th>
            <th>Plato</th>
            <th>Tiempo</th>
            <th>Personas/Cantidad</th>
            <th>Puntuación</th>
        </tr>
    </thead>
    <tbody>
        
        {%- for path in page_paths -%}
            {%- assign my_page = site.pages | where: "path", path | first -%}
            {%- if my_page.tags and my_page.tags.recipe -%}
                {%- if my_page.title -%}
                    <tr>
                        <td><p class="{{my_page.tags.type}}-table">.</p></td>
                        <td><a class="page-link" href="{{ my_page.url | relative_url }}">{{ my_page.title | escape }}</a></td>
                        <td>{{ my_page.tags.time | escape }}</td>
                        <td>{{ my_page.tags.people-quantity | escape }}</td>
                        <td>{{ my_page.tags.punctuation | escape }}</td>
                    </tr>
                {%- endif -%}
            {%- endif -%}
        {%- endfor -%}
        
    </tbody>
    <tfoot>
        <tr>
            <th>Tipo</th>
            <th>Plato</th>
            <th>Tiempo</th>
            <th>Personas/Cantidad</th>
            <th>Puntuación</th>
        </tr>
    </tfoot>
</table>

{%- endif -%}


<div class="recipe-information">
    <div><p class="Aderezo">{{ site.aderezo }}</p></div>
    <div><p class="Principal">{{ site.principal }}</p></div>
    <div><p class="Acompanamiento">{{ site.acompanamiento }}</p></div>
    <div><p class="Postre">{{ site.postre }}</p></div>
    <div><p class="Bebida">{{ site.bebida }}</p></div>
    <div><p class="Desayuno">{{ site.desayuno }}</p></div>
</div>