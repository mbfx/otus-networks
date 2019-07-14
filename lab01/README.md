#  IPv4/v6

###  Задание:

  1. Разработать и задокументировать адресное пространство;
  2. Настроить IP адреса на каждом активном порту;
  3. Использовать IPv4 и IPv6;
  4. Задокументировать все изменения.



###  Решение:

  1. [Задокументируем используемое адресное пространство с использованием IPv4 и IPv6;](README.md#1-%D0%B7%D0%B0%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%B8%D1%80%D1%83%D0%B5%D0%BC-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D1%83%D0%B5%D0%BC%D0%BE%D0%B5-%D0%B0%D0%B4%D1%80%D0%B5%D1%81%D0%BD%D0%BE%D0%B5-%D0%BF%D1%80%D0%BE%D1%81%D1%82%D1%80%D0%B0%D0%BD%D1%81%D1%82%D0%B2%D0%BE-%D1%81-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%D0%BC-ipv4-%D0%B8-ipv6)
  2. [Задокументируем выделенные для маршрутизаторов IP-адреса;](README.md#2-%D0%B7%D0%B0%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%B8%D1%80%D1%83%D0%B5%D0%BC-%D0%B2%D1%8B%D0%B4%D0%B5%D0%BB%D0%B5%D0%BD%D0%BD%D1%8B%D0%B5-%D0%B4%D0%BB%D1%8F-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%82%D0%BE%D1%80%D0%BE%D0%B2-ip-%D0%B0%D0%B4%D1%80%D0%B5%D1%81%D0%B0)
  3. [Настроим IP-адреса с учетом приведённой выше схемы и задокументируем изменения:](README.md#3-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B8%D0%BC-ip-%D0%B0%D0%B4%D1%80%D0%B5%D1%81%D0%B0-%D1%81-%D1%83%D1%87%D0%B5%D1%82%D0%BE%D0%BC-%D0%BF%D1%80%D0%B8%D0%B2%D0%B5%D0%B4%D1%91%D0%BD%D0%BD%D0%BE%D0%B9-%D0%B2%D1%8B%D1%88%D0%B5-%D1%81%D1%85%D0%B5%D0%BC%D1%8B-%D0%B8-%D0%B7%D0%B0%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%B8%D1%80%D1%83%D0%B5%D0%BC-%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D1%8F)
     - [Пример настройки на маршрутизаторе R1;](README.md#%D0%BF%D1%80%D0%B8%D0%BC%D0%B5%D1%80-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8-%D0%BD%D0%B0-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%82%D0%BE%D1%80%D0%B5-r1)
     - [Конфигурационные файлы;](configs/)
     - [Итоговая графическая схема.](README.md#%D0%B8%D1%82%D0%BE%D0%B3%D0%BE%D0%B2%D0%B0%D1%8F-%D0%B3%D1%80%D0%B0%D1%84%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B0%D1%8F-%D1%81%D1%85%D0%B5%D0%BC%D0%B0)

###  1. Задокументируем используемое адресное пространство с использованием IPv4 и IPv6.


  Общая таблица сетей.

| Network IPv4     | Summary net    | Network IPv6             | Summary net         | Description   | Eq&port         |
|-----------------:|:---------------|-------------------------:|:--------------------|:-------------:|-----------------|
| 90.90.128.0/24   | 90.90.128.0/22 | 20FF:CCFF:FFFF:1::/64    | 20FF:CCFF:FFFF::/48 | ISP network   | R17e0/1 R18e0/1 |
| 90.90.129.0/24   | 90.90.128.0/22 | 20FF:CCFF:FFFF:2::/64    | 20FF:CCFF:FFFF::/48 | ISP network   | R17e0/2 R19e0/2 |
| 90.90.130.0/25   | 90.90.128.0/22 | 20FF:CCFF:FFFF:3::/64    | 20FF:CCFF:FFFF::/48 | ISP network   | R18e0/2 R20e0/2 |
| 90.90.130.128/25 | 90.90.128.0/22 | 20FF:CCFF:FFFF:4::/64    | 20FF:CCFF:FFFF::/48 | ISP network   | R19e0/1 R20e0/1 |
| 90.90.131.0/25   | 90.90.128.0/22 | 20FF:CCFF:FFFF:5::/64    | 20FF:CCFF:FFFF::/48 | ISP network   | R17e0/3 R20e0/3 |
| 90.90.131.128/25 | 90.90.128.0/22 | 20FF:CCFF:FFFF:6::/64    | 20FF:CCFF:FFFF::/48 | ISP network   | R18e0/3 R19e0/3 |
| 172.16.17.0/30   | not used       | 20FF:CCFF:1000:17::/64   | not used            | to Internet   | R5e0/0  R17e0/0 |
| 172.16.18.0/29   | not used       | 20FF:CCFF:1000:18::/64   | not used            | to Internet   | R9e0/0  R18e0/0 |
| 172.16.19.0/30   | not used       | 20FF:CCFF:1000:19::/64   | not used            | to Internet   | R1e0/0  R19e0/0 |
| 172.16.20.0/30   | not used       | 20FF:CCFF:1000:20::/64   | not used            | to Internet   | R13e0/0 R20e0/0 |
| 50.50.96.0/23    | 50.50.96.0/21  | 20FF:CCFF:200A:A1::/64   | 20FF:CCFF:200A::/48 | Трум-пум      | R9e0/1  R12e0/1 |
| 50.50.98.0/23    | 50.50.96.0/21  | 20FF:CCFF:200A:A2::/64   | 20FF:CCFF:200A::/48 | Трум-пум      | R11e0/0 R12e0/0 |
| 50.50.100.0/24   | 50.50.96.0/21  | 20FF:CCFF:200A:A3::/64   | 20FF:CCFF:200A::/48 | Трум-пум      | R9e0/2  R10e0/2 |
| 50.50.101.0/24   | 50.50.96.0/21  | 20FF:CCFF:200A:A4::/64   | 20FF:CCFF:200A::/48 | Трум-пум      | R10e0/1 R11e0/1 |
| 50.50.102.8/29   | 50.50.96.0/21  | 20FF:CCFF:200A:A5::/64   | 20FF:CCFF:200A::/48 | Трум-пум      | R9e0/3  R11e0/3 |
| 50.50.104.0/24   | 50.50.104.0/23 | 20FF:CCFF:200B:A1::/64   | 20FF:CCFF:200B::/48 | Трам-пам      | R5e0/2  R7e0/2  |
| 50.50.105.0/25   | 50.50.104.0/23 | 20FF:CCFF:200B:A2::/64   | 20FF:CCFF:200B::/48 | Трам-пам      | R5e0/1  R6e0/1  |
| 50.50.105.128/25 | 50.50.104.0/23 | 20FF:CCFF:200B:A3::/64   | 20FF:CCFF:200B::/48 | Трам-пам      | R6e0/0  R7e0/0  |
| 35.10.0.0/21     | 35.10.0.0/18   | 20FF:CCFF:200C:A1::/64   | 20FF:CCFF:200C::/48 | Трым-пым A0   | R1e0/2  R3e0/2  |
| 35.10.8.0/23     | 35.10.0.0/18   | 20FF:CCFF:200C:A2::/64   | 20FF:CCFF:200C::/48 | Трым-пым A0   | R1e0/1  R2e0/1  |
| 35.10.10.0/23    | 35.10.0.0/18   | 20FF:CCFF:200C:A3::/64   | 20FF:CCFF:200C::/48 | Трым-пым A0   | R2e0/3  R4e0/3  |
| 35.10.12.0/24    | 35.10.0.0/18   | 20FF:CCFF:200C:A4::/64   | 20FF:CCFF:200C::/48 | Трым-пым A0   | R3e0/0  R4e0/0  |
| 35.10.64.0/24    | 35.10.64.0/18  | 20FF:CCFF:200C:B1::/64   | 20FF:CCFF:200C::/48 | Трым-пым A42  | R3e0/1  R8e0/1  |
| 35.10.65.0/25    | 35.10.64.0/18  | 20FF:CCFF:200C:B2::/64   | 20FF:CCFF:200C::/48 | Трым-пым A42  | R3e0/3  R14e0/3 |
| 35.10.65.128/27  | 35.10.64.0/18  | 20FF:CCFF:200C:B3::/64   | 20FF:CCFF:200C::/48 | Трым-пым A42  | R8e0/0  R14e0/0 |
| 35.10.128.0/26   | 35.10.128.0/18 | 20FF:CCFF:200C:C1::/64   | 20FF:CCFF:200C::/48 | Трым-пым A10  | R2e0/0  R24e0/0 |
| 35.10.192.0/24   | 35.10.192.0/18 | 20FF:CCFF:200C:D1::/64   | 20FF:CCFF:200C::/48 | Трым-пым_2 A0 | R22e0/1 R24e0/1 |
| 35.10.193.0/24   | 35.10.192.0/18 | 20FF:CCFF:200C:D2::/64   | 20FF:CCFF:200C::/48 | Трым-пым_2 A0 | R23e0/2 R24e0/2 |
| 35.10.194.0/25   | 35.10.192.0/18 | 20FF:CCFF:200C:D3::/64   | 20FF:CCFF:200C::/48 | Трым-пым_2 A0 | R22e0/0 R23e0/0 |
| 35.11.0.0/24     | 35.11.0.0/22   | 20FF:CCFF:200D:A1::/64   | 20FF:CCFF:200D::/48 | Трям-пам A0   | R13e0/2 R15e0/2 |
| 35.11.1.0/24     | 35.11.0.0/22   | 20FF:CCFF:200D:A2::/64   | 20FF:CCFF:200D::/48 | Трям-пам A0   | R13e0/1 R16e0/1 |
| 35.11.2.0/25     | 35.11.0.0/22   | 20FF:CCFF:200D:A3::/64   | 20FF:CCFF:200D::/48 | Трям-пам A0   | R15e0/0 R16e0/0 |

  Адреса IPv4 будут, где это возможно, в последнем октете иметь цифру, совпадающую с номером маршрутизатора на схеме,
 например, для маршрутизатора **R22** адрес будет иметь вид **35.10.192.__22__**.

  Адреса IPv6 будут, где это возможно, в последнем октете иметь цифру, совпадающую с номером маршрутизатора на схеме,
 например, для маршрутизатора **R22** адрес будет иметь вид **20FF:CCFF:200C:D2::__22__**.

  Link-local адреса IPv6 будут в последнем октете иметь цифру, совпадающую с номером маршрутизатора на схеме,
 например, для маршрутизатора **R22** все link-local адреса будут иметь вид **FE80::__22__**. Link-local адреса
 IPv6 располагаются в подсети `FE80::/10`.


  Служебная информация.

| Network IPv4     | Summary net    | Network IPv6             | Summary net         | Description   |
|-----------------:|:---------------|-------------------------:|:--------------------|:-------------:|
| 10.0.0.0/8       | 10.0.0.0/8     | FC00::/8                 | FC00::/8            | Int serv net  |
|                  |                |                          | 20FF:CCFF::/32      | All IPv6 nets |


###  2. Задокументируем выделенные для маршрутизаторов IP-адреса.


  Общая таблица сетевых адресов на интерфейсах маршрутизаторов.

| Equip | Port | AddrTyp | Address                  | Network                | Description     |
|-------|------|---------|--------------------------|------------------------|-----------------|
| R1    | e0/0 | IPv4    | 172.16.19.2/28           | 172.16.19.0/28         | to ISP (R19)    |
| R1    | e0/0 | IPv6    | 20FF:CCFF:1000:19::2/64  | 20FF:CCFF:1000:19::/64 | to ISP (R19)    |   
| R1    | e0/0 | IPv6 LL | FE80::1                  | FE80::/10              | link-local e0/0 |
| R1    | e0/1 | IPv4    | 35.10.8.1/23             | 35.10.8.0/23           | R1 to R2        |
| R1    | e0/1 | IPv6    | 20FF:CCFF:200C:A2::1/64  | 20FF:CCFF:200C:A2::/64 | R1 to R2        |
| R1    | e0/1 | IPv6 LL | FE80::1                  | FE80::/10              | link-local e0/1 |
| R1    | e0/2 | IPv4    | 35.10.0.1/21             | 35.10.0.0/21           | R1 to R3        |
| R1    | e0/2 | IPv6    | 20FF:CCFF:200C:A1::1/64  | 20FF:CCFF:200C:A1::/64 | R1 to R3        |
| R1    | e0/2 | IPv6 LL | FE80::1                  | FE80::/10              | link-local e0/2 |
| R2    | e0/0 | IPv4    | 35.10.128.2/26           | 35.10.128.0/26         | R2 to R24       |
| R2    | e0/0 | IPv6    | 20FF:CCFF:200C:C1::2/64  | 20FF:CCFF:200C:C1::/64 | R2 to R24       |
| R2    | e0/0 | IPv6 LL | FE80::2                  | FE80::/10              | link-local e0/0 |
| R2    | e0/1 | IPv4    | 35.10.8.2/23             | 35.10.8.0/23           | R2 to R1        |
| R2    | e0/1 | IPv6    | 20FF:CCFF:200C:A2::2/64  | 20FF:CCFF:200C:A2::/64 | R2 to R1        |
| R2    | e0/1 | IPv6 LL | FE80::2                  | FE80::/10              | link-local e0/1 |
| R2    | e0/3 | IPv4    | 35.10.10.2/23            | 35.10.10.0/23          | R2 to R4        |
| R2    | e0/3 | IPv6    | 20FF:CCFF:200C:A3::2/64  | 20FF:CCFF:200C:A3::/64 | R2 to R4        |
| R2    | e0/3 | IPv6 LL | FE80::2                  | FE80::/10              | link-local e0/3 |
| R3    | e0/0 | IPv4    | 35.10.12.3/24            | 35.10.12.0/24          | R3 to R4        |
| R3    | e0/0 | IPv6    | 20FF:CCFF:200C:A4::3/64  | 20FF:CCFF:200C:A4::/64 | R3 to R4        |
| R3    | e0/0 | IPv6 LL | FE80::3                  | FE80::/10              | link-local e0/0 |
| R3    | e0/1 | IPv4    | 35.10.64.3/24            | 35.10.64.0/24          | R3 to R8        |
| R3    | e0/1 | IPv6    | 20FF:CCFF:200C:B1::3/64  | 20FF:CCFF:200C:B1::/64 | R3 to R8        |
| R3    | e0/1 | IPv6 LL | FE80::3                  | FE80::/10              | link-local e0/1 |
| R3    | e0/2 | IPv4    | 35.10.0.3/21             | 35.10.0.0/21           | R3 to R1        |
| R3    | e0/2 | IPv6    | 20FF:CCFF:200C:A1::3/64  | 20FF:CCFF:200C:A1::/64 | R3 to R1        |
| R3    | e0/2 | IPv6 LL | FE80::3                  | FE80::/10              | link-local e0/2 |
| R3    | e0/3 | IPv4    | 35.10.65.3/25            | 35.10.65.0/25          | R3 to R14       |
| R3    | e0/3 | IPv6    | 20FF:CCFF:200C:B2::3/64  | 20FF:CCFF:200C:B2::/64 | R3 to R14       |
| R3    | e0/3 | IPv6 LL | FE80::3                  | FE80::/10              | link-local e0/3 |
| R4    | e0/0 | IPv4    | 35.10.12.4/24            | 35.10.12.0/24          | R4 to R3        |
| R4    | e0/0 | IPv6    | 20FF:CCFF:200C:A4::4/64  | 20FF:CCFF:200C:A4::/64 | R4 to R3        |
| R4    | e0/0 | IPv6 LL | FE80::4                  | FE80::/10              | link-local e0/0 |
| R4    | e0/3 | IPv4    | 35.10.10.4/23            | 35.10.10.0/23          | R4 to R2        |
| R4    | e0/3 | IPv6    | 20FF:CCFF:200C:A3::4/64  | 20FF:CCFF:200C:A3::/64 | R4 to R2        |
| R4    | e0/3 | IPv6 LL | FE80::4                  | FE80::/10              | link-local e0/3 |
| R5    | e0/0 | IPv4    | 172.16.17.2/29           | 172.16.17.0/29         | to ISP (R17)    |
| R5    | e0/0 | IPv6    | 20FF:CCFF:1000:17::2/64  | 20FF:CCFF:1000:17::/64 | to ISP (R17)    |
| R5    | e0/0 | IPv6 LL | FE80::5                  | FE80::/10              | link-local e0/0 |
| R5    | e0/1 | IPv4    | 50.50.105.5/25           | 50.50.105.0/25         | R5 to R6        |
| R5    | e0/1 | IPv6    | 20FF:CCFF:200B:A2::5/64  | 20FF:CCFF:200B:A2::/64 | R5 to R6        |
| R5    | e0/1 | IPv6 LL | FE80::5                  | FE80::/10              | link-local e0/1 |
| R5    | e0/2 | IPv4    | 50.50.104.5/24           | 50.50.104.0/24         | R5 to R7        |
| R5    | e0/2 | IPv6    | 20FF:CCFF:200B:A1::5/64  | 20FF:CCFF:200B:A1::/64 | R5 to R7        |
| R5    | e0/2 | IPv6 LL | FE80::5                  | FE80::/10              | link-local e0/2 |
| R6    | e0/0 | IPv4    | 50.50.105.129/25         | 50.50.105.128/25       | R6 to R7        |
| R6    | e0/0 | IPv6    | 20FF:CCFF:200B:A3::6/64  | 20FF:CCFF:200B:A3::/64 | R6 to R7        |
| R6    | e0/0 | IPv6 LL | FE80::6                  | FE80::/10              | link-local e0/0 |
| R6    | e0/1 | IPv4    | 50.50.105.6/25           | 50.50.105.0/25         | R6 to R5        |
| R6    | e0/1 | IPv6    | 20FF:CCFF:200B:A2::6/64  | 20FF:CCFF:200B:A2::/64 | R6 to R5        |
| R6    | e0/1 | IPv6 LL | FE80::6                  | FE80::/10              | link-local e0/1 |
| R7    | e0/0 | IPv4    | 50.50.105.130/25         | 50.50.105.128/25       | R7 to R6        |
| R7    | e0/0 | IPv6    | 20FF:CCFF:200B:A3::7/64  | 20FF:CCFF:200B:A3::/64 | R7 to R6        |
| R7    | e0/0 | IPv6 LL | FE80::7                  | FE80::/10              | link-local e0/0 |
| R7    | e0/2 | IPv4    | 50.50.104.7/24           | 50.50.104.0/24         | R7 to R5        |
| R7    | e0/2 | IPv6    | 20FF:CCFF:200B:A1::7/64  | 20FF:CCFF:200B:A1::/64 | R7 to R5        |
| R7    | e0/2 | IPv6 LL | FE80::7                  | FE80::/10              | link-local e0/2 |
| R8    | e0/0 | IPv4    | 35.10.65.129/27          | 35.10.65.128/27        | R8 to R14       |
| R8    | e0/0 | IPv6    | 20FF:CCFF:200C:B3::8/64  | 20FF:CCFF:200C:B3::/64 | R8 to R14       |
| R8    | e0/0 | IPv6 LL | FE80::8                  | FE80::/10              | link-local e0/0 |
| R8    | e0/1 | IPv4    | 35.10.64.8/24            | 35.10.64.0/24          | R8 to R3        |
| R8    | e0/1 | IPv6    | 20FF:CCFF:200C:B1::8/64  | 20FF:CCFF:200C:B1::/64 | R8 to R3        |
| R8    | e0/1 | IPv6 LL | FE80::8                  | FE80::/10              | link-local e0/1 |
| R9    | e0/0 | IPv4    | 172.16.18.2/29           | 172.16.18.0/29         | to ISP (R18)    |
| R9    | e0/0 | IPv6    | 20FF:CCFF:1000:18::2/64  | 20FF:CCFF:1000:18::/64 | to ISP (R18)    |
| R9    | e0/0 | IPv6 LL | FE80::9                  | FE80::/10              | link-local e0/0 |
| R9    | e0/1 | IPv4    | 50.50.96.9/23            | 50.50.96.0/23          | R9 to R12       |
| R9    | e0/1 | IPv6    | 20FF:CCFF:200A:A1::9/64  | 20FF:CCFF:200A:A1::/64 | R9 to R12       |
| R9    | e0/1 | IPv6 LL | FE80::9                  | FE80::/10              | link-local e0/1 |
| R9    | e0/2 | IPv4    | 50.50.100.9/24           | 50.50.100.0/24         | R9 to R10       |
| R9    | e0/2 | IPv6    | 20FF:CCFF:200A:A3::9/64  | 20FF:CCFF:200A:A3::/64 | R9 to R10       |
| R9    | e0/2 | IPv6 LL | FE80::9                  | FE80::/10              | link-local e0/2 |
| R9    | e0/3 | IPv4    | 50.50.102.9/29           | 50.50.102.8/29         | R9 to R11       |
| R9    | e0/3 | IPv6    | 20FF:CCFF:200A:A5::9/64  | 20FF:CCFF:200A:A5::/64 | R9 to R11       |
| R9    | e0/3 | IPv6 LL | FE80::9                  | FE80::/10              | link-local e0/3 |
| R10   | e0/1 | IPv4    | 50.50.101.10/24          | 50.50.101.0/24         | R10 to R11      |
| R10   | e0/1 | IPv6    | 20FF:CCFF:200A:A4::10/64 | 20FF:CCFF:200A:A4::/64 | R10 to R11      |
| R10   | e0/1 | IPv6 LL | FE80::10                 | FE80::/10              | link-local e0/1 |
| R10   | e0/2 | IPv4    | 50.50.100.10/24          | 50.50.100.0/24         | R10 to R9       |
| R10   | e0/2 | IPv6    | 20FF:CCFF:200A:A3::10/64 | 20FF:CCFF:200A:A3::/64 | R10 to R9       |
| R10   | e0/2 | IPv6 LL | FE80::10                 | FE80::/10              | link-local e0/2 |
| R11   | e0/0 | IPv4    | 50.50.98.11/23           | 50.50.98.0/23          | R11 to R12      |
| R11   | e0/0 | IPv6    | 20FF:CCFF:200A:A2::11/64 | 20FF:CCFF:200A:A2::/64 | R11 to R12      |
| R11   | e0/0 | IPv6 LL | FE80::11                 | FE80::/10              | link-local e0/0 |
| R11   | e0/1 | IPv4    | 50.50.101.11/24          | 50.50.101.0/24         | R11 to R10      |
| R11   | e0/1 | IPv6    | 20FF:CCFF:200A:A4::11/64 | 20FF:CCFF:200A:A4::/64 | R11 to R10      |
| R11   | e0/1 | IPv6 LL | FE80::11                 | FE80::/10              | link-local e0/1 |
| R11   | e0/3 | IPv4    | 50.50.102.11/29          | 50.50.102.8/29         | R11 to R9       |
| R11   | e0/3 | IPv6    | 20FF:CCFF:200A:A5::11/64 | 20FF:CCFF:200A:A5::/64 | R11 to R9       |
| R11   | e0/3 | IPv6 LL | FE80::11                 | FE80::/10              | link-local e0/3 |
| R12   | e0/0 | IPv4    | 50.50.98.12/23           | 50.50.98.0/23          | R12 to R11      |
| R12   | e0/0 | IPv6    | 20FF:CCFF:200A:A2::12/64 | 20FF:CCFF:200A:A2::/64 | R12 to R11      |
| R12   | e0/0 | IPv6 LL | FE80::12                 | FE80::/10              | link-local e0/0 |
| R12   | e0/1 | IPv4    | 50.50.96.12/23           | 50.50.96.0/23          | R12 to R9       |
| R12   | e0/1 | IPv6    | 20FF:CCFF:200A:A1::12/64 | 20FF:CCFF:200A:A1::/64 | R12 to R9       |
| R12   | e0/1 | IPv6 LL | FE80::12                 | FE80::/10              | link-local e0/1 |
| R13   | e0/0 | IPv4    | 172.16.20.2/29           | 172.16.20.0/29         | to ISP (R20)    |
| R13   | e0/0 | IPv6    | 20FF:CCFF:1000:20::2/64  | 20FF:CCFF:1000:20::/64 | to ISP (R20)    |
| R13   | e0/0 | IPv6 LL | FE80::13                 | FE80::/10              | link-local e0/0 |
| R13   | e0/1 | IPv4    | 35.11.1.13/24            | 35.11.1.0/24           | R13 to R16      |
| R13   | e0/1 | IPv6    | 20FF:CCFF:200D:A2::13/64 | 20FF:CCFF:200D:A2::/64 | R13 to R16      |
| R13   | e0/1 | IPv6 LL | FE80::13                 | FE80::/10              | link-local e0/1 |
| R13   | e0/2 | IPv4    | 35.11.0.13/24            | 35.11.0.0/24           | R13 to R15      |
| R13   | e0/2 | IPv6    | 20FF:CCFF:200D:A1::13/64 | 20FF:CCFF:200D:A1::/64 | R13 to R15      |
| R13   | e0/2 | IPv6 LL | FE80::13                 | FE80::/10              | link-local e0/2 |
| R14   | e0/0 | IPv4    | 35.10.65.130/27          | 35.10.65.128/27        | R14 to R8       |
| R14   | e0/0 | IPv6    | 20FF:CCFF:200C:B3::14/64 | 20FF:CCFF:200C:B3::/64 | R14 to R8       |
| R14   | e0/0 | IPv6 LL | FE80::14                 | FE80::/10              | link-local e0/0 |
| R14   | e0/3 | IPv4    | 35.10.65.14/25           | 35.10.65.0/25          | R14 to R3       |
| R14   | e0/3 | IPv6    | 20FF:CCFF:200C:B2::14/64 | 20FF:CCFF:200C:B2::/64 | R14 to R3       |
| R14   | e0/3 | IPv6 LL | FE80::14                 | FE80::/10              | link-local e0/3 |
| R15   | e0/0 | IPv4    | 35.11.2.15/25            | 35.11.2.0/25           | R15 to R16      |
| R15   | e0/0 | IPv6    | 20FF:CCFF:200D:A3::15/64 | 20FF:CCFF:200D:A3::/64 | R15 to R16      |
| R15   | e0/0 | IPv6 LL | FE80::15                 | FE80::/10              | link-local e0/0 |
| R15   | e0/2 | IPv4    | 35.11.0.15/24            | 35.11.0.0/24           | R15 to R13      |
| R15   | e0/2 | IPv6    | 20FF:CCFF:200D:A1::15/64 | 20FF:CCFF:200D:A1::/64 | R15 to R13      |
| R15   | e0/2 | IPv6 LL | FE80::15                 | FE80::/10              | link-local e0/2 |
| R16   | e0/0 | IPv4    | 35.11.2.16/25            | 35.11.2.0/25           | R16 to R15      |
| R16   | e0/0 | IPv6    | 20FF:CCFF:200D:A3::16/64 | 20FF:CCFF:200D:A3::/64 | R16 to R15      |
| R16   | e0/0 | IPv6 LL | FE80::16                 | FE80::/10              | link-local e0/0 |
| R16   | e0/1 | IPv4    | 35.11.1.16/24            | 35.11.1.0/24           | R16 to R13      |
| R16   | e0/1 | IPv6    | 20FF:CCFF:200D:A2::16/64 | 20FF:CCFF:200D:A2::/64 | R16 to R13      |
| R16   | e0/1 | IPv6 LL | FE80::16                 | FE80::/10              | link-local e0/1 |
| R17   | e0/0 | IPv4    | 172.16.17.1/29           | 172.16.17.0/29         | to client (R5)  |
| R17   | e0/0 | IPv6    | 20FF:CCFF:1000:17::1/64  | 20FF:CCFF:1000:17::/64 | to client (R5)  |
| R17   | e0/0 | IPv6 LL | FE80::17                 | FE80::/10              | link-local e0/0 |
| R17   | e0/1 | IPv4    | 90.90.129.17/24          | 90.90.129.0/24         | R17 to R18      |
| R17   | e0/1 | IPv6    | 20FF:CCFF:FFFF:2::17/64  | 20FF:CCFF:FFFF:2::/64  | R17 to R18      |
| R17   | e0/1 | IPv6 LL | FE80::17                 | FE80::/10              | link-local e0/2 |
| R17   | e0/2 | IPv4    | 90.90.128.17/24          | 90.90.128.0/24         | R17 to R19      |
| R17   | e0/2 | IPv6    | 20FF:CCFF:FFFF:1::17/64  | 20FF:CCFF:FFFF:1::/64  | R17 to R19      |
| R17   | e0/2 | IPv6 LL | FE80::17                 | FE80::/10              | link-local e0/1 |
| R17   | e0/3 | IPv4    | 90.90.131.17/25          | 90.90.131.0/25         | R17 to R20      |
| R17   | e0/3 | IPv6    | 20FF:CCFF:FFFF:5::17/64  | 20FF:CCFF:FFFF:5::/64  | R17 to R20      |
| R17   | e0/3 | IPv6 LL | FE80::17                 | FE80::/10              | link-local e0/3 |
| R18   | e0/0 | IPv4    | 172.16.18.1/29           | 172.16.18.0/29         | to client (R9)  |
| R18   | e0/0 | IPv6    | 20FF:CCFF:1000:18::1/64  | 20FF:CCFF:1000:18::/64 | to client (R9)  |
| R18   | e0/0 | IPv6 LL | FE80::18                 | FE80::/10              | link-local e0/0 |
| R18   | e0/1 | IPv4    | 90.90.129.18/24          | 90.90.129.0/24         | R18 to R17      |
| R18   | e0/1 | IPv6    | 20FF:CCFF:FFFF:2::18/64  | 20FF:CCFF:FFFF:2::/64  | R18 to R17      |
| R18   | e0/1 | IPv6 LL | FE80::18                 | FE80::/10              | link-local e0/1 |
| R18   | e0/2 | IPv4    | 90.90.130.18/25          | 90.90.130.0/25         | R18 to R20      |
| R18   | e0/2 | IPv6    | 20FF:CCFF:FFFF:3::18/64  | 20FF:CCFF:FFFF:3::/64  | R18 to R20      |
| R18   | e0/2 | IPv6 LL | FE80::18                 | FE80::/10              | link-local e0/2 |
| R18   | e0/3 | IPv4    | 90.90.131.129/25         | 90.90.131.128/25       | R18 to R19      |
| R18   | e0/3 | IPv6    | 20FF:CCFF:FFFF:6::18/64  | 20FF:CCFF:FFFF:6::/64  | R18 to R19      |
| R18   | e0/3 | IPv6 LL | FE80::18                 | FE80::/10              | link-local e0/3 |
| R19   | e0/0 | IPv4    | 172.16.19.1/28           | 172.16.19.0/28         | to client (R1)  |
| R19   | e0/0 | IPv6    | 20FF:CCFF:1000:19::1/64  | 20FF:CCFF:1000:19::/64 | to client (R1)  |
| R19   | e0/0 | IPv6 LL | FE80::19                 | FE80::/10              | link-local e0/0 |
| R19   | e0/1 | IPv4    | 90.90.130.129/25         | 90.90.130.128/25       | R19 to R20      |
| R19   | e0/1 | IPv6    | 20FF:CCFF:FFFF:4::19/64  | 20FF:CCFF:FFFF:4::/64  | R19 to R20      |
| R19   | e0/1 | IPv6 LL | FE80::19                 | FE80::/10              | link-local e0/2 |
| R19   | e0/2 | IPv4    | 90.90.128.19/24          | 90.90.128.0/24         | R19 to R17      |
| R19   | e0/2 | IPv6    | 20FF:CCFF:FFFF:1::19/64  | 20FF:CCFF:FFFF:1::/64  | R19 to R17      |
| R19   | e0/2 | IPv6 LL | FE80::19                 | FE80::/10              | link-local e0/1 |
| R19   | e0/3 | IPv4    | 90.90.131.130/25         | 90.90.131.128/25       | R19 to R18      |
| R19   | e0/3 | IPv6    | 20FF:CCFF:FFFF:6::19/64  | 20FF:CCFF:FFFF:6::/64  | R19 to R18      |
| R19   | e0/3 | IPv6 LL | FE80::19                 | FE80::/10              | link-local e0/3 |
| R20   | e0/0 | IPv4    | 172.16.20.1/29           | 172.16.20.0/29         | to client (R13) |
| R20   | e0/0 | IPv6    | 20FF:CCFF:1000:20::1/64  | 20FF:CCFF:1000:20::/64 | to client (R13) |
| R20   | e0/0 | IPv6 LL | FE80::20                 | FE80::/10              | link-local e0/0 |
| R20   | e0/1 | IPv4    | 90.90.130.130/25         | 90.90.130.128/25       | R20 to R19      |
| R20   | e0/1 | IPv6    | 20FF:CCFF:FFFF:4::20/64  | 20FF:CCFF:FFFF:4::/64  | R20 to R19      |
| R20   | e0/1 | IPv6 LL | FE80::20                 | FE80::/10              | link-local e0/1 |
| R20   | e0/2 | IPv4    | 90.90.130.20/25          | 90.90.130.0/25         | R20 to R18      |
| R20   | e0/2 | IPv6    | 20FF:CCFF:FFFF:3::20/64  | 20FF:CCFF:FFFF:3::/64  | R20 to R18      |
| R20   | e0/2 | IPv6 LL | FE80::20                 | FE80::/10              | link-local e0/2 |
| R20   | e0/3 | IPv4    | 90.90.131.20/25          | 90.90.131.0/25         | R20 to R17      |
| R20   | e0/3 | IPv6    | 20FF:CCFF:FFFF:5::20/64  | 20FF:CCFF:FFFF:5::/64  | R20 to R17      |
| R20   | e0/3 | IPv6 LL | FE80::20                 | FE80::/10              | link-local e0/3 |
| R22   | e0/0 | IPv4    | 35.10.194.22/25          | 35.10.194.0/25         | R22 to R23      |
| R22   | e0/0 | IPv6    | 20FF:CCFF:200C:D3::22/64 | 20FF:CCFF:200C:D3::/64 | R22 to R23      |
| R22   | e0/0 | IPv6 LL | FE80::22                 | FE80::/10              | link-local e0/0 |
| R22   | e0/1 | IPv4    | 35.10.192.22/24          | 35.10.192.0/24         | R22 to R24      |
| R22   | e0/1 | IPv6    | 20FF:CCFF:200C:D2::22/64 | 20FF:CCFF:200C:D2::/64 | R22 to R24      |
| R22   | e0/1 | IPv6 LL | FE80::22                 | FE80::/10              | link-local e0/1 |
| R23   | e0/0 | IPv4    | 35.10.194.23/25          | 35.10.194.0/25         | R23 to R22      |
| R23   | e0/0 | IPv6    | 20FF:CCFF:200C:D3::23/64 | 20FF:CCFF:200C:D3::/64 | R23 to R22      |
| R23   | e0/0 | IPv6 LL | FE80::23                 | FE80::/10              | link-local e0/0 |
| R23   | e0/2 | IPv4    | 35.10.193.23/24          | 35.10.193.0/24         | R23 to R24      |
| R23   | e0/2 | IPv6    | 20FF:CCFF:200C:D1::23/64 | 20FF:CCFF:200C:D1::/64 | R23 to R24      |
| R23   | e0/2 | IPv6 LL | FE80::23                 | FE80::/10              | link-local e0/2 |
| R24   | e0/0 | IPv4    | 35.10.128.24/26          | 35.10.128.0/26         | R24 to R2       |
| R24   | e0/0 | IPv6    | 20FF:CCFF:200C:C1::24/64 | 20FF:CCFF:200C:C1::/64 | R24 to R2       |
| R24   | e0/0 | IPv6 LL | FE80::24                 | FE80::/10              | link-local e0/0 |
| R24   | e0/1 | IPv4    | 35.10.192.24/24          | 35.10.192.0/24         | R24 to R23      |
| R24   | e0/1 | IPv6    | 20FF:CCFF:200C:D1::24/64 | 20FF:CCFF:200C:D1::/64 | R24 to R23      |
| R24   | e0/1 | IPv6 LL | FE80::24                 | FE80::/10              | link-local e0/1 |
| R24   | e0/2 | IPv4    | 35.10.193.24/24          | 35.10.193.0/24         | R24 to R22      |
| R24   | e0/2 | IPv6    | 20FF:CCFF:200C:D2::24/64 | 20FF:CCFF:200C:D2::/64 | R24 to R22      |
| R24   | e0/2 | IPv6 LL | FE80::24                 | FE80::/10              | link-local e0/2 |



###  3. Настроим IP-адреса с учетом приведённой выше схемы и задокументируем изменения.

  Изменения на маршрутизаторах сводятся к:
  1. Включению ipv6 unicast-routing (ipv4 unicast-routing по-умолчанию включен);
  2. Включению ipv6 на интерфейсах (ipv4 по-умолчанию включен);
  2. Назначению адресов ipv4 и ipv6 на интерфейсах;
  3. Включению самих интерфейсов (физические интерфейсы по-умолчанию выключены).

###  Пример настройки на маршрутизаторе R1:

```
conf t
 ipv6 unicast-routing
!
 interface Ethernet0/0
  description "to Internet (R19)"
  ip address 172.16.19.2 255.255.255.240
  ipv6 address FE80::1 link-local
  ipv6 address 20FF:CCFF:1000:19::2/64
  ipv6 enable
  no shutdown
  exit
!
 interface Ethernet0/1
  description "R1 to R2"
  ip address 35.10.8.1 255.255.254.0
  ipv6 address FE80::1 link-local
  ipv6 address 20FF:CCFF:200C:A2::1/64
  ipv6 enable
  no shutdown
  exit
!
 interface Ethernet0/2
  description "R1 to R3"
  ip address 35.10.0.1 255.255.248.0
  ipv6 address FE80::1 link-local
  ipv6 address 20FF:CCFF:200C:A1::1/64
  ipv6 enable
  no shutdown
  exit
!
 interface Ethernet0/3
  description "not used"
  no ip address
  shutdown
  exit
 exit
```

Все файлы изменений приведены [здесь](configs/).


###  Итоговая графическая схема:

![](ip-addresses.png)
