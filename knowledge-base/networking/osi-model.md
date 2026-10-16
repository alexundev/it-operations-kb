# Modelo OSI

## Camada 1: Física

**Conceito:**

  Responsável pela transmissão de dados brutos (bits 0 e 1), transformando-os em sinais elétricos e vice-versa.

**Visão de Troubleshooting:**

- É o primeiro passo a se dar em quedas de link ou indisponibilidade de servidores ("Layer 1 first").
- Quando um alarme de indisponibilidade é acionado, as verificações físicas incluem: verificar cabos rompidos ou desconectados, falha em transceiver, checar portas queimadas de Switch, Hub ou repetidores e falta de energia no equipamento.

## Camada 2: Enlace

**Conceito:**

A Camada 2 é responsável por fazer a ligação entre as camadas. É subdividida em dois SubLayers, sendo eles: MAC e LLC.

- **MAC:** Define as regras de conversação entre a Camada 2 e a Camada 1, utilizando protocolos para detectar colisões (CSMA/CD) e evitar colisões (CSMA/CA).

  - **CSMA/CD (Collision Detection):** Protocolo que detecta as colisões e interrompe as transmissões, aguarda-se um tempo aleatório e o envio é refeito. Somente em redes cabeadas.

  - **CSMA/CA (Collision Avoidance):** Protocolo que evita colisões no ar, através da espera, sinalizando a intenção de transmitir e aguardando o canal ficar livre. Somente em redes sem fio.

- **LLC:** Define as regras de conversação entre a Camada 2 e a Camada 3

**Visão de Troubleshooting:**

- **CSMA/CD:** Utilizar a configuração de rede em Full-Duplex, que por sua vez já evita os problemas do Half-Duplex. Se o monitoramento apontar colisões, é por configuração incorreta (Duplex Mismatch), ou problema nos cabos.
Se necessária uma infraestrutura de mais de 100m, configurar as portas do Hub/Repetidor (para aumentar o alcance) em Half-Duplex.
  
- **CSMA/CA:** Como o protocolo obriga os dispositivos a esperarem o meio ficar livre, o primeiro passo do troubleshooting ao investigar lentidão no Wi-Fi é verificar a quantidade de dispositivos conectados simultaneamente. O teste prático para validar se o gargalo é a contenção do meio compartilhado consiste em isolar o teste (reduzir o número de aparelhos na rede) e verificar se a latência e a velocidade normalizam.

## Camada 3: Rede

**Conceito:**

  Responsável por fazer o endereçamento lógico (IP, seja o IPv4 ou IPv6) e enviar os dados, sem se preocupar se os dados chegarão intactos ou não.

**Visão de Troubleshooting:**

- **Sintoma:** Um computador não alcança um servidor em outra rede (o `ping` falhou e não sabemos onde a rede quebrou)
- **Ação de troubleshooting:** Abrir o terminal e utilizar o comando: `traceroute <IP_de_destino>`
- **O que procurar?:** O comando vai mostrar todos os roteadores. Desde a origem até o destino. Terão roteadores que não vão querer gastar energia, então só vão retornar "`***`", no entanto, é necessário prestar atenção, se a partir de determinado roteador, todas as rotas subsequentes mostrarem "`***`", sabemos que as rotas estão quebradas. A partir desse ponto saberemos o último roteador que funcionou, logo, temos noção de onde está o problema. É isso que precisamos procurar.

## Camada 4: Transporte

**Conceito:**

  Responsável pela segmentação e por garantir como a entrega será feita (com confirmação via TCP ou sem confirmação via UDP). Ela utiliza Portas lógicas para formar Sockets.

**Visão de Troubleshooting:**

- **Sintoma:** O `ping`funciona, mas não há conexão.
- **Ação de Troubleshooting:** Utilizar o comando `nc -zv <IP_de_destino> <Porta>
- **O que procurar?:** Caso a porta esteja funcionando, vai retornar "[tcp/ssh succeeded]", caso contrário vai aparecer que a porta falhou. Precisamos procurar a porta que falhou, para saber exatamente o que fazer.
