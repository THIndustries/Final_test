#Итоговая контрольная работа по блоку специализация

1. Используя команду cat в терминале операционной системы Linux, создать
два файла Домашние животные (заполнив файл собаками, кошками,
хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и
ослы), а затем объединить их. Просмотреть содержимое созданного файла.
Переименовать файл, дав ему новое имя (Друзья человека):
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/01.JPG)

2. Создать директорию, переместить файл туда:
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/02.JPG)

3. Подключить дополнительный репозиторий MySQL. Установить любой пакет
из этого репозитория:
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/03.1.JPG)

4. Установить и удалить deb-пакет с помощью dpkg.
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/4.1.JPG)
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/4.2.JPG)

5. Выложить историю команд в терминале ubuntu:
https://github.com/THIndustries/Final_test/blob/main/%D0%B8%D1%81%D1%82%D0%BE%D1%80%D0%B8%D1%8F%20%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4.txt

6. Нарисовать диаграмму, в которой есть класс родительский класс, домашние
животные и вьючные животные, в составы которых в случае домашних
животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные
войдут: Лошади, верблюды и ослы):
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/6.1.JPG)

7. В подключенном MySQL репозитории создать базу данных “Друзья
человека”:
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/7.JPG)

8. Создать таблицы с иерархией из диаграммы в БД
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/8.JPG)



9. Заполнить низкоуровневые таблицы именами(животных), командами
которые они выполняют и датами рождения:
```
mysql> CREATE TABLE cats
    -> (
    ->     Id INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(20),
    ->     Birthday DATE,
    ->     Commands VARCHAR(50),
    ->     Genus_id int,
    ->     Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
    -> );
Query OK, 0 rows affected (0.19 sec)

mysql> INSERT INTO cats (Name, Birthday, Commands, Genus_id)
    -> values ('Puh', '2020-05-09', 'кис-кис', 1),
    -> ('Рыжик', '2015-08-07', 'брысь', 1),
    -> ('Барсик', '2017-03-04', 'сюда', 1);
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> CREATE TABLE dogs
    -> (
    ->     Id INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(20),
    ->     Birthday DATE,
    ->     Commands VARCHAR(50),
    ->     Genus_id int,
    ->     Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql>
mysql> INSERT INTO dogs (Name, Birthday, Commands, Genus_id)
    -> VALUES ('Пёс', '2020-01-01', 'фас, лежать, лапу, голос', 2),
    -> ('Шарф', '2021-06-12', "молчать, лежать, лапу", 2),
    -> ('Пятак', '2018-05-01', "сальто, лежать, лапу, след, фас", 2),
    -> ('Слон', '2021-05-10', "сидеть, лежать, фу, место", 2);
Query OK, 4 rows affected (0.00 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> CREATE TABLE hamsters
    -> (
    ->     Id INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(20),
    ->     Birthday DATE,
    ->     Commands VARCHAR(50),
    ->     Genus_id int,
    ->     Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO hamsters (Name, Birthday, Commands, Genus_id)
    -> VALUES ('Малой', '2020-11-11', '', 3),
    -> ('Медведь', '2021-07-11', "сидеть", 3),
    -> ('Ниндзя', '2021-03-10', '', 3),
    -> ('Бурый', '2022-01-09', '', 3);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> CREATE TABLE horses
    -> (
    ->     Id INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(20),
    ->     Birthday DATE,
    ->     Commands VARCHAR(50),
    ->     Genus_id int,
    ->     Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO horses (Name, Birthday, Commands, Genus_id)
    -> VALUES ('Бег', '2020-01-12', 'стоять, шагом', 1),
    -> ('Снег', '2017-03-12', "трусцой, шагом, хоп", 1),
    -> ('Ухо', '2016-07-12', "ану, шагом, хоп, стоять", 1),
    -> ('Хвост', '2020-11-10', "бегом, шагом, хоп", 1);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> CREATE TABLE donkeys
    -> (
    ->     Id INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(20),
    ->     Birthday DATE,
    ->     Commands VARCHAR(50),
    ->     Genus_id int,
    ->     Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO donkeys (Name, Birthday, Commands, Genus_id)
    -> VALUES ('Ушастый', '2018-03-12', "пошёл", 1),
    -> ('Хвостатый', '2021-11-02', "пошёл", 1),
    -> ('Умный', '2020-02-10', "пошёл", 1),
    -> ('Упрямый', '2022-11-12', "пошёл", 1);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> CREATE TABLE camels
    -> (
    ->     Id INT AUTO_INCREMENT PRIMARY KEY,
    ->     Name VARCHAR(20),
    ->     Birthday DATE,
    ->     Commands VARCHAR(50),
    ->     Genus_id int,
    ->     Foreign KEY (Genus_id) REFERENCES packed_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO camels (Name, Birthday, Commands, Genus_id)
    -> VALUES ('Быстрый', '2022-04-10', 'стоять', 3),
    -> ('Медленый', '2009-01-11', "остановись", 3),
    -> ('Омни', '2005-01-12', "быстро", 3),
    -> ('Плевок', '2012-02-01', "кругом", 3);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0
```

10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой
питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу:
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/10.JPG)

11. Создать новую таблицу “молодые животные” в которую попадут все
животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью
до месяца подсчитать возраст животных в новой таблице
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/11.JPG)

12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на
прошлую принадлежность к старым таблицам.
![Иллюстрация к проекту](https://github.com/THIndustries/Final_test/blob/main/12.JPG)





