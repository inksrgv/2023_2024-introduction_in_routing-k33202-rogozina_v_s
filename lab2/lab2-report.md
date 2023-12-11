University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2023/2024

Group: K33202

Author: Rogozina Veronika Sergeevna

Lab: Lab2

Date of create: 24.11.2023

Date of finished: -

# Лабораторная работа №2 "Эмуляция распределенной корпоративной сети связи, настройка статической маршрутизации между филиалами"

## Цель работы

Ознакомиться с принципами планирования IP адресов, настройки статической маршрутизации и сетевыми функциями устройств.


## Создание файла топологии для развертывания сети
    name: lab2-10
    prefix: ""

    mgmt:
      network: statics
      ipv4_subnet: 172.20.22.0/24
  
    topology:
      nodes:
    
    R01.MSK:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt-ipv4: 172.20.22.5
    
    R01.FRT:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt-ipv4: 172.20.22.6

    R01.BRL:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt-ipv4: 172.20.22.7

    PC1: 
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt-ipv4: 172.20.22.15

    PC2: 
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt-ipv4: 172.20.22.16

    PC3: 
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt-ipv4: 172.20.22.17

    links:
    - endpoints: ["R01.MSK:eth1", "PC3:eth1"]
    - endpoints: ["R01.BRL:eth2", "R01.FRT:eth2"]
    - endpoints: ["R01.BRL:eth3", "R01.MSK:eth2"]
    - endpoints: ["R01.MSK:eth3", "R01.FRT:eth3"]
    - endpoints: ["R01.FRT:eth1", "PC2:eth1"]
    - endpoints: ["R01.BRL:eth1", "PC1:eth1"]



## Результат сборки сети

![Снимок экрана 2023-12-10 191008](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/060bf4b2-384b-4e6a-8e58-32021df1fcae)

## Схема полученной сети
![Снимок экрана 2023-12-11 132025](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/126dca6b-ad94-4ce4-a9cf-9ede1ea33e94)


## Конфигурация устройств

### Роутер R01.BRL
![Снимок экрана 2023-12-10 212420](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/205a81b8-4b08-46df-ad54-f45afb336a2f)


### Роутер R01.FRT
![Снимок экрана 2023-12-10 213759](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/485bfbd8-83d0-4fd8-a44b-95af309a1c58)


### Роутер R01.MSK
![Снимок экрана 2023-12-10 213130](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/3f0d03f1-0622-48fc-a83d-464a1a1cd197)

### PC1
![Снимок экрана 2023-12-10 214253](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/5451ed5e-7823-4825-a69c-cd53470d0f15)

### PC2
![Снимок экрана 2023-12-10 214802](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/97b3268a-45c7-484f-a97e-ed57f5cbdb6d)

### PC3
![Снимок экрана 2023-12-10 215128](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/a754eb32-991b-4375-b0b9-f612405b246b)


## Проверка доступности для некоторый устройств

![Снимок экрана 2023-12-10 215219](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/5620829d-c35c-4f23-89c0-5727a7e3cf6e)

![Снимок экрана 2023-12-10 230602](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/70dabf59-5740-4e06-9e5a-a242d9f9cddf)

![Снимок экрана 2023-12-10 230706](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/899bc564-041e-4671-8230-7392f50aa8bd)

## Вывод 

В ходе выполнения данной лабораторной работы я ознакомилась с принципами планирования IP адресов, настройки статической маршрутизации и сетевыми функциями устройств.



