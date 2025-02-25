---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.viessmann/README.md
title: ioBroker.viessmann
hash: j6m0qzV1f1E3JpYwTGgqLGC8xzydsmg606nEXmekPEg=
---
![商标](../../../en/adapterref/iobroker.viessmann/admin/viessmann.png)

![安装数量](http://iobroker.live/badges/viessmann-stable.svg)
![NPM版本](http://img.shields.io/npm/v/iobroker.viessmann.svg)
![下载](https://img.shields.io/npm/dm/iobroker.viessmann.svg)
![特拉维斯-CI](http://img.shields.io/travis/misanorot/ioBroker.viessmann/master.svg)
![AppVeyor](https://ci.appveyor.com/api/projects/status/github/misanorot/ioBroker.viessmann?branch=master&svg=true)
![NPM](https://nodei.co/npm/iobroker.viessmann.png?downloads=true)

＃ioBroker.viessmann
=================

[![贝宝（https://www.paypalobjects.com/en_US/DK/i/btn/btn_donateCC_LG.gif）](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ZYHW84XXF5REJ&source=url)

**[英文说明](https://github.com/misanorot/ioBroker.viessmann/blob/master/lib/Readme_en.md)**

Mit diesem Adapter istesmöglich，Werte aus einer Viessmann Steuerung die mit demProgramm[Vcontrold](https://github.com/openv/vcontrold)kommuniziert，in Objekten zu speichern。
Ebenso ist das Setzen von Werten，死于围网的人Vito.xml konfigurierthatmöglich。

####（selber主持人）
Sollte Vcontrold auf dem gleichen Host wie auch IOBroker laufen，sot unter Linux eigentlich keineweitereVeränderunginderAdminkonfigurationnötigumdie .xml Dateien einzulesen。
*（Vorausgesetzt，sie liegt in dem Standard Pfad：/etc/vcontrold/vito.xml)*

####（Anderer主持人）
Ist Vcontrold auf einem anderen Host installiert，kann man per SSH Zugang die .xml Dateien einlesen。
HierfürdienötigenInformationenin dem SSH Tab eingeben。
*（Eine funktionierende SSH Verbindung wird vorausgesetzt。）*

Nach dem Neustart der Instanz，wird diese dann automatisch eingelesen，man kann nun in der Konfiguration der Instanz die Werte einstellen。

#### Die Struktur der vito.xml muss in der folgenden Form aufgebaugt sein：
		```<vito>
			<devices>
				<device ID="2094" name="V200KW1" protocol="KW2"/>
			</devices>
			<commands>
				<command name='getOelverbrauch' protocmd='getaddr' >
					<addr>7574</addr>
					<len>4</len>
					<description></description>
				</command>
				<command name='getTempAbgas' protocmd='getaddr'>
					<addr>0808</addr>
					<len>2</len>
					<unit>UT</unit>
					<error>05 05</error>
					<description>Abgastemeratur in Grad C</description>
				</command>
			</commands>
		</vito>```

Eine Sortierung der Befehle，ist durch klicken auf denTabellenkopfmöglich。

## Wichtig！：
 -  Bei jedem neuen einlesen der Vito Daten，werden ggf.死于“alten”Einstellungengelöscht。

Es ist empfehlenswert，bei relativ unwichtigen Abfragewerten，einmöglichstgrosses Abfrageintervallzuwählen。

* die benutzten Bilder stammen von www.viessmann.com。*

＃＃ 去做
 -  Anderung der Vito.xml ohne Verlust der Einstellungen
 - 开启/关闭实施单位

**[CHANGELOG](https://github.com/misanorot/ioBroker.viessmann/blob/master/changelog.md)**

## License

The MIT License (MIT)

Copyright (c) 2017-2019 misanorot <audi16v@gmx.de>

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