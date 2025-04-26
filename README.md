Шпоргалка


Когда можно выбрать 1 вариант - используем ENUM

когда можно выбрать несколько вариантов - используем SET

Вставка данных в таблицу: INSERT INTO table_name (column1, column2, ...) VALUES (value1, value2, ...);

Выборка данных из таблицы: SELECT * FROM table_name;

Удаление данных: DELETE FROM table_name WHERE condition;

Обновление поля во всех записях : update table1 set column1 = new_value

Обновления поля во всех записях, соответствующих условию : update table1 set column 1 =new_value

Добавление одной записи : INSERT INTO table (column1, column2) values (value1, value2)

Добавление нескольких записей : INSERT INTO table (column1, column2) values(value11, value12), (value21, value22), ....

Добавление записей из другой таблицы : insert into table (column1, column2) select (col1, col2) from table 2

INSERT INTO orders (id, products, sum) VALUES (6, 4, 8000) = пример добавления еще одного пункта в таблицу.

asc = от меньшего к большему desc = по убыванию

SELECT * FROM users ORDER BY id LIMIT 10 OFFSET 10;

В SQL порядок выполнения логических операторов AND и OR имеет значение и влияет на результат запроса. Вот основные моменты:

AND имеет более высокий приоритет, чем OR. Это значит, что условия, соединенные с помощью AND, будут обработаны первыми.\

Если вы хотите изменить порядок выполнения, используйте круглые скобки для группировки условий

В этом примере:

LIMIT 10 означает, что вернётся 10 записей.

OFFSET 10 пропускает первые 10 записей, начиная выборку с 11-й.

VARCHAR(50) в SQL обозначает тип данных для столбца, который может хранить строковые значения переменной длины.

VARCHAR - это тип данных, который позволяет хранить строки. При этом длина строки может варьироваться.

(50) - это максимальная длина строки, которая может быть сохранена в этом столбце. В данном случае, максимальная длина составляет 50 символов.

INT в SQL обозначает тип данных, используемый для хранения целых чисел.

DATE в SQL используется для хранения дат

VARCHAR (65535) - максимум

# Практическая 1
1) Выберите из таблицы orders все заказы
2) 
SELECT * FROM orders

![image](https://github.com/user-attachments/assets/5d702153-fbc8-41d9-b7cb-31227f3e43e6)

4) Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in
5) 
select * FROM orders WHERE STATUS NOT IN ('NEW');

![image](https://github.com/user-attachments/assets/4160570f-67d7-45cf-a9bc-bbc5bf93534e)

7) Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new".

SELECT * FROM orders WHERE STATUS IN ('new', 'cancelled');

![image](https://github.com/user-attachments/assets/e2150c23-b6fa-4616-9d36-6011b08ea27f)

8) Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count).
Вывести нужно только номер (id) и сумму (sum) заказа.

SELECT id,sum FROM orders WHERE products_count > 3;

![image](https://github.com/user-attachments/assets/0e16251c-47ec-4c6d-80cf-3b0d2180d0cc)

Примеры задач и их решения 

Измените статус (status) заказа под номером (id) 5 с delivery на success.


update orders set status='success' where id=5


Увеличьте цену 5 самых дешевых товаров на 5%.

update products set price=price*1.05 order by price limit 5


теперь самых дорогих:


update products set price=price*1.05 order by price desc limit 5


В магазин привезли 2 упаковки Сникерса и 2 упаковки Марса. В каждой упаковке по 20 шоколадок. Обновите данные так, чтобы они отражали правильное количество шоколадок.


Удалите из таблицы visits все данные с помощью конструкции DELETE.


Удалите из таблицы products все товары, которых нет на складе.


delete from products where count<1;


Удалите из таблицы cars все автомобили начиная с 2010 года и старше

**Практическая 4**

delete from cars where year<=2010

Создайте таблицу calendar для хранения календаря посетителей.
В таблице должны быть следующие поля:

id – идентификатор записи в календаре, целое положительное;
user_id – идентификатор пользователя, целое положительное;
doctor_id – идентификатор доктора, целое положительное;
visit_date – дата и время визита (точность до секунд).

Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values 
(1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 784, 1,'2017-04-08 13:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')



Создайте таблицу users , в которой будут следующие поля:

id — идентификатор, целые положительные числа.
first_name— имя, строки до 50 символов.
last_name — фамилия, строки до 60 символов.
bio — биография, текст до 65000 символов.


create table users (
id int (10) unsigned,
first_name varchar (50),
last_name varchar (60),
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')


Создайте таблицу articles для хранения данных о статьях. В таблице должны быть следующие поля:
id — идентификатор, целое положительное, NULL запрещен
name — название статьи, строка до 80 символов.text — текст статьи.
state — статус статьи. Поле из 3 вариантов: draft (черновик), correction (корректура), public (опубликована).Добавьте 3 записи так, чтобы получалась таблица ниже:
![изображение](https://github.com/user-attachments/assets/48036e80-b4aa-424b-b2be-589477aa8bc9)

Create table articles (
id int unsigned not null,
name varchar (80),
text text,
state enum('draft', 'correction', 'public')
);
insert into articles (id, name, text, state)
VALUES
(1, 'Новое в Python 3.6', '', 'draft'),
(2, 'Оптимизация SQL запросов', 'При больших объемах данных ...', 'correction'),
(3, 'Транзакции в MySQL', 'По долгу службы мне приходится ...', 'public')


Создайте таблицу rooms для хранения номеров в отеле:

id — идентификатор, целое положительное.
number — номер комнаты, целое положительное. Всего в отеле 107 комнат. NULL запрещен.
beds — количество спальных мест. Выбор из 1+1, 2+1, 2+2. Можно выбрать только один вариант. NULL запрещен.
additional — дополнительные удобства в номере. Можно выбрать несколько вариантов из списка: conditioner, bar, fridge и wifi.
Добавьте 3 записи так, чтобы получалась таблица ниже:
![изображение](https://github.com/user-attachments/assets/ff34575d-6fb5-4695-8dcb-65dd13deb7e0)

create table rooms (
id int unsigned not null,
number tinyint unsigned not null,
beds enum('1+1','2+1','2+2') not null,
additional set('conditioner','bar','fridge','wifi')
);
insert into rooms (id,number,beds,additional)
values
(1,10,'1+1','conditioner,bar,wifi'),
(2,12,'2+1',''),
(3,24,'2+2','fridge,bar,wifi')




Выберите из таблицы products название, цену и страны всех товаров из России и Белоруссии (в поле country обязательно должна присутствовать или Россия, или Белоруссия).
Выбирайте только товары, у которых задана категория.
Данные отсортируйте по цене в обратном порядке.

Поле country относится к типу SET('RU', 'UA', 'BY', 'KZ') NOT NULL.
![изображение](https://github.com/user-attachments/assets/55b9f723-0d48-47b2-b036-4effb7415ec8)



**Практическая 5**


1.Выберите из таблицы orders 4 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.

SELECT * FROM orders WHERE status != 'cancelled' ORDER BY sum DESC LIMIT 4;
![image](https://github.com/user-attachments/assets/0e56e932-dccc-4e94-afe3-618bdc0d3908)

![image](https://github.com/user-attachments/assets/49c9b422-99e2-4f0e-aa4f-af537540197a)


Выберите из таблицы products название и цены четырех самых дешевых товаров, которые есть на складе
SELECT name, price FROM products WHERE count > 0 ORDER BY price ASC LIMIT 4;

![image](https://github.com/user-attachments/assets/2b3879d1-22d3-477e-8978-4360b25dbbcd)

3.Выберите из таблицы orders три последних заказа (по дате date) стоимостью от 3200 рублей и выше. Данные отсортируйте по дате в обратном порядке.

SELECT * FROM orders WHERE sum >= 3200 ORDER BY date DESC LIMIT 3;
![image](https://github.com/user-attachments/assets/460b5aff-abe9-4032-88ad-4987fd993cab)



Создайте дтаблицу: 
![image](https://github.com/user-attachments/assets/a12172ed-1442-4190-a1a3-6d840ae47600)

CREATE TABLE products ( id INT PRIMARY KEY, name VARCHAR(255), count INT, price DECIMAL(10, 2) );

INSERT INTO products (id, name, count, price) VALUES (1, 'Стиральная машина', 5, 10000.00), (2, 'Холодильник', 0, 10000.00), (3, 'Микроволновка', 3, 4000.00), (4, 'Пылесос', 2, 4500.00), (5, 'Вентилятор', 0, 700.00), (6, 'Телевизор', 7, 31740.00), (7, 'Тостер', 2, 2500.00), (8, 'Принтер', 4, 3000.00), (9, 'Активные колонки', 1, 2900.00), (10, 'Ноутбук', 4, 36990.00), (11, 'Посудомоечная машина', 0, 17800.00), (12, 'Видеорегистратор', 23, 4000.00), (13, 'Смартфон', 8, 12300.00), (14, 'Флешка', 4, 1400.00), (15, 'Блендер', 0, 5500.00), (16, 'Газовая плита', 5, 11900.00), (17, 'Клавиатура', 3, 1800.00);

![image](https://github.com/user-attachments/assets/bfe09f98-c486-4e15-ad01-983dc2f14530)


Из этой таблицы сделать выборку на основе задания: Сайт выводит товары по 5 штук. Выберите из таблицы products товары, которые пользователи увидят на 3 странице каталога при сортировке в порядке возрастания цены (price).

SELECT name, price FROM products ORDER BY price ASC LIMIT 5 OFFSET 10;

![image](https://github.com/user-attachments/assets/68fbf47b-8d21-4b78-b951-060fab834327)

SELECT name,price,country FROM products 
WHERE (find_in_set ('RU',country) OR find_in_set ('BY',country)) AND category_id IS NOT NULL ORDER BY price DESC


**Практическая 2**

Выберите из таблицы orders 3 самых дешевых заказа за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
![image](https://github.com/user-attachments/assets/96a415b7-2678-4ee1-b71e-56b36dd2683b)


SELECT * FROM orders WHERE STATUS != 'cancelled' ORDER BY sum ASC LIMIT 3

Выберите из таблицы orders 2 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
![image](https://github.com/user-attachments/assets/65fb9cd8-41c5-4c0a-ba92-c89b15f61391)


SELECT * FROM orders WHERE STATUS != 'cancelled' ORDER BY SUM desc LIMIT 2

Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).

![image](https://github.com/user-attachments/assets/3aa263b2-d6a1-4a2c-b5d9-8eead0852cea)


INSERT INTO orders (id, products, sum) VALUES (6, 4, 8000)

Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.

![image](https://github.com/user-attachments/assets/d8384a2f-1d7f-40d2-8c96-b9b95c2afbfb)

INSERT INTO products (id,NAME,COUNT,price) VALUE (7, 'VR очки',2,70000)

В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.

![image](https://github.com/user-attachments/assets/e2e7531e-928b-4863-bc32-707b4e03c822)


UPDATE products SET NAME='PS5' WHERE NAME='IMAC'


**Практическая 3**


Создайте таблицу users с полем id типа INT и двумя текстовыми полями, которые будут хранить имя (first_name) и фамилию (last_name). Длина имени и фамилии не превышает 50 символов.

Добавьте в таблицу трех пользователей: Дмитрия Иванова, Анатолия Белого и Дениса Давыдова.

![Uploading image.png…]()


create table users (id int, first_name varchar (50), last_name varchar(50)); insert into users (id, first_name, last_name) values (1, 'Дмитрий', 'Иванов'), (2, 'Анатолий', 'Белый'), (3, 'Денис','Давыдов');


Таблицы


Создайте таблицу products для хранения информации о товарах в магазине. Выберите оптимальные поля для хранения данных в соответствии с условиями:

id типа INT – только положительные числа; name – символьный тип до 100 символов; count – количество товара на складе (до 200 штук); price – цена в рублях без копеек (не более 1 млн рублей). Заполните таблицу тремя товарами:

Холодильник, 10 штук, 50 000 рублей. Стиральная машина, 0 штук, 23 570 рублей. Утюг, 3 штуки, 7300 рублей

drop table if exists products; = удаление существующий таблицы

CREATE TABLE products (id INT UNSIGNED, name VARCHAR(100), count TINYINT UNSIGNED, price MEDIUMINT UNSIGNED); INSERT INTO products (id, name, count, price) VALUES (1, "Холодильник", 10, 50000), (2, "Стиральная машина", 0, 23570), (3, "Утюг", 3, 7300);

Создайте таблицу orders для хранения заказов в магазине. Выберите оптимальные поля для хранения данных в соответствии с условиями:

id – тип INT. Только положительные числа. product_id – для хранения номера товара. Только положительные числа от 0 до 4294967295. sale – скидка. Целое положительное число от 0 до 100. amount – сумма заказа. Денежный тип. Максимальная сумма заказа 999999.99 рублей. Добавьте три записи так, чтобы получалась таблица

CREATE TABLE orders (id INT UNSIGNED, products_id INT UNSIGNED, sale TINYINT UNSIGNED, amount decimal(8,2)); INSERT INTO orders (id,products_id,sale,amount) VALUES (1, 245, 0, 230.5), (2, 17, 15, 999999.99), (3, 145677, 21, 1240.00)

drop table if exists products;

Создайте таблицу products для хранения информации о товарах в магазине. Выберите оптимальные поля для хранения данных в соответствии с условиями:

id типа INT – только положительные числа; name – символьный тип до 100 символов; count – количество товара на складе (до 200 штук); price – цена в рублях без копеек (не более 1 млн рублей). Заполните таблицу тремя товарами:

Холодильник, 10 штук, 50 000 рублей. Стиральная машина, 0 штук, 23 570 рублей. Утюг, 3 штуки, 7300 рублей

drop table if exists products; CREATE TABLE products (id INT UNSIGNED, name VARCHAR(100), count TINYINT UNSIGNED, price MEDIUMINT UNSIGNED); INSERT INTO products (id, name, count, price) VALUES (1, "Холодильник", 10, 50000), (2, "Стиральная машина", 0, 23570), (3, "Утюг", 3, 7300);

Создайте таблицу products для хранения информации о товарах в магазине. Выберите оптимальные поля для хранения данных в соответствии с условиями:

id типа INT – только положительные числа; name – символьный тип до 100 символов; count – количество товара на складе (до 200 штук); price – цена в рублях без копеек (не более 1 млн рублей). Заполните таблицу тремя товарами:

Холодильник, 10 штук, 50 000 рублей. Стиральная машина, 0 штук, 23 570 рублей. Утюг, 3 штуки, 7300 рублей

CREATE TABLE products (id INT UNSIGNED, name VARCHAR(100), count TINYINT UNSIGNED, price MEDIUMINT UNSIGNED); INSERT INTO products (id, name, count, price) VALUES (1, "Холодильник", 10, 50000), (2, "Стиральная машина", 0, 23570), (3, "Утюг", 3, 7300);

🖼 Создайте таблицу films с информацией о фильмах. Выберете оптимальные поля для хранения данных в соответствии с условиями:

id типа INT, только положительные числа. name – символьное поле длиной 100. rating – рейтинг, вещественное число. Принимает положительные значения от 0 до 10. country – страна фильма. Символьное поле, содержащее ровно 2 символа. Добавьте в неё 3 записи так, чтобы получалась таблица ниже

CREATE TABLE films ( id INT UNSIGNED, name VARCHAR (100), rating FLOAT UNSIGNED, country VARCHAR (2) ); INSERT INTO films (id, name, rating, country) VALUES (1, 'Большая буря', '3.45', 'RU'), (2, 'Игра', '7.5714', 'US'), (3, 'Война', '10', 'RU');


**Практическая 6 **


Создайте таблицу orders для хранения списка заказов: id — идентификатор, целое положительное. user_id — идентификатор пользователя, который оформил заказ. Целое положительное, NULL запрещен. amount — стоимость заказа. Целое положительное число не более 1 млн. NULL запрещен, по умолчанию 0. created — дата и время создания заказа. NULL запрещен. state — статус заказа. Выбор из new, cancelled, in_progress, delivered, completed. Можно выбрать только один вариант. NULL запрещен. По умолчанию должен стоять new. Добавьте 3 записи так, чтобы получалась таблица ниже:

![image](https://github.com/user-attachments/assets/5c089cec-a51f-45b5-8785-a30a0a6a5655)


CREATE TABLE orders ( id INTEGER PRIMARY KEY AUTO_INCREMENT, user_id INTEGER NOT NULL, amount INTEGER NOT NULL DEFAULT 0, created DATETIME NOT NULL, state ENUM('new', 'cancelled', 'in_progress', 'delivered', 'completed') NOT NULL DEFAULT 'new', CHECK (user_id > 0), CHECK (amount >= 0 AND amount <= 1000000) );

INSERT INTO orders (user_id, amount, created) VALUES (56, 5400, '2018-02-01 17:46:59'); INSERT INTO orders (user_id, amount, created) VALUES (90, 249, '2018-02-01 19:13:04'); INSERT INTO orders (user_id, amount, created) VALUES (78, 2200, '2018-02-01 22:43:09');

SELECT * FROM orders;

![image](https://github.com/user-attachments/assets/6d86c78b-524f-42c4-94d7-d16f0c4687f0)


2.Создайте таблицу users для хранения списка пользователей сайта: id — идентификатор, целое положительное. first_name — имя, строка до 20 символов. NULL запрещен. last_name — фамилия, строка до 20 символов. NULL запрещен. patronymic — отчество, строка до 20 символов. NULL запрещен, по умолчанию пустая строка. is_active — отметка об активности пользователя. Логическое поле, по умолчанию TRUE. is_superuser — отметка администратора. Логическое поле, по умолчанию FALSE. Добавьте 3 записи так, чтобы получалась таблица

![image](https://github.com/user-attachments/assets/c5b8c40b-23f4-4757-a0ce-66e24deff8be)


CREATE TABLE users ( id INTEGER PRIMARY KEY AUTO_INCREMENT, first_name VARCHAR(20) NOT NULL, last_name VARCHAR(20) NOT NULL, patronymic VARCHAR(20) NOT NULL DEFAULT '', is_active BOOLEAN NOT NULL DEFAULT TRUE, is_superuser BOOLEAN NOT NULL DEFAULT FALSE, CHECK (LENGTH(first_name) <= 20), CHECK (LENGTH(last_name) <= 20), CHECK (LENGTH(patronymic) <= 20) );

INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser) VALUES ('Дмитрий', 'Иванов', '', TRUE, FALSE);

INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser) VALUES ('Анатолий', 'Белый', 'Сергеевич', TRUE, TRUE);

INSERT INTO users (first_name, last_name, is_active, is_superuser) VALUES ('Андрей', 'Крючков', FALSE, FALSE);

SELECT * FROM users;

![image](https://github.com/user-attachments/assets/0c105d8e-f56c-45aa-bcbf-7edf22148b6f)


3.Создайте таблицу products для хранения товаров в интернет магазине: id — идентификатор, целое положительное. category_id — категория, целое положительное. Может принимать NULL. По умолчанию NULL. name — название, строка до 100 символов. NULL запрещен. count — количество, целое положительное до 255. NULL запрещен, по умолчанию 0. price — цена типа DECIMAL с 10 знаками, 2 из которых выделены для копеек. NULL запрещен, по умолчанию 0.00. Добавьте 3 записи так, чтобы получалась таблица

![image](https://github.com/user-attachments/assets/f1930e51-5ff9-4b92-b29d-1b7551fae3bb)


CREATE TABLE products ( id INTEGER PRIMARY KEY AUTO_INCREMENT, category_id INTEGER NULL DEFAULT NULL, name VARCHAR(100) NOT NULL, count TINYINT UNSIGNED NOT NULL DEFAULT 0, price DECIMAL(10, 2) NOT NULL DEFAULT 0.00, CHECK (category_id > 0 OR category_id IS NULL), CHECK (count >= 0 AND count <= 255), CHECK (price >= 0) );

INSERT INTO products (category_id, name, count, price) VALUES (1, 'Кружка', 5, 45.90);

INSERT INTO products (category_id, name, count, price) VALUES (17, 'Фломастеры', 0, 78.00);

INSERT INTO products (name, count, price) VALUES ('Сникерс', 12, 50.80);

SELECT * FROM products;
![image](https://github.com/user-attachments/assets/869b1388-e5c4-4360-bec5-f3eabfc0f0b4)

