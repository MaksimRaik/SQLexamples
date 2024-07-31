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

Имеется таблица (сущность) с мобильными телефонами mobile_phones.
У сущности имеются следующие поля(атрибуты):
id – идентификатор;
product_name – название;
manufacturer – производитель;
product_count – количество;
price – цена.

Имеется таблица-справочник (сущность) производителей manufacturer.
У сущности имеются следующие поля(атрибуты):
id – идентификатор;
name – название.

Создайте для сущности mobile_phones внешний ключ manufacturer_id (идентификатор производителя), направленный на атрибут id сущности manufacturer. Установите каскадное обновление - CASCADE, а при удалении записи из сущности manufacturer – SET NULL.

Используя CRUD-операцию UPDATE обновите данные в атрибуте manufacturer_id сущности mobile_phones согласно значений, имеющихся в атрибуте manufacturer.

Удалите атрибут manufacturer из сущности mobile_phones.

Выведите идентификатор, название и идентификатор производителя сущности mobile_phones.

### Решение

```
ALTER TABLE mobile_phones
ADD FOREIGN KEY(manufacturer_id) REFERENCES manufacturer(id);

UPDATE mobile_phones SET manufacturer='Apple' WHERE manufacturer_id=1;
UPDATE mobile_phones SET manufacturer='Samsung' WHERE manufacturer_id=2;
UPDATE mobile_phones SET manufacturer='Huawei' WHERE manufacturer_id=3;

SELECT id, product_name, manufacturer_id FROM mobile_phones;
```

## Задача 4

### Условие

Имеется таблица (сущность) с заказами orders.
У сущности имеются следующие поля(атрибуты):
id – идентификатор;
mobile_phones_id – идентификатор мобильного телефона;
order_status - статус.

Подробное описание статусов заказа:
OPEN – «Order is in open state» ;
CLOSED - «Order is closed»;
CANCELLED - «Order is cancelled»

Необходимо вывести идентификатор и подробное описание статуса заказа.

### Решение

```
SELECT 
	id AS 'Номер заказа',
	CASE order_status 
		WHEN 'OPEN' THEN 'Order is in open state'
		WHEN 'CLOSED' THEN 'Order is closed'
		WHEN 'CANCELLED' THEN 'Order is cancelled'
	END AS full_order_status
FROM orders;
```

