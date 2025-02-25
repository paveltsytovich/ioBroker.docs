---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.meteoalarm/README.md
title: ioBroker.meteoalarm
hash: GiKt6up6qUq4Ido90T1D1UfgDqhAQKHmL3T9gF8Fh48=
---
![логотип](../../../en/adapterref/iobroker.meteoalarm/admin/meteoalarm.png)

![Значок Greenkeeper](https://badges.greenkeeper.io/jack-blackson/ioBroker.meteoalarm.svg)
![Версия NPM](http://img.shields.io/npm/v/iobroker.meteoalarm.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.meteoalarm.svg)
![Количество установок](http://iobroker.live/badges/meteoalarm-stable.svg)
![NPM](https://nodei.co/npm/iobroker.meteoalarm.png?downloads=true)

# IoBroker.meteoalarm
=================

meteoalarm Адаптер для ioBroker ---------------------------------------------- -------------------------------- Этот адаптер получает аварийные сигналы о погоде от meteoalarm.eu, который включает ветер, снег, дождь , высокая и низкая температура, и т. д. Эта информация доступна на местном языке и для подробных регионов.

## Как это использовать
Пожалуйста, перейдите на http://meteoalarm.eu и выберите свой регион. Затем перейдите к символу RSS в правом верхнем углу, щелкните правой кнопкой мыши и скопируйте ссылку. Это ссылка, которую вы, пожалуйста, добавьте в настройку адаптера.

![логотип](../../../en/adapterref/iobroker.meteoalarm/screenshot.png)

## Доступные поля
| Имя поля | Описание |
|:---:|:---:|
| Последнее обновление | Дата, когда адаптер получил данные в последний раз |
| Ссылка | Ссылка на RSS-канал |
| Местоположение | Тревога Местоположение |
| Дата публикации | Дата публикации тревоги по данным сайта |
| HTMLToday | HTML Виджет, который отображает сигналы тревоги на сегодня |
| Сегодня / Завтра | Эти точки данных доступны на сегодня и завтра: |
| Текст | Тревога Текст на языке конкретной страны |
| С | Дата начала тревоги |
| До | Дата окончания тревоги |
| Тип | Тип тревоги как число |
| TypeText | Тип тревоги в виде текста |
| Уровень | Уровень тревоги как число |
| LevelText | Уровень тревоги в виде текста |
| Цвет | Цвет будильника для виджетов |
| Иконка | Значок типа тревоги |

## Типы тревог
| Тип тревоги | Описание |
|:---:|:---:|
| 1 | Ветер |
| 2 | Снег / Лед |
| 3 | Гром и молния |
| 4 | Туман |
| 5 | Высокая температура |
| 6 | Низкая температура |
| 7 | Побережье Событие |
| 8 | Форрест огонь |
| 9 | Avalanche |
| 10 | дождь |
| 11 | Unknown |
| 12 | Flood |
| 13 | Rain-Flood |

## Уровни тревоги
| Уровень тревоги | Описание |
|:---:|:---:|
| Зеленый | На данный момент нет доступных предупреждений. |
| Желтый | Погода потенциально опасна. Прогнозируемые погодные явления не являются необычными, но повышенное внимание следует уделять деятельности, подверженной метеорологическим рискам. Держите себя в курсе ожидаемых метеорологических условий и не подвергайте себя риску, которого можно избежать. |
| Апельсин | Погода опасная. Необычные метеорологические явления были предсказаны. Возможны повреждения и несчастные случаи. Будьте очень внимательны и осторожны и следите за ожидаемыми метеорологическими условиями. |
| Красный | Погода очень опасная. Необычно интенсивные метеорологические явления были предсказаны. Чрезвычайный ущерб и несчастные случаи, часто на больших площадях, угрожают жизни и имуществу. |

## Поддерживаемые страны
* Австрия
* Хорватия
* Финнланд
* Германия
* Венгрия
* Италия
* Нидерланды
* Норвеж
* Словакия
* Испания
* Швейцария

Если вы не можете найти свою страну, пожалуйста, создайте вопрос на github, и я буду рад добавить его

## Невозможные страны
* Франция (RSS-канал недоступен)
* Португалия (разделение невозможно)
* Словения (RSS-канал недоступен)

## Особенности для реализации
* Обработка нескольких аварийных сигналов за один день

## 1.0.6 (2019-10-19)
* (Джек-Блэксон) Добавлено Швейцария и Словакиа

## 1.0.5 (2019-09-22)
* (Джек-Блэксон) Небольшие настройки регистрации

## 1.0.4 (2019-09-11)
* (Джек-Блэксон) Ошибка Трэвиса

## 1.0.3 (2019-09-09)
* (jack-blackson) Небольшие исправления, переход от типа "deamon" к "schedule"

## 1.0.2 (2019-08-25)
* (Джек-Блэксон) Информация о переупорядоченном выпуске

### 1.0.1 (2019-08-18)
* (Джек-Блэксон) Исправлена ошибка без значка тревоги

### 1.0.0 (2019-08-12)
* (Джек-Блэксон) Релиз-версия

### 0.6.0 (2019-08-05)
* (jack-blackson) Хранить иконки погоды локально в адаптере

### 0.5.0 (2019-07-21)
* (Джек-Блэксон) Время ожидания ручки
* (jack-blackson) Переводы для всех языков
* (Джек-Блэксон) проверка URL

### 0.4.0 (2019-07-20)
* (Джек-Блэксон) Добавлены данные для NL, NO, HR, FI, ES
* (jack-blackson) Добавлен тип текста, тип теперь пуст, если уровень равен 1 (без предупреждения)
* (Джек-Блэксон) Скорректированные цвета

### 0.3.0 (2019-07-13)
* (jack-blackson) Добавлен виджет HTML
* (Джек-Блэксон) Значок исправления

### 0.2.0 (2019-07-12)
* (Джек-Блэксон) Добавлены данные "Завтра"

### 0.1.0 (2019-07-11)
* (Джек-Блэксон) начальная версия

## Кредиты
Значок колокольчика, разработанный Freepik с www.flaticon.com

## Changelog

## License
The MIT License (MIT)

Copyright (c) 2019 jack-blackson <blacksonj7@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.