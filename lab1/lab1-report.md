University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2023/2024

Group: K33202

Author: Rogozina Veronika Sergeevna

Lab: Lab1

Date of create: 10.10.2023

Date of finished: -

# Лабораторная работа №1 "Установка ContainerLab и развертывание тестовой сети связи"

## Цель работы

Ознакомиться с инструментом ContainerLab и методами работы с ним, изучить работу VLAN, IP адресации и т.д.

## Подготовка окружения 

Перед началом выполнения работы были выполнены следующие найстроки:

  * Установка Docker на рабочий компьютер.
  * Установка make и кронирование hellt/vrnetlab.
  * Загрузка в папку routeros файла chr-6.47.9.vmdk и сборка образа.
  * Установка ContainerLab

## Создание файла топологии для развертывания сети

    
    name: lab1
    
    prefix: ""
      
    mgmt:
      
       network: statics
   
       ipv4-subnet: 172.20.30.0/24
     
    topology:

     nodes:

      R01.TEST:
          kind: vr-ros
          image: vrnetlab/vr-routeros:6.47.9
          mgmt-ipv4: 172.20.30.8

      SW01.L3.01.TEST:
          kind: vr-ros
          image: vrnetlab/vr-routeros:6.47.9
          mgmt-ipv4: 172.20.30.2
      
      SW02.L3.01.TEST:
          kind: vr-ros
          image: vrnetlab/vr-routeros:6.47.9
          mgmt-ipv4: 172.20.30.3

      SW02.L3.02.TEST:
          kind: vr-ros
          image: vrnetlab/vr-routeros:6.47.9
          mgmt-ipv4: 172.20.30.4

      PC1:
          kind: linux
          image: ubuntu:jammy
          mgmt-ipv4: 172.20.30.5

      PC2:
          kind: linux
          image: ubuntu:jammy
          mgmt-ipv4: 172.20.30.6

    links:
    - endpoints: ["R01.TEST:eth1", "SW01.L3.01.TEST:eth1"]
    - endpoints: ["SW01.L3.01.TEST:eth2", "SW02.L3.01.TEST:eth1"]
    - endpoints: ["SW02.L3.01.TEST:eth2", "PC1:eth1"]
    - endpoints: ["SW01.L3.01.TEST:eth3", "SW02.L3.02.TEST:eth1"]
    - endpoints: ["SW02.L3.02.TEST:eth2", "PC2:eth1"] 


## Результат сборки сети


![Снимок экрана 2023-12-10 111614](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/dc1d1b2d-38b0-4535-b2ce-e00074022480)


## Граф полученной сети

![Снимок экрана 2023-12-10 174539](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/ce257f0b-e490-4a78-a994-3ca95ab0ce3c)

## Конфигурация устройств

### Роутер R01

![Снимок экрана 2023-12-10 171434](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/5bb90d4c-81a3-41a0-8f4a-c25ecc71e1e0)


### Свитч SW01.L3.01.TEST

![Снимок экрана 2023-12-10 173053](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/2a200271-9ac6-4012-9cf8-d47f2aeb70a9)


### Свитч SW02.L3..01.TEST

![Снимок экрана 2023-12-10 173529](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/dc68b8f7-cc0c-4c32-9402-c729c4671120)


### Свитч SW02.L3..02.TEST

![Снимок экрана 2023-12-10 173839](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/5b13e3ca-ca1c-4392-aee0-db5bb7e7a3b7)


## Проверка доступности

![Снимок экрана 2023-12-10 173927](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/d1680f7b-86ba-46e7-a6ad-6eb64ef3d8e4)

![Снимок экрана 2023-12-10 174001](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/53122a42-d5b6-4a29-b971-c3f5651b69c4)

![Снимок экрана 2023-12-10 174026](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/6ce7c446-0a3a-4bab-a391-143004ed244a)

![Снимок экрана 2023-12-10 174057](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/fba36cea-9839-4943-a5af-6052c9852976)

![Снимок экрана 2023-12-10 174120](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/0449ccf3-a339-4773-a18c-1c01b7442daf)


## Вывод 

В ходе выполнения данной лабораторной работы я ознакомилась с инструментом ContainerLab и методами работы с ним, а также изучила работу VLAN, IP адресации и т.д.


