
<b>Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data</b>
  1. Видим, что при переходе по какому-то фильтру у нас идёт SQL запрос прямо из URL
  2. Вставляем туда кавычек и черточек filter?category=Corporate+gifts' OR 1=1 --
  3. Успех
  
<b>Lab: SQL injection vulnerability allowing login bypass</b>
  1. Переходим по ссылке регистрации
  2. Вместо логина пишем administrator, вместо пароля пишем ' OR 1=1 --
  3. Успех


  1. Выбираем любую категорию
  2. '-- возвращают тот же результат
  3. Дописываем мжду ними UNION SELECT и путаемся подобрать колличество столбцов, путем перечисления NULL после SELECT
  4. ' UNION SELECT NULL, NULL , NULL -- подходит 
