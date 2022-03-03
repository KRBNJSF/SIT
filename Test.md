## SÍŤ otázky

1) Co to je routování
   - Směrování packetů po síti

2) Jak pracuje router
   - Přenáší data z jedné sítě do druhé a pracuje na 3. vrstvě OSI modelu

3) Model ISO/OSI – vrstvy a hlavní protokoly v jednotlivých vrstvách
   - ...

4) Na jaké vrstvě pracuje router, co v dané vrstvě představuje adresu
   - Pracuje na 3. vrstvě (Síťové) a přeposílá data směrováním/routováním
 
5) Na jaké vrstvě se uplatňuje MAC adresa a jak je tvořená
   - Pracuje na 2. vrstvě (linková) a je tvořena ze 16kové soutatvy

6) Jaký protokol se stará o zjištění MAC adresy a k ní přiřazení příslušné IP adresy
   - TCP/IP (4. transportní vrstva)

7) Co to je strukturovaná síť – používané prvky
   - ...

8) Jaké jsou konfigurační módy Cisco routerů a switchů
   - Uživatelský, Privilegovaných, Globální konfigurace

9) V jakých módech lze použít příkaz SHOW
   - ...

10) Uveďte dva příkazy pro uložení konfigurace
    - write, copy running-config startup-config

11) Jaké jsou verze protokolu RIP
    - 1, 2, ng

12) Uveďte rozdíly mezi verzemi protokolů RIP
    - 1 - …, 2 - …, ng - podporuje verzi IPv6

13) Rozdělení routovacích protokolů
    - Statické, Dynamické

14) Kde se používá protokol BGP a co je AS
    - Protokol který upravuje IP adresy podle změny topologie, AS je skupina routrů a IP prefixů se společnou správou

15) V jakých sítích použijeme protokol RIP a OSPF a proč
    - RIP má 15 omezených hopů oproti OSPF
    - RIP využijeme v malých sítí a OSPF ve větších

16) Jak funguje protokol RIP
    - Aktualizuje informace o směrovacích tabulkách

17) Jak funguje protokol OSPF, použitý algoritmus
    - Dyjkstrův algoritmus; hledá nejkratší cestu

18) Z jakého důvodu rozdělujeme sítě v prostředí OSPF na oblasti (area)
    - ...

19) V jakém tvaru se zadává v OSPF maska podsítě – uveďte příklad
    - Inverzní tvar - 0.0.0.3

20) Co je „redistribuce“
    - Podpora dvou a více protokolů na jedné síti

21) Jak jsou označovány switche, které umí routovat a jak switche „normální“
    - ...

22) Co způsobí vytvoření VLAN
    - ...

23) Jaké VLANy jsou přítomné ve switchích Cisco a co s nimi (ne)lze dělat
    - ...

24) Způsoby přiřazení koncových zařízení do VLAN
    - ...

25) Co je to TRUNK, co se stane s rámcem a dle jakého protokolu IEEE
    - PORT který je ve více VLAN, IEEE 802.1

26) Jaká čísla VLAN můžeme použít
    - 2 až 1001
    - 0 pro systém
    - 1 defaultní

27) Co je VTP a jaké jsou módy
    - Protokol, který přenáší informace o VLAN do jiné domény, módy: Server, Klient, Transparent

28) O co se stará protokol STP. Kde se doporučuje vypnout a kde ne
    - Odstraňuje LAN smyčky

29) Co je SVI – z jakého důvodu ho nastavujeme
    - ... 

30) K čemu se používá protokol Telnet a SSH. Z jakého důvodu nepoužíváme Telnet
    - Jedná se o protokoly pro řízení switche na dálku přes počítač, Telnet není zabezpečený
