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
* `chatId` - **опционально** id чата, будет открыт после разворачивания приложения

## Методы
* `handleOpen` - открывает окно приложения
* `handleClose` - закрывает окно приложения
* `handleToggle` - открывает или закрывает окно в зависимости от текущего значения

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

        <script src="/index.js"></script>
        <script>
            const expressButton = new ExpressWidget({
                url: 'https://corp.express',
            })
        </script>
    </body>
</html>
```
