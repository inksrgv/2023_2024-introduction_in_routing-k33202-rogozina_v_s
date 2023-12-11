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

![Снимок экрана 2023-12-10 111614](https://github.com/inksrgv/itmo_web_labs/assets/94178896/1c5c18eb-c664-46c7-87c5-4fffaf327e88)



## Граф полученной сети

![Снимок экрана 2023-12-10 174539](https://github.com/inksrgv/itmo_web_labs/assets/94178896/a7497359-7b26-4897-8405-8f3de6b68869)


## Конфигурация устройств

### Роутер R01

![Снимок экрана 2023-12-10 172543](https://github.com/inksrgv/itmo_web_labs/assets/94178896/b108eb32-a257-42fa-a66f-c84679491a75)


### Свитч SW01.L3.01.TEST

![Снимок экрана 2023-12-10 173053](https://github.com/inksrgv/itmo_web_labs/assets/94178896/9c6fa5a2-e934-4031-ab15-7ad47ef3a0ab)


### Свитч SW02.L3..01.TEST

![Снимок экрана 2023-12-10 173529](https://github.com/inksrgv/itmo_web_labs/assets/94178896/8123525c-7317-4dc8-a990-04b2cc216f57)


### Свитч SW02.L3..02.TEST

![Снимок экрана 2023-12-10 173839](https://github.com/inksrgv/itmo_web_labs/assets/94178896/4d446e78-38e0-4129-a29e-3aeb65f6bc1e)

## Проверка доступности

![Снимок экрана 2023-12-10 173927](https://github.com/inksrgv/itmo_web_labs/assets/94178896/186ef7d5-33d3-4546-921f-7cc9f110a4e1)


![Снимок экрана 2023-12-10 174001](https://github.com/inksrgv/itmo_web_labs/assets/94178896/551faadf-3128-43b4-9d83-afae3042754a)


![Снимок экрана 2023-12-10 174026](https://github.com/inksrgv/itmo_web_labs/assets/94178896/a1d7aecf-8d2c-48b4-b571-633f532e1136)


![Снимок экрана 2023-12-10 174057](https://github.com/inksrgv/itmo_web_labs/assets/94178896/905e9a27-eac2-4db4-a9e2-ab1558d9fd74)


![Снимок экрана 2023-12-10 174120](https://github.com/inksrgv/itmo_web_labs/assets/94178896/bd980adb-b68d-40aa-84b7-ad29a859608b)

## Вывод 

В ходе выполнения данной лабораторной работы я ознакомилась с инструментом ContainerLab и методами работы с ним, а также изучила работу VLAN, IP адресации и т.д.


