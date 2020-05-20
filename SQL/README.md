
<b>Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data</b>
  1. Видим, что при переходе по какому-то фильтру у нас идёт SQL запрос прямо из URL
  2. Вставляем туда кавычек и черточек filter?category=Corporate+gifts' OR 1=1 --
  3. Успех
