# Описание

Файлы с примерами решения различных задач поиска информации в базах данных с помощью SQL. Загружено для удобства подлядывания

# Задачи, котрые решались с использованием данных примеров.

## Задача 1

### Условие 

Имеется таблица (сущность) с мобильными телефонами mobile_phones.
У сущности имеются следующие поля(атрибуты):
id – идентификатор;
product_name – название;
manufacturer – производитель;
product_count – количество;
price – цена.

Сущность mobile_phones имеет следующие записи:
| id | product_name | manufacturer | product_count | price | | --- | ------------ | ------------ | ------------- | ----- | | 1 | iPhone X | Apple | 156 | 76000 | | 2 | iPhone 8 | Apple | 180 | 51000 | | 3 | Galaxy S9 | Samsung | 21 | 56000 | | 4 | Galaxy S8 | Samsung | 124 | 41000 | | 5 | P20 Pro | Huawei | 341 | 36000 |

Создайте таблицу (сущность) с заказами {student_schema_name}.manufacturer. При создании необходимо использовать DDL-команды.
Перечень полей (атрибутов):
id – числовой тип, автоинкремент, первичный ключ;
name – строковый тип;

Используя CRUD-операцию INSERT, наполните сущность manufacturer в соответствии с данными, имеющимися в атрибуте manufacturer сущности mobile_phones.

### Решение
Код MySQL
```
DROP TABLE IF EXISTS itresume10574509.manufacturer;

CREATE TABLE itresume10574509.manufacturer(
  id SERIAL PRIMARY KEY,
  name VARCHAR(45)
);

INSERT INTO itresume10574509.manufacturer (name)
VALUES 
('Apple'),
('Apple'),
('Samsung'),
('Samsung'),
('Huawei');

SELECT name FROM itresume10574509.manufacturer;
```
