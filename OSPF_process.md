[logo1]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/1.png
[logo2]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/2.png
[logo3]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/3.png
[logo4]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/4.png
[logo5]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/5.png
[logo6]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/6.png
[logo7]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/7.png
[logo8]: https://github.com/dbudakov/22.route/blob/master/image/OSPF_steps/8.png


### Алгоритм установления смежности и затем соседства   
#### 1. Обмен HELLO-пакетами   
   На схеме два роутера в состоянии DOWN, Hello/Routerdead interval в одинаковых значениях, линки в одной зоне, типы сетей одинаковые(broadcast), Router ID разные(они должны быть разными)   
![logo1]  

#### 2. Формируется таблица состояний связей с соседями (link-state)   
   Один из роутеров переходит в состояние INIT и рассылает HELLO-пакет,в HELLO-пакете он пишет свой RouterID, Hello interval, Dead interval, кол-во соседей.  
![logo2]

#### 3.  Формируют LSA - (router id, neighbor id, net/mask, net type, cost)
HELLO-пакет получает роутер R2, сравнивает показатели, видит что соседей 0, видит несоответствие так как получил пакет в пределах одного канала ![logo3]

