---
layout: post
title: "Axios - популярная библиотека для HTTP запросов"
description: "Axios: http запросы, документация на русском языке, уроки."
author: "Paul Finch"
tags: ["JavaScript", "ReactJS", "Git", "NodeJS"]
image: axios.jpg
---

В этой статье вы сможете прочесть перевод на русский язык оф.документации по Axios - довольно популярной библиотеке среди разработчиков. Ее применяют не только с React, Angular и Vue, но и вместе с серверным Node JS. Axios сочетает в себе простоту использования, богатый функционал и неплохую поддержку. Одной из главых особенностей является то, что Axios основан на [__Promise__](https://learn.javascript.ru/promise)

<!--excerpt-->

<br/>
### Отличительные особенности
- XMLHttpRequests из браузеров
- HTTP запросы из NodeJS
- Полная поддержка Promise API
- Перехват запросов и ответов
- Преобразование получаемых и принимаемых данных
- Отмена запроса
- Автоматическое преобразование JSON
- Защита на стороне клиента от от [CSRF-атак](https://learn.javascript.ru/csrf)

<br/>
### Поддержка браузеров

![axios browser support]({{ "/assets/img/axios-browser-support-2.png" }})

![axios browser support]({{ "/assets/img/axios-browser-support.svg" }})


<br/>
### Установка

_посредством __npm__ (у вас должен быть установлен пакет Node JS [ссылка](https://nodejs.org/en/) )_
```js
$ npm install axios
```
*c помощью менеджера пакетов bower*
```js
$ bower install axios
```
*используя ссылку на CDN, которую можно разместить непосредственно на странице*
```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

<br/>
### Примеры использования
#### GET - запросы
```javascript
// Make a request for a user with a given ID
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

// Optionally the request above could also be done as
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

// Want to use async/await? Add the `async` keyword to your outer function/method.
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

_продолжение следует..._

Если вы заметили неточность в переводе, или хотите дополнить его - пишите на [__e-mail__](trickyfox85@gmail.com) или в ВК. Официальную документацию на английском языке можно найти по адресу - https://github.com/axios/axios
