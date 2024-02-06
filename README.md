#  Виджет для подключения eXpress messenger на сайт

## Установка

Для подключения виджета, скачайте библиотеку в ваш проект и вставьте на странице тег script c ссылкой на файл express.js и link на style.css

```html
<link rel="stylesheet" href="/style.css">
<script src="/index.js">
```

или установите с помощью npm 

```
npm i @expressms/express-widget

import { ExpressWidget } from '@expressms/express-widget'
import '@expressms/express-widget/style.css'
```

## Использование
Разместите на странице следующий код: 
```html
<script type="text/javascript">
    new ExpressWidget({
        elementId: 'express-button',
        url: 'https://corp.express',
    })
</script>
```

## Параметры
* `url` - **обязательно** ссылка на eXpress messenger
* `elementId` - **опционально** id элемента на странице в который отрисуется кнопка вызова eXpress messenger, если не указать будет отрисовано перед закрывающим тегом `body`
* `containerId` - **опционально** id элемента на странице в который отрисуется iframe eXpress messenger (использовать для модальных окон), если не указать будет отрисовано перед закрывающим тегом `body`
* `chatId` - **опционально** id чата, будет открыт после разворачивания приложения
* `buttonStatus` - **опционально** boolean, изменение фона кнопки открытия виджета, в зависимости от входа в приложение

## Методы
* `handleOpen` - открывает окно приложения
* `handleClose` - закрывает окно приложения
* `handleToggle` - открывает или закрывает окно в зависимости от текущего значения
* `handleOpenApp` - открывает приложение если оно установлено, если приложения нет - окно приложения, можно указать ид чата, логин пользователя или huid
* `handleOpenChat` - открывает только окно приложения, можно указать ид чата, логин пользователя, huid и isCall - для совершения звонка
* `handleCallUser` - открывает окно приложения и совершает вызов, можно указать логин пользователя и huid

Пример:
```html
<html>
    <head>
      <link rel="stylesheet" href="/style.css">
    </head>
    <body>
        <button onclick="expressButton.handleOpen()">Open</button>
        <button onclick="expressButton.handleClose()">Close</button>
        <button onclick="expressButton.handleToggle()">Toggle</button>
        
        <button onclick="expressButton.handleOpenApp()">Open app desktop</button>
        <button onclick="expressButton.handleOpenApp('a1f54e85-ba30-53f4-bd57-39d4c2d643b9')">Open app chat id desktop</button>
        <button onclick="expressButton.handleOpenApp('testLogin');">Open chat user name (testLogin) desktop</button>
        <button onclick="expressButton.handleOpenApp({ userHuid: '4015b33e-c7f4-5271-ae50-3b99508cb0d9', isCall: true });">Open chat user huid and call desktop</button>
        <button onclick="expressButton.handleOpenApp({ userName: 'testLogin@test.test.ru' });">Open chat user name (testLogin) desktop</button>
        <button onclick="expressButton.handleOpenApp({ chatId: '28f9a9b2-1a1e-5e25-b99c-fcf0e48fb406' });">Open chat id desktop</button>
        
        <button onclick="expressButton.handleOpenChat('a1f54e85-ba30-53f4-bd57-39d4c2d643b9')">Open chat id</button>
        <button onclick="expressButton.handleOpenChat('testLogin');">Open chat user name (testLogin)</button>
        <button onclick="expressButton.handleOpenChat({ userHuid: '4015b33e-c7f4-5271-ae50-3b99508cb0d9' });">Open chat user huid</button>
        <button onclick="expressButton.handleOpenChat({ userName: 'testLogin@test.test.ru' });">Open chat user name (testLogin)</button>
        <button onclick="expressButton.handleOpenChat({ chatId: '28f9a9b2-1a1e-5e25-b99c-fcf0e48fb406' });">Open chat id</button>

        <button onclick="expressButton.handleCallUser({ userHuid: '4015b33e-c7f4-5271-ae50-3b99508cb0d9' });">Open chat user huid and call</button>
        <button onclick="expressButton.handleCallUser({ userName: 'testLogin@test.test.ru' });">Open chat user name (testLogin) and call</button>
        <script src="/index.js"></script>
        <script>
            const expressButton = new ExpressWidget({
                url: 'https://corp.express',
            })
        </script>
    </body>
</html>
```
