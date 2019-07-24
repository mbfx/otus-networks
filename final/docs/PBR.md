### Маршрутизация на основе политик (PBR)

| Eq  | Policy | Next-hop |
|-----|--------|----------|
| PF-R1 | Traffic IPv4 from ZL-R1 to OV-R1 send to PC-R1 | 99.99.134.2 |
| PF-R1 | Traffic IPv6 from ZL-R1 to OV-R1 send to PC-R1 | 20FF:CCFE:FFFF:2::2 |
| PF-R1 | Traffic IPv4 from ZL-R1 to LP-R1 send to PC-R1 | 99.99.134.2 |
| PF-R1 | Traffic IPv6 from ZL-R1 to LP-R1 send to PC-R1 | 20FF:CCFE:FFFF:2::2 |
| PF-R2 | Traffic IPv4 from OV-R1 to ZL-R1 send to PC-R1 | 99.99.128.1 |
| PF-R2 | Traffic IPv6 from OV-R1 to ZL-R1 send to PC-R1 | 20FF:CCFD:FFFF:1::1 | 

  [PBR на PF-R1](../configs/PF-R1#L91-L116)
  [PBR на PF-R2](../configs/PF-R2#L91-L114)

### Графические схемы PBR

#### PF-R1

![](../pics/pbr_PF-R1.png)

#### PF-R2

![](../pics/pbr_PF-R2.png)
