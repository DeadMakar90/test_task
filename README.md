## Настройка LACP ##
1.Установить пакет ifenslave:
```
sudo apt install ifenslave
```
2. Подключить модуль ядра:
```
sudo modprobe bonding
```
3. Настройка netplan:
```
network:
  version: 2
  renderer: networkd
  ethernets:
        ens18: {}
        ens19: {}
  bonds:
    bond0:
      interfaces: [ens18, ens19]
      addresses:
              - 192.168.2.2/22
      parameters:
          mode: 802.3ad
          mii-monitor-interval: 100
          transmit-hash-policy: layer3+4
```
## Скрипт вотрого задания ##
```
echo "user:какой_то_пароль" | chpasswd  #Смена пароля пользователю user

useradd -m -s /bin/bash user2  # Создание пользователя user2
echo "user2:какой_то_пароль" | chpasswd  # Создание пароля пользователя user2

sed -i 's/^#Port 22/Port 229/' /etc/ssh/sshd_config  # Расскоментировали и поменяли порт для ssh с стандартного на порт 229
systemctl restart sshd # Перезапуск службы ssh
ss -tlpn # Убеждаемся что порт изменился
```
