# Laboratório Prático: Captura e Decodificação de Quadro (Camada 2)

## Comandos Executados

- Descobrir o endereço MAC de origem da interface local:
  `ip link`
- Capturar 10 pacotes e exibi-los em formato hexadecimal (`-XX`):
  `sudo tcpdump -i xxx0 -XX -c 10`

> **Nota de Segurança:** O endereço MAC de origem real e informações específicas da rede local foram anonimizados neste documento para proteção da infraestrutura.

## **Objetivo:**

- **Descobrir qual é o nome da sua interface de rede e anotar o endereço MAC físico da sua própria máquina:**
  - Endereço Físico: XX:XX:XX:XX:XX:XX
  - Nome da interface: xxx0

**Com o nome da interface em mãos, execute o comando para capturar o tráfego bruto:**

                `sudo tcpdump -i <sua_interface> -XX -c 10`

**Escolher um dos blocos gerados e responder as seguintes questões:**

- Bloco escolhido: `AABB CCDD EEFF 0011 2233 4455 6677 8899` *(Dado anonimizado)*

1) Qual é o MAC de Destino nesse pacote?
    O MAC de destino é o: `AA:BB:CC:DD:EE:FF`*(Dado anonimizado)*

2) Qual é o MAC de Origem nesse pacote?
O MAC de Origem é o: `00:11:22:33:44:55`*(Dado anonimizado)*

3) Qual é o EtherType?
O EtherType: `66:77`*(Dado anonimizado)*
