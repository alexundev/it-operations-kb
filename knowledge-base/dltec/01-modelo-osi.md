# Modelo OSI: Camada Física e MAC

## 1. Camada 1 (Física)

- **Conceito:** Responsável pela transmissão de dados brutos (bits 0 e 1), transformando-os em sinais elétricos e vice-versa.
- **Visão de Troubleshooting:**
  - É o primeiro passo a se dar em quedas de link ou indisponibilidade de servidores ("Layer 1 first").
  
  - Quando um alarme de indisponibilidade é acionado, as verificações físicas incluem: verificar cabos rompidos ou desconectados, falha em transceiver, checar portas queimadas de Switch, Hub ou repetidores e falta de energia no equipamento.

## 2. Protocolos MAC

Regras de como os dispositivos "conversam" no meio físico sem que os dados colidam.

- **CSMA/CD (Collision Detection):** Protocolo que detecta as colisões e interrompe as transmissões, aguarda-se um tempo aleatório e o envio é refeito. Somente em redes cabeadas.

- **CSMA/CA (Collision Avoidance):** Protocolo que evita colisões no ar, através da espera, sinalizando a intenção de transmitir e aguardando o canal ficar livre. Somente em redes sem fio.

- **Visão de Troubleshooting:**
  - **CSMA/CD:** Utilizar a configuração de rede em Full-Duplex, que por sua vez já evita os problemas do Half-Duplex. Se o monitoramento apontar colisões, é por configuração incorreta (Duplex Mismatch), ou problema nos cabos.
  Se necessária uma infraestrutura de mais de 100m, configurar as portas do Hub/Repetidor (para aumentar o alcance) em Half-Duplex.
  
  - **CSMA/CA:** Como o protocolo obriga os dispositivos a esperarem o meio ficar livre, o primeiro passo do troubleshooting ao investigar lentidão no Wi-Fi é verificar a quantidade de dispositivos conectados simultaneamente. O teste prático para validar se o gargalo é a contenção do meio compartilhado consiste em isolar o teste (reduzir o número de aparelhos na rede) e verificar se a latência e a velocidade normalizam.
