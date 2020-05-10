после настройки стоимости метрики на eth1 роутера R1, в значение 1000, получаем следующую картину, для анализа будет 
использована утилита `tcpdump`, и запуск ее через такую команду, которая выводит только проходящие icmp пакеты на конкретном интерфейсе

clear && echo "hostname:$(hostname)" && tcpdump -i eth[N] icmp

Запускаем 1 пинг с R1 на R2, 
```
[root@r1 vagrant]# ping 10.0.0.2 -c 1
```

вывод трафика icmp на интерфейсах R1
![logo1]
![logo2]

[logo1]: https://github.com/dbudakov/22.route/blob/master/image/asymmetry_route/R1_asymmetry_route.png
[logo2]: https://github.com/dbudakov/22.route/blob/master/image/asymmetry_route/R2_asymmetry_route.png
[logo3]: https://github.com/dbudakov/22.route/blob/master/image/asymmetry_route/R3_asymmetry_route.png
