# Атрибуты выбора пути в BGP

###  Задание:

  1. Настроить маршрутизатор R18 так, чтобы у всех маршрутов полученных от R20 атрибут local-preference был установлен в 100;
  2. Настроить маршрутизатор R18 так, чтобы у всех маршрутов полученных от R19 атрибут local-preference был установлен в 160;
  3. Настроить маршрутизатор R18 так, чтобы у всех маршрутов полученных от R17 атрибут local-preference был установлен в 200;
  4. На R1 настроить значение MED в 1500 для анонсирования соседям внутри iBGP (для соседей R2 и R3);
  5. Настроить маршрутизатор R17 так, чтобы у всех маршрутов полученных от R20 атрибут weight был установлен в 40;
  6. Настроить маршрутизатор R17 так, чтобы у префикса, полученного от R19 о сети до офиса Трым-Пым атрибут weight был установлен в 60;
  7. Настроить на R20 атрибут weight так, чтобы у всех маршрутов полученных от R17 атрибут weight был установлен в 40;
  8. Задокументировать все изменения.



###  Решение:

  Оборудование, правила и использованные средства.

| Eq   | Rule | Tools |
|------|------|-------|
| R18  | all prefixes from R20 - set local-preference 100 | as-path access-list 20, as-path access-list 500, route-map RM_BGP_R20_IN |
| R18  | all prefixes from R19 - set local-preference 160 | as-path access-list 19, as-path access-list 500, route-map RM_BGP_R19_IN |
| R18  | all prefixes from R20 - set local-preference 120 | as-path access-list 17, as-path access-list 500, route-map RM_BGP_R17_IN |
| R1   | all prefixes to R2 (iBGP) - set metric 1500 (MED) | as-path access-list 500, route-map RM_iBGP_R3_OUT |
| R1   | all prefixes to R3 (iBGP) - set metric 1500 (MED) | as-path access-list 500, route-map RM_iBGP_R3_OUT |
| R17  | all prefixes from R17 - set weight 40 | as-path access-list 20, as-path access-list 500, route-map RM_BGP_R20_IN |
| R17  | prefix 35.10.0.0/18 from R19 - set weight 60 | prefix-list PRLIST_BGP_65219_IN, prefix-list PRLIST_PERMIT_ALL, route-map RM_BGP_R19_IN |
| R17  | prefix 35.10.64.0/18 from R19 - set weight 60 | prefix-list PRLIST_BGP_65219_IN, prefix-list PRLIST_PERMIT_ALL, route-map RM_BGP_R19_IN |
| R17  | prefix 35.10.128.0/18 from R19 - set weight 60 | prefix-list PRLIST_BGP_65219_IN, prefix-list PRLIST_PERMIT_ALL, route-map RM_BGP_R19_IN |
| R17  | prefix 20FF:CCFF:FFFF:1::19 from R19 - set weight 60 | prefix-list PRLISTV6_BGP_65219_IN, prefix-list PRLISTV6_PERMIT_ALL, route-map RM_BGP_R19_IN_V6 |
| R20  | all prefixes from R17 - set weight 40 | as-path access-list 17, as-path access-list 500, route-map RM_BGP_R17_IN |

  Все файлы изменений приведены [здесь](configs/).

  Для манипуляций с префиксами используем route-map. В зависимости от того, к каким группам мы хотим применить route-map, можно использовать ip as-path access-list, ip prefix-list и иные инструменты.
