### CAS (Certificate Authority Server)

  DP-R1 - Certificate Authority Server. К нему могут подключиться только некоторые маршрутизаторы, которые получают от него сертификаты, а конкретно ZL-R1, OV-R1, LP-R1 и сам DP-R1.
  Впоследствии эти сертификаты будут использоваться для аутентификации при использовании протоколов IPsec.

  [CA на DP-R1](../configs/DP-R1#L401-L449)
  [CA client на ZL-R1](../configs/ZL-R1#L352-L366)

### IPsec (Internet Protocol Security)

  Организована защита данных, которые передаются по каналам GRE между ZL-R1 и DP-R1, а также по каналам DMVPN между ZL-R1, OV-R1 и LP-R1. Защита использует протокол ISAKMP с аутентификацией по сертификату и протокол ESP для захиты данных.

  [IPsec на DP-R1](../configs/DP-R1#L451-L469)
  [IPsec на ZL-R1](../configs/ZL-R1#L368-L396)

####  Схема иерархии CA 

![](../pics/ca.png)