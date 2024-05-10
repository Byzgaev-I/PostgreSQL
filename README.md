# Домашнее задание к занятию "`«PostgreSQL»`" - `Бызгаев Александр`

---

### Задание 1

Используя Docker, поднимите инстанс PostgreSQL (версию 13).   
Данные БД сохраните в volume.  
Подключитесь к БД PostgreSQL, используя psql.  
Воспользуйтесь командой \? для вывода подсказки по имеющимся в psql управляющим командам.  
Найдите и приведите управляющие команды для:
- вывода списка БД,  
- подключения к БД,  
- вывода списка таблиц,  
- вывода описания содержимого таблиц,  
- выхода из psql.  

### Выполнения задания 1

1 **Создание Docker Volume**    
```bash
docker volume create postgres_data
```
2 **Запуск контейнера PostgreSQL:**      
```bash
docker run --name my_postgres -e POSTGRES_PASSWORD=mysecretpassword -d -p 5432:5432 -v postgres_data:/var/lib/postgresql/data postgres:13
```
3 **Подключение к БД PostgreSQL используя psql:**       
  - Сначала войдите в контейнер:  
```bash
docker exec -it my_postgres bash  
```
Затем подключитесь к PostgreSQL через psql, используя имя пользователя (по умолчанию postgres):  
```bash
psql -U postgres
```
4 **Вывод подсказки по управляющим командам в psql:**  
  - В psql выполните команду:
```bash
\?
```
5 **Найдите и приведите управляющие команды для:** 
  - вывода списка БД: \l  
  - подключения к БД: \connect db_name  
  - вывода списка таблиц: \dt  
  - удалить базу: drop database db_name;  
  - вывода описания(подробное) содержимого таблиц: \d+ table_name  
  - выхода из psql: \q либо exit  
  - справка: \?  
