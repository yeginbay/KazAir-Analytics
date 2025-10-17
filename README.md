# KazAir Analytics ✈️

## About the Company
**KazAir Analytics** — компания, занимающаяся анализом данных аэропортов, взлётно-посадочных полос и навигационных средств по всему миру.  
Цель — улучшение планирования авиационных маршрутов и инфраструктуры.

---

## Project Overview
Проект анализирует:

- Аэропорты  
- Региональные деления  
- Навигационные средства (navaids)  
- Частоты аэропортов  
- Взлётно-посадочные полосы  

Примеры аналитики:

- Количество аэропортов по странам и континентам  
- Длина и характеристики взлётно-посадочных полос  
- Частоты и типы навигационных средств  
- Связь navaids с аэропортами  

---

## ERD Diagram
<img width="1010" height="864" alt="image" src="https://github.com/user-attachments/assets/85dd903f-3be4-49f5-b227-7f67ce18996d" />


---

## Tools and Resources
- **Database:** PostgreSQL / MySQL  
- **Programming:** Python (pandas, psycopg2)  
- **Visualization:** Apache Superset  
- **Data:** CSV datasets  

---

## Database Schema
Таблицы и описание:

| Table Name             | Description |
|------------------------|-------------|
| `countries`            | Список стран |
| `regions`              | Региональные деления |
| `airports`             | Информация об аэропортах |
| `navaids`              | Навигационные средства |
| `airport_frequencies`  | Частоты аэропортов |
| `runways`              | Взлётно-посадочные полосы |

**Primary & Foreign Keys** настроены:  

- `airports.ident` — уникальный ключ для связи с `navaids`, `airport_frequencies` и `runways`.

---

## How to Run the Project
1. **Установите PostgreSQL/MySQL**.  
2. **Создайте базу данных:**
   ```sql
   CREATE DATABASE airports_db;
Создайте таблицы через SQL (например, через pgAdmin).

Импортируйте CSV-файлы в правильном порядке:

countries

regions

airports

navaids

airport_frequencies

runways

Настройте подключение к базе в main.py:

python
Копировать код
conn = psycopg2.connect(
    dbname="airports_db",
    user="YOUR_USERNAME",
    password="YOUR_PASSWORD",
    host="localhost",
    port="5432"
)
Запустите Python скрипт:

bash
Копировать код
python main.py
Результаты сохранятся в папку analytics_results в формате CSV.

SQL Queries
Все аналитические запросы сохранены в файле queries.sql.

Примеры запросов:

Количество аэропортов по странам:

sql
Копировать код
SELECT iso_country, COUNT(*) AS airport_count
FROM airports
GROUP BY iso_country
ORDER BY airport_count DESC;
Средняя длина ВПП по аэропортам:

sql
Копировать код
SELECT a.name AS airport, AVG(r.length_ft) AS avg_runway_length
FROM runways r
JOIN airports a ON r.airport_ident = a.ident
GROUP BY a.name
ORDER BY avg_runway_length DESC;
Project Structure
graphql
Копировать код
KazAir-Analytics/
│
├─ main.py                 # Python script to execute queries and save CSV
├─ queries.sql             # All SQL analytical queries
├─ README.md               # Project description
├─ screenshot.png          # Example analytics screenshot
├─ csv_data/               # Folder with CSV datasets
└─ analytics_results/      # Folder for CSV output from queries
Notes
Все SQL-запросы проверены и корректны.

Python-скрипт автоматически сохраняет результаты в CSV.

CSV-результаты можно использовать для визуализации в Apache Superset.
