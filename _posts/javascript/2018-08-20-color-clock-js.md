---
layout: post
title: Часы с цветовым фоном на Javascript / Color clock JS.
description: Создание простых часов с цветным фоном на Javascript и CSS.
category: javascript
permalink: /cvetniye-chasy-javascript/
---

Итак, сегодня "накидаем" концепт для простеньких часов, цвет фона которых динамично меняется. Для этого нам потребуется объект [Date](https://learn.javascript.ru/datetime) и конечно же ES6(ES2015).

<!--excerpt-->

#### Структура HTML
Набросаем небольшой "скелет" странички... 

```
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
Затем создадим и подключим файлы **app.js** и **style.css**, в которых соответственно будет наш скрипт и стилизация. Начнем с оформления.

#### Оформление

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
    font-family: -apple-system, BlinkMacSystemFont, Segoe\ UI, Roboto, Oxygen, Ubuntu, Cantarell, Fira\ Sans, Droid\ Sans, Helvetica\ Neue, sans-serif;
    font-weight: 300;
    color: #FFF;
    margin: 10px;
}
p {
    color: #FFF;
    margin-top: 5px;
    font-family: -apple-system, BlinkMacSystemFont, Segoe\ UI, Roboto, Oxygen, Ubuntu, Cantarell, Fira\ Sans, Droid\ Sans, Helvetica\ Neue, sans-serif;
    font-weight: 300;
}
```

Давайте остановимся подробнее на данной строчке. 
```
font-family: -apple-system, BlinkMacSystemFont, Segoe\ UI, Roboto, Oxygen, Ubuntu, Cantarell, Fira\ Sans, Droid\ Sans, Helvetica\ Neue, sans-serif;
```
Это правило проверяет, установлены ли перечисленные семейства шрифтов в системе и устанавливает их. Например **-apple-system** устанавливает отображение системного шрифтаб устанвленного на IOS и Mac OS. В целом эти шрифты аккуранты и легко читаются.

#### Javascript

Притступим непосредственно к написанию скрипта. Здесь нам понадобится Babel для преобразования ES6 -> ES5. Инструкцию по настройке и устанвоке можно поспотреть [здесь](http://babeljs.io/)

Сначала приведу полный листинг кода.
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

1. Итак, в начале мы задаем 3 переменных **body**, **h1** и **p**, выбирая их c помощью нативного метода JS - querySelector('your selector here...'). Его аналог в jQuery это - $('your selector here/...'), который знаком многим. 
```javascript
const body  = document.querySelector('html');
const h1    = document.querySelector('h1');
const p     = document.querySelector('p');
```
2. Напишем функцию **changeColor**, которая кск следует из названия собственно и будет менять фон нашей страницы.
