---
layout: post
author: Paul Finch
title: Цветовая тема браузера в Android
description: Цветовая тема для браузера. Color webkit theme Chrome.
tags: ["CSS", "HTML"]
image: color-theme.jpg
---

Начиная с версии 39, браузер Chrome для Anddroid поддерживает цветовые темы <code>theme-color</code> для вкладок. Вы наврное видели такой эффект, когда заходите на facebook - вкладка окрашивается в цвета сайта. Чтобы использовать цветовую тему нужно сделать следующее.

<!--excerpt-->
<br />
Итак, для отображения цветовой темы нужно добавить специальный мета-тег в блок <head> следующее:
<code> 
    <meta name="theme-color" content="#db5945">
</code>
Где атрибут <em>content</em> содержит цвет в формате <abbr title="цвет в 16-ом формате, например: #fff (белый)">HEX</abbr>. С браузерами в Windows Phone и IOS могу возникнуть проблемы. Чтобы добавить поддержку цветовых тем для всех систем, можно использовать следующий код.
```html
<!-- Chrome, Firefox OS and Opera -->
<meta name="theme-color" content="#4285f4">

<!-- Windows Phone -->
<meta name="msapplication-navbutton-color" content="#4285f4">

<!-- iOS Safari -->
<meta name="apple-mobile-web-app-status-bar-style" content="#4285f4">
```
Кстати,вот неплохой сервис подбора цветовой схемы для сайта [Adobe Color CC](https://color.adobe.com/ru/explore/?filter=most-popular&time=all), ранее известный как Adobe Kuler. В разеде "популярные" много неплохих цветовых схем, которые можно изменить по усмотрению.
