---
layout: post
title: Глубокое копирование объектов на чистом JS.
description: Глубокое копирование объектов в JavaScript. Объекты в Javascript. javascript clone function.
category: javascript
permalink: /clonirovanie-objectov-js/
---

В некоторых ситуациях необходимо глубокое копирование объекта в JavaScript. Например для реализации опций / настроек в модуле. 

<!--excerpt-->
<br />
Небольшая функция для глубокого копирования.
```javascript
function makeClone(obj) {
    var clone = {}; // Создаем новый пустой объект
    
    for (let prop in obj) { 
        // Перебираем все свойства копируемого объекта
        // Только собственные свойства
        if (obj.hasOwnProperty(prop)) { 
        
        // Если свойство так же объект
        if ("object"===typeof obj[prop]) 
        
        // Делаем клон свойства
        clone[prop] = makeClone(obj[prop]); 
        
        // Или же просто копируем значение
        else
            clone[prop] = obj[prop]; 
        }
    }

    return clone;
}
```
Не забывайте, что объекты в JavaScript передаются по ссылке. Почитать про это можно [здесь](https://learn.javascript.ru/object)