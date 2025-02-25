---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.heatingcontrol/README.md
title: ioBroker.HeatingControl
hash: 1ToEgJe7doDulYCX0KfF2YpHGeMzxNdZcpovXFyKcI8=
---
![логотип](../../../en/adapterref/iobroker.heatingcontrol/admin/heatingcontrol.png)

![Количество установок](http://iobroker.live/badges/heatingcontrol-stable.svg)
![Версия NPM](http://img.shields.io/npm/v/iobroker.heatingcontrol.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.heatingcontrol.svg)
![NPM](https://nodei.co/npm/iobroker.heatingcontrol.png?downloads=true)
![Трэвис-CI](http://img.shields.io/travis/rg-engineering/ioBroker.heatingcontrol/master.svg)

# IoBroker.HeatingControl
Адаптер для управления вашей системой отопления.

Функции:

* Контроль заданных уровней температуры всех термостатов в соответствии с расписанием
* Настройка нескольких периодов отопления для каждого дня и ночи
* Поддерживает различные Homematic и Макс! термостаты
* поддерживает несколько профилей
* Если нет прямой связи между термостатом и приводом, привод можно отключить непосредственно от адаптера.
* В настоящее время привод отключается непосредственно при достижении заданной температуры. Как только заданная температура станет ниже фактической температуры, привод будет включен. (Для этого: реализовать улучшенный контроль)
* Поддерживается неограниченное количество термостатов, приводов и датчиков в комнате
* Термостат, привод и датчик автоматически определяются для каждой комнаты. Для этого используется функция (например, «нагрев»).
* Комнаты могут быть исключены из интерфейса администратора, если комната содержит термостат, но не должна контролироваться
* датчик используется для снижения целевой температуры (например, если окно открыто)
* Интерфейс для Feiertag-Adapter или любых других для обнаружения выходных дней. Государственный праздник может быть обычным днем или как воскресенье. (настройка администратора)
* ручное изменение температуры на определенное время
* заданный период нагрева
* Пример визуализации будет предоставлен позже

## Настройки
### Главный
* Функция = Функция, используемая для обнаружения термостатов, исполнительных механизмов и датчиков в помещении. Это один из перечислений системы
* часовой пояс = для использования cron для настройки заданий cron
* Путь к Feiertag - Adapter = если вы хотите использовать Feiertag-Adapter для автоматического определения выходного дня на сегодня, то укажите здесь путь (например, feiertage.0)
* удалить все устройства, когда администратор открывает = должен быть отключен. Включайте его только тогда, когда вам нужно удалить все настройки комнаты, привода и датчика. Поиск устройства будет выполнен, когда администратор адаптера откроет
* датчик используется = если у вас есть датчики окна, и вы хотите уменьшить целевую температуру, когда окно открыто, включите эту опцию
* актеры использовали = если вы хотите управлять приводами непосредственно с адаптера. На всякий случай нет прямой связи между термостатом и приводом.
* Используйте приводы, если период нагрева отсутствует = действителен только для приводов. Определяет, как приводы устанавливаются, когда период нагрева не активен
* Используйте приводы, если термостат отсутствует = действителен только для приводов. Если у вас есть комнаты без термостата, но с приводом отопления, вы можете постоянно включать или выключать их

### Профиль
* Тип профиля = поддерживается три различных типа профиля (понедельник - воскресенье или понедельник - пятница и суббота / воскресенье или каждый день)
* количество профилей = если вам нужно больше, то в профиле увеличьте это значение. Затем вы можете выбрать, какой профиль будет использоваться.
* количество периодов = определить, сколько ежедневных секций с различной температурой вам нужно. Чем больше вы установите, тем больше точек данных будет создано. Лучше использовать низкое значение (например, 5)
* "официальный выходной, например, воскресенье = если вы хотите установить целевые температуры в праздничные дни, например, в воскресенье, включите эту опцию. В противном случае настройки выходных дней такие же, как в обычные дни.
* HeatingPeriod = дата начала и окончания периода нагрева. Используется для установки «HeatingPeriodActive»

### Устройства
* список всех комнат. Вы можете отключить комнату здесь.
* Нажмите кнопку редактирования справа, чтобы открыть окно настроек термостатов, приводов и датчиков для этой комнаты.

### Редактировать комнату
* здесь вы можете проверить и установить идентификаторы объектов для термостатов, приводов и датчиков
* Вы можете добавить вручную новые термостаты, приводы или датчики. Просто нажмите кнопку +. Тогда вы получите пустую строку, которую необходимо заполнить. Кнопка «Правка» открывает список доступных устройств в системе.
* термостаты:

** должны быть заданы имя, целевой температурный OID и текущий температурный OID.

* приводы

** имя и OID для состояния должны быть установлены

* датчики

** имя и OID для текущего состояния должны быть установлены

## Требования
* Требуется версия узла 8 или выше

## Проблемы и запросы функций
* Если вы столкнулись с какими-либо ошибками или у вас есть запросы на функции для этого адаптера, пожалуйста, создайте проблему в разделе проблем GitHub адаптера на [github] (https://github.com/rg-engineering/ioBroker.heatingcontrol/issues ). Любая обратная связь приветствуется и поможет улучшить этот адаптер.

## Changelog

### 0.3.0 (2019-10-xx)
* (René) see issue #20 + #24: start and end of heating period is configurable in admin 
* (René) see issue #24: use external data point to set internal "present" data point 
* (René) see issue #15: manual temperatur override
* (René) reset DeleteAll at next admin start 


### 0.2.3 (2019-09-20)
* (René) see issue #19: handling of enums created in iobroker admin fixed
* (René) see issue #13: check order of periods; if order is wrong (next time is smaller than previous) then time si not used for cron and a warning appears in log
* (René) see issue #21: check temperatures after changing of period settings (e.g. time)
* (René) see issue #25: select OID for target and current of thermostat in admin overworked
* (René) change datapoint type from bool to boolean


### 0.2.2 (2019-09-13)
* (René) see issue #14: description of datapoint time changed ('from' instead 'until')
* (René) see issue #12: unnecessary warnings removed
* (René) see issue #17: seconds removed from time list
* (René) datepoint change handling reworked
* (René) see issue #18: take over values from external PublicHoliday-datapoint

### 0.2.1 (2019-09-08)
* (René) bug fixes in actuator handling

### 0.2.0 (2019-09-05)
* (René) path to Feiertag-Adapter can also include a complete datapoint path 

### 0.1.0 (2019-08-25)
* (René) redesign of data structure
	- more then one actuator, sensor and thermostat per room
	- three different profile types
	- manual configuration of devices (if device is not detected automatically)
	- interface to Feiertag-Adapter
	- public holiday as normal day or like sunday (setting in admin)
	- window sensor support. Reduce target temperature when window is open
	- !!ATTENTION!! data structure/objects has been changed. You need to update your visualisation settings

### 0.0.5 (2019-07-08)
* (René) support for max! thermostats

### 0.0.4 (2019-06-23)
* (René) debugging

### 0.0.3 (2019-06-02)
* (René) ready to publish

### 0.0.2 (2019-05-19)
* (René) actuator handling added

### 0.0.1 (2019-04-27)
* (René) initial release

## License

Copyright (C) <2019>  <info@rg-engineering.eu>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.