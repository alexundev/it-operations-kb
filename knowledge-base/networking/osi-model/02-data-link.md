# Camada 2 — Enlace

## Conceito

A Camada de Enlace é responsável pela comunicação através do enlace local.

Entre suas funções estão o uso de quadros, o endereçamento MAC e o controle de acesso ao meio.

Em tecnologias IEEE 802, a Camada 2 pode ser representada pelas subcamadas **MAC** e **LLC**.

## Funcionamento

### MAC

A subcamada MAC está relacionada ao controle de acesso ao meio e ao endereçamento através de endereços MAC.

#### CSMA/CD

O **CSMA/CD (Carrier Sense Multiple Access with Collision Detection)** foi utilizado em redes Ethernet compartilhadas operando em half-duplex.

Quando uma colisão é detectada, a transmissão é interrompida e uma nova tentativa é realizada após um intervalo aleatório.

Em redes Ethernet modernas utilizando switches e full-duplex, colisões não fazem parte da operação normal do enlace.

#### CSMA/CA

O **CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)** é utilizado principalmente em redes Wi-Fi.

Seu objetivo é reduzir a ocorrência de colisões entre dispositivos que compartilham o meio, verificando a utilização do canal antes de realizar a transmissão.

### LLC

A subcamada LLC participa da interface lógica entre a Camada de Enlace e os protocolos utilizados pelas camadas superiores, incluindo os protocolos da Camada 3 — Rede.

## Visão de Troubleshooting

### Ethernet

Problemas relacionados à Camada 2 podem envolver situações como configuração inadequada de duplex ou erros na comunicação através do enlace.

### Wi-Fi

Como vários dispositivos podem compartilhar o mesmo meio de transmissão, uma quantidade maior de dispositivos utilizando a rede pode contribuir para aumento de latência e redução de desempenho.

Uma forma simples de investigação é observar se o comportamento melhora quando há menos dispositivos utilizando o meio.

## Laboratórios Relacionados

- [Análise de quadro Ethernet com tcpdump](../../../labs/networking/01-tcpdump-ethernet-frame.md)
