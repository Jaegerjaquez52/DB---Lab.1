# Лабораторна робота 1. Робота з СУБД PostgreSQL та основи SQL

## Загальна інформація

**Здобувач освіти:** Поліщук Андрій Володимирович
**Група:** ІПЗ-32
**Обраний рівень складності:** 3
**Посилання на проєкт:** (https://supabase.com/dashboard/project/dmixkebccprqmaybbabu)

## Виконання завдань

!!!Коментарі до всіх запитів розміщені на скріншотах!!!

### Отримати всі записи з таблиці customers.

```sql
SELECT * FROM customers;
```

Результат: Отримано 15 записів клієнтів, включаючи як фізичних осіб, так і юридичні особи з різних міст України.

![alt text](image-1.png)

### Вивести тільки назви товарів і їхні ціни з таблиці products.

```sql
SELECT 
    product_name, 
    unit_price 
FROM products 
```

Результат: Отримано 25 записів, які включають в себе назву товару та його ціну.

![alt text](image-2.png)

### Показати контактні дані всіх співробітників (ім'я, прізвище, телефон, email).

```sql
SELECT 
    first_name, 
    last_name, phone,
    email 
FROM employees 
```

Результат: Отримано 8 записів з контактними даними співробітників, а саме їхнє ім'я, прізвище, номер телефону та електронна пошта.

![alt text](image-3.png)

### Знайти всіх клієнтів з міста Київ.

```sql
SELECT * 
FROM customers 
WHERE 
    city LIKE 'Київ'
```

Результат: Отримано 4 записи, де знаходиться інформація про клієнтів з міста Київ.

![alt text](image-4.png)

### Вивести товари, які коштують більше 25000 грн.

```sql
SELECT * 
FROM products 
WHERE 
    nit_price > 25000
```

Результат: Отримано 13 записів про товари, які вартують більше ніж 25000 грн.

![alt text](image-5.png)

### Показати всі замовлення зі статусом "delivered".

```sql
SELECT * 
FROM orders 
WHERE 
    order_status LIKE 'delivered'
```

Результат: Отримано 26 записів про замовлення, які були доставлені.

![alt text](image-6.png)

### Знайти співробітників, які працюють у відділі продажів.

```sql
SELECT * 
FROM employees 
WHERE 
    title LIKE '%продаж%'
```

Результат: Отримано 3 записи про працівників, які працюють у відділі продажів.

![alt text](image-7.png)

### Відсортувати товари за зростанням ціни.

```sql
SELECT * 
FROM products 
ORDER BY 
    unit_price
```

Результат: Отримано 25 записів, в яких знаходяться інформація про товари, відсортовані за зростанням ціни.

![alt text](image-8.png)

### Показати клієнтів в алфавітному порядку за іменем контактної особи.

```sql
SELECT * 
FROM customers 
ORDER BY 
    contact_name
```

Результат: Отримано 15 записів, в яких знаходяться інформація про клієнтів, відсортовані в алфавітному порядку.

![alt text](image-9.png)

### Вивести замовлення від найновіших до найстаріших.

```sql
SELECT * 
FROM orders 
ORDER BY 
    order_date DESC
```

Результат: Отримано 31 запис про замовлення, які відсортовані від найновіших до найстаріших.

![alt text](image-10.png)

### Показати перша 10 найдорощих товарів.

```sql
SELECT * 
FROM products 
ORDER BY 
    unit_price DESC 
LIMIT 10
```

Результат: Отримано 10 записів з найдорощими товарами.

![alt text](image-11.png)

### Вивести 5 останніх замовлень(за датою).
```sql
SELECT * 
FROM orders 
ORDER BY 
    order_date DESC 
LIMIT 5
```

Результат: Отримано 5 останніх замовленнь (за датою).

![alt text](image-12.png)

### Отримати перших 8 клієнтів в алфавітному порядку

```sql
SELECT * 
FROM customers 
ORDER BY 
    contact_name 
LIMIT 8
```

Результат: Отримано записи про 8 перших клієнтів в алфавітному порядку

![alt text](image-13.png)

### Знайти всіх клієнтів, чиї імена починаються на 'Іван'.

```sql
SELECT * 
FROM customers 
WHERE 
    contact_name LIKE 'Іван%'
```

Результат: Отримано 1 запис про клієнта, контактне ім'я якого починається на 'Іван'

![alt text](image-14.png)

### Вивести товари, в назві яких є слово 'phone' або 'телефон'.

```sql
SELECT * 
FROM products
WHERE 
    product_name LIKE '%phone%' 
    OR 
    product_name LIKE '%телефон%'
```

Результат: Не отримано жодного запису, проте якщо замінити %phone% на %Phone%, то виведе 1 запис(на фото 16)

![alt text](image-15.png)
![alt text](image-16.png)

### Вивести товари, в назві яких є слово '256GB' або '128GB'.

```sql
SELECT * 
FROM products 
WHERE 
    product_name LIKE '%256GB%' 
    OR 
    product_name LIKE '%128GB%'
```

Результат: Отримано 8 записів з товарами в назві яких *міститься* '256GB' або '128GB'

![alt text](image-19.png)

### Вивести замовлення, доставка яких виконується компанією, назва якої закінчуєтьяся на 'Пошта'

```sql
SELECT * 
FROM orders 
WHERE 
    ship_via LIKE '%Пошта' 
```

Результат: Отримано 18 записів з замовленнями, доставкою яких займається компанія, назва якої *закінчується* на 'Пошта'

![alt text](image-20.png)

### Вивести компанії-постачальників, назви яких починаються з 'ТОВ' 

```sql
SELECT * 
FROM suppliers 
WHERE 
    company_name LIKE 'ТОВ%' 
```

Результат: Отримано 5 записів про компанії-постачальників, назви яких починаються на 'ТОВ'

![alt text](image-21.png)

### Знайти товари дорожчів за 15000 грн і дешевші за 50000 грн

```sql
SELECT * 
FROM products 
WHERE 
    unit_price > 15000 
    AND 
    unit_price < 50000
```

Результат: Отримано 16 записів про товари, вартість яких більша за 15000 грн і в той же час не перевищує 50000 грн.

![alt text](image-22.png)

### Вивести клієнтів з Києва чи Львова, які є юридичними особами

```sql
SELECT * 
FROM customers 
WHERE 
    (city LIKE 'Київ' OR city LIKE 'Львів') 
    AND 
    customer_type LIKE 'company'
```

Результат: Отримано 3 записи, про клієнтів, які  є юридичними особами і знаходяться/проживають у Києві.
    P.S. збігів для м. Львів не було.    

![alt text](image-23.png)

### Вивести ноутбуки/комп'ютери та ігрові консолі, вартість яких не перевищує 30000 грн

```sql
SELECT * 
FROM products 
WHERE 
    (category_id = 2 OR category_id = 6) 
    AND 
    unit_price < 30000
```

Результат: Отримано 4 записи в яких міститься інформація про ноутбуки та ігрові консолі дешевші за 30000 грн.

![alt text](image-24.png)

### Вивести замовлення, які будуть або вже відправлені в Київ або Дніпро і досі не доставлені.

```sql
SELECT * 
FROM orders 
WHERE 
    (ship_city LIKE 'Київ' OR ship_city LIKE 'Дніпро') 
    AND NOT 
    order_status = 'delivered'
```

Результат: Отримано 5 записів, а саме замовлення які мають бути відправлені або вже відправлені, проте досі не доставлені

![alt text](image-25.png)

### Вивести клієнтів з Києва, Львова чи Харкова, які є фізичними особами

```sql
SELECT * 
FROM customers 
WHERE 
    (city LIKE 'Київ' OR city LIKE 'Львів' OR city LIKE 'Харків') 
    AND 
    customer_type LIKE 'individual'
```

Результат: 6 записів з фізичними особами, які проживають в Києві, Львові та Харкові

![alt text](image-26.png)

### Вивести працівників на посаді менеджера, проте не менеджер складу. З зарплатою більше ніж 20000 грн

```sql
SELECT * 
FROM employees 
WHERE 
    (title LIKE 'Менеджер%' AND NOT title LIKE '%склад%') 
    AND 
    salary > 20000
```

Результат: 4 записа з інформацією про працівників на посаді менеджера продажу/закупівель з заробітньою платою більше ніж 20000 грн

![alt text](image-27.png)

### Вивести клієнтів з міст Київ, Харків, Одеса, Дніпро.

```sql
SELECT * 
FROM customers 
WHERE 
    city IN ('Київ', 'Харків', 'Одеса', 'Дніпро');
```

Результат: Отримано 12 записів про клієнтів, які проживають в Києві, Харкові, Одесі або в Дніпрі

![alt text](image-28.png)

### Знайти товари в ціновому діапазоні від 10000 до 30000 грн.

```sql
SELECT * 
FROM products 
WHERE 
    unit_price BETWEEN 10000 AND 30000;
```

Результат: Отримано 13 записів з товарами ціна яких належить діапазону від 10000 грн до 30000 грн

![alt text](image-29.png)

### Вивести товари з категорій: смартфони, ноутбуки та коп'ютери, ігрові консолі та ігри

```sql
SELECT * 
FROM products 
WHERE 
    category_id IN (2, 3, 6)
```

Результат: Отримано 12 записів, а саме про товари, що належить до категорій з індексами 2(Смартфони та телефони), 3(Ноутбуки та коп'ютери), 6(Ігрові консолі та ігри)

![alt text](image-30.png)

### Вивести постачальників з Києва та Львова

```sql
SELECT * 
FROM suppliers 
WHERE 
    city IN ('Київ', 'Львів')
```

Результат: Отримано 3 записи про постачальників які розташовані в Києві та Львові

![alt text](image-31.png)

### Вивести замовлення в період з січня по квітень

```sql
SELECT * 
FROM orders 
WHERE 
    order_date BETWEEN '2024-01-01' AND '2024-04-30'
```

Результат: Отримано 15 записів про замовлення, які були зроблені в період з 1 січня по 30 квітня.

![alt text](image-32.png)

### Вивести працівників, які були прийняті на роботу за 2020 рік

```sql
SELECT * 
FROM employees 
WHERE 
    hire_date BETWEEN '2020.01.01' AND '2020.12.31'
```

Результат: Отримано 3 записи про працівників, які влаштувалися на роботу у 2020 році

![alt text](image-33.png)

### Вивести замовлення, які ще не відправленні

```sql
SELECT * 
FROM orders 
WHERE 
    shipped_date IS NULL;
```

Результат: Отримано 4 записи з замовленнями, які не були відправлені

![alt text](image-34.png)

### Вивести доставлені замовлення

```sql
SELECT * 
FROM orders 
WHERE 
    shipped_date IS NOT NULL;
```

Результат: Отримано 27 записи з замовленнями, які були доставлені

![alt text](image-35.png)

### Вивести товари з категоріх 'Телевізори та аудіо' і 'Побутова техніка' в назві яких є слово 'Samsung'

```sql
SELECT * 
FROM products 
WHERE 
    (category_id = 3 OR category_id = 4) 
    AND 
    product_name LIKE '%Samsung%'
```

Результат: Отримано 2 записи з інформацією про товари з категорій 'Телевізори та аудіо' і 'Побутова техніка', в назві яких міститься слово 'Samsung'

![alt text](image-36.png)

### Вивести інформацію за Січень-Травень 2024 року,але лише ті місяці, в яких виручка яких належить діапазону від 130000 грн до  500000 грн

```sql
SELECT * 
FROM monthly_sales_report 
WHERE 
    year = 2024 
    AND 
    month IN (1, 2, 3, 4, 5)
    AND
    total_revenue BETWEEN 130000 AND 500000
```

Результат: Отримано 4 записи з інформацією про замовлення в період з січня по травень, але лише ті місяці дохід яких належить діапазону від 130000 грн до 500000 грн

![alt text](image-38.png)

### Вивести замовлення за червень 2024, які були доставлені Новою Поштою

```sql
SELECT * 
FROM orders  
WHERE 
    order_status IN('pending', 'shipped', 'delivered') 
    AND 
    order_date BETWEEN '2024-06-01' AND '2024-06-30' 
    AND 
    ship_via LIKE 'Нова Пошта';
```

Результат: Отримано 1 запис в якому міститься інформація про замовлення, яке було доставлено в червні 2024 Новою Поштою

![alt text](image-37.png)

### Вивести клієнтів, які є фізичними особами і електронна пошта яких закінчується на 'gmail.com' або 'ukr.net'

```sql
SELECT 
    customer_id, 
    contact_name, 
    city, 
    phone,
    email 
FROM customers 
WHERE 
    company_name IS NULL 
    AND 
    (email LIKE '%gmail.com' OR email LIKE '%ukr.net')
```

Результат: Отримано 7 записів про фізичних осіб в яких електронна адреса закінчується на 'gmail.com' або 'ukr.net'

![alt text](image-39.png)

### Вивести інформацію про мобільні пристрої, об'єм пам'яті яких дорівнює 256 ГБ, а також про ігрові консолі, об'єм пам'яті яких становить 1 ТБ

```sql
SELECT 
    product_name,
    unit_price,
    units_in_stock,
    description
FROM products 
WHERE 
  (category_id = 1 AND product_name LIKE '%256GB%') 
  OR 
  (category_id = 6 AND product_name LIKE '%1TB%')
```

Результат: Отримано 3 записи в яких міститься інформація про мобільні пристрої з об'ємом пам'яті в 256 Гб і про ігрові консолі, об'єм пам'яті яких становить 1 ТБ

![alt text](image-41.png)

### Вивести інформацію про товари, відсортувавши їх за зростанням ціни та алфавітом

```sql
SELECT 
    product_id,
    unit_price, 
    product_name,
    description
FROM products
ORDER BY 
    unit_price, 
    product_name
```

Результат: Отримано 25 записів з короткою інформацією про товари, які були відсортовані за зростанням ціни і за алфавітом.

![alt text](image-42.png)

### Вивести інформацію про працівників, відсортувавши їх за місцем проживання та за зростанням заробітньої плати

```sql
SELECT 
    first_name,
    last_name,
    city,
    salary
FROM employees
ORDER BY 
    city,
    salary
```

Результат: Отримно 8 записів про працівників, відсортованих за місцем проживання та заробтньою платою

![alt text](image-43.png)

### Вивести інформацію спочатку про фізичних осіб, а потім про юридичних осіб. Відсортувати записи за місцем проживання/розташування, а також іменем клієнта

```sql
SELECT 
    company_name,
    contact_name,
    city,
    phone,
    email,
    customer_type
FROM customers
ORDER BY 
    customer_type DESC,
    city,
    contact_name
```

Результат: Отримно 15 записів про клієнтів, спочатку про фізичних осіб, а потім про юридичних осіб. Записи відсортовані за місцем проживання/розташування клієнтів, а також за їх іменем

![alt text](image-45.png)

### Вивести 10 найдорощих товарів

```sql
SELECT 
  product_name,
  unit_price
FROM products
ORDER BY 
  unit_price
OFFSET 15  
```

Результат: Отримно 10 записів з найдорощими товарами

![alt text](image-44.png)

### Вивести 5 останніх замовлень

```sql
SELECT *
FROM orders
ORDER BY 
    order_date 
OFFSET 26 
```

Результат: Отримно 5 записів з інформацією про останні замовлення

![alt text](image-46.png)

### Знайти товари, в назві яких є "Samsung" або "Apple", але немає слова "чохол".

```sql
SELECT *
FROM products
WHERE
    (product_name LIKE '%Samsung%' OR product_name LIKE '%Apple%')
    AND
    product_name NOT LIKE '%чохол%'
```

Результат: Отримно 5 записів з товарами, в назві яких є "Samsung" або "Apple", але немає слова "чохол"

![alt text](image-47.png)

### Знайти товари, в назві яких є "Pro" або "Max", але немає слова "Air".

```sql
SELECT *
FROM products
WHERE
    (product_name LIKE '%Pro%' OR product_name LIKE '%Max%')
    AND
    product_name NOT LIKE '%Air%'
```

Результат: Отримно 1 запис з товаром, в назві якого є "Pro", але немає слова "Air"

![alt text](image-48.png)

### Вивести клієнтів, чиї електронні пошти закінчуються на 'gmail.com' або 'outlook.com', але не містять 'ivan'

```sql
SELECT *
FROM customers
WHERE
    (email LIKE '%gmail.com%' OR email LIKE '%outlook.cim%')
    AND
    email NOT LIKE '%ivan%'
```

Результат: Отримно 4 записи з клієнтами, електронні пошти, яких закінчуються на 'gmail.com' або 'outlook.com', але не містять 'ivan'

![alt text](image-49.png)

### Вивести постачальників, назви яких починаються з 'ТОВ' або 'ПП', але не містять 'Імпорт'

```sql
SELECT *
FROM suppliers
WHERE 
    (company_name LIKE 'ТОВ%' OR company_name LIKE 'ПП%')
    AND
    company_name NOT LIKE '%Імпорт%';
```

Результат: Отримно 6 записів з інформацією про постачальників, назви яких починаються з 'ТОВ' або 'ПП', але не містять 'Імпорт'

![alt text](image-50.png)

### Вивести працівників, посада яких містить 'Менеджер', але не 'складу', або ж містить 'директор'

```sql
SELECT *
FROM employees
WHERE 
    (title LIKE '%Менеджер%' AND title NOT LIKE '%складу%')
    OR 
    title LIKE '%директор%';
```

Результат: Отримно 5 записів з інформацією про працівників, посада яких містить 'Менеджер', але не 'складу', або ж містить 'директор'

![alt text](image-51.png)

### Знайти товари дорожчі 20000 грн (категорії 1 або 2) АБО товари дешевші 5000 грн будь-якої категорії.

```sql
SELECT *
FROM products
WHERE 
    (unit_price > 20000 AND category_id IN (1,2))
    OR unit_price < 5000;
```

Результат: Отримно 12 записів з інформацією про товари дорожчі за 20000 грн з категорії 1 і 2, також про товари дешевші за 5000 грн.

![alt text](image-52.png)

### Вивести інформацію про замовлення з доставкою дорожче 300 і статусом 'delivered' або 'processing' або з доставкою дешевшою за 100 незалежно від статусу(freight це ж про вартість доставки?).

```sql
SELECT *
FROM orders
WHERE 
    (freight > 300 AND order_status IN ('delivered', 'processing'))
    OR freight < 100;
```

Результат: Отримно 10 записів з інформацією про замовлення, доставка яких дорожча за 300 з статусом 'delivered' або 'processing' або про замовлення, доставка яких дешевша за 100

![alt text](image-53.png)

### Вивести інформацію про клієнтів з Києва та Львова, які є юридичними особами та про клієнтів з Харкова, які є фізичними особами

```sql
SELECT *
FROM customers
WHERE 
    ((city IN ('Київ','Львів') AND company_name IS NOT NULL)
     OR (city = 'Харків' AND company_name IS NULL));
```

Результат: Отримно 5 записів з інформацією про клієнтів, а саме про юридичних осіб з Києва та Львова, а також фізичних осіб з Харкова

![alt text](image-54.png)

### Вивести інформацію про працівників з Києва і з зарплатою більшою за 30000грн і про працівників з Львова, зарплата яких 20000-25000грн

```sql
SELECT *
FROM customers
WHERE 
    ((city IN ('Київ','Львів') AND company_name IS NOT NULL)
     OR (city = 'Харків' AND company_name IS NULL));
```

Результат: Отримно 3 записи з працівниками, які проживають у Києві і їхня зарплата перевищує 30000 грн та працівникі, які проживають у Львові, зарплата яких 20000-25000 грн

![alt text](image-55.png)

### Створити звіт товарів з 5+ різними умовами фільтрації одночасно.

```sql
SELECT *
FROM products
WHERE 
        unit_price BETWEEN 10000 AND 50000
    AND 
        units_in_stock > 5
    AND 
        discontinued = false
    AND 
        (product_name LIKE '%GB%' OR product_name LIKE '%OLED%')
    AND 
        category_id IN (1,2,3);
```

Результат: Отримано 7 записів про товари, які належать до категорій смартфонів, ноутбуків або телевізорів, мають ціну в діапазоні від 10000 до 50000 грн, залишок на складі більше 5 одиниць, не зняті з виробництва, а також у назві яких міститься «GB» або «OLED».

![alt text](image-57.png)

### Написати запит для аналізу клієнтської бази з множинними критеріями відбору.

```sql
SELECT 
    customer_id, 
    contact_name, 
    city, 
    email, 
    registration_date
FROM customers
WHERE 
      customer_type = 'individual'
    AND 
      (email LIKE '%gmail.com' OR email LIKE '%ukr.net')
    AND 
      city IN ('Київ','Львів')
    AND 
      registration_date BETWEEN '2023-01-01' AND '2023-12-31';
```

Результат: Отримно 4 записи про клієнтів, які є фізичними особами, електронна пошта яких закінчується на 'gmail.com' або 'ukr.net', проживають у Києві або Львові та зареєструвалися впродовж 2023 року

![alt text](image-61.png)

### Провести аналіз товарів за ціновими сегментами (1).

```sql
SELECT COUNT(*) 
AS cheap_products 
FROM products 
WHERE 
    unit_price < 10000;
```

Результат: Отримно кількість товарів дешевших за 10000 грн - **4**

![alt text](image-58.png)

### Провести аналіз товарів за ціновими сегментами (2).

```sql
SELECT COUNT(*) 
AS mid_products
FROM products
WHERE 
    unit_price BETWEEN 10000 AND 30000;
```

Результат: Отримно кількість товарів ціна яких становить від 10000 грн до 10000 грн - **13**

![alt text](image-62.png)

### Провести аналіз товарів за ціновими сегментами (3).

```sql
SELECT COUNT(*) 
AS premium_products 
FROM products
WHERE 
    unit_price > 30000;
```

Результат: Отримно кількість товарів ціна яких більша за 30000 грн - **8**

![alt text](image-65.png)

### Дослідити розподіл клієнтів за географічним принципом (1).

```sql
SELECT city, COUNT(*)
FROM customers 
GROUP BY city 
ORDER BY COUNT(*) DESC;
```

Результат: Отримно інформацію про кількість клієнтів у кожному місті

![alt text](image-66.png)

### Дослідити розподіл клієнтів за географічним принципом (2).

```sql
SELECT r.region_name, customer_type, COUNT(*)
FROM customers c
JOIN regions r ON c.region_id = r.region_id
GROUP BY 
  r.region_name, 
  customer_type;
```

Результат: Отримно інформацію про кількість фізичних та юридичних осіб по областях

![alt text](image-66.png)

### Дослідити розподіл клієнтів за географічним принципом (3).

```sql
SELECT ship_city, COUNT(*) 
FROM orders 
GROUP BY ship_city 
ORDER BY COUNT(*) DESC 
LIMIT 3;
```

Результат: Отримно інформацію про 3 міста з найбільшою кількістю замовлень

![alt text](image-67.png)

### Дослідити розподіл клієнтів за географічним принципом (4).

```sql
SELECT r.region_name, SUM(oi.unit_price * oi.quantity) AS revenue
FROM orders o
JOIN order_items oi ON o.order_id = oi.order_id
JOIN regions r ON o.ship_region_id = r.region_id
GROUP BY r.region_name
ORDER BY revenue DESC;
```

Результат: Отримно 5 записів з областям, які відсортовані по зменшенню витрат клієнтів

![alt text](image-68.png)

### Проаналізувати часові патерни в замовленнях (1).

```sql
SELECT year_month, SUM(total_revenue)
FROM monthly_sales_report
WHERE year = 2024
GROUP BY year_month
ORDER BY year_month;
```

Результат: Отримно 7 записів з інформацією про дохід по місяцях 2024 року

![alt text](image-69.png)

### Проаналізувати часові патерни в замовленнях (2).

```sql
SELECT TO_CHAR(order_date, 'Month') AS Month, COUNT(*)
FROM orders
GROUP BY Month
ORDER BY COUNT(*) DESC;
```

Результат: Отримно 8 записів з інформацією про кількість замовлень за місяць

![alt text](image-70.png)

### Проаналізувати часові патерни в замовленнях (3).

```sql
SELECT EXTRACT(QUARTER FROM order_date) AS quarter, COUNT(*)
FROM orders
GROUP BY quarter
ORDER BY quarter;
```

Результат: Отримно 3 записи з інформацією про кількість замовлень по кварталах

![alt text](image-71.png)

### 5 нестандартних запитів, які демонструють глибоке розуміння SQL логіки. (1).

```sql
SELECT DISTINCT c.contact_name
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id
WHERE p.category_id IN (1, 2)
```

Результат: Отримно 10 записів з іменами клієнтів, які замовляли смартфони або ноутбуки

![alt text](image-73.png)

### 5 нестандартних запитів, які демонструють глибоке розуміння SQL логіки. (2).

```sql
SELECT DISTINCT c.contact_name
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
JOIN products p ON oi.product_id = p.product_id
WHERE p.category_id IN (1, 2)
```

Результат: Отримно 4 записів з назвами товарів, які не замовляли

![alt text](image-74.png)

### 5 нестандартних запитів, які демонструють глибоке розуміння SQL логіки. (3).

```sql
SELECT 
  p.product_name, 
  SUM(oi.unit_price * oi.quantity * (1 - oi.discount)) AS revenue
FROM order_items oi
  JOIN products p ON oi.product_id = p.product_id
  JOIN orders o ON oi.order_id = o.order_id
WHERE EXTRACT(YEAR FROM o.order_date) = 2024
GROUP BY p.product_name
ORDER BY revenue DESC
LIMIT 5;
```

Результат: Отримно інформацію про 5 найбільш прибуткових товара

![alt text](image-75.png)

### 5 нестандартних запитів, які демонструють глибоке розуміння SQL логіки. (4).

```sql
SELECT 
    e.first_name, 
    e.last_name, 
    COUNT(o.order_id) AS orders_handled
FROM employees e
    JOIN orders o ON e.employee_id = o.employee_id
GROUP BY e.employee_id
ORDER BY orders_handled DESC
LIMIT 1;
```

Результат: Знайдено співробітника з найбільшою кількістю оформлених замовлень

![alt text](image-76.png)

### 5 нестандартних запитів, які демонструють глибоке розуміння SQL логіки. (5).

```sql
SELECT 
    c.contact_name, 
    SUM(oi.unit_price * oi.quantity * (1 - oi.discount)) AS total_spent
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
JOIN order_items oi ON o.order_id = oi.order_id
GROUP BY c.contact_name
ORDER BY total_spent DESC
LIMIT 5;
```

Результат: Виведено 5 клієнтів з найбільшими витратами 

![alt text](image-77.png)


## Висновки
    На цій лабораторній я мав змогу попрацювати в такому середовищі, як `Supabase`. В ході виконання було написано і виконано не один десяток запитів різної складності. Цей процес доволі мутний проте SQL-запити виявилися дуже зручними інструментом, щоб витягнути потрібну інформацію з БД. Звичайно бажано знати структуру бази даних, для економії часу, щоб не перевіряти назву рядка чи таблиці при написанні запиту. 

**Самооцінка**: 5

**Обгрунтування**: За цей час я реалізував доволі багато запитів, як простих так і складних. Старався в самостійних завданнях креативно підходити до написання запитів, хоч це і не завжди вдавалося. 

**P.S.** під час цієї лабораторної я вкотре переконався, що покупка другого монітора сильно полегшить роботу. Приблизно так виглядав екран протягом виконання роботи:

![alt text](image-79.png)