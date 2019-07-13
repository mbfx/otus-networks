# Статическая маршрутизация. Policy-based routing & SLA.

Задание:

1. Настроить статические маршруты так, чтобы маршрутизаторы R1, R5, R9 и R13 стали доступны между собой;
2. На маршрутизаторе R19 необходимо настроить политику маршрутизации так, чтобы пакеты до R13 ходили через R18-R20;
3. На маршрутизаторе R19 необходимо настроить политику маршрутизации так, чтобы пакет до R5 ходили через R18-R17;
4. Разобраться в технологии IP SLA и настроить политику маршрутизации на основе мониторинга каналов. При отключении линка R19-R18, маршруты должны пойти между R19-R20 и R19-R17;
5. Задокументировать все изменения, произведенные в лабораторном стенде.

R19
conf t
!
 route-map PBR-to-R13 permit 10
  match ip address PBR-to-R13-acl
  set ip next-hop verify-availability 90.90.131.129 1 track 100
  exit
!
 route-map PBR-to-R13 permit 20
  match ip address PBR-to-R5-acl
  set ip next-hop verify-availability 90.90.131.129 1 track 100
  exit
!
 route-map PBR-to-R13-v6 permit 10
  match ip address PBR-to-R13-aclv6
  set ipv6 next-hop verify-availability 20FF:CCFF:FFFF:6::18 1 track 200
  set ipv6 next-hop 20FF:CCFF:FFFF:6::18
  exit
!
 route-map PBR-to-R13-v6 permit 20
  match ip address PBR-to-R5-aclv6
  set ipv6 next-hop verify-availability 20FF:CCFF:FFFF:6::18 1 track 200
  set ipv6 next-hop 20FF:CCFF:FFFF:6::18
  exit
!
 ip access-list extended PBR-to-R13-acl
  permit ip any host 172.16.20.2
  deny ip any any
  exit
!
 ipv6 access-list PBR-to-R13-aclv6
  permit any host 20FF:CCFF:1000:20::2
  deny any any
  exit
!
 ip access-list extended PBR-to-R5-acl
  permit ip any host 172.16.17.2
  deny ip any any
  exit
!
 ipv6 access-list PBR-to-R5-aclv6
  permit any host 20FF:CCFF:1000:17::2
  deny any any
  exit
!
 interface e0/0
  ip policy route-map PBR-to-R13
  ipv6 policy route-map PBR-to-R13-v6
  exit
!
 ip sla 1
  icmp-echo 90.90.131.129 source-interface e0/3
  threshold 1000
  timeout 1500
  frequency 3
  exit
!
 ip sla schedule 1 life forever start-time now
!
 track 100 ip sla 1 reachability
  delay down 10 up 5
  exit
!
 ip sla 2
  icmp-echo 20ff:ccff:ffff:6::18 source-interface e0/3
  threshold 1000
  timeout 1500
  frequency 3
!
 ip sla schedule 2 life forever start-time now
! 
 track 200 ip sla 1 reachability
  delay down 10 up 5
  exit
!


R1, R5, R9, R13, R17, R18, R19, R20
Настроена статическая маршрутизация IPv4 и IPv6 согласно вкладке StatRouting
