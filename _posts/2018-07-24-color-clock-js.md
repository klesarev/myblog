---
layout: post
title: Часы с цветовым фоном на Javascript / Color clock JS.
description: Создание простых часов с цветным фоном на Javascript и CSS.
category: javascript
permalink: /cvetniye-chasy-javascript/
image: colorjs.jpg
tags: [documentation,sample]
---

Итак, сегодня сделаем концепт простеньких часов, цвет фона которых динамично меняется. Для этого нам потребуется объект [Date](https://learn.javascript.ru/datetime) и конечно же ES6(ES2015).

<!--excerpt-->

### Структура HTML
Набросаем небольшой "скелет" странички... 

```html
<!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <link rel="stylesheet" href="style.css">
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
Затем создадим и подключим файлы **app.js** и **style.css**, в которых соответственно будут наши файлы - скрипта и стилизация. 

### Оформление
<br/>
```css
/*отцентрируем блок вертикально и горизонтально*/
.wrapper {
    text-align: center;
    position: fixed;
    top: 45%;
    left: 50%;
    transform: translate(-50%,-50%);
}
h1 {
    font-size: 62px;
    font-family: -apple-system, BlinkMacSystemFont, 
                 Segoe\ UI, Roboto, Oxygen, Ubuntu, 
                 Cantarell, Fira\ Sans, Droid\ Sans, 
                 Helvetica\ Neue, sans-serif;
    font-weight: 300;
    color: #FFF;
    margin: 10px;
}
p {
    color: #FFF;
    margin-top: 5px;
    font-family: -apple-system, BlinkMacSystemFont, 
                 Segoe\ UI, Roboto, Oxygen, Ubuntu, 
                 Cantarell, Fira\ Sans, Droid\ Sans, H
                 elvetica\ Neue, sans-serif;
    font-weight: 300;
}
```

Давайте остановимся подробнее на данной строчке. 
```
font-family: -apple-system, BlinkMacSystemFont...;
```
Это правило проверяет, установлены ли перечисленные семейства шрифтов в системе и если да, то применяет один из их. Например **-apple-system** устанавливает отображение системного шрифта на IOS и Mac OS.

### Javascript

Приступим непосредственно к написанию скрипта. Здесь нам понадобится Babel для преобразования ES6 -> ES5. Инструкцию по настройке и установке можно поспотреть [здесь](http://babeljs.io/)
<br />
```javascript
const body  = document.querySelector('html');
const h1    = document.querySelector('h1');
const p     = document.querySelector('p');

function changeColor() {
    const now = new Date();
    let hours = now.getHours() < 10 ? "0" + now.getHours() : now.getHours();
    let minutes = now.getMinutes() < 10 ? "0" + now.getMinutes() : now.getMinutes();
    let seconds = now.getSeconds() < 10 ? "0" + now.getSeconds() : now.getSeconds();
    h1.innerHTML = `${hours}:${minutes}:${seconds}`;
    p.innerHTML = `#${hours}${minutes}${seconds}`;
    body.style.backgroundColor =`#${hours}${minutes}${seconds}`;
};

let timer = setInterval(changeColor,1000);
```
<br />
Давайте теперь разберем код выше. Задаем 3 переменных **body**, **h1** и **p**, c помощью нативного метода JS - querySelector('_your css selector here..._'). Его аналог в jQuery это - $('_your selector here..._'). 
```javascript
const body  = document.querySelector('html');
const h1    = document.querySelector('h1');
const p     = document.querySelector('p');
```
<br />
Напишем функцию **changeColor**, которая кaк следует из названия и будет менять фон нашей страницы.
```javascript
function changeColor() {
    const now = new Date();
}
```
Получаем текущие дату и время с помощью обхекта Date
<br />
```javascript
let hours = now.getHours() < 10 ? "0" + now.getHours() : now.getHours();
let minutes = now.getMinutes() < 10 ? "0" + now.getMinutes() : now.getMinutes();
let seconds = now.getSeconds() < 10 ? "0" + now.getSeconds() : now.getSeconds();
```
С помощью методов: _getHours()_, _getMinutes()_ и _getSeconds()_ извлекаем часы, минуты и секунды. При этом, если число меньше 10, то подставляем 0 - "для красоты", чтобы вместо такого времени - _8:6:20_ получить такое -> _08:06:20_.
<br />
```javascript
h1.innerHTML = `${hours}:${minutes}:${seconds}`;
p.innerHTML = `#${hours}${minutes}${seconds}`;
```
Вставляем в H1 наше текущее время в формате строки с помощью строковых шаблонов, подробнее [здесь](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/template_strings). Для отображения цвета в ставим в начало символ **#** чтобы получить цвет в формате HEX (_например #206542_);
<br />
Применяем получившийся цвет к нашему body с помощью все тех же _строковых шаблонов_.
```javascript
body.style.backgroundColor =`#${hours}${minutes}${seconds}`;
```
<br />
Теперь нам остается вызывать нашу функцию каждую секунду, с помощью метода _**setInterval()**_
```javascript
let timer = setInterval(changeColor,1000);
```

### Вывод
Довольно нехитрые часики получились. В сети похожих примеров "воз и маленькая тележка", поэтому в следующих статьях мы сделаем их немного интереснее:

* Сделаем смену цвета более плавной
* Добавим кадому времени суток свой цвет(диапазон цветов)
* Добавим настройку времени вручную.

To be continued....

