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
