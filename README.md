# KazAir Analytics

## Company
**KazAir Analytics** — компания, занимающаяся анализом данных аэропортов, взлётно-посадочных полос и навигационных средств по всему миру для улучшения планирования авиационных маршрутов и инфраструктуры.

## Project Overview
Этот проект анализирует данные о:
- Аэропортах
- Региональных делениях
- Навигационных средствах (navaids)
- Частотах аэропортов
- Взлётно-посадочных полосах  

Цель — проводить различные аналитические исследования, включая:
- Количество аэропортов по странам и континентам
- Длина и характеристики ВПП
- Частоты и типы навигационных средств
- Связь navaids с аэропортами

## Screenshot of Main Analytics
![Analytics Screenshot](screenshot.png)

## Tools and Resources
- PostgreSQL / MySQL
- Python (pandas, psycopg2)
- Apache Superset
- CSV datasets

## How to Run the Project
1. Установить PostgreSQL/MySQL
2. Импортировать CSV-файлы в базу данных
3. Настроить подключение к базе данных в `main.py`
4. Запустить Python скрипт:
   ```bash
   python main.py

