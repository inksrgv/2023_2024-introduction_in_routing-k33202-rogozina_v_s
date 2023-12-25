University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://github.com/itmo-ict-faculty/introduction-in-routing)

Year: 2023/2024

Group: K33202

Author: Rogozina Veronika Sergeevna

Lab: Lab4

Date of create: 12.12.2023

Date of finished: -

# Лабораторная работ №4 "Эмуляция распределенной корпоративной сети связи, настройка iBGP, организация L3VPN, VPLS"

## Цель работы

Изучить протоколы BGP, MPLS и правила организации L3VPN и VPLS.

## Создание файла топологии для развертывания сети
    name: laba4
    prefix: ''

    mgmt:
    network: statics
    ipv4_subnet: 172.20.23.0/24

    topology:
    nodes:
      R01.NY: 
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
      
    R01.LND: 
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
      
    R01.HKI: 
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
     
    R01.SPB: 
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
     
    R01.LBN: 
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9

    R01.SVL: 
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
    
    PC1:
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
     
    PC2:
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
      
    PC3:
      kind: vr-mikrotik_ros
      image: vrnetlab/vr-routeros:6.47.9
       

    links: 
    - endpoints: ["R01.NY:eth1","PC2:eth1"]      
    - endpoints: ["R01.NY:eth3","R01.LND:eth3"] 
    - endpoints: ["R01.LND:eth1","R01.HKI:eth2"]
    - endpoints: ["R01.LND:eth2","R01.LBN:eth1"] 
    - endpoints: ["R01.LBN:eth2","R01.HKI:eth1"] 
    - endpoints: ["R01.LBN:eth3","R01.SVL:eth3"]
    - endpoints: ["R01.SVL:eth1","PC3:eth1"]     
    - endpoints: ["R01.HKI:eth3","R01.SPB:eth3"]
    - endpoints: ["R01.SPB:eth1","PC1:eth1"]   

## Результат сборки сети

![Снимок экрана 2023-12-23 202944](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/c347304c-bb60-4f46-ad9a-f13e29d56e34)

## Граф полученной сети


# Первая часть работы 

## Конфигурация устройств

### Роутер R01.NY
![Снимок экрана 2023-12-25 120027](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/0f082513-2640-4abe-bf44-7c016b05e862)

### Роутер R01.SPB
![Снимок экрана 2023-12-25 120005](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/a08f2e70-b9d7-40c6-83d4-c56f2cd3063d)

### Роутер R01.SVL
![Снимок экрана 2023-12-25 120014](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/85973579-8957-4f6b-b053-34ab8cae3cd4)

### Роутер R01.HKI
![Снимок экрана 2023-12-25 115927](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/aaa4b26b-42ce-4f7f-bb95-af7efe5def05)

### Роутер R01.LND
![Снимок экрана 2023-12-25 115950](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/48de39ad-623c-4f61-a211-0698967fc3cc)

### Роутер R01.LBN
![Снимок экрана 2023-12-25 123600](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/d49639d5-6bac-4994-b290-54aeb5274802)

## Провекра связности между VRF
![Снимок экрана 2023-12-25 120036](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/11fd642f-189e-49c2-8074-6b1308cff7f2)

![Снимок экрана 2023-12-25 120042](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/593d94d4-ee73-403e-95ab-a1d6f5668012)

![Снимок экрана 2023-12-25 120050](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/7e2f7764-0a39-4428-b59c-dce9ab24fe2d)

## Проверка утилиты ping 
### R01.NY
![Снимок экрана 2023-12-25 120516](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/5e62c41b-6044-4563-95f0-1f06be6d1737)

![Снимок экрана 2023-12-25 120524](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/f6c50262-58b3-41e8-bacb-2df937453e9c)

### R01.SPB
![Снимок экрана 2023-12-25 120721](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/57876da2-8255-4351-9ae0-187c478bb3f9)

### R01.SVL
![Снимок экрана 2023-12-25 120820](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/c982d460-a988-42bc-81b8-b8a9fc2e6129)


# Вторая часть работы 
### PC1
![Снимок экрана 2023-12-25 121018](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/5cdc32ae-af00-4884-8c73-7e1518f0b67a)

### PC2
![Снимок экрана 2023-12-25 121004](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/994177e4-382a-4ee8-accb-5422dc0a1142)


### PC3
![Снимок экрана 2023-12-25 120949](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/29b9b65e-3fb6-466f-b732-1debff166d7c)

### R01.NY
![Снимок экрана 2023-12-25 121204](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/c012389d-bf40-4cd2-94d2-0658205d6af9)

### R01.SPB
![Снимок экрана 2023-12-25 121258](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/980faa2e-b97c-4cb4-9c7a-13b261884424)

### R01.SVL
![Снимок экрана 2023-12-25 121204](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/9d5b8c2b-c762-4637-944f-3faadf3d8c44)

## Проверка доступности 

![Снимок экрана 2023-12-25 121609](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/750bd710-e80a-4616-8a70-143bfd4087bf)

![Снимок экрана 2023-12-25 121622](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/a64e361c-0c5e-48ba-b939-59896ba92916)

![Снимок экрана 2023-12-25 121655](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/fe45e78a-0aa7-4c2b-a503-248d7f2e2b3e)

![Снимок экрана 2023-12-25 121743](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/caa09a29-700c-4d16-b0c1-b150c0aac648)

![Снимок экрана 2023-12-25 121753](https://github.com/inksrgv/2023_2024-introduction_in_routing-k33202-rogozina_v_s/assets/94178896/1cc7838c-df5d-443f-a748-29e8ae51f78e)



## Вывод 

В ходе выполнения данной лабораторной работы я изучила протоколы BGP, MPLS и правила организации L3VPN и VPLS.





