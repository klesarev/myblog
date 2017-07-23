---
layout: post
title: Глубокое копирование объектов на чистом JS.
description: Глубокое копирование объяектов в JavaScript. Объекты в Javascript.
category: javascript
permalink: /clonirovanie-objectov-js/
---

В некоторых ситуациях необходимо глубокуое копирование объекта в JavaScript. Например для реализации опций / настроек в модуле. 

<!--excerpt-->
<br />
Функция для глубокого копирования.
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