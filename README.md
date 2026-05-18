# Кластеризация и балансировка нагрузки

## Задание 1
*- Запустите два simple python сервера на своей виртуальной машине на разных портах*
*- Установите и настройте HAProxy, воспользуйтесь материалами к лекции по ссылке*
*- Настройте балансировку Round-robin на 4 уровне.*
*- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy.*

1) Как показано на лекции, запустил два сервера Python на портах 8888 и 9999 соответственно.
2) Установил HAProxy
![HAProxy](https://github.com/DefAKAAlex/claster-balance/blob/main/IMG/haproxy-status.png)
3) При обращении к HaProxy балансировка показывает равномерное распределение
![balance](https://github.com/DefAKAAlex/claster-balance/blob/main/IMG/curl-balance.png)

[конфигаруционный файл 1](haproxy1.cfg)


## Задание 2
*- Запустите три simple python сервера на своей виртуальной машине на разных портах*
*- Настройте балансировку Weighted Round Robin на 7 уровне, чтобы первый сервер имел вес 2, второй - 3, а третий - 4*
*- HAproxy должен балансировать только тот http-трафик, который адресован домену example.local*
*- На проверку направьте конфигурационный файл haproxy, скриншоты, где видно перенаправление запросов на разные серверы при обращении к HAProxy c использованием домена example.local и без него.*

1) Запустил ещё один сервер на порту 8899
![serv2](https://github.com/DefAKAAlex/claster-balance/blob/main/IMG/serv3-img.png)
После изменения конфигурационного файла получаем следующую картину:
2) При обращении без использования адреса домена example.local возвращает описанную мной 403 ошибку
![HAProxy](https://github.com/DefAKAAlex/claster-balance/blob/main/IMG/denay-exmpl.png)
3) При обращении с использованием адреса examlpe.local HAProxy разбрассывает траффик соответственно весам
![HAProxy](https://github.com/DefAKAAlex/claster-balance/blob/main/IMG/exmpl-ok.png)
![HAProxy](https://github.com/DefAKAAlex/claster-balance/blob/main/IMG/stat3.png)

[конфигурационный файл 2](haproxy2.cfg)