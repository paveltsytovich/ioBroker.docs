---
title: Расширенная настройка - Multihost
lastChanged: 13.09.2018
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/config/multihost.md
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
hash: bn0CAoBAN5DPBn11696x47c991NbZ42OEAQayrrozEY=
---
# Операция с несколькими хостами
ioBroker способен справляться с задачами нескольких серверов. Это позволяет распределить рабочую нагрузку между несколькими хостами.
Но вы также можете использовать системные расширения одноплатного компьютера (GPIO от RaspberryPi, хотя «мэйнфрейм» является более мощным Intel NUC).

После создания системы с несколькими хостами все настройки выполняются централизованно через администратора мастера. Администратор рабов больше не доступен через их веб-интерфейс (ы).

Поэтому для ведомого устройства полезно использовать хост с минимальной установкой, поэтому только js-контроллер и администратор.

## Установка
### Мастер конфигурации
Выполните следующую команду на мастере:

** Этот шаг абсолютно необходим, если используется Redis DB. ** В других случаях вы можете использовать его, если автоматический метод (s.u.) не работает. Но тогда выберите f (ile) вместо r (edis)!

пожалуйста, позвоните через консоль:

1. `iobroker setup custom`

Заполните меню, которое выглядит следующим образом

```
Type of objects DB [(f)ile, (c)ouch, (r)edis], default [file]: f
Host / Unix Socket of objects DB(file), default[0.0.0.0]:
Port of objects DB(file), default[9001]:
Type of states DB [(f)file, (r)edis], default [file]: r
Host / Unix Socket of states DB (redis), default[127.0.0.1]: 0.0.0.0
Port of states DB (redis), default[6379]:
Data directory (file), default[../../../iobroker-data/]: /opt/iobroker/iobroker-data/
Host name of this machine [ioBroker-RasPi]:
```

2. `iobroker multihost enable`

``` enter pass phrase```

3. `sudo service iobroker restart`

### Ведомая конфигурация
** Этот шаг абсолютно необходим, если используется Redis DB. **

Пожалуйста, войдите через консоль на раб

1. `sudo iobroker setup custom`

Заполните меню, которое выглядит следующим образом

```
Type of objects DB [(f)ile, (c)ouch, (r)edis], default [file]: f
Host / Unix Socket of objects DB(file), default[127.0.0.1]: <MASTER-IP>
Port of objects DB(file), default[9001]:
Type of states DB [(f)file, (r)edis], default [file]: r
Host / Unix Socket of states DB (redis), default[<MASTER-IP>]:
Port of states DB (redis), default[6379]:
Host name of this machine [raspi-sub-1]:
```

Наконец появляется информация:

```
creating conf/iobroker.json
```

2. `iobroker multihost connect`

и заполните следующие диалоговые окна соответственно:

```
1 |       <MASTER-IP> |  host |       192.168.86.42 | "authentication required"
Please select host [1]: 1
Enter secret phrase for connection: *****

Config ok. Please restart ioBroker: "iobroker restart"
```

2. `sudo service iobroker restart`

В основной системе вновь созданный хост появится в разделе Хосты.

Если этого не произошло, перезагрузите оба хоста. сначала хозяин, потом раб.

## Мультихост с разными подсетями
** Если оба хоста ioBroker находятся в разных подсетях, ...

Пример: **

* Обычная локальная сеть (для ПК, планшета, используйте.) = 192.168.178.0/24
* IoT LAN (для Shelly, камер и т. Д.) = 10.20.30.0/24

... автоматический режим нескольких хостов («sudo iobroker multihost enable» и «sudo iobroker multihost browse») не работает, а только старый путь (`iobroker setup custom`), см. выше

## Мультихост с редисом
Если необходимо установить среду с несколькими хостами, где состояния хранятся в Redis, необходимо уделить много внимания.

Файл redis.conf на хосте, где хранятся состояния, должен быть изменен следующим образом.

```
nano /etc/redis/redis.conf
```

Строка, содержащаяся в `bind 127.0.0.1`, должна быть дополнена IP-адресом сетевого адаптера, чтобы сервер Redis мог подключаться извне.

так, например,

```
bind 127.0.0.1 192.168.1.10
```

предполагая, что 192.168.1.10 является локальным IP-адресом мастера ioBroker.

Эта настройка необходима только у мастера.

Альтернативно, это работает

```
bind 0.0.0.0
```

Наконец, перезапустите сервер или компьютер Redis. например:

```
sudo service redis-server restart
```

## Распределить задачи
Есть два способа распределить задачи по хостам.

* Если это новая установка, выберите на вкладке «Адаптер» в раскрывающемся меню над списком адаптеров хост, на котором должен быть установлен экземпляр адаптера.

Затем добавьте туда экземпляр, нажав на (+) в правом столбце.

* Если вы ранее установили много адаптеров на хосте, вы можете впоследствии изменить назначение уже установленных экземпляров на вкладке Экземпляры.

## Удалить хост
Чтобы удалить хост, активируйте экспертный режим на вкладке «Администратор» «Объекты мастера» и активируйте хост в столбце «Тип». Затем удалите нужный хост.

## Возможные проблемы
иногда появляется другое сообщение, похожее на:

```> ... bytes ... in strict mode```

Затем, пожалуйста, отредактируйте файл, в котором встречается, с помощью редактора nano. В самом начале `'use strict';` прокомментируйте и прокомментируйте эту строку.

```> IP Address of the host is 127.0.0.1. It accepts no connections. Please change.```

если в основной системе это не было сделано ``` setup custom ```