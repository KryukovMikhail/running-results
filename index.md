layout: hometitle: Результаты пробежек
🏃‍♂️ Мои беговые результаты
Здесь я записываю свои пробежки и слежу за прогрессом.

Дата	Дистанция	Время	Темп	Комментарий
{% assign sorted_runs = site.data.runs	sort: "Дата"	reverse %} {% comment %} Сортируем по дате (новые сверху) {% endcomment %}		
{% for run in sorted_runs %}				
{{ run.Дата }}	{{ run.Дистанция }}	{{ run.Время }}	{{ run.Темп }}	{{ run.Комментарий }}
{% endfor %}	
