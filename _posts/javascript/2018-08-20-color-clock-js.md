---
layout: post
title: Часы с цветовым фоном на Javascript / Color clock JS.
description: Создание простых часов с цветным фоном на Javascript и CSS.
category: javascript
permalink: /cvetniye-chasy-javascript/
---

Итак, сегодня "накидаем" концепт для простеьких часов, цвет фона которых динамично меняется. Для этого нам потребуется объект [Date](https://learn.javascript.ru/datetime) и конечно же ES6(ES2015).

### Структура HTML
Набросаем небольшой "скелет" странички... 
<!--excerpt-->
<br />


```javascript
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
    </head>
    <body>
    
    <div class="wrapper">
        <h1>00:00:00</h1>
        <p>#000000</p>
    </div>

    <script src='app.js'></script>
    
    </body>
</html>
```
Не забывайте, что объекты в JavaScript передаются по ссылке. Почитать про это можно [здесь](https://learn.javascript.ru/object)