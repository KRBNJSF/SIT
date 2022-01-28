# SIT
<a href="https://vydb1.spsmb.cz/phpmyadmin/index.php">phpmyadmin</a><br>

<a href="https://github.com/KRBNJSF/SIT/tree/main/Cisco%20packet%20tracer">🔌 - Cisco files</a>

<b>Rozsah privátních adres: </b><br>
192.168.0.0/16<br>
172.16.0.0/12            ->  Používají se v místní síti<br>
10.0.0.0/8<br>
<b>Routovací tabulka: </b><br>
Statické, Dynamické, Defaultní<br>
Statické: Používá se v malých sítích, pokud nebude změna v topologii<br>
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

Redistribuce je, když routovací protokol zveřejňuje routy, které se naučil jiným způsobem, to jsou statické routy, přímo připojené interfacy nebo jiný routovací protokol. Různé routovací protokoly mají různé charakteristiky (jako metriku, podporu classles).<br>

Zařízení: 
---

<b>HUB</b> 
- Detekuje fyzicky připojené zařízení k HUB. Rozesílá adresy všem

<b>SWITCH</b>
- Detekuje specifická fyzická zařízení připojená ke SWITCH. Zná fyzické adresy (MAC), ukládá je do tabulky. Odesílá adresy na určené místo pomocí MAC

<b>HUB & SWITCH</b>
- Používají se k výměně dat v místní síti (LAN). K přeposílání dat do jiné sítě se využívá router, jelikož dokáže číst IP adresy.

<b>ROUTER</b>
- Směruje nebo předává data z jedné sítě do druhé na základě IP adresy.
- Využívá se k výměně nebo směrování dat do jiné sítě např. na internetu

RIP konfigurace: 
---
- 1)enable
- 2)conf t
- 3)ro RIP
- 4)ver 2
- 5)net [IP sítě]
- end
- wr

OSPF konfigurace
---
- 1)enable
- 2)conf t
- 3)ro ospf [id procesu] (1 - 30)
- 4)net [IP nové sítě] [inverzní maska] area [id oblasti]
- end
- wr

Redistribuce
---
<b>Redistribuce RIP</b>
- 1)ro rip
- 2)red ospf [id procesu] metric 1<br>

 <b>Redistribuce OSPF</b>
 
- 1)ro ospf [id procesu]
- 2)red rip metric 20 subnets


VLAN konfigurace
---
<a href="https://www.samuraj-cz.com/clanek/cisco-ios-7-konfigurace-vlan-vtp/">VLAN konfigurace samuraj</a>
- en
- conf t
- vlan [name ID] (například: 10)
- int [port ID]  (například: f0/1)
- switchport mode [mode] (například: access, dynamic, trunk)
- switchport access vlan [ID name] (například: 10)
- int [port ID]  (například: f0/2)
- switchport access vlan [ID name] (například: 10)

Pokud chci smazat VLAN - no vlan [ID name] (například 10)

<b>VLAN v Cisco packet tracer</b><br>
 <a href="https://github.com/KRBNJSF/SIT/raw/main/VLAN.pkt" target="_blank">
  <img src="https://i.pinimg.com/originals/ae/a2/3e/aea23e6bee60b97b28d41e523604948a.jpg" alt="VLAN v Cisco packet tracer" width="140" height="142">
</a><br>
<b>Click on the router to download: VLAN v Cisco packet tracer</b>

VLAN konfigurace - TRUNK
---

 - en
 - conf t
 - int [port ID] (například: g0/1)
 - sh
 - switchport trunk allowed vlan [rozsah povolených vlan] (například: 10-100)
 - switchport trunk native vlan [ID name] (například: 10)
 - switchport mode trunk
 - switchport nonegotiate
 - no sh
 
<b>Příklad: </b><br>
```
en
conf t
int g0/1
sh
switchport trunk allowed vlan 10-100
switchport trunk native vlan 10
siwtchport mode trunk
switchport nonegotiate
no sh
```
<b>TRUNK v Cisco packet tracer</b><br>
 <a href="https://github.com/KRBNJSF/SIT/raw/main/Trunk.pkt" target="_blank">
  <img src="https://i.pinimg.com/originals/ae/a2/3e/aea23e6bee60b97b28d41e523604948a.jpg" alt="VLAN v Cisco packet tracer" width="140" height="142">
</a><br>
<b>Click on the router to download: TRUNK v Cisco packet tracer</b>

VLAN
---

<a href="https://www.samuraj-cz.com/clanek/vlan-virtual-local-area-network/">Samuraj - VLAN</a><br>
<b>Co je to VLAN? (Vrtual local area network)</b>
- Souží k logickému rozdělení sítě nezávisle na fyzickém uspořádání -> Vše se rozdělí přímo na switchi, nemusí se hardwarově přepojovat.
- Sítě jsou rozděleny na menší sítě uvnitř fyzické struktury původní sítě

<b>Trunk port</b><br>
- Připojení na switchi, jež tvoří VLAN.
- Všechny rámce (jednotka přenosu na linkové (2.) vrstvě ISO/OSI), které prochází tímto portem, jsou VLAN tagged.<br>

<b>Pro zařazení komunikace do VLANy existují čtyři základní metody, ale v praxi je nejvíce využívána možnost první - zařazení dle portu.</b><br>

1. podle portu
2. podle MAC adresy
3. podle protokolu = podle informace z 3. vrstvy
4. podle autentizace

Maximální ID vlan je 4095

<b>IEEE 802.1q tagging</b><br>
Protokolu IEEE 802.1q se říká také trunking protokol nebo dot1q tagging. Jedná se o standardizovanou metodu, kterou podporují všechny moderní switche s podporou VLAN. Funguje na principu tzv. tagování. Vezmeme originální rámec, jeho hlavičku rozšíříme o 4B informací, z nichž první je značka, že se jedná o protokol 802.1q (hodnota 0x8100). Dále následuje priorita dle protokolu 802.1p, příznak, zda je MAC adresa v kanonickém tvaru a poslední je číslo VLANy.

Protože se změnila data, je třeba přepočítat kontrolní součet na konci rámce.


<b>Native VLAN</b><br>
Posílá netaggované rámce

<b>Dynamic trunk protocol (DTP)</b><br>
Protokol automaticky vyjedná na daném portu trunk

IPV4 prefixes
---

<b></b> - <br>
![image](https://user-images.githubusercontent.com/90755554/138130766-d8c7f1a4-0320-443c-a859-b27b63fec8d5.png)
