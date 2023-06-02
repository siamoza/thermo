# thermo
Самодельный датчик температуры и сбор данных с него

За основу была взята статья на муське https://mysku.club/blog/ebay/71006.html
Если статья выжила к моменту, когда вы это читаете, то обратитесь напрямую к ней.
Если нет, то скажу самое главное здесь:

1. Адаптер USB-UART нужно покупать на чипе CP2102.
![Выглядит адаптер так](/img/s-l1600.jpg)
Я взял горсть таких свистков, например, здесь: https://www.ebay.com/itm/152895017873.

2. Второй компонент - термодатчик DS18B20. Купить можно во многих электромагазинах.

3. Теперь нужно собрать в
![Распайка адаптера](/img/cc9b80.jpg)

<pre>
Обновление, установка, настройка

# sudo usermod -a  -G tty www-data
# sudo usermod -a  -G dialout www-data
# apt-get update
# apt-get upgrade
# apt-get install digitemp
# ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 Aug  1 08:13 /dev/ttyUSB0

# digitemp_DS9097 -w -s /dev/ttyUSB0
DigiTemp v3.7.1 Copyright 1996-2015 by Brian C. Lane
GNU General Public License v2.0 - http://www.digitemp.com
Turning off all DS2409 Couplers
.
Devices on the Main LAN
28FF5C5D71160584 : DS18B20 Temperature Sensor

# digitemp_DS9097 -i -s /dev/ttyUSB0
# cp .digitemprc /etc/digitemp.conf

# digitemp_DS9097 -t 0 -q -o "%.1C" -c /etc/digitemp.conf
29.1
 </pre>
 
 Позже напишу пошагово и подробно. Выкладываю пока как есть ввиду срочности задачи.
