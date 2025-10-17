KazAir Analytics
Company

KazAir Analytics — компания, занимающаяся анализом данных аэропортов, взлётно-посадочных полос и навигационных средств по всему миру для улучшения планирования авиационных маршрутов и инфраструктуры.

Project Overview

Этот проект анализирует данные о:

Аэропортах

Региональных делениях

Навигационных средствах (navaids)

Частотах аэропортов

Взлётно-посадочных полосах

Цель проекта — проводить аналитические исследования, включая:

Количество аэропортов по странам и континентам

Длина и характеристики ВПП

Частоты и типы навигационных средств

Связь navaids с аэропортами

Screenshot of Main Analytics

Tools and Resources

PostgreSQL / MySQL

Python (pandas, psycopg2)

Apache Superset

CSV datasets

Database Schema

Таблицы: countries, regions, airports, navaids, airport_frequencies, runways

PK и FK настроены

airports.ident — уникальный ключ для связи с navaids, frequencies и runways

How to Run the Project

Установить PostgreSQL/MySQL.

Создать базу данных:

CREATE DATABASE airports_db;


Создать таблицы через SQL (например, через pgAdmin).

Импортировать CSV-файлы в таблицы (в правильном порядке):

countries

regions

airports

navaids

airport_frequencies

runways

Настроить подключение к базе данных в main.py:

conn = psycopg2.connect(
    dbname="airports_db",
    user="YOUR_USERNAME",
    password="YOUR_PASSWORD",
    host="localhost",
    port="5432"
)


Запустить Python-скрипт для выполнения аналитики и сохранения результатов:

python main.py


Результаты сохранятся в папку analytics_results в формате CSV.

SQL Queries

Все аналитические запросы сохранены в queries.sql с комментариями по назначению каждого запроса.

