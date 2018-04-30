---
layout: post
author: Paul Finch
title: "Копирование объектов."
description: "Копирование объектов в JavaScript. Объекты в Javascript. javascript clone function."
categories: javascript
tags: [ES6, ES5, OOP]
---

В некоторых ситуациях необходимо копирование объекта в JavaScript с перебором всех свойств. Например для реализации опций / настроек в модуле. 

<!--excerpt-->
<br />
Небольшая функция для копирования объекта в javascript.
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