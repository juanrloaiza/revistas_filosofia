---
title: Revistas de filosofía en español
layout: default
---

<table class="table" id="theTable">
<thead>
  <th>Nombre</th>
  <th>País</th>
  <th>Universidad</th>
  <th>Índices</th>
  <th>Mejor cuartil</th>
</thead>

<tbody>
{% assign revistas = site.data.revistas | sort: 'nombre' %}
{% for revista in revistas %}
<tr>
  <td><a href='{{ revista.web }}'>{{ revista.nombre }}
  {% for item in revista.indices %}
  {% if 'DOAJ' == item or 'ROAD' == item %}
  <img src="https://upload.wikimedia.org/wikipedia/commons/2/25/Open_Access_logo_PLoS_white.svg" width="12px" style="margin-left: 6px">
  {% endif %}
  {% endfor %}
  </a></td>
  <td>{{ revista.pais }}</td>
  <td>{{ revista.universidad }}</td>
  <td>
    <ul>
    {% assign indices = revista.indices | sort %}
    {% for indice in indices %}
      <li>{{ indice }}</li>
    {% endfor %}
    </ul>
  </td>
  <td>
  {% if revista.cuartil %}
  Q{{ revista.cuartil }}
  {% else %}
  --
  {% endif%}

  </td>
</tr>
{% endfor %}
</tbody>

</table>
