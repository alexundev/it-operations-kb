# Laboratório Prático: Rastreamento de Portas e Sockets (Camada 4)

**Objetivo:** Rastrear conexões ativas e portas em estado de escuta na máquina virtual Linux utilizando a ferramenta de estatísticas de socket (`ss`).

## 1. Comandos Executados

  `sudo ss -tpan`

## 2. Análise de Troubleshooting (Camada 4)

**Linha capturada da análise do servidor:**
`LISTEN   0    128    0.0.0.0:80    0.0.0.0:*    users:(("nginx",pid=1043,fd=6))`

**Decodificação técnica dos parâmetros:**

1) **Qual é o Socket Local (IP + Porta)?**
   - **Socket:** `0.0.0.0:80`
   - *Nota:* A junção do IP `0.0.0.0` com a porta `80` indica que o servidor está aceitando requisições web (HTTP) de qualquer interface de rede IPv4.

2) **Qual é o Daemon em execução?**
   - **Daemon:** `nginx`
   - *Nota:* O serviço de servidor web Nginx é o dono desse processo.

3) **Qual é a Situação atual (State)?**
   - **Estado:** `LISTEN`
   - *Nota:* O processo não está em comunicação ativa no momento (ESTABLISHED), mas sim no estado de "escuta", aguardando ativamente que clientes (navegadores) iniciem a conexão.

> *Nota: Definição do código:*
ss  Estatísticas de Sockets
-t → Mostra apenas conexões TCP
-p → Montra o nome do Deamon que está utilizando a porta
-a → Mostra quem está escutando e quem já está conectado
-n → Mostra tudo em números