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
 -IGP->
Distance vector -> RIP, RIP2<br>
                ->IGRP, EIGRP<br>
   -Link state -> IS-IS<br>
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
<br>
<br>
<b>DHCP</b> - Používá se pro automatickou konfiguraci počítačů připojených do počítačové sítě. DHCP server přiděluje počítačům pomocí DHCP protokolu IP adresu. Je součástí většiny switchů a routerů. V default settings je zapnutý,ale nemá parametry -> Nepřiděluje adresy <br>
<b>MAC adresa</b> - Je přidělena na pevno. Je psaná v Hexadecimalní soustavě. První polovina je udána výrobci -> celosvětově. Druhá polovina samotným výrobcem. Je to jednoznačný modifikátor síťového zařízení.<br>
<b>ARP table</b> - Dočasně obsahuje Mac adresy<br>
<b>DNS</b> - Je zahrnutý v TCP/IP. Slouží k překladu jmen objektů na IP adresy či jiné zdrojové adresy. => Zadáme do vyhledávače Google.com, abychom si nemuseli pamatovat IP adresu, DNS to přeloží na IP. <br>
<b>ARP</b> - Protokol, který získává MAC adresy pro ARP tabulku. Běží na druhé síťové vrstvě TCP/IP.<br>
DHCP - Dynamic host configuration protocol
DNS - Domain name system
Adress resolution protocol<br>
<b>L3 switch</b> - Umožňuje routování<br>
<b>Dijkstrův algoritmus</b> - Algoritmus,podle kterého se vypočítávají nejlepší cesty. (SPF) <br>
<b>Vyhody oblastí OSPF</b> - Sníží výpočet SPF, menší routovací tabulky, snížení Link state update, odlehčení HW<br>
<b>Tabulky OSPF</b><br> 
- Routovací: Nejlepší routy do destinací<br>
- Topologie: Routovací záznamy do všech destinací<br>
- Sousedů: Informace o sousedních routerech<br>
- Link state database: Stejná pro všechny routery, pomocí ní se vytvoří routovací tabulky, obraz síťové topologie ve stromové struktuře

<b>Oblasti</b><br>
- Standard area: Přijímá link updaty a sumární routy i externí
- Backbone area: 
- Stub area
- Totally stubby area
- Not so stubby area
<br>
<br>

Propojení routovacích protokolů - <b>Route Redistribution</b><br>
Aby se dalo efektivně podporovat více routovacích protokolů v jedné internetwork, musí se sdílet informace mezi protokoly. Tomu se říká route redistribution. Redistribuce může být jednosměrná nebo obousměrná. Routery, které provádí redistribuci, se nazývají boundary (hraniční).

Redistribuce je, když routovací protokol zveřejňuje routy, které se naučil jiným způsobem, to jsou statické routy, přímo připojené interfacy nebo jiný routovací protokol. Různé routovací protokoly mají různé charakteristiky (jako metriku, podporu classles).

<b></b> - <br>
![image](https://user-images.githubusercontent.com/90755554/138130766-d8c7f1a4-0320-443c-a859-b27b63fec8d5.png)
