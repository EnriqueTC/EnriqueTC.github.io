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
            <th>Plato</th>
            <th>Tipo</th>
            <th>Tiempo</th>
            <th>Personas/Cantidad</th>
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
                    </tr>
                {%- endif -%}
            {%- endif -%}
        {%- endfor -%}
        
    </tbody>
    <tfoot>
        <tr>
            <th>Plato</th>
            <th>Tipo</th>
            <th>Tiempo</th>
            <th>Personas/Cantidad</th>
        </tr>
    </tfoot>
</table>

{%- endif -%}


<div class="recipe-information">
    <div><p class="aderezo">{{ site.aderezo }}</p></div>
    <div><p class="principal">{{ site.principal }}</p></div>
    <div><p class="acompanamiento">{{ site.acompanamiento }}</p></div>
    <div><p class="postre">{{ site.postre }}</p></div>
    <div><p class="bebida">{{ site.bebida }}</p></div>
</div>