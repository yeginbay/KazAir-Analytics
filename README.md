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
1️⃣ Создание таблиц и импорт данных

Создайте таблицы в базе данных (например, через pgAdmin).

Импортируйте CSV-файлы в правильном порядке:

countries

regions

airports

navaids

airport_frequencies

runways

2️⃣ Настройка подключения к базе

В файле main.py настройте подключение к вашей базе данных:

import psycopg2

conn = psycopg2.connect(
    dbname="airports_db",
    user="YOUR_USERNAME",
    password="YOUR_PASSWORD",
    host="localhost",
    port="5432"
)

3️⃣ Запуск Python-скрипта
python main.py


Результаты автоматически сохранятся в папку analytics_results в формате CSV.

4️⃣ Примеры аналитических запросов

Количество аэропортов по странам:

SELECT iso_country, COUNT(*) AS airport_count
FROM airports
GROUP BY iso_country
ORDER BY airport_count DESC;


Средняя длина ВПП по аэропортам:

SELECT a.name AS airport, AVG(r.length_ft) AS avg_runway_length
FROM runways r
JOIN airports a ON r.airport_ident = a.ident
GROUP BY a.name
ORDER BY avg_runway_length DESC;


Все SQL-запросы сохранены в файле queries.sql и проверены на корректность.

5️⃣ Структура проекта
KazAir-Analytics/
│
├─ main.py                 # Python-скрипт для выполнения запросов и сохранения CSV
├─ queries.sql             # Все SQL аналитические запросы
├─ README.md               # Описание проекта
├─ screenshot.png          # Пример визуализации аналитики
├─ csv_data/               # Папка с исходными CSV-дatasets
└─ analytics_results/      # Папка для CSV-результатов запросов

6️⃣ Примечания

Python-скрипт автоматически сохраняет результаты в формате CSV.

CSV-файлы из папки analytics_results можно использовать для визуализации в Apache Superset.
