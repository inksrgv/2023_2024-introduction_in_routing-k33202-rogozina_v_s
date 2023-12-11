University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2023/2024

Group: K33202

Author: Rogozina Veronika Sergeevna

Lab: Lab3

Date of create: 12.12.2023

Date of finished: -

# Лабораторная работa №3 "Эмуляция распределенной корпоративной сети связи, настройка OSPF и MPLS, организация первого EoMPLS"

## Цель работы

Изучить протоколы OSPF и MPLS, механизмы организации EoMPLS.

## Создание файла топологии для развертывания сети
    name: lab3-new
    prefix: ''

    mgmt:
    network: statics
     ipv4_subnet: 172.20.20.0/24

    topology:
    nodes:
    R01.NY:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.11

    R01.LND:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.12

    R01.LBN:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.13

    R01.HKI:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.14
    
    R01.MSK:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.15

    R01.SPB:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.16
    
    SGI-Prism:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.17

    PC1:
      kind: vr-ros
      image: vrnetlab/vr-routeros:6.47.9
      mgmt_ipv4: 172.20.20.18
    
    links:
    - endpoints: ["SGI-Prism:eth1","R01.NY:eth1"]
    - endpoints: ["R01.NY:eth2","R01.LND:eth1"]
    - endpoints: ["R01.NY:eth3","R01.LBN:eth1"]
    - endpoints: ["R01.LND:eth2","R01.HKI:eth1"]
    - endpoints: ["R01.LBN:eth2","R01.MSK:eth1"]
    - endpoints: ["R01.LBN:eth3","R01.HKI:eth3"]
    - endpoints: ["R01.HKI:eth2","R01.SPB:eth2"]
    - endpoints: ["R01.MSK:eth2","R01.SPB:eth1"]
    - endpoints: ["R01.SPB:eth3","PC1:eth1"]



## Результат сборки сети

![Снимок экрана 2023-12-11 004532](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/adc44b51-1a04-4769-88a0-0166da66ad13)


## Граф полученной сети
![Снимок экрана 2023-12-11 004702](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/bef54810-6301-447c-b66a-f8c08c897922)


## Конфигурация устройств

### Роутер R01.SPB
![Снимок экрана 2023-12-11 011933](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/b4028fc7-6eb1-4eca-83f2-a8b9cec8225c)

### Роутер R01.NY
![Снимок экрана 2023-12-11 010116](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/8755096a-e08e-41aa-a309-d5b7545239d9)

### Роутер R01.HKI
![Снимок экрана 2023-12-11 014133](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/f2fe4613-a00b-4538-b114-88a402a26335)

### Роутер R01.LBN
![Снимок экрана 2023-12-11 013653](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/83bbfd45-292f-4b97-966c-4f1c1dca98b8)

### Роутер R01.LDN
![Снимок экрана 2023-12-11 013114](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/4f7bb834-c0f4-47df-b712-141e779db1f3)

### Роутер R01.MSK
![Снимок экрана 2023-12-11 014558](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/09ca4c61-8c6e-4780-a662-4e1bc2b12781)


### PC1
![Снимок экрана 2023-12-11 012419](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/ddde3e33-7d5b-4722-bbac-a4ba9032404a)


### SGI-Prism
![Снимок экрана 2023-12-11 012636](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/122308fa-55ee-4b66-84ba-410a59334057)


## Проверка доступности 
![Снимок экрана 2023-12-11 014705](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/8b302856-21e4-4e2a-80cb-1c868c08ceba)

![Снимок экрана 2023-12-11 014747](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/4c3395e8-782c-4afc-9380-8ec1bc0e139e)

![Снимок экрана 2023-12-11 014833](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/d4881855-43f2-4a72-94db-ecc9e797c399)

![Снимок экрана 2023-12-11 014913](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/d11a1af9-a8ac-46c7-88d9-a9efa171adc6)

![Снимок экрана 2023-12-11 014957](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/e777c4c1-bb1a-4c9d-9328-1c42be58141c)

![Снимок экрана 2023-12-11 015106](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/067eae2b-f3b3-4f00-8fed-de6f240b841c)

![Снимок экрана 2023-12-11 015243](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/17c979d7-d77e-4a3f-97b1-aab9e2d18724)

![Снимок экрана 2023-12-11 015325](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/be6adb41-5398-4291-820b-27c4d8d89b13)

## Вывод 

В ходе выполнения данной лабораторной работы я изучила протоколы OSPF и MPLS, а также механизмы организации EoMPLS.




