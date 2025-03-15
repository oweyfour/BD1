Шпоргалка

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

# BD1
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
