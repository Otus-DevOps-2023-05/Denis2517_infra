#### 1. Исследовать способ подключения к someinternalhost в одну команду из вашего рабочего устройства, проверить работоспособность найденного решения и внести его в README.md в вашем репозитории
Решение с помощью shh-jump:
**$ ssh -j 158.160.109.218 10.128.0.34**

The authenticity of host '10.128.0.34 (<no hostip for proxy command>)' can't be established.
ED25519 key fingerprint is SHA256:GAhh6fZUAAn3bwlSaZ5mRhnXuU2KgtzLuXyq4Uz7//0.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.128.0.34' (ED25519) to the list of known hosts.
Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.15.0-76-generic x86_64)
Last login: Sun Jul  9 15:27:37 2023 from 10.128.0.12
**appuser@ someinternalhost:~$**

####  Дополнительное задание:
Предложить вариант решения для подключения из консоли при помощи
команды вида ssh someinternalhost из локальной консоли рабочего
устройства, чтобы подключение выполнялось по алиасу
someinternalhost и внести его в README.md в вашем репозитории

**Решение:**
В /home/appuser/.ssh/config добавить следующее:
`Host someinternalhost
ProxyJump 158.160.113.141`
В /etc/hosts добавить имя, чтобы оно резолвилось нужным айпишником:
`10.128.0.34 someinternalhost`
Далее подключаемся командой
`ssh someinternalhost`


#### 2. Создаем VPN-сервер для серверов Yandex.Cloud
Для установки pritunl на ubuntu 22.04 взял скрипт с https://docs.pritunl.com/docs/installation
По инструкции создал сервер, организацию с привязкой и пользователя. После старта сервера скачал конфиг ovpn и подключился.
bastion_IP = 158.160.113.141
someinternalhost_IP = 10.128.0.34
