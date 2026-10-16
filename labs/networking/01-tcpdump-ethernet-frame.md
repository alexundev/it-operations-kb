# Análise de Quadro Ethernet com tcpdump

## Objetivo

Capturar tráfego de rede em uma interface Linux e analisar diretamente o cabeçalho de um quadro Ethernet, identificando os campos de **MAC de destino**, **MAC de origem** e **EtherType**.

O laboratório tem como objetivo relacionar os conceitos da Camada 2 do Modelo OSI com dados observados em tráfego real.

---

## Ambiente

- Sistema operacional: Linux
- Ferramenta de captura: `tcpdump`
- Interface de rede: anonimizada
- Ambiente virtualizado: UTM

> **Nota de segurança:** endereços MAC e informações específicas da rede local foram anonimizados neste documento.

---

## Identificação da Interface

Para identificar as interfaces disponíveis e seus respectivos endereços MAC:

```bash
ip link
```

Interface utilizada:

```text
xxx0
```

Endereço MAC:

```text
XX:XX:XX:XX:XX:XX
```

---

## Captura do Tráfego

Foi utilizado o `tcpdump` para capturar 10 unidades de tráfego da interface selecionada e exibir seu conteúdo em formato hexadecimal e ASCII.

```bash
sudo tcpdump -i xxx0 -XX -c 10
```

Parâmetros utilizados:

- `-i xxx0`: define a interface monitorada;
- `-XX`: exibe o conteúdo do quadro em formato hexadecimal e ASCII, incluindo o cabeçalho da camada de enlace;
- `-c 10`: encerra a captura após 10 ocorrências.

---

## Análise do Quadro

Um dos cabeçalhos capturados foi selecionado para análise.

Trecho anonimizado:

```text
AABB CCDD EEFF 0011 2233 4455 6677 8899
```

Considerando a estrutura de um cabeçalho Ethernet:

```text
| MAC Destino | MAC Origem | EtherType | Dados... |
|   6 bytes   |  6 bytes   |  2 bytes  |          |
```

### MAC de Destino

Os primeiros 6 bytes correspondem ao endereço MAC de destino:

```text
AA:BB:CC:DD:EE:FF
```

### MAC de Origem

Os 6 bytes seguintes correspondem ao endereço MAC de origem:

```text
00:11:22:33:44:55
```

### EtherType

Os 2 bytes seguintes representam o campo EtherType:

```text
0x6677
```

O valor apresentado neste documento foi anonimizado juntamente com os demais dados da captura.

---

## Resultado

A análise permitiu identificar diretamente no tráfego capturado a estrutura básica de um quadro Ethernet:

1. endereço MAC de destino;
2. endereço MAC de origem;
3. campo EtherType;
4. início dos dados transportados pelo quadro.

A captura demonstrou na prática como as informações estudadas na Camada 2 podem ser observadas diretamente no tráfego de uma interface de rede.

---

## Conclusão

O laboratório permitiu relacionar a estrutura teórica de um quadro Ethernet com uma captura real realizada em Linux.

A utilização do `tcpdump` com exibição hexadecimal tornou possível identificar os campos do cabeçalho diretamente a partir de seus bytes, reforçando a compreensão sobre endereçamento MAC e encapsulamento na Camada de Enlace.