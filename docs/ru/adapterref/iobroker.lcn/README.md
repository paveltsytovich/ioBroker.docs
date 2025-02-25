---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.lcn/README.md
title: ioBroker.lcn
hash: fqNOdd76eIu4H7mYnlg3q/hxtJukZdAZ2vLp8u0uEyw=
---
![логотип](../../../en/adapterref/iobroker.lcn/admin/lcn.png)

![Версия NPM](http://img.shields.io/npm/v/iobroker.lcn.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.lcn.svg)
![NPM](https://nodei.co/npm/iobroker.lcn.png?downloads=true)

# IoBroker.lcn
Этот адаптер позволяет подключить локальную сеть управления [LCN](https://www.lcn.eu/) к ioBroker.

## Поддерживаемые шлюзы
- LCN-PKE

![ПКЕ](../../../en/adapterref/iobroker.lcn/img/lcn-pke.png)

- ЛКН-ФКУ с ЛКН-ПЧК

![ПКЕ](../../../en/adapterref/iobroker.lcn/img/lcn-pku.png)

** Не забывайте, что ioBroker.lcn заблокирует одну лицензию на подключение LCN. **

Конфигурация и модули будут автоматически обнаружены сканированием, которое должно быть запущено вручную из диалогового окна конфигурации и может быть повторено в любое время снова.

## Типы
Поддерживаются следующие группы чтения и записи:

- Аналоговые значения (выход / вход)
- Реле (выход)
- Датчики (входные)
- светодиоды (выход / вход)
- Переменные (входные)

## Переменные
Чтобы применить действительные функции преобразования к переменным, переменные должны иметь действительные роли. Поддерживаются следующие роли:

- **значение. температура** - температура в градусах Цельсия
- **значение. яркость** - люкс (I-вход) в люксах
- **value.speed.wind** - скорость ветра в м / с
- **значение. напряжение** - напряжение в вольтах
- **значение. ток** - ток в амперах
- **значение.сун.азимута** - азимут солнца
- **значение.sun.elevation** - высота солнца

## Как пользоваться
После первого запуска устройства должны быть отсканированы. Это можно сделать в диалоговом окне конфигурации с помощью кнопки сканирования.

![сканирование](../../../en/adapterref/iobroker.lcn/img/scanButton.png)

## Сделать
- Конфигурационный диалог для определения типа переменных.

## Changelog

### 0.4.2 (2019-06-12)
* (bluefox) Support of old measure values was added

### 0.3.2 (2018-11-19)
* (bluefox) add variables support

### 0.2.1
* (bluefox) initial release

## License
CC-BY-NC-4.0

Copyright (c) 2018-2019 bluefox <dogafox@gmail.com>

Up to 10 devices can be connected for free. If you need more devices, you must buy a commercial license.