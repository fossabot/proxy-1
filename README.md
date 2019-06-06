# proxy
Готовый вариант запуска собственного прокси-сервера на базе протокола MTProto.

### Что необходимо?
Для запуска собственного прокси-сервера, вам необходимо:

1. Абсолютно чистый сервер с ОС Ubuntu 18.04 или старше
2. Любой процессор/ОЗУ/диск (хотя бы: 1 ядро, 512 Мб ОЗУ, 5 ГБ диска)
3. Открытый порт и отсутствие любого файерволла (желательно)

### Как запустить?
Для запуска собственного прокси-сервера, вам необходимо выполнять всё **строго по пунктам**. Если вы опытный разработчик, то можете сразу переходить к пункту "6" без лишней шумихи. Если нет, то инструкция ниже.

1. `curl -sL https://deb.nodesource.com/setup_12.x | bash - && sudo apt-get install nodejs npm`
2. `npm install pm2 -g`
3. `cd && mkdir mtproxy && cd mtproxy`
4. `npm install @mtproto-org/mtproxy`
5. `touch *.js`
7. 
```javascript
const mtproxy = require('@mtproto-org/mtproxy')

mtproxy()
```
8. `pm2 start *.js -i max`

[![Application Result](https://i.kxj.ru/scr/2019-06-06_17.32.00.png)


#### Дополнительные настройки

1. Запустить: `pm2 start *.js -i max`
2. Перезапустить: `pm2 restart *.js`
3. Выключить: `pm2 stop *.js`

### Что дальше? 
```javascript
const mtproxy = require('@mtproto-org/mtproxy')

const options = {
  port: 2233,
  secret: '11112222333344445555666677778888'
}

mtproxy(options)
```

1. Порт для подключения: `2233`
2. Секретный ключ: `11112222333344445555666677778888`

Вы можете поменять стандартный порт и секретный ключ, если хотите полной приватности. Рекомендуем сгенерировать секретный ключ из 32-х случайных чисел. Эти настройки установлены для тех, кому необходимо сразу запустить и пользоваться прокси-сервером.

### Как подключиться?
1. Перейдите в `Настройки`
2. Далее в `Продвинутые настройки`
3. Далее в `Тип соединения`
4. Выберите `Использовать собственный прокси`
5. `Добавить прокси`
6. Выберите `MTPROTO`
7. Хост - IP-адрес сервера или его `hostname`
8. Порт - по умолчанию стоит `2233` или смените на свой (если меняли `mtproxy.js`)
9. Ключ - введите ключ прокси-сервера (по умолчанию: `11112222333344445555666677778888`)
10. Нажмите кнопку `Сохранить`
11. Как только сервер добавится в список ваших прокси, выберите его и дождитесь статуса `Подключён`
12. Готово!

### Ревизия от Fossa

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fmtproto-org%2Fproxy.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fmtproto-org%2Fproxy?ref=badge_large)

### Копирайт
Разработано командой [MTProto.org](https://mtproto.org) и опубликовано согласно с условиями лицензии MIT License.

Copyright 2019, MTProto.org Team

*Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:*

*The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.*

*THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.*
