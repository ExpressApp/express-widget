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
        url: 'https://web-alpha.ccsteam.ru',
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
* `handleOpenApp` - открывает приложение если оно установлено, если приложения нет - окно приложения, можно указать ид чата или логин пользователя
* `handleOpenChat` - открывает только окно приложения, можно указать ид чата или логин пользователя

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
        
        <button onclick="expressButton.handleOpenChat('a1f54e85-ba30-53f4-bd57-39d4c2d643b9')">Open chat id</button>
        <button onclick="expressButton.handleOpenChat('testLogin');">Open chat user name (testLogin)</button>
        
        <script src="/index.js"></script>
        <script>
            const expressButton = new ExpressWidget({
                url: 'https://web-alpha.ccsteam.ru',
            })
        </script>
    </body>
</html>
```
