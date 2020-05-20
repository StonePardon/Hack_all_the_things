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
