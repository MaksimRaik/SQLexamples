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
## Задача 2

### Условие

Имеется таблица (сущность) с мобильными телефонами mobile_phones.
У сущности имеются следующие поля(атрибуты):
id – идентификатор;
product_name – название;
manufacturer – производитель;
product_count – количество;
price – цена.

Статусы количества мобильных телефонов (в зависимости от количества): меньше 100 – «little»; от 100 до 300 – «many»; больше 300 – «lots».

Необходимо вывести название, производителя и статус количества для мобильных телефонов.

### Решение

```
SELECT 
	product_name AS 'Название',
	manufacturer AS 'Производитель',
	CASE 
		WHEN product_count < 100 THEN 'little'
		WHEN product_count BETWEEN 100 AND 300 THEN 'many'
		WHEN product_count > 300 THEN 'lots'
	END AS 'Статус количества'	
FROM mobile_phones;
```

## Задача 3

### Условие



