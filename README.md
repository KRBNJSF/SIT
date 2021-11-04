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
IGP - Routuje uvnitř AS
EGP - Routuje mezi AS
Defaultní routování: Pokud neexistuje jiná cesta, použije se default gateway - router. 

VLSM - Možnost s subbnetu použít různé velikosti masky
Routování - Směřování: Určování cest dat. Propojení jednotlivých subbnetů za účelem určení cesty poslaných dat mezi sítěmi. Slouží k tomu routery, switche, servery a PC. 
AS - Je skupina podsíti a routerů, které jsou pod správou jedné nebo více jednotek. (Lokální síť) 
CIDR - Zapsání masky ve zkrácené formě (prefix),CIDR notace. Reprezentuje počet jedničkových bitů v masce. 
TTL - Smrtelnost paketu
RIP

![image](https://user-images.githubusercontent.com/90755554/138130766-d8c7f1a4-0320-443c-a859-b27b63fec8d5.png)
