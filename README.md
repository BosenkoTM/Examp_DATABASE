# My SQL, Postgre SQL.

Цикл задач для курса `"  МГПУ, МГТУ.  DATABASE, SQL"`
## Этапы решения заданий
### 1. Спроектировать инфологическую модель базы данных(нотация [IDEF1X](https://infostart.ru/pm/1430187/)). 
Редактор для инфологических эскизов или аналог:
SQL Developer Data Modeler 24.3+ [скачать офсайт](https://www.oracle.com/database/sqldeveloper/technologies/sql-data-modeler/download/), [скачать яндекс-диск](https://disk.yandex.ru/d/1IbKy9AYDTmVwQ).
### 2. Разработать даталогическую(реляционную) модель базы данных.  
Cоздать ER-диаграмму. Редакторы для создания ER-диаграмм:
- [MySQL Workbench](https://www.mysql.com/products/workbench/).
- [Lucidchart](https://www.lucidchart.com/pages/?).
- [Draw.io](https://www.drawio.com/).
- [PhpMyAdmin](http://95.131.149.21:8080/phpmyadmin/).
- [Database diagram](https://databasediagram.com/app).
Для каждой из таблиц создайте диаграмму, которая включает в себя:
- Имя таблицы.
- Поля и их типы данных.
- Первичные и внешние ключи.
### 3. Реализовать физическую модель базы данных(выгрузить DDL-скрипт в СУБД или создать в облачном сервисе).

[1. Задание 1](TASKS/Task1.md)

[2. Задание 2](TASKS/Task2.md)

[3. Задание 3](TASKS/Task3.md)

[4. Задание 4](TASKS/Task4.md)

## Cтудент должен предоставить:
- Инфологическую модель в `IDEF1X`.
- ER-диаграмму с детальным описанием таблиц.
- DDL-скрипт для создания физической модели.
- Выполненный перечень заданий на языке `SQL` согласно индивидуальному варианту. 

## Критерии оценки
- Корректность моделирования предметной области.
- Соответствие нотации IDEF1X.
- Правильность определения связей между таблицами.
- Оптимальность структуры базы данных.
- Качество и полнота DDL-скрипта.
- Соблюдение соглашений об именовании.
- Наличие необходимых индексов и ограничений.

```mysql

CREATE TABLE author (
  author_id  INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
  name_author VARCHAR(50) NOT NULL
);

CREATE TABLE genre (
  genre_id  INT PRIMARY KEY AUTO_INCREMENT NOT NULL,
  name_genre VARCHAR(30) NOT NULL
);

CREATE TABLE book (
    book_id INT PRIMARY KEY AUTO_INCREMENT, 
    title VARCHAR(50), 
    author_id INT NOT NULL, 
    genre_id  INT,
    price DECIMAL(8,2), 
    amount INT, 
    FOREIGN KEY (author_id)  REFERENCES author (author_id) ON DELETE CASCADE,
    FOREIGN KEY (genre_id)  REFERENCES genre (genre_id) ON DELETE SET NULL
);

-----------------Пример 2 Заполнение данными таблицу Автор
 
INSERT INTO author (`author_id`, `name_author`)
VALUES (NULL, 'Булгаков М.А.');

INSERT INTO author (`author_id`, `name_author`)
VALUES (NULL, 'Достоевский Ф.М.');

INSERT INTO author (`author_id`, `name_author`)
VALUES (NULL, 'Есенин С.А.');

INSERT INTO author (`author_id`, `name_author`)
VALUES (NULL, 'Пастернак Б.Л.');

INSERT INTO author (`author_id`, `name_author`)
VALUES (NULL, 'Лермонтов М.Ю.');
 
 
 ---Задание 2 -----------------------

INSERT INTO genre (`genre_id`, `name_genre`)
VALUES (NULL, 'Роман');

INSERT INTO genre (`genre_id`, `name_genre`)
VALUES (NULL, 'Поэзия');

INSERT INTO genre (`genre_id`, `name_genre`)
VALUES (NULL, 'Приключения');


-------------------------------------------
 ---Задание 3 Для каждой строки таблицы book занесите значения в поля author_id и genre_id. 
 ----Считать, что книга Есенина относится к жанру «Поэзия», остальные книги – к жанру «Роман».
 
 INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Мастер и Маргарита', 1, 1, 670.99, 3);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Белая гвардия', 1, 1, 540.50, 5);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Идиот', 2, 1, 460.50, 10);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Братья Карамазовы', 2, 1, 799.01, 3);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Игрок', 2, 1, 480.50, 10);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Стихотворения и поэмы', 3, 2, 650.00, 15);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Черный человек', 3, 2, 570.20, 6);
INSERT INTO book (`book_id`, `title`,`author_id`, `genre_id`, `price`, `amount`)
VALUES (NULL, 'Лирика', 4, 2, 518.99, 2);

```
