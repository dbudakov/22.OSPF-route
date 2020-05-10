после настройки стоимости метрики на eth1 роутера R1, в значение 1000, получаем следующую картину, для анализа будет 
использована утилита `tcpdump`, и запуск ее через такую команду, которая выводит только проходящие icmp пакеты на конкретном интерфейсе

clear && echo "hostname:$(hostname)" && tcpdump -i eth[N] icmp

Запускаем 1 пинг с R1 на R2, 
```
[root@r1 vagrant]# ping 10.0.0.2 -c 1
```

Из вывода трафика icmp на интерфейсах роутера R1, видно что `ICMP echo request` отправляется с `eth2` в `08:31:29.096045`, несмотря на то что на R2 идет прямой линк с `eth1`, а пакет `ICMP echo reply` приходит на `eth1`, на тот самый прямой линк, в `08:31:29.102351` ![logo1]

Из вывода трафика icmp на интерфейсах роутера R2, видно что `ICMP echo request` приходит на `eth2` от адреса `192.168.103.1`, который является линком R1 на R3, и `ICMP echo reply` выходит с `eth1`, который является прямым линком на R1 ![logo2]

Из вывода трафика icmp на интерфейсах роутера R3 видно что он просто переправляет `ICMP echo request`, с `eth2` на  `eth1`, об этом свидетельствует время обработки пакета, на интерфейсах R3 он появляется в `08:31:29.095908`, и следует на R2 и появляется там в `08:31:29.096199` ![logo3]

[logo1]: https://github.com/dbudakov/22.route/blob/master/image/asymmetry_route/R1_asymmetry_route.png
[logo2]: https://github.com/dbudakov/22.route/blob/master/image/asymmetry_route/R2_asymmetry_route.png
[logo3]: https://github.com/dbudakov/22.route/blob/master/image/asymmetry_route/R3_asymmetry_route.png
