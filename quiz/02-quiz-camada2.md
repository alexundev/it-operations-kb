# Quiz 02 - Camada 2 e Quadro Ethernet

**Resultado:** 9 de 10 (90%)

## Parte 1: Camada 2 (Enlace) e Visão de Troubleshooting

**1. A Camada 2 é dividida em duas subcamadas. Qual é a principal função da subcamada LLC?**

- [ ] A) Controlar o acesso físico ao cabo e evitar colisões.
- [x] B) Fazer a ponte e definir as regras de conversação entre a Camada 2 (Enlace) e a Camada 3 (Rede).
- [ ] C) Definir o Endereço MAC de 48 bits da placa de rede.
- [ ] D) Transmitir os dados em formato de luz ou pulsos elétricos.

**2. Em relação aos protocolos de acesso ao meio, qual a diferença fundamental entre eles?**

- [ ] A) O CSMA/CD atua em redes sem fio evitando colisões, enquanto o CSMA/CA atua em cabos detectando colisões.
- [ ] B) Ambos atuam apenas em redes Wi-Fi, mas o CD é para frequências 2.4GHz e o CA para 5GHz.
- [x] C) O CSMA/CD detecta colisões em redes cabeadas, enquanto o CSMA/CA tenta evitar colisões no ar em redes sem fio.
- [ ] D) O CSMA/CA atua no LLC e o CSMA/CD atua na Camada Física.

**3. Visão NOC: Se o sistema de monitoramento alertar um alto número de colisões em uma porta de Switch, qual é o diagnóstico inicial mais provável?**

- [ ] A) O servidor DHCP parou de distribuir IPs.
- [x] B) Incompatibilidade de negociação (Duplex Mismatch) ou defeito físico no cabo.
- [ ] C) A subcamada LLC travou no sistema operacional.
- [ ] D) Excesso de dispositivos conectados ao mesmo tempo no Access Point.

> *Nota de Troubleshooting:* Layer 1 First. Um problema físico gerando colisões detectadas na Camada 2.

**4. Visão NOC: Por que uma rede Wi-Fi sofre degradação de performance e aumento de latência quando há muitos usuários conectados simultaneamente no mesmo roteador?**

- [ ] A) Porque os IPs disponíveis se esgotam rapidamente.
- [ ] B) Porque o cabo de fibra ótica do provedor não suporta o tráfego.
- [x] C) Porque o protocolo CSMA/CA obriga os dispositivos a sinalizarem e esperarem o meio (o ar) ficar livre antes de transmitir, gerando um gargalo de espera.
- [ ] D) Porque as ondas de rádio começam a colidir fisicamente com o Bluetooth.

**5. O MAC (Media Access Control) é a subcamada inferior da Camada de Enlace. Com qual camada do Modelo OSI ela conversa diretamente para enviar os bits para a rede?**

- [ ] A) Camada 3 (Rede).
- [ ] B) Camada 4 (Transporte).
- [ ] C) Camada 7 (Aplicação).
- [x] D) Camada 1 (Física).

> *Nota:* O MAC conversa para baixo (Camada 1), e o LLC conversa para cima (Camada 3).

## Parte 2: O Quadro Ethernet e Endereçamento MAC (Tanenbaum)

**6. De acordo com a estrutura do quadro Ethernet, qual é o tamanho exato de um Endereço MAC (seja de Origem ou de Destino)?**

- [ ] A) 2 bytes (16 bits).
- [ ] B) 4 bytes (32 bits).
- [x] C) 6 bytes (48 bits). *Resposta correta*
- [ ] ~~D) 8 bytes (64 bits).~~ *Minha resposta*

> *Correção:* O quadro Ethernet inteiro deve ter no mínimo 64 bytes (usando "PAD" para encher espaço se necessário), mas o campo específico do MAC Address tem sempre 6 bytes.

**7. Logo após os endereços MAC no cabeçalho do quadro, existe um campo de 2 bytes chamado "Tipo" (ou EtherType). Para que ele serve?**

- [x] A) Para avisar qual protocolo da camada superior (ex: IPv4 ou ARP) está dentro do campo de "Dados" do pacote.
- [ ] B) Para identificar o fabricante da placa de rede (ex: Intel, Realtek).
- [ ] C) Para verificar se houve corrompimento de bits no cabo.
- [ ] D) Para informar se o computador está usando cabo ou Wi-Fi.

**8. Somando as caixinhas de "MAC de Destino", "MAC de Origem" e "Tipo", quantos bytes possui esse cabeçalho inicial que você vai procurar no tcpdump?**

- [ ] A) 8 bytes.
- [x] B) 14 bytes.
- [ ] C) 32 bytes.
- [ ] D) 64 bytes.

> *Nota:* Endereço de destino: 6 bytes | Endereço de origem: 6 bytes | Type ou Ethertype: 2 bytes.

**9. Como é representado visualmente, em formato hexadecimal, o Endereço MAC de "Broadcast" (aquele usado para enviar um quadro para todas as máquinas da rede local simultaneamente)?**

- [ ] A) `00:00:00:00:00:00`
- [ ] B) `255.255.255.255`
- [x] C) `FF:FF:FF:FF:FF:FF`
- [ ] D) `AA:BB:CC:DD:EE:FF`

> *Nota:* Broadcast significa enviar bits `1` para todas as posições (48 bits ligados). Em hexadecimal, isso se traduz em todos os campos "F".

**10. Imagine que a sua placa de rede acabou de receber um quadro. Ao ler os primeiros 12 bytes desse pacote, qual é a ordem exata de leitura das informações pelo padrão Ethernet?**

- [ ] A) Ela lê primeiro o MAC de Origem, e depois o MAC de Destino.
- [x] B) Ela lê primeiro o MAC de Destino, e depois o MAC de Origem.
- [ ] C) Ela lê primeiro o Tipo do protocolo, e depois os dois MACs.
- [ ] D) Ela lê os dados primeiro, e só depois verifica o endereço MAC.

> *Nota:* Ela lê o Destino primeiro para poupar processamento. Se o MAC não for o dela (ou não for Broadcast), ela descarta o pacote na mesma hora sem precisar ler o resto.
