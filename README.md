# SIT
<b>Rozsah privátních adres: </b><br>
192.168.0.0/16<br>
172.16.0.0/12            ->  Používají se v místní síti<br>
10.0.0.0/8<br>
<b>Routovací tabulka: </b><br>
Statické, Dynamické, Defaultní<br>
Statické:Používá se v malých sítích, pokud nebude změna v topologii<br>
Dynamické: Funguje na základě routovacích protokolů, síť se automaticky přizpůsobuje změnám v topologii a dopravě dat. <br>
Automaticky se vypočítávají cesty pomocí routovacího protokolu.<br>
Dynamické routovací protokoly jsou dvou základních typů: <br>
Distance vector, Link state<br>
<br>
IGP->Distance vector -> RIP, RIP2<br>
                     ->IGRP, EIGRP<br>
   ->Link state -> IS-IS<br>
                -> OSPF<br>
EGP->Path vector -> BGP<br>
Link - Kvalita linky; Distance - počet hopů<br>
IGP - Routuje uvnitř AS<br>
EGP - Routuje mezi AS<br>
<b>Defaultní routování:</b> Pokud neexistuje jiná cesta, použije se default gateway - router. <br>
<br>
<b>VLSM</b> - Možnost s subbnetu použít různé velikosti masky<br>
<b>Routování</b> - Směřování: Určování cest dat. Propojení jednotlivých subbnetů za účelem určení cesty poslaných dat mezi sítěmi. Slouží k tomu routery, switche, servery a PC. <br>
<b>AS</b> - Je skupina podsíti a routerů, které jsou pod správou jedné nebo více jednotek. (Lokální síť) <br>
<b>CIDR</b> - Zapsání masky ve zkrácené formě (prefix),CIDR notace. Reprezentuje počet jedničkových bitů v masce. <br>
<b>TTL</b> - Smrtelnost paketu<br>
<b>RIP</b><br>
<br>
<a href="https://www.samuraj-cz.com/clanek/cisco-routing-3-ospf-open-shortest-path-first/">
Samuraj - OSPF
</a>
![image](https://user-images.githubusercontent.com/90755554/138130766-d8c7f1a4-0320-443c-a859-b27b63fec8d5.png)
