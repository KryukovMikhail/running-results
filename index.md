---
layout: none
---
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Михаил Крюков — Беговые результаты</title>
    <style>
        :root {
            --primary-color: #0f172a;
            --secondary-color: #38bdf8;
            --text-dark: #e2e8f0;
            --text-light: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: #334155;
            --bg-page: #020617;
            --bg-card: #1e293b;
            --success-color: #4ade80;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--bg-page);
            color: var(--text-dark);
            line-height: 1.6;
        }

        .container {
            max-width: 1100px;
            margin: 40px auto;
            background: var(--bg-card);
            box-shadow: 0 4px 20px rgba(0,0,0,0.4);
            border-radius: 8px;
            overflow: hidden;
        }

        .content-wrapper {
            display: flex;
        }

        /* Sidebar Styles */
        .sidebar {
            width: 30%;
            background-color: var(--primary-color);
            color: var(--text-light);
            padding: 40px 30px;
        }

        .profile-header {
            text-align: center;
            margin-bottom: 40px;
        }

        .avatar-icon {
            font-size: 64px;
            margin-bottom: 15px;
            display: block;
        }

        .sidebar h1 {
            font-size: 24px;
            margin-bottom: 5px;
            border: none;
            padding: 0;
            color: var(--text-light);
        }

        .sidebar h2 {
            font-size: 16px;
            font-weight: 400;
            opacity: 0.9;
            border: none;
            padding: 0;
            margin: 0;
            color: var(--text-muted);
        }

        .stats-section {
            margin-bottom: 30px;
        }

        .sidebar h3 {
            font-size: 18px;
            border-bottom: 2px solid var(--secondary-color);
            padding-bottom: 8px;
            margin-bottom: 15px;
            color: #7dd3fc;
        }

        .stats-list {
            list-style: none;
        }

        .stats-list li {
            margin-bottom: 12px;
            font-size: 15px;
            background: rgba(255,255,255,0.05);
            padding: 8px 12px;
            border-radius: 4px;
            border: 1px solid rgba(255,255,255,0.1);
            display: flex;
            justify-content: space-between;
        }

        .stat-value {
            font-weight: bold;
            color: var(--secondary-color);
        }

        .latest-sneakers {
            font-size: 13px;
            color: var(--text-muted);
            margin-top: 5px;
        }

        /* Main Content Styles */
        .main-content {
            width: 70%;
            padding: 40px 50px;
        }

        .main-content h2 {
            font-size: 22px;
            color: var(--secondary-color);
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 10px;
            margin-bottom: 25px;
            margin-top: 40px;
        }

        .main-content h2:first-child {
            margin-top: 0;
        }

        .table-container {
            overflow-x: auto;
        }

        .running-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 14px;
            min-width: 600px;
        }

        .running-table th {
            background-color: #0f172a;
            color: var(--secondary-color);
            padding: 14px 16px;
            text-align: left;
            border-bottom: 2px solid var(--border-color);
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .running-table td {
            padding: 12px 16px;
            border-bottom: 1px solid var(--border-color);
            color: var(--text-dark);
        }

        .running-table tr:last-child td {
            border-bottom: none;
        }

        .running-table tr:hover {
            background-color: rgba(56, 189, 248, 0.05);
        }

        .comp-name {
            font-weight: 600;
            color: var(--text-light);
        }

        .pb-badge {
            background: rgba(56, 189, 248, 0.2);
            color: var(--secondary-color);
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 11px;
            margin-left: 8px;
            font-weight: bold;
            border: 1px solid rgba(56, 189, 248, 0.3);
        }

        .trail-badge {
            background: rgba(74, 222, 128, 0.15);
            color: var(--success-color);
            padding: 2px 8px;
            border-radius: 12px;
            font-size: 11px;
            font-weight: bold;
            border: 1px solid rgba(74, 222, 128, 0.3);
        }

        .result-time {
            font-family: monospace;
            font-size: 15px;
            font-weight: bold;
            color: var(--success-color);
        }

        .pace {
            font-family: monospace;
            color: var(--text-muted);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .content-wrapper {
                flex-direction: column;
            }
            .container {
                margin: 0;
                border-radius: 0;
            }
            .sidebar {
                width: 100%;
                padding: 30px 20px;
            }
            .main-content {
                width: 100%;
                padding: 20px;
            }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="content-wrapper">
        
        <!-- САЙДБАР С СОБОЙ И СТАТИСТИКОЙ -->
        <aside class="sidebar">
            <div class="profile-header">
                <span class="avatar-icon">🏃‍♂️</span>
                <h1>Михаил Крюков</h1>
                <h2>Дневник забегов</h2>
            </div>

            <div class="stats-section">
                <h3>Общая статистика</h3>
                <ul class="stats-list">
                    <!-- Jekyll сам посчитает эти значения из вашего CSV! -->
                    <li>Всего забегов <span class="stat-value">{{ site.data.runs.size }}</span></li>
                    
                    {% assign total_dist_m = 0 %}
                    {% assign trail_count = 0 %}
                    {% for run in site.data.runs %}
                        {% assign d = run["Split, м"] | plus: 0 %}
                        {% assign total_dist_m = total_dist_m | plus: d %}
                        {% if run.Trail == "Yes" %}
                            {% assign trail_count = trail_count | plus: 1 %}
                        {% endif %}
                    {% endfor %}
                    
                    <li>Общий километраж <span class="stat-value">{{ total_dist_m | divided_by: 1000.0 | round: 1 }} км</span></li>
                    <li>Из них трейлов <span class="stat-value">{{ trail_count }}</span></li>
                </ul>
            </div>

            <div class="stats-section">
                <h3>Экипировка</h3>
                <ul class="stats-list">
                    <!-- Выводим последние кроссовки из базы -->
                    {% for run in site.data.runs reversed limit: 5 %}
                        {% if run.Sneakers != "" and run.Sneakers != nil %}
                        <li>
                            Бегал в <br>
                            <span style="color: var(--text-light); font-size: 13px;">{{ run.Sneakers }}</span>
                        </li>
                        {% endif %}
                    {% endfor %}
                </ul>
            </div>
        </aside>

        <!-- ОСНОВНОЙ КОНТЕНТ С ТАБЛИЦЕЙ -->
        <main class="main-content">
            <h2>История результатов</h2>
            
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
                        </tr>
                    </thead>
                    <tbody>
                        {% for run in site.data.runs reversed %}
                        <tr>
                            <td>{{ run.Date }}</td>
                            <td>
                                <span class="comp-name">
                                    {{ run.Competition }}{{ run.Соревнование }}{{ run.Name }}{{ run["Название"] }}
                                </span>
                                {% if run.PB == "Yes" %}<span class="pb-badge">🏆 PB</span>{% endif %}
                                {% if run.Trail == "Yes" %}<span class="trail-badge">Trail</span>{% endif %}
                            </td>
                            <td>
                                {% assign dist_m = run["Split, м"] | plus: 0 %}
                                {% if dist_m >= 1000 %}
                                  {{ dist_m | divided_by: 1000.0 | round: 2 }} км
                                {% elsif dist_m > 0 %}
                                  {{ dist_m }} м
                                {% endif %}
                            </td>
                            <td class="result-time">{{ run.Result }}</td>
                            <td class="pace">{{ run.Pace }}</td>
                            <td>{{ run["Place Overall"] }}</td>
                        </tr>
                        {% endfor %}
                    </tbody>
                </table>
            </div>
        </main>
        
    </div>
</div>

</body>
</html>
