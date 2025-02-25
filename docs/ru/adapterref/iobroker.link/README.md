---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.link/README.md
title: ioBroker.link
hash: 3SVNU91/5JWyIAkycj0waKAt6eWMFrap0jxcmoNb0ok=
---
![логотип](../../../en/adapterref/iobroker.link/admin/link.png)

![Версия NPM](http://img.shields.io/npm/v/iobroker.link.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.link.svg)
![NPM](https://nodei.co/npm/iobroker.link.png?downloads=true)

# IoBroker.link
Этот адаптер обеспечивает безопасное соединение через облако [ioBroker.link](https://iobroker.link/).

## ЧАСТО ЗАДАВАЕМЫЕ ВОПРОСЫ
### Что я могу сделать, используя этот адаптер?
Этот адаптер позволяет безопасно подключаться к локальной установке ioBroker и другим серверам / устройствам в вашей локальной сети за модемом / маршрутизатором / брандмауэром DSL. Подключение осуществляется через общедоступное облако ioBroker.link (link-cloud). Даже множественная локальная установка ioBroker может быть настроена и доступна через облако ссылок.

### В чем разница с переадресацией портов, которую я могу настроить на своем маршрутизаторе?
В то время как вы можете настроить переадресацию портов на вашем маршрутизаторе и, таким образом, получить доступ к локальной установке ioBroker из любого места, облачное соединение обеспечивает следующие основные преимущества:

- на вашем роутере не нужно открывать порты в интернет
- для вашей локальной установки ioBroker не требуется общедоступный IP-адрес или (динамическое) DNS-имя
- link-cloud заботится об аутентификации и авторизации
- link-cloud защищает соединение с использованием SSL / TLS
- link-cloud предоставляет журнал аудита
- к нескольким локальным установкам ioBroker можно получить доступ через один и тот же пользовательский интерфейс сервера link-cloud
- Адаптер ioBroker.link действует как обратный прокси и позволяет получить доступ к другим серверам / устройствам в вашей локальной сети, которые поддерживают протоколы HTTP / TCP / UDP
- вы можете предоставить временный или постоянный доступ к вашей локальной установке ioBroker <sup>третьему</sup> лицу, например, для устранения неисправностей устройства, без необходимости раскрывать свой пароль или управлять учетными данными

### Как установить соединение с моей локальной установкой ioBroker, если нет открытого IP-адреса и не открыты порты?
Облако ссылок никогда не подключается к вашей локальной установке, это адаптер ioBroker.link, который работает локально и инициирует подключение к облаку ссылок в случае запроса на подключение.

### Что такое запрос на соединение?
Запрос на соединение - это намерение установить соединение с локальной установкой ioBroker, выполненное авторизованным и авторизованным лицом через облако ссылок.

### Как адаптер ioBroker.link распознает наличие запроса на подключение?
Адаптер ioBroker.link периодически проверяет наличие ожидающих запросов на подключение, опрашивая облако ссылок. Вы можете настроить интервал опроса в настройках адаптера ioBroker.link.

### Как я могу убедиться, что адаптер ioBroker.link устанавливает соединение с облаком ссылок, а не с человеком в середине?
Адаптер ioBoker.link может подключаться только к серверу, который предоставляет действительный сертификат SSL, выданный iobroker.link.

### Как облако ссылок идентифицирует и авторизует все адаптеры ioBroker.link, опрашивающие ожидающие запросы соединения или устанавливающие соединение?
Каждый адаптер ioBroker.link генерирует свою уникальную 2048-битную пару ключей. При регистрации в link-cloud адаптер передает свой открытый ключ. При каждом последующем запросе к облаку ссылок (проверка на наличие ожидающих запросов на подключение, принятие или отклонение ожидающего подключения, закрытие открытого подключения и т. Д.) Адаптер авторизует себя, предоставляя JSON Web Token (JWT), подписанный с помощью закрытого ключа адаптера. , Облако ссылок проверяет подпись JWT, используя сохраненный открытый ключ, и принимает или отклоняет соединение.

### Может ли один адаптер подключиться к облаку ссылок, используя другой адаптер JWT?
Нет. Адаптер подписывает JWT, используя свой собственный уникальный закрытый ключ, который никогда не покидает локальную установку. Облако ссылок использует соответствующий открытый ключ для проверки подписи.

### Могу ли я повысить безопасность, поворачивая ключи, используемые для авторизации моего адаптера?
Да. Ключи хранятся в папке / keys вашего адаптера. Удалите все файлы в этой папке и перезапустите адаптер. Адаптер создаст новую пару ключей при запуске и обновит регистрацию в облаке ссылок, отправив новый открытый ключ.

### Как защищено само установленное соединение?
Если есть ожидающий запрос на соединение, адаптер ioBroker.link сначала устанавливает SSH-туннель к облаку ссылок и принимает входящее соединение. Обе стороны авторизуются с помощью сертификатов. Как только SSH-туннель настроен, начинается само сообщение. Как только соединение закрывается, например, пользователем через пользовательский интерфейс сервера облака ссылок, туннель SSH закрывается, и связь больше не возможна.

### Можно ли также подключиться к моим локальным устройствам через облако ссылок?
Да. Если ваши устройства поддерживают протокол HTTP, вы можете получить к ним доступ через облако ссылок. Каждое устройство, к которому вы хотите подключиться через облако ссылок, должно быть явно настроено в настройках адаптера ioBroker.link. Ни одно устройство не может быть подключено по умолчанию. Даже веб-интерфейс ioBroker.admin должен быть предварительно настроен, чтобы иметь возможность подключаться к нему.

### Что мне нужно установить, чтобы подключиться к локальным устройствам через облако ссылок?
Подключение к локальным устройствам с поддержкой протокола HTTP осуществляется через браузер по вашему выбору. Никакого дополнительного программного обеспечения не требуется.

### Мое локальное устройство поддерживает только протокол TCP / UDP. Возможно ли подключение к устройствам TCP / UDP?
Да. Для подключения к локальным TCP / UDP-устройствам используйте ioBroker.link-box: https://www.npmjs.com/package/iobroker.link-box

### Как мне получить доступ к моей локальной установке ioBroker?
Любой, кому должен быть предоставлен доступ к локальной установке ioBroker, должен быть явно настроен в настройках адаптера ioBroker.link. Никто не имеет доступа по умолчанию. Это означает, что вам также необходимо настроить себя, чтобы иметь возможность подключиться к вашей локальной установке ioBroker.

### Как и где я могу создать пользователя, которому я бы хотел предоставить доступ к моей локальной установке?
Сначала вы должны создать бесплатную учетную запись на https://iobroker.pro. После создания вы можете настроить зарегистрированную электронную почту в параметре _Allowed users_ адаптера ioBroker.link. В настройках адаптера пароль не требуется.

### У меня уже есть аккаунт на https://iobroker.pro. Могу ли я использовать его для облака ссылок?
Да. Вы можете использовать уже существующую учетную запись https://iobroker.pro.

### Можно ли использовать https://iobroker.pro и облачные сервисы ссылок одновременно?
Да. Между этими двумя службами нет никаких зависимостей. Вы можете использовать их отдельно или параллельно.

### Почему облако ссылок использует учетные записи https://iobroker.pro?
Облако ссылок не использует учетные записи https://iobroker.pro. Никакая информация, связанная с учетными записями https://iobroker.pro, не передается / доступна в облаке ссылок. Облако ссылок просто объединяет аутентификацию с https://iobroker.pro. Авторизация, в свою очередь, полностью обрабатывается облаком ссылок.

### Как я могу отозвать доступ к моей локальной установке?
Вы можете отозвать разрешения на доступ, предоставленные отдельным лицам, удалив их электронные письма из настройки _Allowed user_ адаптера ioBroker.link. В качестве альтернативы вы можете полностью запретить доступ к локальной установке, оставив настройку _Allowed users_ пустой. Также остановка или удаление адаптера ioBroker.link предотвратит любой доступ через облако ссылок.

### Могу ли я платить за использование облака ссылок?
На данный момент плата не взимается, и облако ссылок полностью бесплатное. Также не зависит, используете ли вы бесплатный или платный аккаунт https://iobroker.pro. Пожалуйста, имейте в виду, что это может быть изменено в будущем.

### Почему вы планируете взимать плату за эту простую услугу?
Даже это простое обслуживание требует круглосуточной работы и приводит к затратам. Обеспечение высокой доступности этой услуги, устранение неисправностей и улучшение или добавление новых функций занимает значительное количество нашего времени. Чтобы посвятить себя дальнейшему развитию, нам нужны чипы. Это позволило бы нашим женам ходить по магазинам и дать нам больше времени уделять внимание этому проекту.

### Каковы ограничения облака ссылок?
На данный момент только одно соединение может быть открыто для локальной установки ioBroker. Это означает, что если нескольким пользователям предоставлены разрешения на доступ к локальной установке, то к ним может подключиться только один пользователь за раз. Также допускается единственное соединение для каждого пользователя. Это означает, что один и тот же пользователь, получивший доступ к нескольким локальным установкам, может одновременно обращаться только к одной установке.

### Как я могу отслеживать, кто и когда получил доступ к моей локальной установке?
Все метаданные всех запрошенных соединений сохраняются и могут быть просмотрены по адресу https://iobroker.link.

## Конфигурация адаптера :: Основные настройки
### Имя клиента
Это имя вашей локальной установки ioBroker. Вы можете выбрать его свободно. Это помогает вам различать различные установки ioBroker при выполнении запроса на соединение через облако ссылок.

### URI сервера
Это доменное имя облака ссылок. Этот параметр предварительно настроен с помощью https://iobroker.link и должен быть изменен.

### URI прокси
Если ваш ioBroker установлен за прокси-сервером, вы можете настроить прокси-сервер здесь. Прокси может быть определен здесь как: *http:// proxy: 8080* или через **HTTPS_PROXY** переменную среды.

### Интервал опроса (сек)
Определяет, как часто ваш адаптер опрашивает облако ссылок на предмет ожидающих запросов на подключение.
Рекомендуемая настройка: 10

### Разрешенные пользователи
Определяет существующие учетные записи https://iobroker.pro, которым должны быть предоставлены права доступа к вашей локальной установке ioBroker.

Если вы хотите предоставить доступ к себе и своей жене и предполагаете, что вы указали me@gmail.com и darling@gmail.com при создании учетных записей https://iobroker.pro, параметр _Allowed users_ будет содержать эти почтовые адреса.

## Конфигурация адаптера :: Устройства
Здесь вы определяете список устройств, которые будут доступны через облако ссылок.

### Включено
Определяет, должно ли настроенное устройство быть доступным.

### Название
Свободно выбранное название устройства. Это помогает различать разные устройства при подключении через облако ссылок.

### IP
IP-адрес устройства для подключения в локальной сети. Вы можете указать имя хоста, например, _localhost_, вместо IP-адреса, но имейте в виду, что это имя должно быть разрешено на компьютере, на котором работает адаптер ioBroker-link, а также что имена хостов не могут использоваться для устройств UDP.

### Порт
Номер порта вашего устройства прослушивает входящие соединения.

### Тип
- TCP - для устройств, поддерживающих протокол TCP и / или HTTP
- UDP - для устройств, поддерживающих протокол UDP

## Конфигурация адаптера :: Пример конфигурации устройства
Чтобы сделать ваш веб-интерфейс ioBroker.admin доступным через облако ссылок, вы должны сконфигурировать его в _Adapter configuration :: Devices_ следующим образом:

- включено: проверено
- name: ioBrokerAdminWebUI (или любое другое имя, которое вам нравится)
- IP: localhost (или 127.0.0.1)
- Порт: 8081 (если вы не изменили порт по умолчанию в ioBroker.admin)
- Тип: TCP

Для доступа к веб-интерфейсу вашего маршрутизатора у вас может быть следующая конфигурация:

- включено: проверено
- имя: Маршрутизатор
- IP: 192.168.0.1 (или IP-адрес локальной сети вашего маршрутизатора)
- Порт: 80 (если вы не изменили порт веб-интерфейса маршрутизатора по умолчанию)
- Тип: TCP

## Changelog
### 0.4.4 (2019-07-16)
* (gh-got) closing tunnels in case server considers an agent as offline
* (gh-got) fixed timeout to query active connection status

### 0.4.2 (2019-03-28)
* (gh-got) agents will report own version by registration

### 0.4.0 (2019-03-10)
* (bluefox) Made this adapter to be compatible with the new server

### 0.3.7 (2018-09-23)
* (bluefox) Do not connect to the cloud if no configuration defined

### 0.3.6 (2018-06-26)
* (bluefox) The download of SSF from github depending on platform was added

### 0.2.7 (2018-06-17)
* (bluefox) UDP communication is now supported

### 0.2.6 (2018-06-10)
* (bluefox) HTTP proxy support

### 0.1.3 (2018-04-25)
* (bluefox) Initial commit

## License
Creative Common Attribution-NonCommercial (CC BY-NC)

Copyright (c) 2018-2019 bluefox <dogafox@gmail.com>, gh-got

http://creativecommons.org/licenses/by-nc/4.0/

![CC BY-NC License](https://github.com/GermanBluefox/DashUI/raw/master/images/cc-nc-by.png)

Short content:
Licensees may copy, distribute, display and perform the work and make derivative works based on it only if they give the author or licensor the credits in the manner specified by these.
Licensees may copy, distribute, display, and perform the work and make derivative works based on it only for noncommercial purposes.
(Free for non-commercial use).