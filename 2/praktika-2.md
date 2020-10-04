1) В поисковом запросе ресурса google.com вводим `intitle:"forum" inurl:http after:2019`

В результате запроса находим ресурсы, использующие протокол `http`

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/google1.jpg)

2) Определяем ip адрес первого найденного ресурса, используя несколько способов

Способ №1. Узнаем адрес через утилиту `ping`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/worldskills1.jpg)

Способ №2. Узнаем адрес через утилиту `nslookup`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/worldskills2.jpg)

3) Изучаем аргументы утилиты `nslookup`:

* аргумент `-query=mx`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/worldskills3.jpg)

* аргумент `-query=soa`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/worldskills4.jpg)

* аргумент `-query=nx`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/worldskills5.jpg)

* аргумент `-type=any`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/worldskills6.jpg)

4) Изучаем трафик с сайта `http://forum.worldskills.ru/` с помощью WireShark:

* Начнем захват пакетов без применения фильтров на Беспроводном подключении, после чего откроем сайт `http://forum.worldskills.ru/`
и совершим переходы по нескольким ссылкам внутри этого сайта.
После того, как мы совершили несколько переходов, остановим захват пакетов в wireshark и применим фильтр `ip.addr == 188.127.229.20`
где ip 188.127.229.20 это адрес сайта, который мы обнаружили в предыдущих пунктах.

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/wireshark1.jpg)

* Применим фильтр `ip.dst == 188.127.229.20`:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/wireshark2.jpg)

* Применим фильтр `udp == 188.127.229.20` (получаем пустой результат):

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/wireshark3.jpg)

* Так же, следуя заданию, мы пытаемся применить фильтры `ip.src==192.168.1.4; ip.dst; ip.addr, udp.src, arp.src.hw_mac, eth.dst, eth.src`
но данный синтаксис либо устарел, либо выдает пустые результаты. Примеры на скриншотах ниже:

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/wireshark4.jpg)

![screenshot of google1](https://github.com/YatsushkoKatya/praktika2/blob/master/screenshots/wireshark5.jpg)
