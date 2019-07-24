### Проектная работа:
### Комплексная реализация слияния геораспределённых сетей предприятий через сеть провайдера.

#### Задание:

  1. Распределить адресное пространство;
  2. Реализовать нескольких видов статической маршрутизации;
  3. Настроить VPN-туннели (статические и динамические);
  4. Настроить протоколы маршрутизации OSPF и EIGRP внутри локальных сетей;
  5. Настроить протокол маршрутизации BGP;
  6. Оптимизировать основные параметры и метрики протоколов IGP;
  7. Оптимизировать работу протокола BGP;
  8. Настроить инфраструктурные сервисы (NTP, DNS, DHCP и т.п.);
  9. Обеспечить шифрование VPN-туннелей;
  10. Обеспечить безопасность и мониторинг сетевой инфраструктуры;
  11. Задокументировать все выполненные действия.

#### Базовая схема.

![](pics/final_base.png)

###  1. Адресное пространство
 - [Автономные системы и принадлежащие им публичные адреса сетей](docs/AS_and_their_addresses.md)
 - [Таблица используемых подсетей IPv4.](docs/subnets_ipv4.md)
 - [Таблица используемых подсетей IPv6.](docs/subnets_ipv6.md)
 - [Таблица назначенных сетевых адресов на интерфейсах маршрутизаторов.](docs/rtr_addresses.md)

###  2. Статическая маршрутизация
 - [Static routing](docs/static_routing.md)
 - [PBR (Policy-based routing)](docs/PBR.md)

###  3. VPN-туннели
 - [GRE (Generic Routing Encapsulation)](docs/vpn.md)
 - [DMVPN (Dynamic Multipoint VPN)](docs/vpn.md#DMVPN)

###  4. Динамическая маршрутизация
 - [OSPF (Open Shortest Path First)](docs/OSPF.md)
 - [EIGRP (Enhanced Interior Gateway Routing Protocol)](docs/EIGRP.md)
 - [BGP (Border Gateway Protocol)](docs/BGP.md)
   - [eBGP (Exterior Border Gateway Protocol)](docs/BGP.md#ebgp-exterior-border-gateway-protocol)
   - [iBGP (Interior Border Gateway Protocol)](docs/BGP.md#ibgp-interior-border-gateway-protocol)

###  5. Инфраструктурные сервисы
 - [NTP (Network Time Protocol)](docs/NTP.md)
 - [DNS (Domain Name System)](docs/DNS.md)
 - [DHCP (Dynamic Host Configuration Protocol)](docs/DHCP.md)

###  6. Защита VPN-туннелей
 - [CAS (Certificate Authority Server)](docs/CA_and_IPSec.md#cas-certificate-authority-server)
 - [IPsec (Internet Protocol Security)](docs/CA_and_IPSec.md#ipsec-internet-protocol-security)

###  7. Безопасность и мониторинг
 - [AAA (Authentication, Autorization and Accounting)](docs/AAA.md)
 - [ACL (Access Control Lists)](docs/ACL.md)
