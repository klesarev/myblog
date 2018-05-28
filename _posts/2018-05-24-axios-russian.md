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
#### GET - запрос
```javascript
// делаем GET запрос чтобы получить пользователя (user) 
// с указанным параметром ID = 12345
axios.get('/user?ID=12345')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });

// так же, параметры можно передавать отдельно, в виде объекта
// схема ('url', params), где params объект
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

// Хотите использовать async/await? Не проблема! Добавьте "async" - перед вашим методом/функуцей,
// и await перед самими запросом.
// Подробнее про async/await
// https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/async_function
async function getUser() {
  try {
    const response = await axios.get('/user?ID=12345');
    console.log(response);
  } catch (error) {
    console.error(error);
  }
}
```

> NOTE: async/await - часть нового стандарта ECMAScript 2017/ Этот функционал не поддерживается браузерами IE и более старыми.
> подробнее здесь - https://caniuse.com/#feat=async-functions
> также применяйте BABEL для того чтобы использовать поcелдение нововведения в JS - https://babeljs.io/

#### GET - запрос
```javascript
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
})
.then(function (response) {
    console.log(response);
})
.catch(function (error) {
    console.log(error);
});
```
#### Несколько запросов одновременно
```javascript
function getUserAccount() {
  return axios.get('/user/12345');
}

function getUserPermissions() {
  return axios.get('/user/12345/permissions');
}

axios.all([getUserAccount(), getUserPermissions()])
  .then(axios.spread(function (acct, perms) {
    // Both requests are now complete
  }));
```

<br />
### Axios API

Запросы могут быть выполнены путем передачи параметров/настроек в axios. Схема - ```axios(config)```
```javascript
// отправка POST запроса
axios({
  method: 'post',
  url: '/user/12345',
  data: {
    firstName: 'Fred',
    lastName: 'Flintstone'
  }
});
```
```javascript
// отправка GET запроса для получения изображения
// с другого сервера
axios({
  method:'get',
  url:'http://bit.ly/2mTM3nY',
  responseType:'stream'
})
  .then(function(response) {
  response.data.pipe(fs.createWriteStream('ada_lovelace.jpg'))
});
```
__axios(url[, config])__
```javascript
// отправка GET запроса с параметрами по умолчанию
axios('/user/12345');
```
<br />
### Методы для HTTP запросов

Для Вашего удобства были созданы псевдонимы для всех поддерживаемых методов запросов.
- __axios.request(config)__
- __axios.get(url[, config])__
- __axios.delete(url[, config])__
- __axios.head(url[, config])__
- __axios.options(url[, config])__
- __axios.post(url[, data[, config]])__
- __axios.put(url[, data[, config]])__
- __axios.patch(url[, data[, config]])__

Используя данные методы, Вам необязательно указывать свойства ```method``` и ```data``` в настройках.

<br/>
### Мультизапросы
Вспомогательные функции для того чтобы использовать несколько запросов одновременно
- __axios.all(iterable)__
- __axios.spread(callback)__

<br/>
### Cоздание нового экземпляра Axios
Вы можете создать новый экземпляр(образец) **Axios** cо своими настройками
__axios.create([config])__
```javascript
const instance = axios.create({
  baseURL: 'https://some-domain.com/api/',
  timeout: 1000,
  headers: {'X-Custom-Header': 'foobar'}
});
```  

<br />
### Методы экземпляра
Доступные методы экземпляра(образца) Axios перечислены ниже. Указанные настройки в них будут объединены с конфигурацией экземпляра.
- __axios#request(config)__
- __axios#get(url[, config])__
- __axios#delete(url[, config])__
- __axios#head(url[, config])__
- __axios#options(url[, config])__
- __axios#post(url[, data[, config]])__
- __axios#put(url[, data[, config]])__
- __axios#patch(url[, data[, config]])__



<br />
### Настройки запроса

Это параметры конфигурации для запросов. Требуется только URL-адрес. Если тип запроса не указан, то по умолчанию будет выполняться GET запрос. Запросы указываются при вызове метода, в объекте.
_пример: axios.get(params)_, где __*params*__ настройки

```javascript
{
  // `url` адрес сервера, куда отправляется запрос
  url: '/user',

  // `method` метод/тип запроса
  method: 'get', // по умолчанию

  // `baseURL` will be prepended to `url` unless `url` is absolute.
  // It can be convenient to set `baseURL` for an instance of axios to pass relative URLs
  // to methods of that instance.
  baseURL: 'https://some-domain.com/api/',

  // `transformRequest` allows changes to the request data before it is sent to the server
  // This is only applicable for request methods 'PUT', 'POST', and 'PATCH'
  // The last function in the array must return a string or an instance of Buffer, ArrayBuffer,
  // FormData or Stream
  // You may modify the headers object.
  transformRequest: [function (data, headers) {
    // Do whatever you want to transform the data

    return data;
  }],

  // `transformResponse` allows changes to the response data to be made before
  // it is passed to then/catch
  transformResponse: [function (data) {
    // Do whatever you want to transform the data

    return data;
  }],

  // `headers` are custom headers to be sent
  headers: {'X-Requested-With': 'XMLHttpRequest'},

  // `params` are the URL parameters to be sent with the request
  // Must be a plain object or a URLSearchParams object
  params: {
    ID: 12345
  },

  // `paramsSerializer` is an optional function in charge of serializing `params`
  // (e.g. https://www.npmjs.com/package/qs, http://api.jquery.com/jquery.param/)
  paramsSerializer: function(params) {
    return Qs.stringify(params, {arrayFormat: 'brackets'})
  },

  // `data` is the data to be sent as the request body
  // Only applicable for request methods 'PUT', 'POST', and 'PATCH'
  // When no `transformRequest` is set, must be of one of the following types:
  // - string, plain object, ArrayBuffer, ArrayBufferView, URLSearchParams
  // - Browser only: FormData, File, Blob
  // - Node only: Stream, Buffer
  data: {
    firstName: 'Fred'
  },

  // `timeout` specifies the number of milliseconds before the request times out.
  // If the request takes longer than `timeout`, the request will be aborted.
  timeout: 1000,

  // `withCredentials` indicates whether or not cross-site Access-Control requests
  // should be made using credentials
  withCredentials: false, // default

  // `adapter` allows custom handling of requests which makes testing easier.
  // Return a promise and supply a valid response (see lib/adapters/README.md).
  adapter: function (config) {
    /* ... */
  },

  // `auth` indicates that HTTP Basic auth should be used, and supplies credentials.
  // This will set an `Authorization` header, overwriting any existing
  // `Authorization` custom headers you have set using `headers`.
  auth: {
    username: 'janedoe',
    password: 's00pers3cret'
  },

  // `responseType` indicates the type of data that the server will respond with
  // options are 'arraybuffer', 'blob', 'document', 'json', 'text', 'stream'
  responseType: 'json', // default

  // `responseEncoding` indicates encoding to use for decoding responses
  // Note: Ignored for `responseType` of 'stream' or client-side requests
  responseEncoding: 'utf8', // default

  // `xsrfCookieName` is the name of the cookie to use as a value for xsrf token
  xsrfCookieName: 'XSRF-TOKEN', // default

  // `xsrfHeaderName` is the name of the http header that carries the xsrf token value
  xsrfHeaderName: 'X-XSRF-TOKEN', // default

  // `onUploadProgress` allows handling of progress events for uploads
  onUploadProgress: function (progressEvent) {
    // Do whatever you want with the native progress event
  },

  // `onDownloadProgress` allows handling of progress events for downloads
  onDownloadProgress: function (progressEvent) {
    // Do whatever you want with the native progress event
  },

  // `maxContentLength` defines the max size of the http response content in bytes allowed
  maxContentLength: 2000,

  // `validateStatus` defines whether to resolve or reject the promise for a given
  // HTTP response status code. If `validateStatus` returns `true` (or is set to `null`
  // or `undefined`), the promise will be resolved; otherwise, the promise will be
  // rejected.
  validateStatus: function (status) {
    return status >= 200 && status < 300; // default
  },

  // `maxRedirects` defines the maximum number of redirects to follow in node.js.
  // If set to 0, no redirects will be followed.
  maxRedirects: 5, // default

  // `socketPath` defines a UNIX Socket to be used in node.js.
  // e.g. '/var/run/docker.sock' to send requests to the docker daemon.
  // Only either `socketPath` or `proxy` can be specified.
  // If both are specified, `socketPath` is used.
  socketPath: null, // default

  // `httpAgent` and `httpsAgent` define a custom agent to be used when performing http
  // and https requests, respectively, in node.js. This allows options to be added like
  // `keepAlive` that are not enabled by default.
  httpAgent: new http.Agent({ keepAlive: true }),
  httpsAgent: new https.Agent({ keepAlive: true }),

  // 'proxy' defines the hostname and port of the proxy server
  // Use `false` to disable proxies, ignoring environment variables.
  // `auth` indicates that HTTP Basic auth should be used to connect to the proxy, and
  // supplies credentials.
  // This will set an `Proxy-Authorization` header, overwriting any existing
  // `Proxy-Authorization` custom headers you have set using `headers`.
  proxy: {
    host: '127.0.0.1',
    port: 9000,
    auth: {
      username: 'mikeymike',
      password: 'rapunz3l'
    }
  },

  // `cancelToken` specifies a cancel token that can be used to cancel the request
  // (see Cancellation section below for details)
  cancelToken: new CancelToken(function (cancel) {
  })
}
```
__продолжение следует...__

Если вы заметили неточность в переводе, или хотите дополнить его - пишите на [__e-mail__](trickyfox85@gmail.com) или в ВК. Официальную документацию на английском языке можно найти по адресу - https://github.com/axios/axios
