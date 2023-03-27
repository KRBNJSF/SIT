# SIT

## 4. ročník
<a href="https://github.com/neostetic/School-Zapisky/tree/main/SIT/4_rocnik">ZDE</a>

## MD5 zabezpečení OSPF
// upravit

- ip ospf authentication-key [libovolnýKlíč]
- ip ospf authentication-key ck8z
- ip ospf message-digest-key 1md5 ck8z
- area 0 authentication message-digest

## IPv6
První čtyři části je adresa sítě, zbylé čtyři části adresy pro hosty
např. `2000:abcd:0000:0000` - adresa sítě `0000:0000:0000:0000` - adresy pro hosty

### Povolení routování IPv6
- en
- conf t
- ipv6 unicast-routing
- ipv6 cef

### IPv6 rozdělení adres
- en
- conf t
- ipv6 unicast-routing // pro routovani slouzi tento prikaz
- ipv6 cef
- int g0/0
- ipv6 add [adresa]/prefixMasky
- ipv6 add `2000:abcd:1234::1/90` eui-64

### RIP IPv6
- ipv6 rip [libovolnyIdentifikatorProcesu] enable
- ipv6 rip test enable

### OSPF IPv6
- en
- conf t
- int g0/1
- ipv6 add `2001:abcd::1/100`
- ex //Do globalni konfigurace
- ipv6 router ospf [id]
- ipv6 router ospf 1
- router-id [libovolnyIDRouteru - musi byt na kazdem routeru jedinecne]
- router-id 1.1.1.1 nebo router-id 2.2.2.2 apod.
- ex //Do globalni konfigurace
- int g0/1
- ipv6 ospf [id] area [id]
- ipv6 ospf 1 area 0

### Redistribuce IPv6
#### Stejné jako u IPv4, tzn. V OSPF redistribuce pro rip; v RIP redistribuce pro ospf
- Zde redistribuci provádíš na portu, ne na celém routeru
- Kam port směřuje, tam bude protokol
- na port g0/0 bude např. rip
- na port g0/1 bude např. ospf

#### OSPF
- ipv6 router ospf [id]
- ipv6 router ospf 1
- red rip [id]
- red rip test

#### RIP
- red rip [id]
- router rip test
- red ospf [id] metric [velikost]
- red ospf 1 metric 1

### VLAN IPv6
#### Stejné jako u IPv4; Pokud máme adresu `2000:abcd::0`, musíme do sub-if přidat adresu `2001:abcd::0`, aby nebyla ze stejné podsítě
- doplnit

### Zobrazení routovací tabulky IPv6
- show ipv6 ro

### Smazání IPv6 adresy
#### IPv6 adresy se nedají přepsat jako u IPv4. Místo toho se na jedno rozhraní přidají 2 adresy - to může dělat problémy.
- no ipv6 add [adresaKterouNechceme]/PrefixMasky
- no ipv6 add `2000:abcd:1234::1/90`

### Test funkce IPv6
#### Testování funkčnosti pouze pingem, obálky nefungují - jsou pouze pro IPv4
- do sh ipv6 int br //zkopiruji adresu
- ping [adresa]
- ping `2001:abcd::2`


## 3. ročník

<a href="https://vydb1.spsmb.cz/phpmyadmin/index.php">🔌 phpmyadmin</a><br>

<a href="https://github.com/KRBNJSF/SIT/tree/main/Cisco%20packet%20tracer">💾 Cisco files</a>

<a href="http://www.staggeringbeauty.com/">Stránka pro frajery</a>

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

DV (Distance vector) - <a href="http://www.cs.vsb.cz/grygarek/SPS/projekty0405/RouteOptimization/dokumentace/ar01s01.html">Distance vector</a>

LSA (Link State Advertisement) - <a href="https://www.geeksforgeeks.org/link-state-advertisement-lsa/">LSA</a>

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

Ukládání konfigurace
---
- copy running-config startup-config
- write

2 způsoby konfigurace (router, switch)
---
 - running config
 - startup config

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
<b>Zobrazení všech VLAN</b>
- show vlan

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

<b>2 způsoby tvorby VLAN</b>
- int [port ID] (například: f0/1)
- switchport acess VLAN [name ID]<br>
(Pokud VLAN neexistuje, tak se automaticky vytvoří)

- int [port ID] (například: f0/1)
- VLAN [name ID]

<b>VLAN v Cisco packet tracer</b><br>
 <a href="https://github.com/KRBNJSF/SIT/raw/main/VLAN.pkt" target="_blank">
  <img src="https://i.pinimg.com/originals/ae/a2/3e/aea23e6bee60b97b28d41e523604948a.jpg" alt="VLAN v Cisco packet tracer" width="140" height="142">
</a><br>
<b>Click on the router to download: VLAN v Cisco packet tracer</b>

<b>Změna názvu Switche</b>
- hostname [název]

<b>Změna názvu VLAN</b>
- VLAN [name ID]
- name [yourName] (například: sklady)

VLAN konfigurace - TRUNK
---

 - en
 - conf t
 - int [port ID] (například: g0/1)
 - sh
 - switchport trunk allowed vlan [rozsah povolených vlan] (například: 10-100)  |nebo|  sw tr all vlan [rozsah povolených vlan]
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


protocol VTP (VLAN Trunking Protocol)
---

<a href="https://www.samuraj-cz.com/clanek/cisco-ios-7-konfigurace-vlan-vtp/#diggs">🌐VTP - samuraj</a>

![image](https://user-images.githubusercontent.com/90755554/152783279-499b80a5-dd02-4360-a5a6-a9c089f3d371.png)<br>

<b>VTP modes</b>
- server (Obsahuje VLANy)
- client (Zkopíruje VLANy ze serveru)
- transparent (Žádné informace nebere, jen projde)


<b>Konfigurace VTP</b>

- en
- conf t
- vtp domain [domain name] (například: spsmb)
- vtp mode [mode] (například: client, server, transparent)


switch 1
```
- en
- conf t
- vtp domain spsmb
- vtp mode server
```
switch 2
```
- en
- conf t
- vtp domain spsmb
- vtp mode client
```
switch 3
```
- en
- conf t
- vtp domain spsmb
- vtp mode client
```

SVI (Switch Virtual Interface)
---
<a href="https://www.samuraj-cz.com/clanek/cisco-ios-7-konfigurace-vlan-vtp/">SVI - samuraj</a>

<b>SVI v Cisco packet tracer</b><br>
 <a href="https://github.com/KRBNJSF/SIT/raw/main/Cisco%20packet%20tracer/VLAN%20-%20TRUNK%20-%20SVI.pkt" target="_blank">
  <img src="https://i.pinimg.com/originals/ae/a2/3e/aea23e6bee60b97b28d41e523604948a.jpg" alt="VLAN v Cisco packet tracer" width="140" height="142">
</a><br>
<b>Click on the router to download: SVI v Cisco packet tracer</b>


![image](https://user-images.githubusercontent.com/90755554/153408309-d4947b1e-d158-455d-85ac-d08b3eba0388.png)

<b>Konfigurace SVI</b>
- en
- conf t
- int vlan [ID name]
- ip add [IP add] [mask]

```
- en
- conf t
- int vlan 2
- ip add 10.0.0.10 255.0.0.0
```

STP (Spanning Tree Protocol)
---
<a href="https://www.samuraj-cz.com/clanek/cisco-ios-9-spanning-tree-protocol/">STP - samuraj</a>
<p align="center">
<img src="https://user-images.githubusercontent.com/90755554/153857801-a15f0c1e-548f-43fd-a064-ae1356ab6c57.png" alt="STP" width="85%">
 
<img src="https://user-images.githubusercontent.com/90755554/153857831-2c82f5bd-5d94-493d-8b93-d2bcd4fcad62.png" alt="STP" width="85%">
</p>

### <b>Problémy smyček</b>
- <b>broadcastová bouře</b> - u broadcastů se tyto budou rozmnožovat, až dosáhnou kritického množství
- <b>problémy s konektivitou</b> nebo nestabilita tabulky MAC adres (CAM)
  - díky smyčce zpráva přijde na switch z více portů a on si stále mění adresu zdroje, v určitém případě může dojít k tomu, že si switch myslí, že je stanice připojena ke špatnému portu a nikdy ji nedoručí zprávu
- <b>několikanásobné doručení</b>
  - zpráva koluje v síti stále dokola a stále se doručuje

![image](https://user-images.githubusercontent.com/90755554/153859402-91e22655-a6ff-4039-af90-c5ece23b3f42.png)


<b>STP v Cisco packet tracer</b><br>
 <a href="https://github.com/KRBNJSF/SIT/raw/main/Cisco%20packet%20tracer/STP.pkt" target="_blank">
  <img src="https://i.pinimg.com/originals/ae/a2/3e/aea23e6bee60b97b28d41e523604948a.jpg" alt="VLAN v Cisco packet tracer" width="140" height="142">
</a><br>
<b>Click on the router to download: STP v Cisco packet tracer</b>

### <b>Konfigurace STP</b>
- <b>Konfigurace pro celý switch</b>
  - en
  - conf t
  - spanning-tree portfast default
 
```
- en
- conf t
- spanning-tree portfast default
```

- <b>Konfigurace na určitý port</b>
  - en
  - conf t
  - int [port ID] (například: f0/1)
  - spanning-tree portfast

```
- en
- conf t
- int f0/1
- spanning-tree portfast
```
 


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

Maximální ID vlan je 4095<br>
2-1001	běžný rozsah pro ethernetové VLANy

<b>IEEE 802.1q tagging</b><br>
Protokolu IEEE 802.1q se říká také trunking protokol nebo dot1q tagging. Jedná se o standardizovanou metodu, kterou podporují všechny moderní switche s podporou VLAN. Funguje na principu tzv. tagování. Vezmeme originální rámec, jeho hlavičku rozšíříme o 4B informací, z nichž první je značka, že se jedná o protokol 802.1q (hodnota 0x8100). Dále následuje priorita dle protokolu 802.1p, příznak, zda je MAC adresa v kanonickém tvaru a poslední je číslo VLANy.

Protože se změnila data, je třeba přepočítat kontrolní součet na konci rámce.


<b>Native VLAN</b><br>
Posílá netaggované rámce

<b>Dynamic trunk protocol (DTP)</b><br>
Protokol automaticky vyjedná na daném portu trunk

### SVI (Telnet, SSH)

TELNET CONNECTION
 - Switch(config)#int vlan [number] (příklad: 10)
 - Switch(config-if)#ip address [ip] [mask] (příklad: 192.168.1.10  255.255.255.0)
 - Switch(config-if)#exit

SVI
 - Switch(config)#line vty [numbers] (příklad: 0 1)
 - Switch(config)#password [password] (příklad: cisco)
 - Switch(config)#enable secret [password] (příklad: cisco)

SVI + SSH configuration
 ...
 - Switch(config)#hostname [name]
 - name(config)#username [username] secret [password] (příklad: cisco ... heslo)
 - name(config)#ip ssh time-out [time is seconds] (příklad: 60)
 - name(config)#ip ssh authentication-retries [tries] (příklad: 3)
 - name(config)#ip ssh version 2
 - name(config)#ip domain name [name] (příklad: spsmb.local) 
 - name(config)#crypto key generate rsa
 - ...
 - How many bits in the modulus [512]: 1024
 - name(config)#line vty [numbers] (příklad: 0 1)
 - name(config)#transport input ssh

TELNET CONNECTION
 - On pc:
   - Telnet / SSH Client
     - Telnet
     - IP : [ip address]

### Konfigurace TRUNKu na Routeru
 - int [idPortu].[idVlan] (př.: int g0/0.10)
 - encapsulation dot1Q [idVlan] native (př.: encapsulation dot1Q 10 native)
 - ip add 192.168.1.2 255.255.255.0
 - exit
 - int [idPortu].[idVlan] (př.: int g0/0.20)
 - encapsulation dot1Q [idVlan] (př.: encapsulation dot1Q 20) - Nenativní Vlan
 - ip add 192.168.2.2 255.255.255.0
 - exit
 - int g0/0
 - no sh

<a href="https://github.com/KRBNJSF/SIT/raw/main/Cisco%20packet%20tracer/Schema.pkt" target="_blank">
  <img src="https://i.pinimg.com/originals/ae/a2/3e/aea23e6bee60b97b28d41e523604948a.jpg" alt="VLAN, SVI, Telnet v Cisco packet tracer" width="140" height="142">
</a><br>

ACL (Access Control list)
---
<a href="https://www.samuraj-cz.com/clanek/cisco-ios-8-access-control-list/">ACL</a>

<b>Použití ACL: </b>
 - filtrování paketů - řízení (omezování) síťového provozu


### Typy ACL
 - IP ACL - filtruje IPv4 provoz – IP, TCP, UDP, IGMP (multicast), ICMP
   - Port ACL - pro fyzický L2 interface (aplikujeme na port), pouze příchozí směr
 - MAC ACL - non-IP provoz
   - Port ACL
   - VLAN map


IPV4 prefixes
---

<b></b> - <br>
![image](https://user-images.githubusercontent.com/90755554/138130766-d8c7f1a4-0320-443c-a859-b27b63fec8d5.png)

---

## IPv6

<a href="https://github.com/KRBNJSF/SIT/tree/main/IPv6">IPv6 - prezentace</a>

 - větší adresní prostor - 128 bitů
 - změna IP hlavičky - 40 bytů
 - rozšířující hlavičky
 - síťová maska - min. 64 bitů
 - skupiínové adresy
   - FF02::1 - všichni hosté
   - FF02::2 - všechny směrovače
   - FF02::1:2 - všechny DHCP servery
 - absence překladu adres (NAT)
 - ARP je nahrazen ICMPv6 ND
 - detekce duplicitních adres (DAD)
 - prostředky pro jednodušší správu sítě
 - vestavěné bezpečnostní mechanismy (IPsec)
 - mobilita
 - podpora jumbogramů = větší než 64kB - 4GB
 - optimalizace pro směrování
 - IP fragmentace
 
![image](https://user-images.githubusercontent.com/83291717/165069573-d4b415fa-61ce-4388-b4f0-ac51ad5bac70.png)

#### IP adresa
 - zápis je realizován v 16-kové soustavě
 - 128 bitů (16 bytů) rozděleno po 2 bytech oddělených dvojtečkou
 - ukázka globální inviduální adresy (obdoba IPv4 veřejné adresy)
 - `2001:0db8:ab00:00c3:0000:0000:0000:0002`
 - `ff01:0000:0000:0000:0000:0000:0000:0101`
 - pro zjednodušení lze použít následující pravidla:
   - počáteční nuly v každé dvojici bytů lze vynechat
     - např. `ff01:0:0:0:0:0:0:101`
   - sousedící nulu lze nahradit
     - např. `ff01::101`
 - **zkrácení zápisu lze provést pouze jednou!!! (nejednoznačnost interpretace)**
 - ***špatný zápis adresy:***
 - `2001::FFD3::57ab`
 - RFC 5952 - zaveden **"kanonický zápis"**
 - účelem je snížit polymorfii adres
 - aplikace na vstup podporuje všechny tvary adres, ale na výstupu je používán pouze kanonický zápis
 - pravidla kanonického zápisu:
 		- šestnáctkové číslice se zapisují malými písmeny
 		- vynechání počátečních nul ve čteřici je povinné
 		- konstrukce "::" musí mít co největší efekt
 
 #### Typy Adres	
  - **Inviduální adresy (unicast)**
    - označuje jedno rozhrání připojeného počítače či zařízení
  - **Slupinové adresy (multicast)**
    - představují adresu skupiny síťových rozhrání
    - paket se skupinovou cílovou adresou bude dopraven všem členům skupin
    -  tyto adresy se používají nejčastěji pro zvukové či obrazové sdílení
  - **Výběrové adresy (anycast)**
    - také označují skupinu síťových rozhrání, ale datagram bude dopraven jen na jedno z nich 
  - **Neexistuje broadcast!!!**

| prefix | význam |
| --- | --- |
| ::/128 | nedefinovaná adres |
| ::1/128 | lokální smyčka |
| fc00::/7 | unikátní inviduální lokální |
| fe80::/10 | individuální lokální linkové adresy |
| ff00::/8 | skupinové |
| ostatní | individuální globální |

#### Prefix
- **Prefixy** se zapisují stejně jako IPv4 adresa/délka, kde adresa určuje začátek adresy (její nevýznamné bity bývá zvykem vynulovat) a délka definuje, kolik bitů se významných
- Například prefixu ***ff::/8*** vyhoví každá adresy, jež má v privních osmi bitech samé jedničky

#### Hlavička IPv6
![image](https://user-images.githubusercontent.com/83291717/165735687-7f526331-d129-42e8-b75d-13f6226597e9.png)

- **Verze IP** = 6
- **Třída dat** - 4 bity (0 - 15)
  - specifukuje přenášená data pro případ rozhodování v okamžiku zahlcení sítě
- **A)** - 0 - 7 - klasický provoz
  - 0 - nespecifikovaná data
  - 1 - provoz na pozadí
  - 2 - automatický provoz
  - 4 - uživatelem prováděné velké přenosy (ftp)
  - 6 - interaktivní provoz (telnet)
  - 7 - řízení sítě (směrovací protokoly)
- **B)** - 8 - 15 - určeno pro přenosy v reálném čase (audio)
- datagramy s nižší hodnotou se zahazují dříve než s hodnotou vyšší - platí pouze pro interval **8 - 15**
- **identifikace toku dat** - řeší směrování datagramů
- datagramy jednoho souboru dostanouá svou identifikaci
- směrovač řeší úlohu směrování **pouze pro první datagram**
- cestu si uloží do paměti (max. na 6 vteřin)
- zbylé datagramy posílá na základě záznamu v paměti
- lze využít i k zajištění šířky přenášeného pásma
- **délka dat** - specifikuje délku IP datagramu
- velikost - 2 bajty
- možnost zvětšení - v další hlavičce
- **další hlavičky** - specifikuje typ následující hlavičky
  - nepovinná položka
  - obsahuje jen nutné hlavičky
  - pole **délka hlavičky** - specifikuje posunutí, které je potřeba udělat k další hlavičce 
#### Směrované informace
- v současnosti je využívána jediná volba (typ=0) - explicitní směrování
- jsem specifikovány IP adresy směrovačů
#### Záhlaví fragmentu
- každý IP datagram neobsahuje identifikaci
- identifikace je pouze v dalším záhlaví
#### Autentiyační hlavička
- odesílatel autentizuje data
- datagram je zabezpečen proti změně
- kontrolní součet se počítá pomocí algoritmu MD-5
- klíč je dlouhý 128 bitů - vymění si jej odesílatel s příjemcem
#### Bezpečnostní hlavička
- umožňuje šifrování přenášená data
- musí být poslední hlavičkou
- první 4 bajty - info pro šifrování (typ šifry, mód šifry, šifrovací klíče atd.)
- využití bezpečnosti hlavičky:
- šifruje odesílatel, dešifruje příjemce
- odesílatel ani příjemce se šifrováním nezabývají. Šifrují až směrovače (bezpečnostní brány)

### Přechod IPv4 do IPv6
#### Dvojí zásobník
- uzly podporují oba protokoly
- je vyžadován IPv4
- východisko pro další dvě metodyd
- v současné době se v tomto režimu nachází většina sítí a zařízení
#### Tunelování
- tunel slouží k domluvě dvou zařízení pracující na stejném protokolu, ale mezi nimi ležící síť tento protokol nepodporuje
- existují dva typy tunelů
  - **1. Explicitně konfigurovaný** - vytváří správce dotyčného zařízení
    - podporu nabízí "tunelové servery" - po registraci se konfiguračním scriptem vytvoří tunel do IPv6 sítě
  - **2. Automatický** - vytvořen bez lidského zásahu
#### Transátory
- řeší komunikaci stroje podporující jen IPv4 se strojem s pouze IPv6
- základn představuje překlad adres a algoritmus pro překlad IP datagramů
- nejvýznamnější je **NAT64**
- umístění - mezi koncovou (IPv6) sítí a Internetem (IPv4)
- má k dispozici sadu **IPv4** adres a na ně mapuje **IPv6** adresy z koncové sítě
- spolupracuje s **DNS64** - místním strojům jsou jména IPv4 adres překádána na IPv6 adresy mapující jejich skutečné IPv4 adresy
#### 6to4
- **Oficiálně**: Connection of IPv6 Domains via IPv4 Clouds
- automatický tunelovací mechanismus
- uplatnění např. když chceme nasadit IPv6, IPS podpuruje jen IPv4
- je nutná jedna veřejná IPv4 adresa
- veřejná IPv4 adresa přiřazena 6to4 směrocači
- vytvoří se prefix std. dělky **48** bitů
- prvních 16 bitů - **2002**
- následující 32 bitů je tvořeno IPv4 adresou 6to4 směrovače
- **příklad**: IPv4 adresa je 1.2.3.4
- **prefix**: 2002:102:304::/48 *(5 skupinek se nahradilo ::)*
- komunikaci s IPv6 světem zajišťují 6to4 zprostředkovatelé
- jedná se o směrovače v Internetu mající přístup k IPv4 i IPv6 Internetu a podporující 6to4
- směrocacími protokoly ohlašují dostuppnost prefixu **2002::/16**
- pro přestup ze 6to4 do nativního IPv6 je přidělena pevná výběrová adresa **192.88.99.1** (6to4 **2002:c058:6301::**)
- 6to4 směrovač si tuto adresu nastaví jako implicitní cestu
- **přednosti**
  - nenáročnost a jednoduchost - jedna veřejná IPv4 adresa + konfigurační příkazy na přístupovém směrovači
- **nedostatky**
  - nespolehlivost (vysoká) - využívají se prvky provozované různými subjekty
  - asymetrické směrování - nelze ovlivnit
- tyto nedostatky odstraňuje **6rd**
#### 6rd - rapid deployment
- mechanismus vychází z 6to4
- prefixy vychází z IPv4 adres adresního prostoru **poskytovatele**
- pro prefix vyčleněno **32 bitů**
- **přednosti**
  - operace probíhající v síti poskytovatele
  - vyšší míra spolehlivosti 
- **nedostatky**
  - závislost na poskytovateli - pokud 6rd nepodporuje je nedostupný pro klienty
  - prefix /32 představuje všechny IPv6 adresy poskytovatele a nemůže je vyhradit pro 6rd

### ICMP v6
- signalizace chybových stavů a diagnostika
- definován v RFC 2463
- nové funkce oproti ICMP pro IPv4
- z hlediska struktury paketu se jeví jako protokol vyšší vrstvy

![image](https://user-images.githubusercontent.com/83291717/171611129-ec4da8e5-4538-413e-abe6-469f173ad935.png)
![image](https://user-images.githubusercontent.com/83291717/171611192-b6ec4407-1359-4673-8084-f987b714c607.png)

#### překlad IP adres na linkové adresy
- stanice „**A**“ chce odeslat IP datagram stanici „**B**“
- potřebuje zjistit linkovou adresu (IP adresu zná)
- pro zjištění slouží **dva typy** ICMP zpráv:
- **1) 6ádost o linkovou adresu – oběžník**
  - pole Hopy = 255
  - při průchodu přes směrovač je hodnota snížena na menší hodnotu
  - příjemce následně zjistí, že se jedná o zatoulanou žádost
  - **neodpovídá** na ní
  - pole příjemce – IP adrese `FF02:1::4321:1234`
  - jedná se o oběžník
  - první část adresy specifikuje oběžník
  - druhá část – poslední čtyři bajty IP adresy příjemce
  - každá stanice je povinna poslouchat oběžníky výše uvedeného typu
  - snižuje se zatížení stanic na síti
- **2) oznámení o linkové adrese**
  - odpovědí na žádost je „oznámení o linkové adrese“
  - příjemce tuto informaci ukládá do paměti
  - pole „Hopy“ = 1 – zamezí zatoulání
  - IP adresa příjemce = IP adresa žadatele, ne oběžník
  - bit „**R**“ = 1 – odesílatel je směrovač
  - bit „**S**“ = 1 – odpověď na žádost
  - bit „**O**“ = 1 – odesílatel zdůrazňuje příjemci nutnost přepsání hodnoty uložené v paměti
#### zjištění adresy směrovače na LAN
- stanice při komunikaci mimo LAN musí znát IP adresu směrovače – získá položku „default“ do své směrovací tabulky
- směrovače tuto informaci pravidelně šíří pro všechny počítače v LAN oběžníkem pomocí ICMP zprávy oznámení o směrování
- po přijetí zprávy: směr default = odesílatel
#### ICMP zpráva oznámení o směrování
- typ: 134; Kód: 0
- max. hopů: stanicím je doporučována hodnota, kterou mají vyplňovat do pole počet hopů v základním záhlaví IP datagramu
- bity „M“ a „O“: pro protokoly vyšších vrstev (slouží pro automatickou konfiguraci stanice. Např. DHCP)
- životnost informace (Router Lifetime): čas ve vteřinách, po který by měla stanice položku default udržovat ve směrovacích tabulkách
- hodnota „0“ – neudržovat default ukazující na odesílatele
- čas dosažitelnosti a časový interval opakování žádosti: týkají se žádostí o linkovou adresu souseda - údaj je v milisekundách
- čas dosažitelnosti: předpoklad dosažitelnosti souseda
- časový interval opakování žádosti: jak dlouho se má udržovat položka v paměti
