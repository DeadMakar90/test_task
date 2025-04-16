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
Представлен в виде ansible-playbook.yml
