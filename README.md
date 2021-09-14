This Arduino code is for receiving and transmitting data in Oregon Scientific RF protocol version 2.1 and 3.0. and Explore Scientific weather station protocol also<br>
The folowed sensors data format are supported including calculation of CRC8:<br>
<br>
Receive and emulate:<br>
<dl>
<li>THGN132N (THGN122N, THGN123N, THGR122N, THGR228N, THGR238N, THGR268),</li>
<li>RTGN318 (RTGN130),</li>
<li>THGR810 (THGN800, THGN801, THGR800, THWR800, THGR221(?), THGR511(?)),</li>
<li>BTHGN129,</li>
<li>BTHR968.</li>
</dl>
Receive only:<br>
<dl>
<li>THN132N (THR238N, THRN122, THN122, THWR288N, THR268),</li>
<li>RTHN318 (RTHR328N, RTHN129),</li>
<li>THGN500,</li>
<li>THN800,</li>
<li>WGR800,</li>
<li>UVN800,</li>
<li>PCR800,</li>
<li>ST1004,</li>
<li>ST1005.</li>
</dl>
</list>
<br><br>

Aslo supported self-developed sensors. Please contact author for additional infromation.<br>

<br>
Данная библиотека Ардуино предназначена для приема и передачи данных в формате беспроводного протокола Oregon Scientific v2.1 и v3.0 а также данных в формате метеостанций Explore Scientific<br>
<br>
Поддерживается формат следующих датчиков, включая рассчёт CRC8.<br>
<br>
Приём и эмуляция:<br>
<dl>
<li>THGN132N (THGN122N, THGN123N, THGR122N, THGR228N, THGR238N, THGR268),</li>
<li>THN132N (THR238N, THRN122, THN122, THWR288N, THR268),</li>
<li>RTGN318 (RTGN130),</li>
<li>THGR810 (THGN800, THGN801, THGR800, THWR800, THGR221(?), THGR511(?)),</li>
<li>BTHGN129,</li>
<li>BTHR968.</li>
</dl>
<br>
Только приём:<br>
<dl>
<li>RTHN318 (RTHR328N, RTHN129),</li>
<li>THGN500,</li>
<li>THN800,</li>
<li>WGR800,</li>
<li>UVN800,</li>
<li>PCR800,</li>
<li>ST1004,</li>
<li>ST1005.</li>
</dl>
<br>
Код приёмника протестирован на оригинальных датчиках THGN132N, THN132N, WGR800 и ST1004.<br>
<br>
Код передатчика протетстирована на погодных станциях BAR206, BAR208 эмуляцией сигнала THGN132N<br>
Для успешного приёма погодной станцией сигнала необходимо соблюдать следующие условия при передаче данных:<br>
Влажность 2-98%<br>
Температура -50...+70С<br>
При создании энергосберегающих датчиков с режимом "глубокого сна" нужно учесть, что интервалы между пакетами для успешного приёма погодной станцией 
должны отличаться от номинальных не более чем на +-1сек. Например для THGN132:<br>
<dl>
Канал 1 - 39 (38 - 40) c <br>
Канал 2 - 41 (40 - 42) c<br>
Канал 3 - 43 (42 - 44) c<br>
</dl>
<br>
Если пришёл пакет с корректной CRC и контрольной суммой, но значение температуры и влажности некорректные, например +3.0С переданы не как 0300, а A200
то датчик может быть заблокирован до смены ID или до сброса погодной станциии.<br>
Блокировка навсегда возможна и при неправильном сочетании номера канала и ID датчика. Этот вопрос пока до конца не изучен<br>
br>
Передача сигналов в формате RTGN318 и THGR810 до конца не протестирована. Поэтому возможны проблемы с приёмом этих сигналов погодной станцией<br>
на отдельных каналах<br>
Полное описание протокола: <href>https://habr.com/ru/post/525446/</href><br><br>
Новое в версии<br>
20.9.26 <br>
<dl>
<li>Добавлена поддержка THN800, PCR800 (последний пока без CRC8),</li>
<li>Добавлен CRC8 WGR800,</li>
<li>Исправлен CRC8 RTGN318,</li>
<li>Улучшены библиотека передатчика и пример ретранслятора,</li>
<li>ДОбавлена возможность сконфигурировать библиотеку под приём длинных пакетов.</li>
</dl>
20.9.27 <br>
<dl>
<li>Добавлен CRC8 PCR800.</li>
</dl>
20.9.28 <br>
<dl>
<li>Исправлена ошибка, приводящая к нестабильной работе при больших длинах пакета.</li>
</dl>
20.9.29 <br>
<dl>
<li>Исправлен CRC8 THGR810 в приёмнике и передатчики,</li>
<li>Добавлен пример с поиском CRC8.</li>
</dl>
20.10.6 <br>
<dl>
<li>Добавлена поддержка THGN500,</li>
<li>Возможность установки размера буферов приёма и передачи в конструкторе.</li>
</dl>
20.10.7 <br>
<dl>
<li>Исправлены ошибки в подсчёте CRC8 третьей версии протокола.</li>
</dl>
20.10.8 <br>
<dl>
<li>Добавлена поддержка RTHN318,</li>
</dl>
20.10.10 <br>
<dl>
<li>Добавлена поддержка BTHGN129 и BTHR968</li>
</dl>
20.10.12 <br>
<dl>
<li>Улучшен приём на ESP</li>
<li>Исправлена расшифровка данных PCR800 и UVN800</li>
<li></li>
</dl>
20.11.28<br>
<dl>
<li>Исправлена ошибка с некорректным определением версии пакета</li>
<li>Улучшен тайминг передатчика</li>
<li></li>
</dl>
21.01.28<br>
<dl>
<li>ДОбавлен эмулятор передатчиков BTHR968 и BTHGN129</li>
<li>Исправлена ошибка при рассчёте давления для этих же датчиков</li>
<li></li>
</dl>
21.03.25<br>
<dl>
<li>Добавлен эмулятор передатчика THN132 (thanks to karev-anton)</li>
<li></li>
</dl>
21.08.31<br>
<dl>
<li>Добавлен приём пакетов от Explore Scientific ST1004 (beta)</li>
<li>Исправлена ошибка при работе с длинными пакетами данных</li>
<li></li>
</dl>
21.09.14<br>
<dl>
<li>Добавлен приём пакетов от Explore Scientific ST1005 (beta)</li>
<li>Изменён метод поиска пакетов в эфире</li>
<li></li>
</dl>
