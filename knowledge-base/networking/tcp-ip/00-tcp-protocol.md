# Protocolo TCP

## Conceito

O Protocolo TCP é um dos principais Protocolos do TCP/IP. Ele é um Protocolo que tem como principais características:

- Orientado à conexão;
- Ponto a ponto;
- Confiabilidade;
- Full Duplex;
- Handshake;
- Entrega Ordenada;
- Controle de Fluxo.

## Funcionamento

### Arquitetura Client/Server

A Arquitetura Cliente/Servidor funciona de forma que o Cliente se conecta ao Servidor para enviar dados (segmentos). Assim, a conexão TCP é estabelecida. E após a conexão, tanto o servidor quanto o cliente podem realizar o envio de dados.

### Conexão

A Conexão TCP tem um cabeçalho com 6 campos de 1 bit, que são as flags relacionada aos dados, são elas:

- URG;
- ACK;
- PSH;
- RST;
- SYN;
- FIN.

Cada uma delas tem uma finalidade, sendo as principais: ACK e SYN, que significam "Acknowledge" e "Synchronization", respectivamente. É através dessas flags que a conexão entre Cliente/Servidor é feita.
O cliente manda uma requisição através da flag SYN, o servidor responde com ACK + SYN e o cliente finaliza com ACK (3-way handshake).

### Confirmação de Recebimento

O número de confirmação é um campo do cabeçalho TCP que indica o próximo byte que o receptor espera receber. Já o número de sequência identifica a posição dos bytes enviados.

### Retransmissão de Segmentos

O TCP possui um mecanismo para auxiliar caso algum segmento não seja recebido. Esse mecanismo retransmite os dados que não foram confirmados, buscando manter a entrega confiável. Ele identifica a necessidade de retransmissão através dos números de sequência, números de confirmação e temporizadores.

### Controle de Congestionamento

O Controle de Congestionamento ajusta a quantidade de dados que podem ser enviados sem confirmação, considerando as condições da rede, para reduzir o risco de congestionamento.

Já o campo Window Size do cabeçalho TCP está relacionado ao controle de fluxo, indicando a quantidade de dados que o receptor pode receber.

O Slow Start inicia com uma janela de congestionamento pequena, aumentando a quantidade de dados em trânsito conforme recebe confirmações (ACKs).

### Reagrupamento

O Regrupamento por sua vez serve para garantir que os segmentos ou dados, cheguem de forma ordenada.

Os segmentos podem não seguir um caminho único. Cada um pode tomar uma rota diferente, e dependendo da largura de banda ou velocidade, a forma que os segmentos/dados são enviados, não necessariamente chega na mesma ordem. Por isso há o número de sequência.

O número de sequência permite que, independentemente da ordem em que os segmentos chegaram, o TCP organize os dados e os entregue de forma sequencial.
