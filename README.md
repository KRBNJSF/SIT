# SIT
Rozsah privátních adres: 
192.168.0.0/16
172.16.0.0/12  Používají se v místní síti
10.0.0.0/8
Routovací tabulka: 
Statické, Dynamické, Defaultní
Statické:Používá se v malých sítích, pokud nebude změna v topologii
Dynamické: Funguje na základě routovacích protokolů, síť se automaticky přizpůsobuje změnám v topologii a dopravě dat. 
Automaticky se vypočítávají cesty pomocí routovacího protokolu.
Dynamické routovací protokoly jsou dvou základních typů: 
Distance vector, Link state

IGP->Distance vector -> RIP, RIP2
                     ->IGRP, EIGRP
   ->Link state -> IS-IS
                -> OSPF
EGP->Path vector -> BGP
Link - Kvalita linky; Distance - počet hopů
Defaultní routování: Pokud neexistuje jiná cesta, použije se default gateway - router. 


![image](https://user-images.githubusercontent.com/90755554/138130766-d8c7f1a4-0320-443c-a859-b27b63fec8d5.png)
