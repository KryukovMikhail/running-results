---
layout: home
title: Результаты пробежек
---

<h1>🏃‍♂️ Мои беговые результаты</h1>
<p>Дневник соревнований и прогресса.</p>

<style>
  .table-container {
    width: 100%;
    overflow-x: auto; /* Позволяет прокручивать таблицу на телефоне */
  }
  .running-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
    font-size: 14px;
    min-width: 800px; /* Чтобы таблица не сжималась в кашу */
  }
  .running-table th, .running-table td {
    border: 1px solid #ddd;
    padding: 10px;
    text-align: left;
  }
  .running-table th {
    background-color: #f4f4f4;
    font-weight: bold;
  }
  .running-table tr:nth-child(even) {
    background-color: #f9f9f9;
  }
  .running-table tr:hover {
    background-color: #f1f1f1;
  }
</style>

<div class="table-container">
  <table class="running-table">
    <thead>
      <tr>
        <th>Дата</th>
        <th>Соревнование</th>
        <th>Дистанция</th>
        <th>Результат</th>
        <th>Темп</th>
        <th>Место</th>
        <th>Кроссовки</th>
      </tr>
    </thead>
    <tbody>
      {% for run in site.data.runs reversed %}
      <tr>
        <td>{{ run.Date }}</td>
        <td><strong>{{ run.Competition }}</strong></td>
        <td>
          {% comment %} Переводим метры в километры {% endcomment %}
          {% assign dist_m = run["Split, м"] | plus: 0 %}
          {% if dist_m >= 1000 %}
            {{ dist_m | divided_by: 1000.0 }} км
          {% elsif dist_m > 0 %}
            {{ dist_m }} м
          {% endif %}
        </td>
        <td>{{ run.Result }}</td>
        <td>{{ run.Pace }}</td>
        <td>{{ run["Place Overall"] }}</td>
        <td>{{ run.Sneakers }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
</div>
