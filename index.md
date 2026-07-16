---
layout: home
title: Результаты пробежек
---

<h1>🏃‍♂️ Мои беговые результаты</h1>
<p>Здесь я записываю свои пробежки и слежу за прогрессом.</p>

<style>
  .running-table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 20px;
    font-size: 14px;
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
</style>

<table class="running-table">
  <thead>
    <tr>
      <th>Дата</th>
      <th>Дистанция</th>
      <th>Время</th>
      <th>Темп</th>
      <th>Комментарий</th>
    </tr>
  </thead>
  <tbody>
    {% assign sorted_runs = site.data.runs | sort: "Дата" | reverse %}
    {% for run in sorted_runs %}
    <tr>
      <td>{{ run.Дата }}</td>
      <td>{{ run.Дистанция }}</td>
      <td>{{ run.Время }}</td>
      <td>{{ run.Темп }}</td>
      <td>{{ run.Комментарий }}</td>
    </tr>
    {% endfor %}
  </tbody>
</table>
