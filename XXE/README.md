<b> Lab: Exploiting XXE using external entities to retrieve files </b>
  1. Переходим по сайту, кликаем на Check stock. 
  2. Перехватываем в Burp Post запрос
  3. Вставляем там следующий текст в XML часть запроса:
  4. Успех
![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/XXE/Screenshot_20200520_202913.png)


<b> Lab: Exploiting XXE to perform SSRF attacks </b>
 1. Перехватыаем аналогично 1 лабе запрос
 2. Пытаемся пройти по ip -вместо данных нам возвращают название папки latest.
 3. Приписываем её к URL
 ![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/XXE/Screenshot_20200520_205120.png)
 4. Проделываем так, пока не находим нужные нам данные.
 5. Успех
 ![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/XXE/Screenshot_20200520_205223.png)
 

 <b>Lab: Exploiting XInclude to retrieve files</b>
  1. Перехватывам такой же запрос, как и в прошлый раз.
  2. Видим,что открытого XML текста там нет
  3. Используем Xi : вставлеям в ProductId строчку:
     <foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>
  4. Успех
  ![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/XXE/Screenshot_20200520_210039.png)


 <b>Lab: Exploiting XXE via image file upload</b>
  1. В указаниях к лаюе написано, что SVG картинки используют xml
  2. Находим, что в комментариях можно прислать картинку, забрасываем его всяким мусором и перехватываем запрос
  3. Смотрим на структуру запроса, касающися картинки - кроме названия файла туда же подгружается всё его содержимое. 
  4. Пишим в структуру запроса классическую xml - 
    <?xml version="1.0" standalone="yes"?>
    <!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]>
  5. Теперь надо вывести куда-то содержимое xxe. Благо, мы подгружаем картинку, так что запишем текст туда
  ![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/XXE/Screenshot_20200520_212552.png)
  6. Смотрим загруженный нами аватар.
  7. Успех
  ![alt text](https://raw.githubusercontent.com/StonePardon/Hack_all_the_things/master/XXE/avatars.png)
