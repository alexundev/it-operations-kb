# Análise de Portas e Sockets TCP com ss

## Objetivo

Analisar sockets TCP e portas em estado de escuta em uma máquina virtual Linux utilizando a ferramenta `ss`.

O laboratório tem como objetivo relacionar os conceitos da Camada de Transporte com a identificação de portas, sockets, estados de conexão e processos associados.

---

## Ambiente

- Sistema operacional: Linux
- Ambiente virtualizado: UTM
- Ferramenta utilizada: `ss`

---

## Comando Utilizado

```bash
sudo ss -tpan
```

Parâmetros utilizados:

- `-t`: exibe sockets TCP;
- `-p`: exibe o processo associado ao socket, quando disponível;
- `-a`: exibe sockets em diferentes estados, incluindo sockets em escuta;
- `-n`: exibe endereços e portas numericamente, sem resolução de nomes.

---

## Análise

Durante a execução do comando, foi identificada a seguinte entrada:

```text
LISTEN   0   128   0.0.0.0:80   0.0.0.0:*   users:(("nginx",pid=1043,fd=6))
```

### Socket Local

```text
0.0.0.0:80
```

O endereço `0.0.0.0` indica que o socket está associado às interfaces IPv4 disponíveis no sistema.

A porta `80` corresponde à porta convencionalmente utilizada pelo protocolo HTTP.

---

### Processo Associado

```text
nginx
```

O processo `nginx` é o responsável pelo socket identificado.

---

### Estado do Socket

```text
LISTEN
```

O estado `LISTEN` indica que esse socket está aguardando novas conexões TCP de entrada.

Esse estado é diferente de `ESTABLISHED`, utilizado para representar uma conexão TCP já estabelecida entre dois endpoints.

---

## Resultado

A análise permitiu identificar:

- o protocolo de transporte utilizado;
- o endereço e a porta local;
- o estado do socket;
- o processo associado ao socket;

A utilização do `ss` possibilitou relacionar portas TCP e processos em execução diretamente com o estado dos sockets do sistema.

---

## Conclusão

O laboratório demonstrou como o `ss` pode ser utilizado para verificar quais serviços estão disponíveis para receber conexões em um sistema Linux.

A identificação do endereço local, porta, estado e processo associado fornece informações importantes para análise de conectividade e troubleshooting de serviços de rede.
